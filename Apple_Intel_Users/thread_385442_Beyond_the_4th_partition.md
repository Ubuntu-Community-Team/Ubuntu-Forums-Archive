---
title: "Beyond the 4th partition"
date: 2007-03-15
forum: Apple Intel Users
---

### Post by oskarloko on 2007-03-15
I've a triple booting system, which I've like this

```

Current GPT partition table:
 #      Start LBA      End LBA  Type
 1             40       409639  EFI System (FAT)
 2         409640     63324199  Mac OS X HFS+
 3       63324200     94044200  Basic Data
 4       94044201    124764201  MS Reserved
 5      124764202    126812202  Linux Swap
 6      126812203    156296384  MS Reserved

Current MBR partition table:
 # A    Start LBA      End LBA  Type
 1              1       409639  ee  EFI Protective
 2         409640     63324199  af  Mac OS X HFS+
 3 *     63324200     94044200  83  Linux
 4       94044201    124764201  0b  FAT32

```

And it works fine... almost fine. I want a partition just to share data between all OSs.

I'm planning to install Ubuntu Feisty - currently I'm writing from a Egdy - on the 6th partition ( now i'ts fat32, but this will change soon...)

And make the 4th one to be fat32 to share data, just every system can access it without pain.

( I tried with ext3 drivers for winxp and mac, but for the osx the drivers are very buggy )

I'm using refit to launch every OS. GRUB is now on the 4th partition - only booting the tux one. 

So... 

¿ It's possible to use GRUB2/PUPA to boot on the 6th partition ?
¿ Maybe ELILO ?
¿ Can it work with a simple GRUB ?


( I'm afraid it'll be myself who answer these questions... after a hard try-error phase :-P  )

Thanks !!

---

### Post by oskarloko on 2007-03-15
*(I cant wait to said this, even is  off-topic here  )*
... it makes me feel me strange, the new web-theme on ubuntu web and ubuntu forums...
... a little more commercial and.. cold ?   :confused:

---

### Post by redfox on 2007-03-15
(Continuing off-topic...)

Pretty much the main thing that attracted me to Ubuntu originally was the website and forum.  Very simple and unconfusing, with a current web design.  I tend to judge projects by their web pages.  (That pretty much killed my impression of Debian. :D)

I guess somebody figured it was time for a site design.  I wonder if it's too much on the minimalist side?

(... end digression.)

You're right.  You're probably on your own with your setup.  There doesn't seem to be many 'already been there many times' experienced people in this segment of the Ubuntu world.

---

### Post by oskarloko on 2007-03-16
... I'm thinking I'll wait until a second beta release.. 

MacBooks are now PC (intel-based) but aren't just standart PC hardware...

As far as I can see, Feisty will suit better on the C2D apple macbook, but tweaking - maybe a lot - will be neccesary.

and tweaking into a unstable system can become hell-like system


Well, there's no reason to stop really: also Egdy is far from a 100% setup, and most things will apply onto the Feisty

---

### Post by jtholmes on 2007-03-21
Grub2/PUPA is Grub2
Yes you can do it in Grub2 (dont know how but Grub2
is a rewrite of Grub and there is no reason it wont
do what you want

Dont know about ELILO

Yes simple grub will work, I do it all the time
However I make things easier on myself and
created a boot floppy and grub will boot any
slice that way. Of course floppy drives are
scarce on Laptop these days so that may
be a bit of a delima.

---

