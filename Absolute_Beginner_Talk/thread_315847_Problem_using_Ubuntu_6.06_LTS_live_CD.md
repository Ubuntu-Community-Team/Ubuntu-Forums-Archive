---
title: "Problem using Ubuntu 6.06 LTS live CD"
date: 2006-12-09
forum: Absolute Beginner Talk
---

### Post by fizikz on 2006-12-09
The Ubuntu 6.06LTS live CD is not working when I choose to "Start/install Ubuntu". It goes through the loading phase, only to hang on a blank screen when the graphical interface would usually come on. At this point I can only hard-shut down the PC. Only "Start in graphics safe mode" works on my system. I already used the option to verify that the CD is ok, and it checks out fine. 

When in "graphics safe mode", I noticed a few things don't work: I can't change the screen resolution from 1024x768 to any other setting. I also can't read my hard drive (it says error mounting sd1, or something like that). 

I also tried booting an older PIII 450, 384MB ram system, and it was able to boot with the "Start/install Ubuntu" option, so I guess the problem is system specific. For your reference my system is as follows:

Athlon 64 3200+ (2.0Ghz winchester)
1GB RAM 
Asus A8V-Deluxe (VIA based)
ATI X850XT
Creative Audigy 4

---

### Post by meng on 2006-12-09
You probably can't change the screen res because you're in safe graphics mode (as an analogy, think of when you boot Windows in safe mode, your options are limited even more than that). The error mounting sda1 (or whatever) probably has nothing to do with safe graphics mode, my guess is that you're double clicking on a device expecting pmount to play nice when things aren't configured to allow that.

Perhaps you could explain what you're trying to achieve (e.g., do you want to continue to use the LiveCD intermittently as an alternative to Windows, or are you interested in a permanent install, and if so, do you want to dual-boot with Windows or replace Windows?)

A permanent install should allow you to solve these problems permanently.

---

### Post by igknighted on 2006-12-09
The problem is your graphics card.  The liveCD has issues with some graphics cards (especially ATI), but once you install you can then install the proper drivers (not included on the live CD because they are proprietary) and it will work just fine.  When I used an ATI card (essentially the same one you have) I could never use the live CD either, so I always installed from the alternate disc, then booted in recovery mode, and then installed the fglrx driver from the repositories.  Then reboot normally and its good to go.

---

### Post by fizikz on 2006-12-09
Well, I eventually want to dual boot, but right now is not a good time for me to start that project. I was hoping to use the live CD to get a bit more familiar with Ubuntu. I'm completely new to Ubuntu, and my linux knowledge is rather limited.

From igknighted's response, it would appear that my problem with the live CD could stem from my ATI graphics card, possibly with no solution without a permanent install. 

meng said "my guess is that you're double clicking on a device expecting pmount to play nice when things aren't configured to allow that"

Could you explain what I need to do (assuming it's possible with the live CD)? I was hoping to access some documents, video and musics files to get a feel for how it would be in Ubuntu.

---

### Post by igknighted on 2006-12-09
You could try this... start Ubuntu and wait for it to hang.  Then hit ctrl-alt-F1.  This should tke you to a text-only terminal.  Now type:
```
sudo nano /etc/X11/xorg.conf
```
This should open a terminal text editor with a large file.  Scroll down a ways until you see the line: Section "Device"

In the section, there should be a line that says 'driver "ati"'.  Change 'ati' to 'radeon'.

Then hit ctrl-o to save, then enter to confirm, then ctrl-x to exit the editor.  Finally, type startx and hopefully your GUI will load as it should.

---

### Post by fizikz on 2006-12-09
When it hangs, nothing works. Period. I can only press the hard-reboot button or hold the shut down button for 3 seconds. 
When in safe graphics mode, after the the liveCD loads (the Ubuntu splash screen with the progress bar), it momentarily goes to a blank screen, after which the Ubuntu user interface appears. But when I try to the "Start/install Ubuntu" option, it get stuck right at that blank screen, before I have a chance to do anything at all. 

One thing I noticed is that at the screen where you choose the "Start/install Ubuntu" or safe graphics mode loading options, there is the possiblility of loading with command line options. I read the help file a bit, and tried a few option, but to no avail. I wonder if your suggestion could be applied at that stage.

EDIT: I would also like to mention that I also tried the 64 bit edition Live CD, and that it would not boot at all, even in safe graphics mode. Since I have a 64 bit processor, I thought it might be advantageous to try a 64 bit OS. What could I try to get it to work?

---

