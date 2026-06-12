---
title: "Keyboard locks up on laptop"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by dongerw on 2007-03-16
Hey guys.

I have a Dell Inspiron E1505 laptop and I blasted everything and installed Ubuntu edgy.  Everything works nice for a while, but at random times my keyboard will lock up.  The caps lock button doesn't make the light toggle.  Pressing Ctrl - Alt - Backspace does nothing.  I can press and hold down the function key and press F3 to see the battery status.  The volume control with the function button doesn't do anything.  I can do Fn + Esc and it will lock the computer, but I can't unlock it because the keyboard doesn't work to type in my password.  I usually have to hold the power button down to shut the computer off, and when it restarts, I can use the keyboard again.  Please, if you have any thoughts or suggestions, please let me know.  Thanks in advance.

---

### Post by hyper_ch on 2007-03-16
Have you noticed any pattern when this occurs?

---

### Post by dongerw on 2007-03-16
All I have open is Intellij IDEA and firefox usually, and a few command prompts.  I haven't noticed any particular sequence of events that triggers the keyboard to lock.

---

### Post by Ozor Mox on 2007-03-18
I posted in another thread about this problem but this is a more recent thread so perhaps you have some more information or a solution?

This has happened a couple of times to me. The laptop keyboard on my Dell Latitude D600 running Edgy completely stops functioning, including caps lock and num lock keys changing the LED lights. No applications would start (starting application... then nothing), the internet would disconnect, and the shutdown button would have no effect when clicked on, nor Ctrl-Alt-Backspace, requiring a hard reboot. After that everything worked just fine. Very strange bug of some kind I assume.

---

### Post by dongerw on 2007-04-03
This is the craziest thing I have ever seen.  At first I thought I was overheating the machine or something, but when I reboot everything works again.  Man, this thing is starting to remind me of a windows machine.

How is it possible that the keyboard doesn't respond to anything but a few of the Fn key combinations???  I would figure that when the keyboard locks, it would be an all or nothing type deal.

---

### Post by mikesignguy on 2007-04-04
have the same problem with my hp laptop........

---

### Post by rjfioravanti on 2007-04-04
I am experience the same thing on my desktop computer

For me however nothing works ,just the keyboard and mouse freeze, and I can't do anything except hard reboot

I have a feeling it has something to do with samba, because it happens when I install it, but doesn't happen if I remove it. However, even after I remove it, it happens if I try and add a windows network samba printer.

---

### Post by vronp on 2007-05-08
Same problem on a Dell Inspiron 9400 running Feisty.

I am usually only running Firefox.  When the keyboard locks up, I can use the mouse (usually).

In other words, I can always move the mouse cursor and I can usually shut down programs and the laptop (but not always).

I believe I can force this behavior when I unplug and replug my Linksys WUSB54G usb wireless interface.

---

### Post by dongerw on 2007-06-28
ARGH!!!  It is so frustrating when trying to do work and the keyboard just locks up.  Has anyone found a solution, a hack, or anything that resolves or even helps pinpoint the problem???   Thanks

---

### Post by DanielKeshet on 2008-01-13
I don't know if you have still been experiencing this, but I have just figured out what is causing it on my Dell laptop (Inspiron 1521, Kubuntu gutsy with feisty kernel).  My keyboard randomly locked up; sometimes when resuming from suspend, sometimes just when using the computer.  For me, it turned out amarok, the media player that accepts input from the media buttons on my keyboard, had crashed.  I don't know exactly what was happening, but by killing amarok, I got functionality back for my keyboard.

If you figure out what programs in ubuntu are accepting input from your media buttons, try killing those programs, using whatever means you can if you still have mouse functionality, and then see if you get your keyboard back.

---

### Post by isotope_239 on 2008-03-04
I'm having the same problems with my HP laptop. It's been months. I tried installing the 32 bit version as i thought it was some problem with the 64-bit one. Anybody out there who has a solution or can pinpoint the problem?

---

### Post by kevjaun on 2008-05-07
Bit of necromancy on an old thread here, but I am having the same problem and it is driving me mad. I'm using a desktop with 7.10. I'm unlikely to move to Hardy as this has ticked me off so much and the word is that Hardy is less stable than the Gibbon. Unless anyone has a solution (which I would love dearly) I'm off to another distro and taking my converts with me.

---

