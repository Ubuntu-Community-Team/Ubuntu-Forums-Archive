---
title: "wondering if install cd is corrupt (maybe cos of incomplete download)"
date: 2007-07-17
forum: Absolute Beginner Talk
---

### Post by intransit on 2007-07-17
Hey all,

New to Ubuntu, just thinking of trying it out now so i downloaded the iso file from the website

Anyway, before I go about arranging dual boot for this actual computer, I just want to install it on a virtual pc and have a play around with it first. So anyway, i'm using Virtual PC 2007, and I get the cd to boot and it loads the screen where you get those options
start or install
start ubuntu in sgm
...
check cd for defects
...
etc

anyway so when i select check cd for defects this msg pops up
title: Boot Loader
"Could not find kernel image: lesystem.manifest-desktopPX$"
[OK]

So should I take it that the disk has defects? I was downloading from firefox and it was on about 540 mb or so and it had taken about 1:30-45 mins, then i think it may have jumped the rest and lost it. Funny thing is i can open the iso file in WinRAR and see files fine no corrupt message, but i'm not entirely sure how iso's work maybe its different to archives.

Anyway when I select to start or install ubuntu I get this output
Booting from local disk...
isolinux: Disk error 80, AX = 0201, drive 00

Boot failed: press a key to retry...

Just my last question, if it is like I thought and the download was dodgy, can you reccomend a download program or something to ensure it doesn't happen again? Firefox says it is complete, but maybe its not?

---

### Post by intransit on 2007-07-17
ok stupid i should've thought a bit more

i right click on the iso file just on my normal desktop check how big it is
its 495 MB
so i'm pretty sure it must be missing a bit


so maybe this post should change to how can I ensure it doesn't happen again?

---

### Post by oilchangeguy on 2007-07-17
you may want to read this:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by intransit on 2007-07-17
just while your here...lol

i'm also following

[https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004](https://help.ubuntu.com/community/HowToConfigureUbuntuForMicrosoftVirtualPC2004)


so these  are the steps i understand i am to take

Microsoft Virtual PC 2007 and Ubuntu 6.10

For Microsoft Virtual PC 2007 and Ubuntu 6.10 do the following:

1. Install from ubuntu-6.10-alternate-i386.iso and complete the installation.

2. Hit the Esc key when the GRUB loader appears after reboot and boot into recovery mode.

3. Run dpkg-reconfigure xserver-xorg and leave all the default settings as below except set color depth to 16.

4. Send Ctrl+Alt+Del to reboot once it's done and you should be set. 

Interrupt the reboot at the GRUB prompt and select the (recovery mode) option

5. When the system restarts, the GRUB loader briefly appears. Immediately hit escape, then the down arrow to select the recovery mode option. It will read something like "Ubuntu, kernel 2.6.15-23-386 (recovery mode)". Then press "Enter". Ubuntu will boot into a console text mode.
Edit the xorg.conf file to fix the color depth

6. Read the instruction below under the Video heading to change the default color depth. 


--------
I think this is what i'm meant to do

cool, not too sure if i still have to do it in virtual pc 2007 but probably worthwhile anyway.

---

### Post by intransit on 2007-07-17
oilchangeguy,

muchos gracias

---

### Post by sancho panza on 2007-07-17
> **intransit said:**
> ok stupid i should've thought a bit more

i right click on the iso file just on my normal desktop check how big it is
its 495 MB
so i'm pretty sure it must be missing a bit


so maybe this post should change to how can I ensure it doesn't happen again?

Hey, before you burn the cd, make sure you [read this]("https://help.ubuntu.com/community/HowToMD5SUM?highlight=%28checksum%29").
Even if the file sizes match, the iso file maybe corrupt. Checksum is the way to verify if the download was correct. Then burn the iso to the cd.

---

