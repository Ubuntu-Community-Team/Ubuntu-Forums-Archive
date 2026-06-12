---
title: "Ctrl+Alt+F1 not working!"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by richardward101 on 2006-10-11
I just did a fresh ubuntu install with my brand new graphics card (a raedon 9550), installed fglrx (as per ubuntu wiki), and now I can't get to my virtual teminals, nothing happens when I press the combo. Any ideas? Its a non starter for me I don't know whet to try.
Thanks

---

### Post by bodhi.zazen on 2006-10-11
Try Ctrl-Alt-F2

---

### Post by richardward101 on 2006-10-11
thanks, but none of the virtual terminals are working.

---

### Post by jordanmthomas on 2006-10-11
Not the ultimate solution, but what happens if you do this in a terminal:
```
sudo /etc/init.d/gdm stop
```
Does it dump you to a VT then?

Also, do your keys work (Ctrl, Alt, F1) for other things?

---

### Post by bodhi.zazen on 2006-10-11
Can you post /etc/inittab ?

---

### Post by richardward101 on 2006-10-28
/etc/inittab:
```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3


```

---

### Post by odelay on 2006-10-28
Hey, I'm having a similar problem.  Ctrl+Alt+F1 gives me a super jumbled screen with no terminal/prompt/anything interactive.  Same for Ctrl+alt+f2-f6.  Going back to Ctrl+alt+f7, everything goes back to normal.

I'm using the proprietary ATI drivers.  
fglrxinfo
```
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6065 (8.29.6)
```

gedit /etc/inittab
```
# /etc/inittab: init(8) configuration.
# $Id: inittab,v 1.91 2002/01/25 13:35:21 miquels Exp $

# The default runlevel.
id:2:initdefault:

# Boot-time system configuration/initialization script.
# This is run first except when booting in emergency (-b) mode.
si::sysinit:/etc/init.d/rcS

# What to do in single-user mode.
~~:S:wait:/sbin/sulogin

# /etc/init.d executes the S and K scripts upon change
# of runlevel.
#
# Runlevel 0 is halt.
# Runlevel 1 is single-user.
# Runlevels 2-5 are multi-user.
# Runlevel 6 is reboot.

l0:0:wait:/etc/init.d/rc 0
l1:1:wait:/etc/init.d/rc 1
l2:2:wait:/etc/init.d/rc 2
l3:3:wait:/etc/init.d/rc 3
l4:4:wait:/etc/init.d/rc 4
l5:5:wait:/etc/init.d/rc 5
l6:6:wait:/etc/init.d/rc 6
# Normally not reached, but fallthrough in case of emergency.
z6:6:respawn:/sbin/sulogin

# What to do when CTRL-ALT-DEL is pressed.
ca:12345:ctrlaltdel:/sbin/shutdown -t1 -a -r now

# Action on special keypress (ALT-UpArrow).
#kb::kbrequest:/bin/echo "Keyboard Request--edit /etc/inittab to let this work."

# What to do when the power fails/returns.
pf::powerwait:/etc/init.d/powerfail start
pn::powerfailnow:/etc/init.d/powerfail now
po::powerokwait:/etc/init.d/powerfail stop

# /sbin/getty invocations for the runlevels.
#
# The "id" field MUST be the same as the last
# characters of the device (after "tty").
#
# Format:
#  <id>:<runlevels>:<action>:<process>
#
# Note that on most Debian systems tty7 is used by the X Window System,
# so if you want to add more getty's go ahead but skip tty7 if you run X.
#
1:2345:respawn:/sbin/getty 38400 tty1
2:23:respawn:/sbin/getty 38400 tty2
3:23:respawn:/sbin/getty 38400 tty3
4:23:respawn:/sbin/getty 38400 tty4
5:23:respawn:/sbin/getty 38400 tty5
6:23:respawn:/sbin/getty 38400 tty6

# Example how to put a getty on a serial line (for a terminal)
#
#T0:23:respawn:/sbin/getty -L ttyS0 9600 vt100
#T1:23:respawn:/sbin/getty -L ttyS1 9600 vt100

# Example how to put a getty on a modem line.
#
#T3:23:respawn:/sbin/mgetty -x0 -s 57600 ttyS3
```

Thanks!

---

### Post by richardward101 on 2006-10-28
killing gdm just seems to make it hang, but when I shut down I briefly see a tty before the shutdown splash appears.
Just upgraded to edgy, problem still there. could it be to do with keyboard shortcuts in X, if I configures it incorrectly?

And yes, ctrl+c/v for copying and pasting works, and Alt+F1 opens the menu.

---

### Post by odelay on 2006-10-28
Since I'm having a similar problem with Ctrl+alt+F1, and I know it has worked fine before I don't think there's a problem with the keyboard shortcut.  Plus, ctrl+alt+F7 does what it's supposed to, so I imagine the other 6 are doing what they're supposed to also.

