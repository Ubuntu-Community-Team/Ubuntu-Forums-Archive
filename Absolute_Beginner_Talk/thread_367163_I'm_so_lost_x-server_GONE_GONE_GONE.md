---
title: "I'm so lost x-server GONE GONE GONE"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2007-02-21
Updating/troubleshooting the ALSA, I was given advice which has caused the desktop (Ubuntu-desktop) to fail and now, after other advice, starting in from the grub menu in recovery mode in the 2.x.x.27-i686 kernel cannot load and returns a FATAL msg., it can't find some library it needs.

Starting in a "lower" kernel xxx-i386 does start a gui, but the mouse fails and won't move at all. Shutting down without pulling the plug is the only option, so after getting caught in that loop once, I'm not trying any of those kernel's again.

Because I can't be completely without a computer (I work at home), I have swapped the "broken" gui hdd for another. That is to say: the bad system is now hdb1 and the working drive is hda1, primary slave and primary master -- respectively.

I have read and applied the ideas at PsychoCats "Troubleshooting X" pages, but in it's current broken state the i686 kernel can't access the CD-rom, so the first command sudo apt-cdrom add 

fails with a 

no device -- something or other

sudo aptitude update did some work and because it cannot be on the 'net, returned warnings about http:// xxxxxxx not found or not updated

sudo aptitude install ubuntu-desktop caused the system to get some files, but the program still returns the same messages as boot time as before.

sudo /etc/init.d/gdm restart starts the gnome desktop, but the mouse freezes and the computer has to be shutdown with Ctrl-Alt-Backspace.

Any help appreciated. Thanks.

---

### Post by poohbear1616 on 2007-02-21
Have yoy tried to reconfigure xserver?

If not try this:
```
sudo dpkg-reconfigure xserver-xorg
```

It has straightened me out before.

---

### Post by Mark_in_Hollywood on 2007-02-21
I tried:

sudo dpkg-reconfigure xserver-xorg

the screens were all answered and then when I tried to restart, the screen went to gray background, black mouse cursor and nothing worked.

---

### Post by taurus on 2007-02-21
Did you pick **vesa** as a driver for your graphic card?

---

### Post by poohbear1616 on 2007-02-21
> sudo aptitude update did some work and because it cannot be on the 'net, returned warnings about http:// xxxxxxx not found or not updated

If you cannot access the net, then sudo aptitude install ubuntu-desktop will not work either.

What kind of graphics card you have?

I'll try more after your answer.

---

### Post by poohbear1616 on 2007-02-21
Sorry taurus, we posted at the same time.
That's where I was headed with the graphics question.

---

### Post by Mark_in_Hollywood on 2007-02-22
I am responding to two separate posts in this one:

Yes, VESA

This is a stock Dell 4100 computer. The graphic card is an ATI Rage 128 Pro or Pro 128, it always depends on where whether you see the ATI website or Dell as to which is first, 128 or Pro. Sorry.

---

### Post by nalmeth on 2007-02-22
So you've tried both the 'vesa' driver AND the 'ati' driver?

---

### Post by Mark_in_Hollywood on 2007-02-22
sudo dpkg --reconfigure xserver-xorg gave an ATI option, I tried with that and with VESA.

Just a reminder the boot time messages, before the gui starts or would/should start say their is a FATAL kernel error, some library can't be found/loaded, it repeats this message many many times, so fast I can't tell whether it is just one file/library or many. These lines scroll by at many times the usual speed of the boot time messages. And it an i686 kernel, not the i386.

---

### Post by fwar on 2007-12-01
i have the same problem  plz help

fatal server error:
no screen found
XIO : fatal error 104(connection rest by peer) on x server ":0.0"
after 0 requests (0 known processed) with 0 events remaining.

package 'x-server' is not installed

---

