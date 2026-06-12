---
title: "USB Stick"
date: 2007-12-25
forum: Absolute Beginner Talk
---

### Post by skymera on 2007-12-25
its Christmas day, yay

i got a new memory stick for my college work, its an Integral 2GB password protected stick.

when i plug into ubuntu nothing happens..
the install is 20mins old, anything i need to download? tyhanks!

_____________________

also i installed ubuntu on a new seperate hard drive, how do i make windows appear on Grub?
or even mount it?

---

### Post by %hMa@?b&lt;C on 2007-12-25
after you plug it in, try typing 
"dmesg |tail" into terminal and please post the output.,

---

### Post by skymera on 2007-12-25
right this appears:

scott@scott-desktop:~$ dmesg |tail
[ 1225.639280] scsi 8:0:0:1: Direct-Access              Removable Disk   PMAP PQ: 0 ANSI: 0 CCS
[ 1225.883719] sd 8:0:0:0: [sdc] 4026368 512-byte hardware sectors (2062 MB)
[ 1225.884339] sd 8:0:0:0: [sdc] Write Protect is off
[ 1225.884342] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1225.884344] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1225.887711] sd 8:0:0:0: [sdc] 4026368 512-byte hardware sectors (2062 MB)
[ 1225.888361] sd 8:0:0:0: [sdc] Write Protect is off
[ 1225.888365] sd 8:0:0:0: [sdc] Mode Sense: 23 00 00 00
[ 1225.888367] sd 8:0:0:0: [sdc] Assuming drive cache: write through
[ 1225.888371]  sdc:
scott@scott-desktop:~$ 


so im guessing its being detected

---

### Post by %hMa@?b&lt;C on 2007-12-25
hmmm....
its getting detected, what exact brand/model is it.
just to see if it is indeed not mounted try typing in "sudo fdisk -l"

---

### Post by skymera on 2007-12-25
crap i cut up the book getting it out the stupid packaging bear with me...

ok got it

Integral Ice 2GB USB 2.0 Password Protected Flash Drive

says it needs Windows 98 - XP and Mac 8.6 - OSX

No linux? maybe it has somesort of software on it..like the U3 drives

---

### Post by %hMa@?b&lt;C on 2007-12-25
can you boot into mac/win and see if it needs to be set up/needs software?

---

### Post by skymera on 2007-12-25
sureee...

but i dont have windows in grub, thats my second question ^_^

---

### Post by bern1939 on 2007-12-25
Don't know if this means anything but I plugged in a new 2gb Datatraveller and nothing happened after 5 minutes.
I unplugged it and re-inserted it ... and lo it found it ..... perhaps first time it was just looking for the correct driver!!
Good luck & Happy Christmas!


Bern

---

### Post by skymera on 2007-12-25
yeah you too!

---

### Post by skymera on 2007-12-25
got it to mount.

but shows up as 2MB!?

which is strange, XP is saying it has 2GB

and my dads isnt showing up at all!

he wants me to burn him a CD with K3B but i cant even get the songs off of his USB Stick

---

### Post by skymera on 2007-12-25
its reporting that the drive is actually a Fat12 filsesystem, which to my ubuntu is unknown.

any thing that can mount it?

---

### Post by %hMa@?b&lt;C on 2007-12-25
you may need to reformat it.

---

### Post by skymera on 2007-12-25
meh i really cba with it.

i'll stick to using it windows :)

thanks for your help anyway

---

