---
title: "G3 Pismo, Feisty, booting from Firewire external DVD drive"
date: 2007-06-22
forum: Apple PPC Users
---

### Post by ecoppel on 2007-06-22
Hi.  I'm new.  I downloaded the PowerPC image of Feisty yesterday, and I'm trying to get it to boot.  I'll hopefully be getting another computer soon, and I'll run Ubuntu on that full-time, but for now I just want to load it from the CD and have some fun experimenting.

My computer is a Powerbook G3 with Firewire, running Mac OS 10.3.9.
My internal DVD drive is dead, so I'm trying to boot from a Firewire external DVD drive.

I burned the image to a CD-R.   I couldn't get the checksum to work, but I think that's just me not getting the checksum to work, not that it was bad.  The directories and files are there, I looked.

Here's what I've tried:

Reboot.  Held down option.  Got to the white open firmware screen.  Typed mac-boot, return.  Got this error message:
DEFAULT CATCH!
code = fffffff6
at %SRR0: ff806320
%SRR1: 00006030

Searched this forum, then tried this:
boot cd:,install\yaboot
Got this:
can't OPEN cd:,\install\yaboot

Searched here again.  Tried:
boot \\yaboot
Got this:
parsing <CHRP-BOOT>
evaulating <BOOT-SCRIPT>
method <set-colors> not found;
ihandle=ff9c9280 phandle=80
and then the same DEFAULT CATCH! errors message as before.

Searched here again.  Reset the PRAM memory with apple-option-pr.
Tried boot \\yaboot again.  That got rid of "method <set-colors> not found" etc, but gave the same DEFAULT CATCH! as before.

Tried copying all the files and directories to my USB external HD and booting from that.  I didn't expect that to work, and it didn't - didn't even show up.

I'm going to go to my parents' house tonight with the CD, to test it on one of their iMacs.
I can't try booting from the OS X system disks, as I got this computer years ago secondhand from my mother, and she didn't keep them (or, possibly, have them in the first place: my parents get the people at the shop to do the upgrading for them, and if there's a problem they just take them in again.)

Any other pointers?  Thank you for your time, and for reading all this!

---

### Post by pxwpxw on 2007-06-23
**ecoppel**

for the internal CD drive "boot cd:,install\yaboot" should work, but in your case open firmware sees a firewire drive, not a cd.

Possibly you could boot the installer in the firewire drive using
(from open firmware)
```

0> boot   fw/node/sbp-2/disk:,\install\yaboot

```
(use / to left of the : and use \ after the colon) 

I dont know if that will work for your powerbook g3, it might.

You can get a clue here ( these O/Fw commands should work for you):
```

0> devalias fw

#### if the alias fw exists, should return something like 
 /pci@xxxxxxxx/firewire@e

```
then
```

0> dev fw pwd ls

```

should show you enough to work out the rest (or post here).

However, I think a feisty live cd might have trouble after booting if it tries to mount the "cdrom" and cant find it, you would have to do that manually.  Maybe try it and see what happens.

For an install from the Alternate CD, you could use an iso downloaded to the Macosx partition, thats another story. I am assuming you dont want to install just now.

---

### Post by ecoppel on 2007-06-24
Hi, and thank you!  I've tried your suggestions, and here's what I got.

```

0> boot   fw/node/sbp-2/disk:,\install\yaboot

```

Returned:
```

method <load> not found; ihandle=ff9c9340 phandle=ff8d10d0
load-size=0 adler32=1
LOAD-SIZE is too small

```

```
0> devalias fw
```
Returned:
```
pci@4000000/firewire
```

```
0> dev fw pwd ls
```
Returned:
```
ff8d0f10: /node@0030e0005008912
ff8d10d0: /sbp-2@c000
ff8d12e8:/disk@0
```

Which is utter Greek to me.  I understood "dev fw pwd ls", but nothing after that, I'm afraid.

> **pxwpxw said:**
> For an install from the Alternate CD, you could use an iso downloaded to the Macosx partition, thats another story. I am assuming you dont want to install just now.

You're right about that too.  :-)  I want to keep Panther on my laptop and run Ubuntu on the desktop when it comes.  (It will be a PC, so much easier to install Linux on - to say nothing of working on the hardware!)

I visited my parents last night and successfully booted from the LiveCD on my mother's iMac, so I both got to have a play with it and now know that the CD does work.  So it's no drama if I can't get Ubuntu to work on the Pismo.

---

### Post by pxwpxw on 2007-06-25
Thats usefull info for me thanks re g3 pismo in general, also shows you can do booting from openfiremware. I am thinking about why it did not boot, no answers yet, will post if I think of something easy. Anyway, now you know the CD is ok.


But a question for you, how did you get the open firmware results onto the post? I would like to be able to do that. but  have to write down or photo nd then transcribe in by hand (very error prone).

Edit: having checked a Desktop CD here, you might get it to boot with thiis variation (tries partition 2) :
```

0> boot   fw/node/sbp-2/disk:2,\install\yaboot

```
I would be very interested to know what that does.

---

### Post by joninkrakow on 2007-06-26
I can't speak for others, but I have had no success getting Firewire to work on my Pismo. I have an external HD, and if it's plugged in on boot, the boot freezes. If I connect it after booting, it doesn't register as existing. USB 2.0 hard drives and CDs via a PC card show up fine, but won't boot a Pismo either. :-( You may just have to wait.

(BTW, to get around my problems, I just tossed an external 10 gig internal I had lying around into my Pismo.) ;-)

-Jon

---

