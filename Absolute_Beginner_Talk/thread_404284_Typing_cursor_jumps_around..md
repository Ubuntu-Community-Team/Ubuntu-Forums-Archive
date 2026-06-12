---
title: "Typing cursor jumps around."
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2007-04-08
Okey, so I can't find this anywhere else. When I type the typing cursor randomly jumps back and forth now and then without me doing anything, its very annoying. I use a standard laptop keyboard and use the generic keyboard settings. help?

---

### Post by r00tintheb0x on 2007-04-08
You need to use imps2 as your mouse driver in xorg.conf

---

### Post by jcrnan on 2007-04-08
No effect.

---

### Post by wackimonki on 2007-04-21
I am having the same issue.

I have recently installed Ubuntu 7.4 as my first Ubuntu system. It is all going well except for this random cursor problem.

As I was typing the previous paragraph, the focus/cursor would randomly jump up, left, sometimes highlighting previous link. A 'link to' box even popped up!

As you can imagine I'm a little frustrated. Oh, it jumped up 4 lines up just now.

How do I apply the driver previously mentioned?

Any other suggestions?

I have checked for updates etc.

I was using Desktop Effects. I have disabled it now thinking that was the root cause. Not so.

---

### Post by wackimonki on 2007-04-21
ahh! I think I have it figured out.

It's the over-sensative touchpad. I have now disabled it by adding:
Option "SHMConfig" "On"
to my synaptics section.

Add switch it off with:
synclient touchpadoff=1

:)

---

### Post by EBAR on 2007-04-22
I'm sorry, I'm sure it makes me sound like a dolt....but how do I apply the changes mentioned? What file do I edit and where is it?

Thanks in advance.

---

### Post by ReillyRoo on 2008-04-15
> **wackimonki said:**
> ahh! I think I have it figured out.

It's the over-sensative touchpad. I have now disabled it by adding:
Option "SHMConfig" "On"
to my synaptics section.

Add switch it off with:
synclient touchpadoff=1

:)


how do i impliment these changes

---

### Post by wackimonki on 2008-04-15
Sorry guys!

You need to edit this file:
etc/X11/xorg.conf 

Here's my section for touchpad:
Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "SHMConfig"             "On"
EndSection


I am using Compaq Presario v3000. The touchpad has a enable/disable button which miraculously works in Ubuntu now.

---

### Post by ReillyRoo on 2008-04-15
but i still dont see were i put in the toucpadoff=1 thing

---

### Post by ReillyRoo on 2008-04-15
NM i figured it out. THANKS SOOO MUCH!! problem fixed

---

### Post by wackimonki on 2008-04-15
synclient touchpadoff=1

is a shell command. Type it into a console.

If I remember right, you don't need to touch the config file at all. Just call this command with =1, or =0 for off and on.

---

