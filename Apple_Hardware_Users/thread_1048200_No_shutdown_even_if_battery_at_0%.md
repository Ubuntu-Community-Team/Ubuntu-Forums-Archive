---
title: "No shutdown even if battery at 0%"
date: 2009-01-23
forum: Apple Hardware Users
---

### Post by linux_user_ on 2009-01-23
I've been using intrepid on my MacBookPro 4,1 for a month with no problem, until today. Here's what happened:
Yesterday I worked on OSX and shut down the Mac when the battery was very low.
Today I booted Ubuntu, and saw the battery icon empty, moved the mouse over the icon and the tooltip said "Battery 0.0%", so I expected the computer to shutdown, but it did not happen...
I also clicked on "Power history" and the battery voltage was 9.4V, and "Charge history" option in "Graph type" wasn't present so I couldn't look at the battery percentage graph. It also looked like the graph were freezed, since I waited more than one minute but did not change.
So I rebooted the computer, but it hanged during last stage (after the Ubuntu logo with progress bar completed) with screen off but fans on.
I forced shutdown holding the power button, and tried to turn on the computer again but didn't work until I plugged the power cable.

I guess power management has some bug when the mac is booted with a battery level very close to 0%.

---

### Post by cyberdork33 on 2009-01-23
it sounds like the smc needed a reset.
[http://support.apple.com/kb/HT1411](http://support.apple.com/kb/HT1411)

---

