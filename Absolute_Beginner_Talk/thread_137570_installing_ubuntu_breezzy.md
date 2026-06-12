---
title: "installing ubuntu breezzy"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by manchette on 2006-02-28
hi all,
i just installed ubuntu breezy on my pc but i can't log in for i'm stuck at the log in screen with no more keyboard, nor mouse
can you help me?
i've heard about the server X, or sthg? 
is there something to change there and how do i have access to it please?
thanks

---

### Post by Kapre on 2006-02-28
[QUOTE=manchette]hi all,
i just installed ubuntu breezy on my pc but i can't log in for i'm stuck at the log in screen with no more keyboard, nor mouse
can you help me?
i've heard about the server X, or sthg? 
is there something to change there and how do i have access to it please?
thanks[/QUOTE]

manchette - hello and welcome to Linux (Ubuntu)! Just would like to ask if you have a USB keyboard and mouse? Maybe that's the reason why you can't log-in. Try using a standard keyboard and ps/2 mouse.

K

---

### Post by manchette on 2006-02-28
thanks,

i used usb wireless keyboard+mouse from Genius :  twintouch luxmate
and also wired usb original ones from fujitsu siemens 
my pc ain't got no ps2 connection option, only Usb is available.

someone told me to hold down Ctrl+alt+F1
then run
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo nano /etc/X11/xorg.conf

but you can **not** hold anything down for the keyboard does not receive anything

---

### Post by Razorback on 2006-02-28
One thing to try, see if there is a setting in your bios for usb legacy support.  Change the setting and see if that works.

---

### Post by manchette on 2006-02-28
well, why would it work in Suse if ko in bios then?
i'm afraid i'm too afraid to mess things up to adventure into bios if not Absolutely mandatory :)

---

### Post by Razorback on 2006-02-28
Changing that setting to see if it will work won't mess anything up.  I had seen a post here that was successful for a person with a similar problem.  If it doesn't work, all you need to do is change it back.  The only problem I could see is if you are dual booting with Windows and some hardware requires it to be set a certain way.  I can't answer why it worked fine in Suse and not in ubuntu.  Even though it is Linux, there are differences.

---

### Post by manchette on 2006-02-28
ok, usb legacy support you say?
how do i access the bios ? F2 while booting i guess?

where shall i find this data about usb?
is fixing for ubuntu not gonna change things for the others?

are you sure it can't be linked with the X server ? may i change this from suse?

some said it's not hardware, other it is ( :-k  )

---

### Post by Razorback on 2006-02-28
First off, what motherboard are you running?  Different bios developers use different keys - AMI (del), compaq (f10), dell (f2), etc.  Are you running ubuntu by itself on the machine?  I would think if you want to reinstall Suse, it should reinstall.

Could be hardware, I have had problems setting up my machine where others have had no problems.  In fact, I am still messing around with my vid card.  Getting ready to chunk it!! :)

Here is the link I was talking about:

[http://ubuntuforums.org/showpost.php?p=524762&postcount=1](http://ubuntuforums.org/showpost.php?p=524762&postcount=1)

---

### Post by manchette on 2006-02-28
usb legacy support is ok in bios (enabled)
i plugged out the sender part, then plugging it again, 
the sender led of the wifi system (mouse&keyboard) became green :D

but still no move of the mouse, nor anything while typing on keyboard :-?

---

### Post by Razorback on 2006-02-28
Did you try to disable it and see what it does?  It should not hurt anything as I have had to do the same thing in Windows.

---

### Post by manchette on 2006-02-28
wow , no i'm not so dubious ( :-D )...,
... disable it and try if it works ? 
i can't figure out how disabling Universal Serial Bus plug support will enable an USB mouse&keyboard
...or maybe i did not get the right spirit...yet ? ;)

---

### Post by Razorback on 2006-02-28
I am just suggesting different things I would try to exhaust all possibilities. ;)

---

### Post by manchette on 2006-02-28
you're right though computers are often mysterious , but i think we can skip this last one
Argh! i'm  still w.o ubuntu then :cry:
well, tell me more about Tenessee then, how is it there?
by chance i'm living in a very sunny place (300 days a year!! :D )

---

