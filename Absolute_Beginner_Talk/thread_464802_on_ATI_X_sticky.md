---
title: "? on ATI X**** sticky"
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by snipes23 on 2007-06-05
k I did the sticky above for Ati cards, and it says to reboot at the.  Sorry for bein a noob, but how do u reboot?

I used sudo killall gdm, then sudo gdm.  I don't know if this is the right way, because when I did that I get a black screen and a thing from the monitor saying "Signal is not compatible with this input" and monitor goes from 60hz to 85hz I believe it was.  Any help appreciated

Darn Ati cards


Have x1800xt, don't know if that matters

---

### Post by mcduck on 2007-06-05
To reboot from a terminal, just use command 'sudo reboot'. ('sudo halt' would shut down the computer).

Killing GDM and restarting it will only reload your graphical environment. And better way to do that would be 'sudo /etc/init.d/gdm restart'

---

### Post by snipes23 on 2007-06-05
is it just sudo reboot, or reboot?  Reinstallin ubuntu, would like to know so I can do this right.

---

### Post by snipes23 on 2007-06-05
k thats what i figured, so hopefully after i reinstall, do sudo reboot rather than what I did, it will work.  Crossing my fingers, been tryin to get this and fedora installed for like the past 3 days with no luck.  If anyone knows of any other things I may need to try for an ati x1800 card please share.  Thanks, mike

---

### Post by snipes23 on 2007-06-05
quick question, one site suggested installing xp/linux dual boot as fat32 system, should I try that? Thanks

---

### Post by mcduck on 2007-06-05
> **snipes23 said:**
> quick question, one site suggested installing xp/linux dual boot as fat32 system, should I try that? Thanks
I believe the NTFS driver for linux works fairly nice today, and XP really works better on NTFS than on FAT partition. (and Ubuntu needs some real Linux filesystem).

If you need read/write access to your windows partition, and you don't trust the fairly new Linux NTFS driver, use FAT. In any other case go for NTFS.

---

### Post by tantradallastexas on 2007-07-24
I  followed the ATI sticky in the Absolute Beginner Talk and it broke my system. Right now I am up because I am running from a live CD.. but heck I really am a Noob and I dont know how to undo what I did - and I dont want to reinstall Ubuntu if I dont have to. I would rather just revert to the original settings. I am running Feisty Fawn 7.04 on a HP ze5185 laptop. 

Can someone help me out. 

I need literally if you will step by step command line instructions because once i restart the machine I have no GUI - just goes to the black screen and says "no device detected" 
"no screens found". 

This machine has a ATI Technologies Inc Radeon Mobility M6 LY VGA compatible controller (if thats is any help). 

I was trying to upgrade from the working default driver installed with the standard ubuntu install because it did not allow me to change the screen resolution. However it WAS working so if nothing else can someone help me get back to that?

Thank you,
Lynna


Yes, a female running a Linux box

---

### Post by Brian96 on 2007-07-24
> **snipes23 said:**
> is it just sudo reboot, or reboot?  Reinstallin ubuntu, would like to know so I can do this right.

sudo reboot

Shutting down and restarting the computer require root privileges, which sudo emulates.

---

### Post by Brian96 on 2007-07-24
> **tantradallastexas said:**
> I  followed the ATI sticky in the Absolute Beginner Talk and it broke my system. Right now I am up because I am running from a live CD.. but heck I really am a Noob and I dont know how to undo what I did - and I dont want to reinstall Ubuntu if I dont have to. I would rather just revert to the original settings. I am running Feisty Fawn 7.04 on a HP ze5185 laptop. 

Can someone help me out. 

I need literally if you will step by step command line instructions because once i restart the machine I have no GUI - just goes to the black screen and says "no device detected" 
"no screens found". 

This machine has a ATI Technologies Inc Radeon Mobility M6 LY VGA compatible controller (if thats is any help). 

I was trying to upgrade from the working default driver installed with the standard ubuntu install because it did not allow me to change the screen resolution. However it WAS working so if nothing else can someone help me get back to that?

Thank you,
Lynna


Yes, a female running a Linux box

Which sticky did you follow? Can you post a link?

I'm a noob as well, but if it were me, this is what I would try first:

