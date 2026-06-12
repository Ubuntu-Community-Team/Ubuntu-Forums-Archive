---
title: "Can a kind someone give me step by step instructions on these Wireless drivers?"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by Frostshock on 2006-08-15
I would have posted this in networking, but I figured this belonged here since I'm a first time Linux user.

First things first, I'm trying to install the Ralink 2500 USb Chipset drivers for Linux for my D-Link DWL-G122 Rev. B1. I'm thinking as soon as I see them thank god, this should be simple, no fooling around with ndiswrapper.

I was wrong.

I've been trying to install them but being a first time Linux user I haven't gotten much farther than extracting the Tarball.

The Readme just confuses me, it's full of #'s and $'s. And it has steps for 2.4 Kernel and 2.6 kernel (but I think Ubuntu 6.06 is 2.6 kernel, according to GRUB). And at one point it says to type make, but make is apparantly not a bash command, so says the Terminal. ](*,) 

Now, I have a question about GRUB. Will I be unable to boot if I reformat the Ubuntu drive and reinstall Ubuntu on it right after, so I can get a fresh install and hopefully get directions on what to do so nothing bad goes wrong (not to mention I have an undeletable folder in Trash...)? GRUB is installed onto the MBR on my main hard drive. If something does go wrong, I know I insert the Windows CD, but what do I do from there to fix the MBR?

A million thank yous in advance to whoever is willing to walk me through this. And I really only know tar -xvzf, ls, and cd commands, so you'd need to be descriptive. Here are the drivers I'm trying to use:

[http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.7.0.tar.gz](http://www.ralinktech.com/drivers/Linux/RT25USB-SRC-V2.0.7.0.tar.gz)

Or should I be using something from here?

[http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page](http://rt2x00.serialmonkey.com/wiki/index.php/Main_Page)

I'm sorry I can't post the Driver's readme, but the file does not display right in Windows.

---

### Post by damianubuntu on 2006-08-15
Have a look at the wireless help page in my signature.  It should get you all the way....
If not post back.

good Luck

---

### Post by Frostshock on 2006-08-15
Hmmm....

[http://doc.gwos.org/index.php/RalinkDrivers](http://doc.gwos.org/index.php/RalinkDrivers) at the bottom says that Dapper Drake 6.0.4 has those drivers isntalled by default, tha would mean 6.06 has them as well...

But when I try to activate my wireless connection (it DOES see my Access Point) everything freezes and I need to power off.

What's happening?

---

### Post by Frostshock on 2006-08-15
Guess who's posting this from his Ubuntu desktop?

I took the Wireless Card out ad put it in after the ssytem started, it didn't freeze when activating. :D

I have no idea what I did, but I really want to thank you for taking the time to post and help me ^_^

---

### Post by damianubuntu on 2006-08-16
Sometimes for me on Xubuntu 6.06 activating the wireless causes a freeze. What I do is make sure the settings are correct, and then save and close and reboot.  During the reboot the wireless gets activated and everything is OK.
Seems like an awfully MS type of solution, but its the best I have so far:-)

---

### Post by Frostshock on 2006-08-16
Yup, I reinstalled Ubuntu because I had an undeletable folder in the trash, which meant if I had deletable files in there I couldn't use the "Empty trash" command and had to delete them from trash manually. Now I'm getting freezing on activation again.

I'll try a restart after putting in the settings like you said, if that doesn't work I'll retrace my steps from last time an just extract the drivers for my card, even though Ubuntu should have them already...

---

### Post by oldcity on 2006-08-16
re post #5 in this thread: 
"Sometimes for me on Xubuntu 6.06 activating the wireless causes a freeze. What I do is make sure the settings are correct, and then save and close and reboot. During the reboot the wireless gets activated and everything is OK."

How exactly are you doing this.
tia
oldcity

---

### Post by damianubuntu on 2006-08-17
> **oldcity said:**
> re post #5 in this thread: 
"Sometimes for me on Xubuntu 6.06 activating the wireless causes a freeze. What I do is make sure the settings are correct, and then save and close and reboot. During the reboot the wireless gets activated and everything is OK."

How exactly are you doing this.
tia
oldcity

Normally a variety of ways!  But the easiest is by using the networking GUI to check that the wireless device is recognised and OK.  (Mine is a USB wireless), Click on properties and check the ip address etc is configured OK.  If the device is showing as active, I deactivate it, if its already showing as inactive, I just check the ip address and gateway settings are correct and don't activate the device.  Click OK to save the settings and then reboot.

For me the problem (especially on first installing the device) was that because of the freeze on activate, I couldn't get the settings to stay registered.  I would freeze, and then have to force a reboot, whereupon the device would remain unconfigured.  This was you can configure teh device without risking the freeze.  Then I guess in reboot the activation happens at a different run-level (?) where whatever is causing the freeze isn't yet active.  (or soemthing like, guessing wildly in the dark!)

HTH

---

