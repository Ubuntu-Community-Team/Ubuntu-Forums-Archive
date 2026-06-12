---
title: "cant get Ubuntu to run"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by boon72 on 2007-04-01
Ok this is my first post, iv tried several attempts (and versions) to get this on a old pc to no avail.

the pc is as below

Celeron 800mhz
512mb sdram
20gb quantum fireball
dvd rom
pci ATI 9000 gfx (onboard turned off)

each version says its installing, 1 even finished. but they all stop with a black screen with a white underscore in the top left corner.

ive tried 5.10, 6.06 & just downloaded 6.10.

any ideas?

---

### Post by joshbax on 2007-04-01
see what 6.10 throws up.

but apart from that, could be a gfx problem. try installing with the onboard to start with maybe?

---

### Post by overdrank on 2007-04-01
> **boon72 said:**
> Ok this is my first post, iv tried several attempts (and versions) to get this on a old pc to no avail.

the pc is as below

Celeron 800mhz
512mb sdram
20gb quantum fireball
dvd rom
pci ATI 9000 gfx (onboard turned off)

each version says its installing, 1 even finished. but they all stop with a black screen with a white underscore in the top left corner.

ive tried 5.10, 6.06 & just downloaded 6.10.

any ideas?

Hi and welcome, The one installation that finished, did it ask to restart and remove the live cd? If it did and you rebooted,:-k  did it not start ubuntu?

---

### Post by boon72 on 2007-04-01
yes it said to remove the cd while it rebooted, but that was it. after it rebooted it starts of with the brown ubuntu screen stuff and the list says its doing things and then it will go to the black screen n stay there.

---

### Post by Woody@N87 on 2007-04-01
Just as an FYI, it's not the horsepower of your computer, I'm on a 550 mghrtz with 256 of ram.  6.10 is running fine.

---

### Post by rillip on 2007-04-01
Do you get a GRUB interface at startup?  If so, have you tried the recovery mode?

I had somehing similair happen when xserver-xorg couldn't start because I ran myself completely out of disk space.  I was able to get to the login prompt at least, so I'm not confident it's the same, but it could be.

You say it takes you to a black screen with a white underscore.  That sounds to me like a terminal cursor.  Try typing a command like ps, and see if it lets you do anything.  Maybe it's dumping you to a terminal session in single suer mode (agian, possibly due to disk space).

---

### Post by pxwpxw on 2007-04-01
> **boon72 said:**
> yes it said to remove the cd while it rebooted, but that was it. after it rebooted it starts of with the brown ubuntu screen stuff and the list says its doing things and then it will go to the black screen n stay there.

After it stops at the black screen
try the 3 keys  
control alt F1
and see if a text screen comes up.

---

### Post by boon72 on 2007-04-01
nope, nothin happens

---

### Post by Bartender on 2007-04-01
One thing you could try is removing the ATI card, going into BIOS, and setting the PC to use onboard.  ATI cards are often problematic.  This would be a relatively easy way to check and see if that's the issue.
Did you check the CD on another PC?  Did you burn it slowly?

---

### Post by pxwpxw on 2007-04-01
If you have tried all of the above and nothing works, you can use the ubuntu 610 Alternate CD and select the "rescue" option from the CD startup menu.
It runs in text mode. That should let confirm if your install completed except for the graphics.

The alternate CD also has the option for a "cli" install, command line, no graphics.

A desktop package can be installed separately later.

---

### Post by boon72 on 2007-04-01
ive not tried that, but i have just downloaded and installed the server version. and it installed and i have a command prompt which seems to work (although i have no idea what to tdo :-)

---

### Post by pxwpxw on 2007-04-02
OK thats established that the Server CD install works, and the problem was possibly due to the Xwindows/graphics configuration, as already suggested above.

I think there is an option in the server install (in the later stages) to
install a desktop, did you see it.

Edit: looking at the Server CD now, cant see any desktop option so far.

I think the easiest thing to do is try another Alternate CD  reinstall, this time with desktop, if there is a problem with graphics after restart it should either drop you back to a command line console, or allow you to get a console by Alt + Contol + F1, (or F2.....F6). Then you can check log and configuration files,  
( /var/log/Xorg.0.log and /etc/X11/xorg.conf ) and post them here for help.

If you are unable to get a console from an installed Xwindows and desktop system, then the Alternate CD and the Server CD have Recovery or Rescue options, which should allow you to do what is needed, but from a command line text console, when Xwindows is not working. Dont use the Desktop CD here.

Edit2:
Installed ubuntu610 server, now installing xubuntu-desktop, 290 MB download, 1020 MB disk space required.
Will see how that goes.
Installed xubuntu-desktop this is it. 
Done using oldibm - celeron 700Mhz, nvida mx100, 512MB ram.

Questions?

---

### Post by codewarrior00007 on 2007-04-03
> **paul capps said:**
> Hi and welcome, The one installation that finished, did it ask to restart and remove the live cd? If it did and you rebooted,:-k  did it not start ubuntu?

Hi, I figured I should continue this thread instead of opening a new one.  My install both regular and safe for 6.0 LTS has been grinding my HDD.  I did see the initial splash and then some icons appeared on the splash.  But after that screen went blank and I only see a cursor.  Please assist.  My 1st time playing with Linux install.  I followed the dowload, hash check, and burning instructions to the letter.  What gives?? :confused:

Edit: I'm trying to install Desktop version'

---

### Post by pxwpxw on 2007-04-03
> **codewarrior00007 said:**
> 
 My install both regular and safe for 6.0 LTS has been grinding my HDD. 
 I did see the initial splash and then some icons appeared on the splash. 
 But after that screen went blank and I only see a cursor. 


Could you clarify that. Are you able to complete the install,  restart,  and get the blank screen after a minute or so  (i.e. not immediately).

 If so, try the  control + alt + F1 keys to get a text console and if that works, next step.
If not read through the above.

Post the result here anyway.

---

### Post by codewarrior00007 on 2007-04-03
Hi,

Sorry for being vague. :popcorn: 

Here is what the problem is.  I'm trying to install and run Ubuntu on a machine which had W2K installed on it.

I've:

1. Created a CD of 6.06 LTS and it has been hashed successfully.

2. The install runs ok and all the devices are loaded.  

3. A splash screen appears (in Graphics mode).

4. Then screen dies.  

5. Can still hear CD working and HDD working.

Any ideas?

---

### Post by pxwpxw on 2007-04-04
**codewarrior00007**  

I do not have the LTS version here, I assume the CD startup menu is similar to the Alternate version, and that it installs a desktop (xorg and desktop manager).

If you run the CD again, there should be a menu item to "Rescue a broken system", or something like that.

If you run that it will allow you to select and mount the root partition of what you installed and give you a text console to examine it.

You can then estblish what is the xorg situation by
```

ls -l /etc/X11/xorg*
ls -l /var/log/Xorg*
df

```

if the gui desktop installation has completed it will have installed **xorg.conf**, and if it tried to start it will have written **Xorg.0.log**. Both files are key to gui startup problems.

**df** will show the installed system size which should be around 1500MB or more for a completed desktop workstation, or less than 1000MB for a commandline or server installation.

---

