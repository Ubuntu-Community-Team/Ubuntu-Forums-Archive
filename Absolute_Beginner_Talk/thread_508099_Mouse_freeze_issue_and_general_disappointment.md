---
title: "Mouse freeze issue and general disappointment"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by Phosphoros on 2007-07-23
Please forgive me if this is a repost (and I'm sure it is) but I had to bring this up.
I've done about 15 searches for info and I only find partial info.  Some poor guy pleading for help and someone telling them to send the xconf or something.  Which is a little hard when you have NO MOUSE.
It's been a while since I've had linux, which is why I'm posting in the newbie forums, and I thought I'd give 7.04 a whirl.  It was looking great and I'm hearing good things about it.
So I get a friend to grab a copy as well and we sit on the phone together and do the install.
Fresh hard drive, no dual boot.  Completely clean.
The install is a breeze until the mouse locks up.  Not only mine, but my friends as well.  About 3 - 5 minutes after the system has been running during install.
I dismiss it thinking it's a glitch with the install process.
After the install is over, the system reboots and it happens again to both of us.  We have totally different machines btw.
My craptop (Windows machine) has a cow and won't pick up my network so I figure "How hard can it be to navigate with keyboard shortcuts?", either I'm a complete retard (which is likely) or navigating through Linux with keyboard shortcuts sucks massively.  I'm inclined towards the massive sucking.
Now that I've killed Ubuntu and reinstalled Windows I've been trying to track down the problem, doing searches here and generally on the web but I can not find anything to address the problem. 
Is this a HAL (Not sure what HAL exactly is but I gather it's USB related?) issue?  If so, how the hell do you fix it without a mouse and limited keyboard shortcuts (I'm sure linux has them, I just apparently have no idea what they are)?
Trying to use forums via tabbing is a total nightmare.   
The Ubuntu Device Helper (whatever it's called) is a little silly.  It asks if specific hardware is working, Sound, Keyboard, Video, Mouse.  The problem is without the mouse, there is no way to select the "NO, It's not bloody working, HALP!" checkbox.

Just for reference, my mouse is a USB Logitech G5 Laser mouse but NONE of my mice worked.  The Microshaft intellimouse, the Belkin cheaptronics, etc...  I tried a few.

So, sorry for the long post but I needed to express my disgust over this issue.
It didn't exactly leave a pleasant taste with my friend on Linux either.  Though he's trying Fedora later tonight.

So thanks for reading this.  
Is there a fix for this?  Is it only a small minority of people who experience this?  Are the Devs gonna fix this someday?  I'd love to move back to Ubuntu since I don't work at a place that I need Windows anymore.
As long as I can fix it, Windows is in the trash for me.  I just don't know enough about Linux to hack around it to fix stuff like that.

Thanks for your time and patience.

Phosphoros

---

### Post by rillip on 2007-07-23
The last time I had an issue with my mouse ona Linux box, I found there was a setting in the bios labeled "usb mouse support."  Effectively, if it wasn't set to "enabled" then the mouse would never get initialized, so I couldn't use it.  Try setting any usb related options in your bios to on and this might help.

---

### Post by Phosphoros on 2007-07-23
Thanks rillip for replying.
I did indeed go through all the varies USB options in BIOS.  They were all on so I'm a little stumped still.

Thanks again.

---

### Post by eiskalt on 2007-07-23
kudos on a 1337 hard to follow post, it was like reading "a million little pieces".  So, you have two machines with the same problem?  What kind of machines are they?  what are their specs?  Can you boot off the live cd and if so, does your mouse work there?

---

### Post by Phosphoros on 2007-07-23
Sorry for what apparently seems to be a rambling post.
Yes I have two machines, one is a windows laptop.  I suppose I shouldn't have brought that one up so as not to confuse people.  I was only installing Ubuntu on my desktop.  
The Live Ubuntu CD does the exact same mouse freeze up after a couple minutes.
I tried a few other Live CDs from other Distros and none of them do it.
The desktop machine I'm installing Ubuntu on is an older machine but has run Ubuntu 6.xx fine and Windows forever.
The "other" machine with the problem is a friends.  Not to worried about him though.  If I can figure this out I can fix his too.  We were chatting and installing Ubuntu together over the phone.

Setup for Desktop
AMD 3000+
Epox 8RDA3+Pro Mobo
gig of crucial ram
7600 GT nVidia (AGP)
80 Gig IDE WD Hard drive
Lite-on DVD-RW drive
Logitech G5 Laser Mouse
Generic USB Keyboard
Acer 17" LCD monitor.

---

### Post by Phosphoric on 2007-07-24
I had a mouse freezing problem which I fixed by re-configuring the mouse in xorg.

code:  sudo dpkg-reconfigure xserver-xorg

Worth a try?

---

### Post by Cappy on 2007-07-24
Also try boot parameters ```
noapic acpi=off
```
If you don't know how to add a boot parameter in grub look here:
[http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html](http://grumpymole.blogspot.com/2007/05/ubuntu-how-to-edit-grub-boot-parameters.html)

---

### Post by PryGuy on 2007-07-24
That's a pretty strange problem 'cause I had many problems with Ubuntu, but I've *never *had a mouse issue. Do you and your friend have different motherboards? 'Cause it appears to be a hardware incompatibility problem. Do you and your friend have the same USB devices?

---

### Post by ovidiubar on 2007-07-27
Hi! I'm a newbie to Linux and I am experimenting the same problem with the mouse. I have ubuntu 7 on a Toshiba 110 Laptop and each time I use it the mouse is freezing after a few minutes of normal functionning. I have a Toshiba USB mouse, and I tried to use a Logitech usb mouse with the same effect. ANd of course, the same problem occurs if I use the Ubuntu Live CD. Sometimes the mouse is ok for half an our, maybe more. But finally it freezes every time. I'm very excited about Ubuntu and I don't want to give it up because of that.

---

### Post by tanari on 2007-12-02
have the same problem with ubuntu 7.10 and suse 10.3
on some forum (don't remember) I read that it is problem with new linux kernel version, but I can't find solution. Even google can't help :(

---

