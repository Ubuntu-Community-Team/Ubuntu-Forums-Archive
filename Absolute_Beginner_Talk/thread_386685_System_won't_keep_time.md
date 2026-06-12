---
title: "System won't keep time"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by bparham on 2007-03-17
Ok, here's the scenario, anytime I shut my system down, when I restart it; my time/date are always off, sometimes by a couple hours, other times by days. The system never connects to the server to update time, so it stays that way until I manually update the time. 

How can I correct this? Is there a setting that I can change to instruct the computer to check the time/date after every start? Not that it is of any help, but windows is having the same trouble. 

thanks... brad

---

### Post by AtrejuT on 2007-03-17
is that computer rather old? any chance the battery on the mainboard might be running empty?


atreju

---

### Post by bparham on 2007-03-17
It's a Dell Dimension, only about 2 years old or so. Yeah, i expect that is most likely the root cause, however, I was hoping for an easier solution where i could simply tell the computer to update the time each time it boots.

---

### Post by h0ax on 2007-03-17
Hey there,

I was having the same problem but I think I may have fixed it

Right click on the date -> Preferences, then Use UTC

Make sure your location is right.

hope this helps
--hoaX

---

### Post by Efwis on 2007-03-17
if the above doesn't help, replace your battery, you can get it for about $5 at any computer store, or even Radio Shack. Since this is causing Windows to screw, you need a new battery. Besides thats easier than doublechecking the time everytime you boot up the computer. 

Another point to look out for on this, if the battery is dead, you could end up scewing up your CMOS, in turn not being able to boot your computer. I have had to fix more computers with that issue because people were to lazy to replace a $5 battery, after I get done that $5 dollar battery change costs them an extra $30.

---

### Post by bparham on 2007-03-18
I have been paying a little more attention to the system, and it appears that the time is only thrown off when I boot into the other operating system. For instance, lets say I shut my system down at night and boot back into Ubuntu, the time is correct, now lets say that I shut the system down and boot into Windows instead, my time is off. This occurs in reverse as well. 

I have two separate hd, one with Window's and one with Ubuntu. Is there any reason that this set-up should cause problems with the time/date feature? 

I will go ahead and pick up a battery just in case, but I'm no longer sure that is the issue.

---

### Post by Sam Clemens on 2007-03-18
Sounds like Windows is setting the hardware clock to local time and linux is assuming it's set to UTC.

If it's possible to set Windows to use a hardware clock set to UTC that would be the best solution but I don't see how you do that.

Check /etc/default/rcS. If UTC is set to yes, try changing this to no

(sudo gedit /etc/default/rcS)

or a nastier solution: change your timezone in Windows or Linux to compensate (with all the ramifications that has).

The best solution is to fix Windows but I'm not sure how you do that.

---

### Post by Efwis on 2007-03-20
a few things to consider.

1. Are you in an area that uses Daylight savings time?
2. Is Windows not accurate with Daylight savings time?
3. Is Windows accurate with your time zone?

the reason I ask is because windows resets the computer's clock to what it sees. If you are using windows XP and didn't install the patch that was released a couple of weeks back, then it won't recognize the new Daylight savings time changes. (i.e. the date change for daylight savings time to start and end thanks to the people who bring you taxation.)

if you didn't get the patch for Windows when it was sent out, go to windows update and get it. If you have Win 98, Win ME, or Win 2k I have links to instructions on taking care of those operatings systems on my forums, you can find a link to my site in my profile, then click on the forums button. You can then do a search for daylights savings time in there.

---

### Post by mcduck on 2007-03-20
> **Sam Clemens said:**
> Sounds like Windows is setting the hardware clock to local time and linux is assuming it's set to UTC.

If it's possible to set Windows to use a hardware clock set to UTC that would be the best solution but I don't see how you do that.

Check /etc/default/rcS. If UTC is set to yes, try changing this to no

(sudo gedit /etc/default/rcS)

or a nastier solution: change your timezone in Windows or Linux to compensate (with all the ramifications that has).

The best solution is to fix Windows but I'm not sure how you do that.

Your on the tracks here, but the easiest way to solve the problem is to right-click on the clock applet in Ubuntu, select 'Properties' and then disable 'Use UTC' ;)

---

