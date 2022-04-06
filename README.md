# Smart retrofit using the Shelly Dimmer 2

## Summary

This tutorial describes how to upgrade of an existing 3-way switch setup to a smart setup 
based on the Shelly 2 dimmer.

The setup I propose exhibits the following advantages:
- dimmable: lights can now be dimmed
- smart: you can now control lights via all apps and ecosystems compatible with Shelly devices
- minimally invasive: no additional wiring is needed; I reuse the existing traveller wires
- style-consistent: I use Leviton Decora switches of form factor identical to original setup
- invisible: the setup is indistinguishable from a non-smart one for users of the physical switches. 

This is a relatively simple project, accessible to most hobbyists, and inexpensive.

## Steps


### 1. Determine your power requirements

Survey your existing lighting and ensure that it absorbs a total power below 250W, which is the 
Shelly 2 dimmer’s output power rating. If you need to control lights in excess of that power 
such as candelabra with numerous bulbs, re-evaluate your installation. 

The easieast option is often to replace incandescent light bulbs with LED bulbs, which typically 
reduces power consumption by 90% and brings many installations within the 250W envelope.

### 2. Reverse engineer your existing setup

This step is crucial if you aren't the person who installed the original setup, or it is not well documented.

Safely examine the existing switches and wires to identify the hot and leg side, respectively, and identify the traveller wires. 

INSERT DIAGRAM HERE

The “before” diagram depicts the original setup I identified, which is a traditional 3-way switch 
configuration with two switches, albeit with a non-conventional wire colors.

Less experienced hobbyists should be aware that “hot side” and “leg side” are terms conventionally 
used to distinguish the two three-way switches, depending on whether their common wire is the live
or the switched output, respectively.

One way to identify the hot-side switch with a multimeter is to check that its common terminal, 
usually denoted by a black rather than brass screw, is always hot (i.e., at 120VAC) regardless 
of the switch position.  

By contrast, on the leg side, the voltage at the common terminal (i.e., whether it is hot or not)
depends on the switch position. 

Because this task is performed with the circuit energized, employ adequate safety precautions or
request the help of a licensed electrician.

I drew my “before” diagram to reflect faithfully my existing setup, including its color coding, 
even if non-standard. Specifically, I object to using white wires for travelers as hazardous, 
as white is conventionally reserved for neutral, whereas a traveler could be hot at any time. 
I chose to preserve the existing wiring but I marked white travellers with yellow tape at the 
endpoints for increased awareness and safety.

### 3. Replace the hot-side three-way switch with a momentary switch

Take a second to examine the “after” diagram and compare it against its “before” counterpart. 
You will replace each 3-way switch with a double-throw, center-off, momentary-contact switch. 

Notice that in the original setup, the full current absorbed by the lights flows through both 
switches any time the lights are on. By contrast, in the upgraded setup, switches only carry 
“up” and “down” signals to the SW1 and SW2 input terminals of the Shelly dimmer. 
Those are dry contacts, i.e., virtually no current will flow into them or from them.

To preserve style, you should be able to find switches that are virtually indistinguishable from the original. 
For example, my original setup used Leviton Decora switches. I replaced them with Leviton Decora 
Part Number 5657-2W switches, which are single-pole, double-throw, center-off, commercial grade, 
self-grounding rockers rated for 15A, 120/277V, and have the same form factor and color choices as the original.

Before wiring, use a multimeter to identify the “up” and “down” terminals of the momentary switches 
in relation to the top and bottom of the switch. At the risk of stating the obvious, the top is identified 
by TOP markings on the metal bracket.

Connect the travelers to the up and down terminals of the new, hot-side, momentary switch. 
In my setup, I chose to use the red and white traveler for the “up” and “down” signals, respectively.
Again, I mark my white travelers with yellow tape at the endpoints for safety.


### 4. Rewire the leg side

Remove the leg-side 3-way switch after tagging the wire attached to its common terminal. 
Feed each traveler originally going to it into two separate wire connectors or wire nuts.

Wire the new momentary switch with new, consistently colored travellers, going into the same
two connectors, carrying the “up” and “down” signals, respectively. In my case, red with red, 
white/yellow with white/yellow. 

Finally, connect the travelers carrying the “up” signal to terminal SW1 on the Shelly 2 dimmer,
and travelers carrying the “down” signal to terminal SW2.

Connect the switched output wire, originally attached to the common terminal on the 3-way switch, 
to the O terminal of the smart dimmer.

Complete the installation by feeding the live and neutral wires to the dimmer’s L and N terminals, respectively.


### 5. Test run

After verifying that all connections are consistent with the “after” diagram and that the overall setup 
is safe and compliant with applicable electrical code and regulations, energize the circuit at the breaker.

The Shelly dimmer should broadcast a new Wi-Fi network, of name starting with the “shellydimmer-” prefix. 
Use your laptop or phone to connect to this Wi-Fi network. 

If you are not experienced with configuring Shelly devices from a smart phone, pay special attention 
to messages on your phone complaining about the Wi-Fi not offering Internet connectivity and asking how to proceed. 

Ensure you choose the option to **remain connected** to the “shellydimmer-…” network 
even if it does not offer Internet connectivity. Do not disregard those messages, or your phone 
might revert to your residential Wi-Fi with no warning, thus disconnecting from the Shelly device 
and making it impossible for you to configure it.

On your laptop or smartphone, point a web browser to IP address 192.168.33.1 and configure the dimmer. 
Under “Settings” and “Button type”, select “dual button mode”.

Set the necessary credentials for the dimmer to connect to your residential Wi-Fi, then switch your laptop 
or smartphone to the same residential Wi-Fi network and use a browser to connect to the dimmer at its new IP address.
You might need to discover what IP that is by connecting to your router first. 

Ensure you let the dimmer download and install the latest firmware. 
This is not optional. 
In my personal experience, firmware upgrades played an important factor in resolving a phantom over-temperature shutdown issue.

Calibrate the dimmer by selecting the appropriate option under settings.

Select the “Leading edge” or “Trailing edge” calibration option as recommended by your lighting manufacturer. 
Many LED bulbs manufacturers recommend trailing edge switching.

Test proper operation from the app and from both control points.

A short press should toggle the lights on and off, regardless of whether you pressed the up or down buttons. 
Long presses will either dim the lights up or down, in the direction corresponding to the button you pressed.

Complete the cloud setup for your device as desired. 

Set up a schedule as desired.



## Conclusions

I enjoyed using the Shelly 2 dimmer to retrofit an existing set of porch lights, turning them into a programmable setup. 

I appreciate that the system is invisible to home occupants, who can continue to fully operate the system 
from its original control points without having to use any app and without any reduction in functionality.

The ability to create schedules is also very valuable to me. 

I can turn on my lights on at 30% brightness every day thirty minutes after sunset, and progressively reduces brightness till 11pm, when lights turn off completely. 

I also appreciate that Shelly devices are interoperable with a variety of home automation ecosystems, thus offering future-proof development options. I use Home Assistant, and Shelly device integrate with it very well.
