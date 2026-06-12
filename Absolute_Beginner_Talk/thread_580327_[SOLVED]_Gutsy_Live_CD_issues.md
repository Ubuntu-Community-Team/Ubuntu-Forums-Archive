---
title: "[SOLVED] Gutsy Live CD issues"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Mike54 on 2007-10-18
A bit of background.  A month or so back, I tried a Feisty Live CD in a Dell XPS 410.  I was intrigued, so I set up a Wubi install of Feisty.  Everything has been working great.  The machine is an Intel E6300, with 1 GB of RAM, a 250 GB HD and a Radeon X1300 Pro video card.  It took some tweaking, but all media will play, screen resolution is 1280 X 1024 and my printer is set up.  In short, everything was working incredibly well.

I then set up a Wubi install of Feisty on an older Sony VAIO and when I realized it was time to be serious about Ubuntu, I wiped Windows off that machine and went with a full Feisty install.  Last weekend, I upgraded that machine to Gutsy RC and again, everything went well.  A minor tweak here and there and everything was working as I had hoped.

I then decided it might be time to wipe Windows off this XPS 410, so earlier today I downloaded and burned a Gutsy Live CD.  I actually booted an Athlon-based Dell with the Live CD, so I know everything is right with it.  (That machine responded better to Gutsy than it does to Feisty)  I also checked the disc in that machine and it came back as being 100% healthy.

This evening, I sat down in front of the XPS 410, inserted the Gutsy Live CD and started to boot from it.  When I got to the options screen, I realized my keyboard was not being recognized.  I couldn't use any of the function keys or the cursor keys.  I waited for the timeout, the kernel loaded and off we went.  I watched the progress bar move across the screen and the screen went dark for a couple of seconds.

Then suddenly, I was looking at two, alternating screens.  It would first display:

[CENTER] Analog Input
Cannot display this video mode
Optimum resolution 1280 X 1024 60 hz
[LEFT]
This would be centered on the monitor screen for a few seconds.  Then the screen would clear and display the following:

* Starting deferred execution scheduler atd [OK]
* Checking periodic command scheduler crond [OK]
* Checking battery status [OK]
* Running local boot scripts (/etc/rc.local) [OK}

These two screens would alternate ~6-8 times and then a dialog box in a third screen appeared, saying:

The display server has been shut down about 6 times in the last 90 seconds.  It is likely Something bad is going on.  Waiting for 2 minutes before trying again on display :0.

The machine would wait 2 minutes and then go back to the alternating screens, after which it would tell me it was going to wait another 2 minutes.

I've tried other Live CD's (Linux Mint, Simply MEPIS & Ubuntu Feisty) and they all boot up as they should.  When I got back to trying the Gutsy Live CD, the problem persists.

I'm really a newbie with Ubuntu, but this is the first real curve ball it has thrown me and I am at a loss.  (Ubuntu humbled me in a heartbeat)  I really would like to see how well Gutsy plays with this machine before going ahead with a full installation.

Does anyone have any suggestions for the new guy on the block?
[/LEFT]
[/CENTER]

---

### Post by johnn1949 on 2007-10-18
dell e1505 ati X1400 intel 7200 cpu

I get this same message and can't run live cd

Running local boot scripts (/etc/rc.local) [OK}

These two screens would alternate ~6-8 times and then a dialog box in a third screen appeared, saying:

The display server has been shut down about 6 times in the last 90 seconds. It is likely Something bad is going on. Waiting for 2 minutes before trying again on display :0.

The machine would wait 2 minutes and then go back to the alternating screens, after which it would tell me it was going to wait another 2 minutes.
John

---

### Post by Mike54 on 2007-10-19
> **johnn1949 said:**
> I get this same message and can't run live cd
While this tells me I am not alone in this, I am sorry to hear you are having the same problem, as no solution has been suggested thus far.  Maybe we will learn something today.

I found a Gutsy RC Live CD and tried booting with it and had the same problem.

I burned a PCLinuxOS Live CD last evening and can boot right up with it.  It appears there is something about Gutsy that my system does not particularly like.

---

### Post by imbjr on 2007-10-19
I have just experienced this too.

Try:

Alt+Ctrl+F1 and then at the prompt type:

sudo dpkg-reconfigure -phigh xserver-xorg

Select vesa and then the two lowest resolutions. When the system makes its attempt at starting the xserver again - it should boot up to a more recognisable deskop.

---

### Post by Jeffrey Magder on 2007-10-19
I had the same problem, this time with an ATI Xpress 1270.  In my case, the problem was that the default mode which was being used was incompatible with the loaded driver.  To get things working, I needed to make two changes to  [FONT="Courier New"]/etc/X11/xorg.conf[/FONT]:

[LIST=1]
[*]Modify the default resolution to 1024x768 (even though my screen is 1920x1200)
[*]Specify some mode hints. 
[/LIST]   
To modify the default resolution to 1024x768, I had to edit the section:
 
[INDENT][FONT="Courier New"]Section "Screen"[/FONT][/INDENT]

so that it contained:

[INDENT][FONT="Courier New"]Modes "1024x768"[/FONT][/INDENT]

The actual mode may differ for you depending on your screen, but I believe that should work.

To specify mode hints, I had to edit the section:

[INDENT][FONT="Courier New"]Section "Screen"[/FONT][/INDENT]

By adding the following:

[INDENT][FONT="Courier New"]HorizSync   36-60
VertRefresh 36-60[/FONT][/INDENT]

When that is done, wait for GDM to automatically restart.   **Don't** use [FONT="Courier New"]/etc/init.d/gdm restart[/FONT], unless you want to see the installer try to start a second GDM instance.   Its a pain, but it should work.  Let me know how it goes!  :-)

---

### Post by Mike54 on 2007-10-19
> **imbjr said:**
> I have just experienced this too.

Try:

Alt+Ctrl+F1 and then at the prompt type:

sudo dpkg-reconfigure -phigh xserver-xorg

Select vesa and then the two lowest resolutions. When the system makes its attempt at starting the xserver again - it should boot up to a more recognisable deskop.
And it did exactly that!  Many thanks for your help.

---

### Post by johnn1949 on 2007-10-20
I tried it again with 800X600 and1224X768 with a new live cd.  Same thing happened and I can't get to a command prompt.

I still need help. thanks.

---

### Post by nuggib on 2007-10-20
This is good info, my XPS 410 is doing the exaxt same thing.

Concerning the keyboard issue, upgrading the BIOS to the latest version solved that problem for me.

---

