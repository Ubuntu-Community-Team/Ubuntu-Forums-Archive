---
title: "My kingdom for a mouse!!"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by jctaft on 2007-02-05
Hi, everyone.

I need some help getting my usb mouse working.  I am now on my third version of Ubuntu, and none has worked.  (although my touchpad works fine).  I've read google pages and forum posts ad infinitum, and nothing seems to apply to my problem.  (maybe mine is too basic).  anyway my mouse doesn't work at all.  It does nothing.  I've tried leaving it in while I boot up.  I've checked that my USB port works.  I've checked that the mouse works on another machine (and even this one with my other OS).  Nothing happens whatsoever.  I figure this may be a very basic problem, and that's why nobody else has it, but I might just be a little slow.  I'm very new to Linux.  It's a very basic mouse that probably only cost 5 bucks, nothing special.

Any ideas? This touchpad is driving me up a wall! I'd really appreciate it.

j

---

### Post by irish_flu on 2007-02-05
Have you checked out your xorg config file?

I don't know if your touchpad is "Synaptics" or not, but this might be of help to you (if you haven't already tried it):
[http://ubuntuforums.org/showthread.php?t=348115](http://ubuntuforums.org/showthread.php?t=348115)

---

### Post by jimrz on 2007-02-05
look in /etc/X11/xorg.conf and see if you have a section that looks like
```
Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection
```

it should be there from the default install. even on a laptop when the mouse was not plugged in during install, but you never know ...

---

### Post by jctaft on 2007-02-05
I did try that, and it didn't work, I'll try it again I suppose, just in case I did something wrong.


any other ideas?

---

### Post by jctaft on 2007-02-05
yes, that section is there verbatim

---

### Post by bodhi.zazen on 2007-02-05
What type of mouse is it ?

USB yes, but does it have a ball or is it a LED mouse ?

I have had trouble with USB LED mice, I have a few old fashioned PS2 mice around so I use one of those (with a ball).

Perhaps try a different mouse ???

---

### Post by jimrz on 2007-02-05
> **jctaft said:**
> yes, that section is there verbatim

oh well, just a thought. have you tried a different mouse with that box to see if any will work?

---

### Post by jctaft on 2007-02-05
It's a led mouse.  On the bottom it says "Basic Optical Mouse" USB/PS2 compatible.  I just plugged in another mouse, also optical, and nothing happened there either.

I REALLY don't want to go back to windows but I can't type while the touchpad is on because I'm always bumping it and erasing what I'm typing.

any other thoughts?

---

### Post by chick penguin on 2007-02-05
[QUOTE=jctaft;2112357]Hi, everyone.

Any ideas? This touchpad is driving me up a wall! I'd really appreciate it.

>>>>turn off the touch pad on your machine.

---

### Post by jctaft on 2007-02-06
um . . .then I have no mouse at all.  Doesn't help.

J

---

### Post by Spr0k3t on 2007-02-06
Couple things to try.

Turn off the touchpad (this worked on my lappy)

If you have no mouse, use the hotkeys in the following manner:

ALT+F2 to run, type in gnome-terminal

At the prompt type in "lsusb" and report your output.  You should see information listed about a connected mouse, even if it is generic.  You should see an ID like: 046d:c01e and then the name of the device.  Post your findings here.

---

### Post by jctaft on 2007-02-06
> jeff@jeff-laptop:~$ lsusb
Bus 001 Device 001: ID 0000:0000 


is the output of lsusb

---

### Post by jctaft on 2007-02-06
I know you said post to irc.FreeNode#ubuntuforums, but I don't know how to do that.

j

---

### Post by Spr0k3t on 2007-02-06
That's my signature, my meaning was to post the pertinent information on the forums, you did right.

Anyway, give me an updated information of your PCI devices.  Using the same method I mentioned earlier, type the following

```
lspci | grep USB
```

Report your findings back to this thread.  Thanks

---

### Post by jctaft on 2007-02-06
The output:


> jeff@jeff-laptop:~$ lspci|grep USB
00:02.0 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.1 USB Controller: nVidia Corporation nForce3 USB 1.1 (rev a5)
00:02.2 USB Controller: nVidia Corporation nForce3 USB 2.0 (rev a2)


---

### Post by jonnyburns on 2007-02-06
well since you already looked in the xorg and it does look like it sees the mouse than i guess the only thing you could do is try a different mouse, but since you already did that than the only thing you could do is to just use the touchpad... your mouses rnt supported obviously... i just use a ball mouse and it works terriffic... well here's my last idea, do u have the mouse plugged in to the computer when you start it, or do u plug it in when the os is already at the desktop... i wuold try and plug it in when the mouse is already at the desktop and see if you get a different response...

---

### Post by jctaft on 2007-02-06
Granted, I don't know my way around a computer like everyone else on this forum, but I find it unlikely that my simple basic mouse would not be supported, when much fancier mice are supported. If this is the case, however, I guess I have to be a sellout and return to the other guys' OS.  I spend too much of my time with LaTeX editing, and I can't leave the touchpad on because I'm too clumsy and always bump it.  Switching it on and off every time I need it is far too tedious.  This mouse problem may seem trivial, but to me it's the difference between staying with linux and returning to windows.

---

### Post by lyceum on 2007-02-06
I had the same problem on my Dell laptop. No matter what I did, I could not get the mouse to work. I shut off the touch pad, and then the mouse works. I do not know enough to explain why or how, only that it did. If you have not tried thet, I would, it shouldn't hurt.

Also, have you tried an non-USB mouse?

Just throwing out ideas...

---

### Post by jctaft on 2007-02-06
Yes, I have tried every permutation of booting with/without the mouse plugged in, touchpad on/off, and with the mouse in every usb port.  I get absolutely nothing.  Strangely, my laptop has no other port for a mouse.

j

---

### Post by lyceum on 2007-02-06
I don't know. I spent $15 on a wireless USB mouse that works fine. It sounds like that mouse just won't work w/ Ubuntu. Did you try the live disk on another PC to see if the mouse would work w/ Ubuntu on another PC? or did you jsut try it with MS on another PC? Also, are you sure the USB posrt even works? (After that I am out of ideas...:confused: )

---

### Post by ramzai on 2007-02-06
Let's have a look whether your mouse is recognized by kernel.

cd /dev/input
ls

now try possibilities such as
sudo cat mice
[move your mouse a little bit]
sudo cat mouse0
[move your mouse a little bit]

if you'll guess your device, you'll see some symbols while moving mouse and we'll know that it is X misconfiguration problem.

---

### Post by jctaft on 2007-02-06
I tried that and nothing happened either time.  Oh and I forgot to say this, but I put that mouse into another machine in my office that's probably ten years old and running Ubuntu Breezy Badger and it worked just fine.

j

---

### Post by ramzai on 2007-02-06
please post the output of
ls -al /proc/bus/usb/

and 1 more question, did your mouse work during installation?

---

### Post by lyceum on 2007-02-06
> **jctaft said:**
> I tried that and nothing happened either time.  Oh and I forgot to say this, but I put that mouse into another machine in my office that's probably ten years old and running Ubuntu Breezy Badger and it worked just fine.

j

It is looking like it is your USB port... I am at the end of my knowhow though.. sorry :(

---

### Post by jctaft on 2007-02-06
Here's the output:

> jeff@jeff-laptop:~$ ls -al /proc/bus/usb/
total 0
drwxr-xr-x 4 root root 100 2007-02-06 08:44 .
dr-xr-xr-x 6 root root   0 2007-02-06 08:44 ..
drwxr-xr-x 2 root root  60 2007-02-06 01:44 001
lrwxrwxrwx 1 root root  14 2007-02-06 08:44 devices -> .usbfs/devices
drwxr-xr-x 3 root root   0 2007-02-06 01:44 .usbfs


I don't think it's the USB port.  I thought of that and plugged a pin drive into it, and it worked fine.  Also, I booted in Xp and my usb mouse works there.

I would go and buy a different mouse, but I have no reason to believe it would work either, since I've tried another mouse and it didn't work.

J

---

### Post by ramzai on 2007-02-06
> **jctaft said:**
> Here's the output:



I don't think it's the USB port.  I thought of that and plugged a pin drive into it, and it worked fine.  Also, I booted in Xp and my usb mouse works there.

I would go and buy a different mouse, but I have no reason to believe it would work either, since I've tried another mouse and it didn't work.

J

AFAIK you should have one directory for each usb host. For example, my lspci | grep -i usb is
```
00:13.0 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.1 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.2 USB Controller: ALi Corporation USB 1.1 Controller (rev 03)
00:13.3 USB Controller: ALi Corporation USB 2.0 Controller (rev 01)

```
therefore ls -al /proc/bus/usb gives
```
total 0
drwxr-xr-x 7 root root 160 2007-02-06 18:25 .
dr-xr-xr-x 5 root root   0 2007-02-06 18:25 ..
drwxr-xr-x 2 root root  60 2007-02-06 18:25 001
drwxr-xr-x 2 root root 100 2007-02-06 18:25 002
drwxr-xr-x 2 root root  60 2007-02-06 18:25 003
drwxr-xr-x 2 root root  80 2007-02-06 18:40 004
lrwxrwxrwx 1 root root  14 2007-02-06 18:25 devices -> .usbfs/devices
drwxr-xr-x 6 root root   0 2007-02-06 18:25 .usbfs
```
So if you have 3 controllers in lspci, you should have 001 thru 003 so I think it's problem with your kernel - usb host combination, regarding you have the same with other mice. I may be wrong of course.

My suggestions:
1. if you have 001, maybe it's your usb 2.0 port, try plugging there and repeating my post 1
2. read the last post on [http://www.linuxforums.org/forum/debian-linux-help/46802-usb-mouse-not-working-udev-hotplug-problem.html](http://www.linuxforums.org/forum/debian-linux-help/46802-usb-mouse-not-working-udev-hotplug-problem.html) as it may be similar to your situation.

EDIT: your pin works on all ports on linux? if that's so, ignore all above ;)
Anyway, executing
```
more /proc/bus/usb/devices
```
will help you localizing your problem. Try this on different combinations, include your usb pin drive, etc.

---

### Post by MiuGu on 2007-02-06
Well, it would seem that I finally found a topic that addresses my problem... as I have exatly the same problem.

Just installed Ubuntu 6.06 yesterday and since then have been trying to get rid of using this god-awful touchpad, it's really bothersome when you type and have you ever tried playing games with a touchpad?

Anyways I've got a MX610 Logitech mouse, have tried my friends mouse too. My friends optical, mine laser and neither worked. The USB drives are working just fine as I can see all of them and when the mouse is connected it detects a Logitech USB Receiver in that slot. Have even tried my Logitech Headset which plug'n'played just fine.

Any help would be appreciated as I don't have any other problems with this OS and would love to keep using it over that piece of junk they call XP. 

Thanks in advance for any help.

---

### Post by fenian on 2007-02-06
Boot into the BIOS and under the USB seciton enable legacy devices.

---

### Post by jctaft on 2007-02-09
After many hours of headache, I have finally solved the problem.  I had to upgrade my BIOS.  I saw in other posts that this had worked for people, but I assumed it wouldn't apply to me because I reasoned that if it were a BIOS issue, the mouse wouldn't have worked in windows either.  I was wrong as it turned out, and I am finally with mouse

---

### Post by xfce1952 on 2007-02-12
> **jctaft said:**
> Hi, everyone.

I need some help getting my usb mouse working.  I am now on my third version of Ubuntu, and none has worked.  (although my touchpad works fine).  I've read google pages and forum posts ad infinitum, and nothing seems to apply to my problem.  (maybe mine is too basic).  anyway my mouse doesn't work at all.  It does nothing.  I've tried leaving it in while I boot up.  I've checked that my USB port works.  I've checked that the mouse works on another machine (and even this one with my other OS).  Nothing happens whatsoever.  I figure this may be a very basic problem, and that's why nobody else has it, but I might just be a little slow.  I'm very new to Linux.  It's a very basic mouse that probably only cost 5 bucks, nothing special.

Any ideas? This touchpad is driving me up a wall! I'd really appreciate it.

j

1

---

### Post by xfce1952 on 2007-02-12
> **jctaft said:**
> Hi, everyone.

I need some help getting my usb mouse working.  I am now on my third version of Ubuntu, and none has worked.  (although my touchpad works fine).  I've read google pages and forum posts ad infinitum, and nothing seems to apply to my problem.  (maybe mine is too basic).  anyway my mouse doesn't work at all.  It does nothing.  I've tried leaving it in while I boot up.  I've checked that my USB port works.  I've checked that the mouse works on another machine (and even this one with my other OS).  Nothing happens whatsoever.  I figure this may be a very basic problem, and that's why nobody else has it, but I might just be a little slow.  I'm very new to Linux.  It's a very basic mouse that probably only cost 5 bucks, nothing special.

Any ideas? This touchpad is driving me up a wall! I'd really appreciate it.

j

Can't help,l but do commiserate. I've got precisely the same problem. I've also got a problem with my CD drive - doesn't auto mount. I wonder if it's a UDEV issue. Nor are USB pendrives recognised.

I wonder if it's a UDEV problem. Does anyone know how to test whether UDEV works properly? Any good how-to's or guides?

---

