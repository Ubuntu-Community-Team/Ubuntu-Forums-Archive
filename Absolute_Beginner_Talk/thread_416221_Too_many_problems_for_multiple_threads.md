---
title: "Too many problems for multiple threads"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Gorthus on 2007-04-20
Okay, I'm getting really tired of getting so close to having something work, then either have the person that was helping me suddenly go inactive, or it just stops working...

Over the single week that I have had Ubuntu, I've grown in anger and stress.. I've come across too many problems to put into multiple threads...


[LIST=1]
[*]Beryl won't start for crap in Feisty
[*]Avant WM stopped working because of Feisty
[*]I can't seem to get my ATI card working right
[*]My internet speed is EXTREMELY slow
[*]GAIM and Firefox crash, frequently at best
[*]I don't know how to end programs like the task manager in windows would
[*]My printer wont work (Canon MP160)
[/LIST]

This is about half of it...

Please contact me, I'd prefer you didn't reply to this thread as it probably won't provide much help.

MSN: [email]gorth@gorthus.com[/email]
AIM: klarathios

EDIT: When I run beryl:
```
Detected xserver                                : AIGLX

Checking Display :0.0 ...

Checking for XComposite extension               : passed (v0.3)
Checking for XDamage extension                  : passed
Checking for RandR extension                    : passed
Checking for XSync extension                    : passed

Checking Screen 0 ...

Checking for GLX_SGIX_fbconfig                  : passed
Checking for GLX_EXT_texture_from_pixmap        : passed
Checking for non power of two texture support   : failed

Support for non power of two textures missing
beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

```

---

### Post by jiminycricket on 2007-04-20
"Beryl won't start for crap in Feisty
Avant WM stopped working because of Feisty
I can't seem to get my ATI card working right"

Is all due to your ATI card, composite not working.  What kind of card is it?  lspci | grep ati

end program is in System->Administration->System Monitor, on the second tab right under the menu.  Or in a terminal (I use tilda), do "killall PROGRAMNAME " or "sudo killall PROGRAMNAME" if it has root priveleges.

Canon may be a problem, I think they're unfriendly to free software.  Regardless, this should help: [http://ubuntuforums.org/showthread.php?p=2432538](http://ubuntuforums.org/showthread.php?p=2432538)

Slow internet, you usually need to disable ipv6 if this happens.  [http://www.linuxforums.org/forum/debian-linux-help/55412-slow-internet-ubuntu.html](http://www.linuxforums.org/forum/debian-linux-help/55412-slow-internet-ubuntu.html) also has a link to a thread here.

For Firefox crashing, can you create a new profile or go into safe mode to see if it's an extension problem? (firefox -ProfileManager OR firefox -safe-mode  Does apport pop up when GAIM crashes to send a sigsev report to Launchpad?

---

### Post by igknighted on 2007-04-20
> **Gorthus said:**
> Okay, I'm getting really tired of getting so close to having something work, then either have the person that was helping me suddenly go inactive, or it just stops working...

Over the single week that I have had Ubuntu, I've grown in anger and stress.. I've come across too many problems to put into multiple threads...


[LIST=1]
[*]Beryl won't start for crap in Feisty
[*]Avant WM stopped working because of Feisty
[*]I can't seem to get my ATI card working right
[*]My internet speed is EXTREMELY slow
[*]GAIM and Firefox crash, frequently at best
[*]I don't know how to end programs like the task manager in windows would
[*]My printer wont work (Canon MP160)
[/LIST]

This is about half of it...

Please contact me, I'd prefer you didn't reply to this thread as it probably won't provide much help.

MSN: [email]gorth@gorthus.com[/email]
AIM: klarathios

Please keep support on the forum, this way other users have the benefit of seeing the solution.  The irc channel is also a good place for support if you need more immediate help.

as for your issues:
1) we need a lot more info than that.  Many many things can cause this.  What graphics card are you using?  XGL or AIGLX?  Error messages when run in the terminal?

2) See above

3) This is a well known bug, see the sticky in this forum for a workaround... what card is it, as if its old enough it may not work with the newest drivers in feisty

4) IPv6 needs to be disabled most likely... search the forum here for a guide to do that, as I'm not sure off the top of my head

