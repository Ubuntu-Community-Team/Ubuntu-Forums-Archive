---
title: "[SOLVED] Desperate: problems with xserver"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by c3genesis on 2007-08-23
Okay.  I will try anything.  I bought this computer last week, hoping to install ubuntu/kubuntu and rid myself of linux.  This was not the case however.  I started by partitioning my harddrive.  Im completely new to this so please dont criticise.  I cloned my harddrive and formatted the primary logical slot to linux ext 2 thinking that it would need to go in the primary partition.  This is all I did before installing, so please let me know if im skipping a step.  I restarted the computer and went into the boot menu to start kubuntu since vista wont recognize the live-cd.  When i went to install it, it would stop halfway and take me out to a black screen where i could do nothing.  So quickly I was ready to give up, then I decided to try my regular copy of ubuntu thinking maybe there was a defect with the kubuntu cd.  I thought maybe i was making it alot harder than it actually is, so my first attempt was to simply pop the cd in and restart and try to install it(my computer is back to factory settings, all partitions have been deleted)  after getting through the install process, it sends me immediately to an error screen saying failed to start the x-server.  if you want more detailed information check out this persons thread, my problem is almost identical to his.  [http://ubuntuforums.org/showthread.php?t=493273](http://ubuntuforums.org/showthread.php?t=493273)
I tried many different approaches listed in different threads as this seems to be a common problem with ati  graphics cards.  But considering that I am so new to this I am not surprised that nothing has come of my efforts.  Im getting very frustrated and I really need someone patient that can walk me through this.  Ive done several different commands to get into xserver reconfig.  Changed everything to suit my computer and things keep going awry.  Ive also tried installing an nvidia driver?  that was also unsuccessful.  Please!  someone help!

---

### Post by w4ett on 2007-08-23
From the command line interface (CLI) type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "vesa" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:
```
startx
```

 to restart X.

---

### Post by c3genesis on 2007-08-23
Okay. Before it was automàtically taking me to a command screen where i was entering my commands. I dont know whats changed but its not taking me there automàtically anymore. What ways are there to get there?

---

### Post by w4ett on 2007-08-23
From the Grub boot menus, select "recovery mode" this will take you to a Command Line

---

### Post by c3genesis on 2007-08-23
The only thing i can hey into from there is the windows command prompt.
And sudo commands arent recognized there

---

### Post by w4ett on 2007-08-23
It is probably taking to to the Login prompt...Login with your username and password  (Note: you will not see your password characters echo'd on the screen...as an additional security layer it is blank, just type your password in normally then hit <enter>

then type in the command:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

as stated before.

---

### Post by c3genesis on 2007-08-23
Okay, i did what you said and when i restarted x it has EE's at the bottom: vesa(0): no matching modes
:screen(s) found but none have a usable configuration.

Fatal server error: no screens found what am i doing wrong. I entered the screen resolutions that my còmputer accepts. Should i only have 1?

---

### Post by w4ett on 2007-08-23
> **c3genesis said:**
> Okay, i did what you said and when i restarted x it has EE's at the bottom: vesa(0): no matching modes
:screen(s) found but none have a usable configuration.

Fatal server error: no screens found what am i doing wrong. I entered the screen resolutions that my còmputer accepts. Should i only have 1?

What video card/chipset  are you using?

---

### Post by c3genesis on 2007-08-23
Ati radeon x1200

---

### Post by w4ett on 2007-08-23
So, if I am reading your initial post correctly....you WERE able to run the live CD ok....OR did you use safe graphics mode to get to the GUI desktop?  Then this problem is happening when you attempt to boot from your HDD install of Ubuntu?  Sorry to be repetitive, but I am trying to get the underlying problem clear in my mind.

---

### Post by c3genesis on 2007-08-23
Sorry. I have yet to even see the gui desktop. I go to the boot screen and choose the option start or install and during this process ús when i recieve the errors.

---

### Post by w4ett on 2007-08-23
From that initial screen, select safe graphics mode and boot the live cd

---

### Post by c3genesis on 2007-08-23
Same results. Thats where ive been putting in my commands after it gives me the error there it let me use a command prompt

---

### Post by w4ett on 2007-08-23
OK were getting somewhere then.......what it sounds like you are going to have to do is download the Alternate Install CD, which uses a text based installer, and install Ubuntu that way.   Some of the newer boards are not yet fully supported by the live cd so the alternate install method must be used.  the Download is here:

[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

Tic the box below "Start Download" to select the Alternate Install CD

---

### Post by c3genesis on 2007-08-23
Ill let you know how it turns out tomorrow. Im stuck at work til 5am. Thanks for all your help thus far

---

### Post by jeff_p on 2007-08-24
Hello,

I am having the same problem.  ATI video card, with a "Screen(s) found, but none have a usable configuration" error preventing X from starting up.

I have installed ubuntu from the alternate install CD.  Everything seems to be working..I set the driver to "vesa" and everything.

The machine I am using is an Inspiron 1521, and it is fully functional.

It seems like there is some piece of coniguration missing...can someone help me fill in the bits?

---

### Post by smo0th on 2007-08-27
I have the same problem I'm running an old AMD K6-2 450 PC and it comes with a generic PCI video card, X server displays the following error:

Fatal server error:
no screens found
XIO: fatal IO error 104 (Connection reset by peer) on X server ":0.0"
        after 0 requests (0 known processed) with 0 events remaining.

...what can I do???  :confused:

---

### Post by smo0th on 2007-08-27
well... well..... I run an old AMD K6-2 450 with a generic PCI trashy video card, my problem was that the card was not able to display the default 24-bit graphic mode LOL.... so here's a recreation of what I did... 

first get into command shell mode and do the "sudo dpkg-reconfigure xserver-xorg" thing...

now type "sudo nano /etc/X11/xorg.conf"

scroll way down to the line where says DefaultDepth      24

I changed it for 16... you may play along with the values there but always keep a backup file before modifying anything.... just in case ;)

c-ya.

---