1. Reboot the computer, and select the "failsafe" option (or recovery mode or whatever it is called) in GRUB.
2. It will boot to a command line prompt that says root@[yourcomputer].
3. At the command prompt type "dpkg-reconfigure xserver-xorg" (you normall have to run this as root with the "sudo" command first, but if you boot to recovery mode it gives you a root prompt)
4. In the xorg setup that appears, select "fglrx" when it gives you the list of drivers. When it gives you the list of screen resolutions be sure to tick the box next to the one for your display's native resolution. For most of the other options you can accept the default.

When that finishes try rebooting normally and let us know what happens. Oh, and this assumes that in the tutorial you followed you already enabled the ATI restricted drivers. If you haven't, select "ATI" from the xorg drivers list. You'll then have to go back and try to follow the tutorial instructions again.

Hope this helps.

---

### Post by tantradallastexas on 2007-07-24
> **Brian96 said:**
> Which sticky did you follow? Can you post a link?

I'm a noob as well, but if it were me, this is what I would try first:

1. Reboot the computer, and select the "failsafe" option (or recovery mode or whatever it is called) in GRUB.
2. It will boot to a command line prompt that says root@[yourcomputer].
3. At the command prompt type "dpkg-reconfigure xserver-xorg" (you normall have to run this as root with the "sudo" command first, but if you boot to recovery mode it gives you a root prompt)
4. In the xorg setup that appears, select "fglrx" when it gives you the list of drivers. When it gives you the list of screen resolutions be sure to tick the box next to the one for your display's native resolution. For most of the other options you can accept the default.

When that finishes try rebooting normally and let us know what happens. Oh, and this assumes that in the tutorial you followed you already enabled the ATI restricted drivers. If you haven't, select "ATI" from the xorg drivers list. You'll then have to go back and try to follow the tutorial instructions again.
Hope this helps.


Thank you - the sticky I followed is found at [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

i will follow your  instructions but i am fairly new to Linux and not so knowledgeable - about how to go into 'recovery' mode or enabling  ATI drivers. I followed the directions in the sticky and now when it boots up, it shuts down ..........to the black screen with the prompt. 
 command line.. yes i can login there.. but i dont know my way around linux commands and file systems well enough to know how to move / copy and undo 'blind'.. - I am such a wimp.
Need a GUI

thanks again,
Lynna

---

### Post by Brian96 on 2007-07-24
> **tantradallastexas said:**
> Thank you - the sticky I followed is found at [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

i will follow your  instructions but i am fairly new to Linux and not so knowledgeable - about how to go into 'recovery' mode or enabling  ATI drivers. I followed the directions in the sticky and now when it boots up, it shuts down ..........to the black screen with the prompt. 
 command line.. yes i can login there.. but i dont know my way around linux commands and file systems well enough to know how to move / copy and undo 'blind'.. - I am such a wimp.
Need a GUI

thanks again,
Lynna

Okay, what problem were you having that you decided to use that sticky?

I also have an ATI card, and the first time I installed Ubuntu, after I rebooted it gave me a popup message about restricted drivers. In this instance there is usally a flashing icon in the top right of the screen. You click on it and it takes you to the Restricted Drivers Manager (which you can also get to through the System menu). In there you click on the ATI proprietary drivers, it installs them, and then you reboot.

My previous instructions assumed that you cannot get to a command prompt. If you can get to a command prompt just type "sudo dpkg-reconfigure xserver-xorg". Then follow the other instructions. If you are not sure whether you have enabled the proprietary ATI drivers, then tick "ATI" instead of "fglrx" at that prompt. (I promise this will all make sense when you get into the dialog.) Also be sure to tick the box for whatever your display's native resolution is.

After this you *should* be able to get into a GUI. From there you may need to start over with figuring out how to enable the proprietary ATI drivers (if you even need them--not everyone does). If you can't get to the GUI after that just come back and let us know!

---

### Post by Brian96 on 2007-07-25
> **tantradallastexas said:**
> Thank you - the sticky I followed is found at [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

i will follow your  instructions but i am fairly new to Linux and not so knowledgeable - about how to go into 'recovery' mode or enabling  ATI drivers. I followed the directions in the sticky and now when it boots up, it shuts down ..........to the black screen with the prompt. 
 command line.. yes i can login there.. but i dont know my way around linux commands and file systems well enough to know how to move / copy and undo 'blind'.. - I am such a wimp.
Need a GUI

thanks again,
Lynna

Any luck yet?

---

