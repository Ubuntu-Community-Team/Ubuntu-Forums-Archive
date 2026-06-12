---
title: "Bluetooth Mouse, 12.04 Macbook Pro 8,1"
date: 2012-06-09
forum: Apple Hardware Users
---

### Post by Radly on 2012-06-09
I have a triple-boot (OS X 10.6.8, Win7/64, Ubuntu 12.04) running on my Macbook Pro 8,2, and all is well except for today.  I have been using a wireless USB mouse for months, but now I'd like to have that USB port back, so I am trying to move to a Bluetooth Mouse.  I bought a Logitech V470, which works nicely on Windows and OS X, but won't pair on Ubuntu 12.04.  It occasionally shows up in the device list, but pairing fails.  So I have a couple of questions:

1.  Are there any bluetooth mice that are known to work in this context?

2.  Is the Logitech V470 one of them?

3.  What might I be missing?

---

### Post by markmaus on 2012-06-10
I just installed Lubuntu 12.04 on a MacBook Air.  It dual boots with OSX.  I'm using a Logitech Bluetooth Mouse. Unfortunately the part number is illegible on this mouse.  At first it would not connect in Linux. I played around with it until it was visible. Then I think that the correct settings, under Bluetooth Devices, are:
Device/Setup/Proceed without pairing/Input Service.
I think that input services means keyboards and mice.
My biggest problem is that when typing, the touchpad seems to move the cursor to random points on the screen.  I must have had to relocate the cursor every four or five keystrokes when typing this message.  It has made Linux unusable on this machine.

---

### Post by Radly on 2012-06-10
My problem is that I can't reliably get the device to show up in the list.  I notice now (after rebooting) that at boot time I'm getting a popup asking if I want to allow the mouse access to a service (with a really long identifier), to which I reply "Grant", but that doesn't seem to matter much.

And FWIW, my Macbook is really an "8,2"--I didn't notice that I fatfingered that when I made the original post.

I guess I'll keep fiddling around with it.  Fortunately, it's a low priority issue, as Mac and Windows are where I make my living.

---

### Post by eivindsm on 2012-06-16
There are known bugs related to dual booting and Bluetooth. See eg this thread: [http://ubuntuforums.org/showthread.php?t=1980171](http://ubuntuforums.org/showthread.php?t=1980171)

---

### Post by daryllee on 2012-06-18
Thanks.  I'll just stop worrying about this.  I'm just glad I'm not a heavy Ubuntu user on my laptop.

---

### Post by kgunn72 on 2013-02-15
OK, had the same trouble...but solution was much easier than what is posted here.

Using GUI....go to the "Ubuntu Software Center"...search for Blueman Bluetooth Manager....install it. Reboot. Click on the new bluetooth spider icon appearing in your indicator icons (or launch the app from the dash).....then click setup device.
It found my mouse....viola.

note, i was using newish macbook pro, dual boot, ubuntu 12.10+ using a Rocksoul bt mouse.

hope it helps.

---

### Post by Radly on 2013-02-23
Thanks for the tip, but not only did it not work, it left me a bit concerned about "Blueman".  After trying a few options, I clicked Help on the app and tried "Get Help Online".  The site it took me to blueman-project.org, is a newly expired domain name.  I guess that's life in the fast lane, eh?

I see you're running 12.10.  I tried upgrading but got a warning about graphics support, so I backed off.  I may need to try that again, but it's a hassle due to the manual wifi installation required.

---

