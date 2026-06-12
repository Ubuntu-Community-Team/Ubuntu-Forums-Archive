---
title: "Apple bluetooth keyboard"
date: 2005-03-17
forum: Apple PPC Users
---

### Post by noodles on 2005-03-17
Has anyone had success with the Apple bluetooth keyboard? I installed the bluez packages 
and can now see my two cell phones and my iMac, but no keyboard and mouse.

I'm using the D-Link dongle.

---

### Post by noodles on 2005-03-18
ok: here is where I am now. I have edited the file /ect/default/bluez-utils. I changed it to HIDD_ENABLED=1. Saved and rebooted. I turned the keyboard off and then back on. Then I typed HIDD --search  and got this

mordini@ubuntu:~$ hidd --search
Searching ...
        Connecting to device 00:0A:95:3E:F9:AA
Can't create HID control channel: Function not implemented


Anyone any ideas

---

### Post by noodles on 2005-03-18
I got it to work. I booted up in osX and paired it from there. When I rebooted in Ububtu it worked. There must be a way to pair it using bluez though. Hope this helps anyone thinking about using Apples BT keyboard.

---

### Post by charlesv on 2005-09-27
are you using ubuntu exclusively on your mac? I was hoping to dual boot, but don't think yaboot would recognize the bt keyboard. I've got a USB mouth, I wonder if I can rig yaboot to load one on lmb and the other on rmb.

HMM

---

### Post by notanatheist on 2005-10-21
FIRST POST! Oh, sorry, this ain't Slashdot. 

Anyway, I too have the Apple BT keyboard and would like to get it working with linux in general. No success yet on Ubuntu but I'll do more research and keep trying. I did get it working with that *other* OS on another box but I only turn that one on for 30 minutes a week.

---

### Post by tvijlbrief on 2007-03-31
I have the bluetooth mouse and keyboard working on a normal Intel Compaq notebook
with kubuntu and a usb bluetooth device:

tom@nomad:~$ hidd --show
00:0A:95:46:38:6E Apple Wireless Keyboard [05ac:0209] connected
00:0A:95:11:58:17 Apple Wireless Mouse [05ac:0309] connected

Do a:

hcitool scan

This will give you the ids.

Do a:

sudo hidd --connect 00:0A:95:46:38:6E

to connect the mouse or keyboard.

For the mouse kubuntu asked the PIN-code, I entered 0000 and it worked.

The keyboard was a bit more trial and error. It depends on the order of
switching on the keyboard, hitting some keys and entering a pin.

I suggest:

- switch the keyboard off, wait a few seconds and switch it on
- type the "sudo hidd --connect 00:0A:95:46:38:6E"
- wait a few seconds and hit "1234 return"
- the pin-code screen should pop up
- enter 1234 choose ok

After pairing the behaviour is different, so I cannot reproduce it easily.

It is good to know it works however, so just try it!

---

### Post by naag on 2007-04-02
He guys, you might also want to check out my Apple Wireless Keyboard howto at [http://www.ubuntuforums.org/showthread.php?t=224673](http://www.ubuntuforums.org/showthread.php?t=224673). Maybe this will help you.

---