I'm pretty sure the problem is with the ATI drivers.  According to the wiki ([http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)), did you use Method 1 or Method 2?  This time around, I used Method 2 which involves recompiling the drivers into the kernel I think.  I've reinstalled those drivers about 3 times and tried different stuff in between, so I'm sure my xorg.conf is all messed up.  However, I'm at the right resolution, fglrxinfo shows the correct driver up and running, and everything seems to be working fine.  I just have the messed up virtual terminals and I get a few ugly lines after the Ubuntu splash screen.

---

### Post by LoermansA on 2006-10-29
I'm pretty sure it's the ATI drivers. I have the same problem. The thing is, the virtual terminal actually do seem to work. When typing stuff you can see from the disc activity that the laptop responds. Typing
```
# sudo shutdown -h now
```

Shuts down the machine, even though the screen is garbled.

For clarity, my laptop is an HP 8430 with onboard X1600.

Arjan

---

### Post by bodhi.zazen on 2006-10-29
for grabled screens type (even though you can not see what you are typing):```
reset
```

If this works, to keep from typing it every time you login try, in a terminal,:```
echo reset >> ~/.bashrc
```

---

### Post by odelay on 2006-10-30
hmm...I still get no response in either of the virtual terminals.  Restarting (sudo shutdown -r now) or resetting (reset) have no effect.  Luckily, I'm able to switch back to #7 without any problems (unlike a few other people here).  I wonder if this means our problems are significantly different.  Either way, I imagine they both deal with the ATI drivers.

---

### Post by richardward101 on 2006-10-31
So no one has any idea about my original problem, of the keys actually doing nothing? I don't get a garbled terminal, just nothing happens. X stays there, thats it.
thanks

---

### Post by ironfistchamp on 2006-11-01
I have the same kind of problem. The Ctrl+Alt+F1 and higher keys do nothing. When I had a gnome terminal open Ctrl+Alt+F1 just made it go full screen. I found I had to log out then press C+A+F1 to get to the terminal. I have a NVIDIA 7800GTX and hadn't installed any drivers. It was just using the basic ones that Edgy installed.

---

### Post by kdevil on 2006-11-02
I'm having the same problem, and I'm using Beryl with the NVIDIA beta drivers.  Ctrl-Alt-F1 just makes terminals go fullscreen.

I'm fairly certain it's not related to graphics drivers, though.

---

### Post by Fraz on 2006-11-05
Here is how to fix Ctrl-Alt-F1 or F2, etc. from giving you garbled colors instead of a Virtual Terminal.

The problem is caused by "splash", that Ubuntu logo thing during startup, which is a useless feature anyway since it prevents useful information from being shown about the bootup process and slows things down. Disable it with the instructions here:

[http://ubuntuforums.org/showthread.php?t=107472](http://ubuntuforums.org/showthread.php?t=107472)

:)

---

### Post by odelay on 2006-11-05
Is there anyway to do it if you still want to see the pretty edgy splash screen?

---

### Post by richardward101 on 2006-11-23
ok I seem to have fixed the problem, not sure what it was tbh, I just used an xorg.conf from gentoo and edited it to use fglrx. now works fine. I tried to single out which bit was causing the problem, but I'm sorry to say I got bored. I can post it if anyone thinks it'd be useful.

---

### Post by kdevil on 2006-11-24
Huh, Ctrl-Alt-F1 seems to be working for me now, although I can't remember changing anything.  Weird.

---

### Post by Phase1 on 2007-08-14
> **richardward101 said:**
> ok I seem to have fixed the problem, not sure what it was tbh, I just used an xorg.conf from gentoo and edited it to use fglrx. now works fine. I tried to single out which bit was causing the problem, but I'm sorry to say I got bored. I can post it if anyone thinks it'd be useful.

hey guys im new here, windows is the only OS i have ever used since 2.0.

i dont know what this forum feels about bringing back old posts, but this thread title is the same problem i am having.

-could you post what you did to fix this
-if anyone has any thoughts i would appreciate hearing them.

---

### Post by Eithel on 2007-10-22
Same problem for me with Nvidia driver.

If i remove the splash options in grub file, nothing appear on my screen until login screen apper and if if i press ctrl+alt+F[1-6] the screen is complety black !

Another problem, is when i click on esc-button the system block for 15-20 second befor the "form esc" (with all the options) come out! (the mouse move, but the system is "blocked")

---

### Post by Eithel on 2007-10-22
In my menu.lst i added the option vga=***, now i remove it, and the ctrl+alt+f[1-6] works !

---

### Post by Eithel on 2007-10-22
> **Eithel said:**
> 
Another problem, is when i click on esc-button the system block for 15-20 second befor the "form esc" (with all the options) come out! (the mouse move, but the system is "blocked")

In session manager i remove the gnome-power-manager and when i try to logout this service starts and block the pc. Now all work s!:guitar:

---

### Post by bigboy_pdb on 2007-10-22
The problem of tty[1-6] having no output and a black screen also occurred for me. There seem to be a number of problems occurring in cards with ATI chips. It has been filed as a bug in launchpad at the following url:
[https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/129910)

Removing vga=791 from /boot/grub/menu.lst fixed the problem for me as well.

---

