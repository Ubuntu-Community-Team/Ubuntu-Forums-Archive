---
title: "My Snes9X won't run my games. Why?"
date: 2008-02-16
forum: Apple PPC Users
---

### Post by khelben1979 on 2008-02-16
I get this message when I try to run a snes game:

Write 03 to 432b!
Write 03 to 431b!
Write 35 to 431b!
Write 35 to 430b!
Write 00 to 430b!
Write 35 to 437b!
Write 00 to 437b!
Write 00 to 436b!

It just keeps on looping and I can't run any games because of this. :-( I know that snes9x works on my hardware, although it's very old by todays standards... So, I need support here.

First I compiled snes9x from source code and I got this message and then I tried the ubuntu packages of 1.42-2 of both the common package and the snes9x package itself.

---

### Post by jsmiith on 2008-02-16
What ROMs are you using? They might be corrupted. I use snes9express from the repos and it runs super mario and super mario cart fine for me. Thats all I have tried.

---

### Post by erginemr on 2008-02-16
If you do not dislike ZSnes particularly, I suggest you to download and try it:
[http://www.getdeb.net/app/ZSNES](http://www.getdeb.net/app/ZSNES)

---

### Post by khelben1979 on 2008-02-16
Okay, so I have recently configured zsnes from source code and I get an error when I try to compile it. Is there a deb package for ppc available for zsnes somewhere? (I have been unable to find it...)

When it comes to snes9x I have recently reinstalled the one which comes with the Etch distribution and apparently today it went through some kind of software update. This is what happens now:

bear@81-224-174-203-o1123:~/emulering/SNES_ROMS$ snes9x 7th\ Saga\,\ The\ \(U\)\ \[\!\].smc
Reading config file /etc/snes9x/snes9x.conf
Controller Port 1: Pad 1
Controller Port 2: <none>
Rate: 22050, Buffer size: 2048, 16-bit: yes, Stereo: yes, Encoded: no
No ROM file header found.
"" [bad checksum] LoROM, Corrupt, Type: ROM only, Mode: 00, TV: NTSC, S-RAM: 0KB, ROMId:  Company: 00 CRC32: AC2C5EE1
joystick: No joystick found.
Can't open "/dev/mem", full screen mode not available: Permission denied
Unrecognized input device name 'K00:grave'
Could not map 'Superscope ToggleTurbo' to 'K00:grave'
Unrecognized input device name 'K00:grave'
Could not map 'Superscope ToggleTurbo' to 'K00:grave'

What's wrong?

---

### Post by stmiller on 2008-02-16
Try one of the snes9x front ends. You need more options than just 'snes XXX.smc' on the command line.

---

### Post by chipants on 2008-02-19
i never really dug into it, but, snes9x has trouble running fullscreen unless you run as root (or via sudo). also, snes9x pretty much fails if the options aren't set exactly right. so, you should really try to run it with minimal options, and add them one by one to make sure you're using them correctly. i've had it die because of errors setting up gamepad buttons.

if you're going to use a frontend, you should definitely use snes9express. although, some default settings in the repo version of snes9express are incorrect, and may cause a failure to launch a rom. for example, if you use a gamepad, it looks for it in /dev/js0. this is not correct. i believe (i'm at work on a *grrr* windows machine) it should be /dev/input/js0. but, double-check that first.

---

