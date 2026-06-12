---
title: "soundcard problem"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by darkeale on 2007-02-23
ok im trying to get my soundcard back. i was suffering from the only one app. can use it at a time and after following a how to its not working at all now. 

0000:00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8 237 AC97 Audio Controller (rev 40)
Subsystem: C-Media Electronics Inc: Unknown device 0301
Flags: medium devsel, IRQ 5
I/O ports at e000 [size=256]
Capabilities: <available only to root>

this is my soundcard in lspci -v

ithink the problem is where i configured using this line -

sudo ./configure --with-cards=hda-intel

when install the alsa driver.

what would i change hda-intel to to correctly configure my soundcard?

and also does anyone know how to get multiple apps sound working on this soundcard?

---

### Post by darkeale on 2007-02-23
got it back. hda-intel had to changed to hw

still stuck on the multiple sounds tho...

---

### Post by tcebak on 2007-02-23
hey awesome job.  ok that fourm did not work for me either. ok so this is what i have
00:1b.0 Audio device: Intel Corporation 82801FB/FBM/FR/FW/FRW (ICH6 Family) High Definition Audio Controller (rev 03)
        Subsystem: Dell Unknown device 01c9
        Flags: bus master, fast devsel, latency 0, IRQ 169
        Memory at dfebc000 (64-bit, non-prefetchable) [size=16K]
        Capabilities: <access denied>

you said something about sudo and "your cards" what do i put there thanks(or is there a step by step forum) thanks

---

### Post by darkeale on 2007-02-23
sudo ./configure --with-cards=hda-intel

you mean that line? have you lost sound all together?

---

### Post by tcebak on 2007-02-23
hmmm when i type that it says command not found. no thankfull i did not lose all sound. i was joking that it was awsome you sound went away. i had an error half way through so i stoped. it was probley a typo but oh well. this is a sucky problem.

---

### Post by darkeale on 2007-02-23
yeah it certainly wasnt awesome. this problems getting really frustrating now. think i might just invest in the cheapest compatible soundcard money can buy whatever it may be

---

### Post by tcebak on 2007-02-23
yeah its crazy. i take it your on a desktop. i am converting a dell laptop and i had some major problems with the wireless card. but i think i am just going to listen to music with only one program. which sucks. becasue that means when i switch i have to close everything. but i think i am going to ask some on the linux user's here and see if they have a solution. we meet in two weeks but i can't wait. wow this was a long point less post.

---

### Post by darkeale on 2007-02-23
yeah this is my desktop i built years ago. strangely i stopped using windows (well apart from it being rubbish) because of my soundcard. the driver kept making the system reset and there was no fix. i thought my soundcard troubles were behind me when i switched to ubuntu but apparently not

---

### Post by tcebak on 2007-02-23
well i am going to grab some food. haven't eaten all day. stupid energy. but maybe i get relaxed and stop cussing every five seconds. and find something.

---

