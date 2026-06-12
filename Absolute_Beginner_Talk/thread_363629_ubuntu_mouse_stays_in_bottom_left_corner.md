---
title: "ubuntu mouse stays in bottom left corner"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by trapperxjohn on 2007-02-17
Hey, I've been trying to use Ubuntu on a live CD to test it before I install it on my computer (Dell Latitude C610). I have recently found out that this particular model is difficult to get working with Ubuntu. When i run the OS on the live CD the mouse goes crazy and will retract to the bottom left of the screen. trying to move it only retracts back to the corner. 
I cannot even get it to work long enough to try and fix it through Ubuntu, the only way to stop it is to not use Ubuntu. I have tried switching the pointer stuff in bios and even fedora 6 live CD but the same thing happens. Is there anyone who has a solution to this extreme problem?
A reply would be fantastic.
-thanks

---

### Post by duality on 2007-02-17
Hi
i had the same problem, its because it should be configured to use ALPS touchpad, if its the touchpad that you are refering to.

I put this in /etc/X11/xorg.conf in the mouse and synaptic sections:

        Option          "SHMConfig"             "on"

Then I installed ksynaptic, since im on KDE, or gsynaptics for gnome:

sudo apt-get install gsynaptics             #gnome
sudo apt-get install ksynaptics             #kde


then restarted X with  ctrl+alt+backspace, then you can configure the touchpad in some control panel to enable ALPS and it wont move to the corner automatically.
gl

---

### Post by bodhi.zazen on 2007-02-17
I also had this same problem (on a different dell laptop).

I had trouble configuring the touch pad ...

My solution was to plug in an external mouse ... Problem solved :)

---

### Post by trapperxjohn on 2007-02-20
Hey, Im new and would need a step by step instruction on how to get the mouse to work. I do have an external mouse and that didnt help at all. I just freaks out with the external mouse too.- Thanks.

---

### Post by bodhi.zazen on 2007-02-20
> **trapperxjohn said:**
> Hey, Im new and would need a step by step instruction on how to get the mouse to work. I do have an external mouse and that didnt help at all. I just freaks out with the external mouse too.- Thanks.

In my case there was nothing to configure. I just plugged in the mouse and rebooted.

In your case, perhaps disable the touch pad ( add a # in the front of the lines in /etc/X11/xorg.conf)

HTH

---

### Post by trapperxjohn on 2007-02-27
Im still having trouble with the mouse on the pad and on an external mouse. I slowed the motion down by going into mouse settings but it still does the samething. I would apreciate help on what to do step by step because I wouldn't know how to do it otherwise. please help!

---