5) probably related to #4, but post error messages from the terminal from the crashes

6) Use the system monitor in system->admin or use the command top in the terminal and kill via the PID (or use the kill command)

7) I don't see your printer in the printer database at all, but the mp360 only partially works, which for all intents and purposes means it doesn't work.  I wouldn't hold your breath on this.

---

### Post by Gorthus on 2007-04-21
When I run FGLRXINFO i get this: ```
display: :0.0  screen: 0
OpenGL vendor string: Tungsten Graphics, Inc.
OpenGL renderer string: Mesa DRI R300 20060815 AGP 1x x86/MMX/SSE2 TCL
OpenGL version string: 1.3 Mesa 6.5.2

```

---

### Post by jiminycricket on 2007-04-21
What about

lspci | grep ati

and

glxinfo | grep rendering

---

### Post by Tundro Walker on 2007-04-21
> **Gorthus said:**
> [LIST]
[*]GAIM and Firefox crash, frequently at best
[*]I don't know how to end programs like the task manager in windows would[/LIST]

**Kill off a process...**

Ok, for killing off a process, if you're using Kubuntu / KDE, you should be able to do the ctrl+alt+esc to get a skull and cross-bones, which you click on the window you want to kill off.  If you're not using Kubuntu / KDE, you can use "top" to find the PID of the process that's screwing up, and use "kill <PID>" to bump it off.  Look at this thread for more...

[http://ubuntuforums.org/showthread.php?t=343227&highlight=kill+ctrl+alt+esc](http://ubuntuforums.org/showthread.php?t=343227&highlight=kill+ctrl+alt+esc)


**Create a running log of program...**

For programs giving you problems, go into the terminal and run them as follows:

```
<your program> > /home/<your home directory>/Desktop/blah.log 2>&1
```What this does is log the results of the program's run (both ok messages and error messages) to a file called "blah.log" on your desktop.  You replace "<your program>" and "<your home directory>" with the name of the program and the name of your home dir respectively.  Linux is case-sensative, so make sure you capitalize the "D" in "Desktop".

So, for instance, to log Gaim (assuming your home directory is called "HelloKitty")...

```
gaim > /home/HelloKitty/Desktop/blah.log 2>&1
```Open the "blah.log" file after the program crashes, and see what kinds of errors you got at the bottom.  Or, attach it to a post in the forums for help, or paste the contents in if it's not too much (if it's over 50 lines or such, it may just be easier to attach the file),  An error log will get you a lot more help from folks in the forums, since it gives them some hard evidence to sift through.  IE: a week's worth of posting tennis, with them trying to play 20 questions with you to figure out what the root-cause problem is, can get reduced down to 1 post by you with an error log, and then 20 posts from folks checking it out and telling you what's up.

---

### Post by Gorthus on 2007-04-21
> **jiminycricket said:**
> What about

lspci | grep ati

and

glxinfo | grep rendering

```
gorthus@gorthus-desktop:~$ lspci | grep ati
00:00.0 Host bridge: Intel Corporation 82865G/PE/P DRAM Controller/Host-Hub Interface (rev 02)
00:01.0 PCI bridge: Intel Corporation 82865G/PE/P PCI to AGP Controller (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #3 (rev 02)
00:1d.3 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB UHCI Controller #4 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801EB/ER (ICH5/ICH5R) USB2 EHCI Controller (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 PCI Bridge (rev c2)
00:1f.0 ISA bridge: Intel Corporation 82801EB/ER (ICH5/ICH5R) LPC Interface Bridge (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801EB/ER (ICH5/ICH5R) IDE Controller (rev 02)
00:1f.2 IDE interface: Intel Corporation 82801EB (ICH5) SATA Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801EB/ER (ICH5/ICH5R) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: ATI Technologies Inc R430 [Radeon X800 (PCIE)]
02:02.0 Ethernet controller: 3Com Corporation 3c905C-TX/TX-M [Tornado] (rev 78)
gorthus@gorthus-desktop:~$ glxinfo | grep rendering
direct rendering: No

```

---

### Post by jiminycricket on 2007-04-22
This thread seems to have some links and tips for the X800 that worked: [http://ubuntuforums.org/showthread.php?p=2439609](http://ubuntuforums.org/showthread.php?p=2439609)

---

