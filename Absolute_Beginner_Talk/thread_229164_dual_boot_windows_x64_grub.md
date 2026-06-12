---
title: "dual boot windows x64 grub"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by jrussel316 on 2006-08-04
I currently have windows x64 installed on a slave drive, and ubuntu 5.1 on my master.  I'm trying to configure grub to boot my windows install as well, and have tried adding quite a few different things to my menu.lst file, as well as reinstalling ubuntu to see if grub would autodetect my windows install, but nothing has worked.  here are all the relevant files I know of:

device.map
(hd0) /dev/hda
(hd1) /dev/hdb

menu.lst (or at least what's immediately relevant - if more is needed i can provide it, but i'll have to type it myself since I haven't gotten my linux install online yet and dont have east access to a usb drive)

title Windows XP x64 Professional
rootnoverify (hd1,0)
map  (hdo) (hd1)
map  (hd1) (hd0)
makeactive
chainloader +1


and here's the error I get when I try to boot windows: 
A disk read error occurred

thanks for your help

---

### Post by anaconda on 2006-08-04
This is from my menu.lst (I also have windows on a separate hd (hdb))

# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title		Windows NT/2000/XP (loader)
map (hd0,0) (hd1,0)
map (hd1,0) (hd0,0)
rootnoverify (hd1,0)
chainloader	+1

so I think you should have the rootnoverify.. after remapping the hd:s..
And the makeactive isn't necessary, but it wont hurt. (your windows partition should be active partition already)

---

### Post by jrussel316 on 2006-08-04
I just tried putting the rootnoverify after the map commands, and it still gives me the disk read error.  Playing around with it some more, I found that if I use:
title Windows XP x64 Professional
rootnoverify (hd1,0)
chainloader +1
makeactive

I dont get an error, but it doesn't do anything either.  Not exactly progress, but then again I really dont know what it is.

Is there anything other than menu.lst that I should be editing to make it boot windows? ubuntu didnt detect my windows install, so im configuring it all from scratch, if that makes any difference.

thanks, 
jrussel316

---

### Post by confused57 on 2006-08-04
This link may help you, maybe not:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

You definitely need the mapping commands to boot Windows, if you haven't already, make sure the slave drive is enabled in bios.

In Ubuntu, you might want to check the output of:
```
sudo fdisk -l
```
The -l is a small "L"

This will show the partitioning of both drives.

---

### Post by jrussel316 on 2006-08-04
thanks so much - im up and running now.  the bit about checking to see if my hdb is enabled in bios did the trick - wasnt exactly what was needed, but got me thinking on the right track.  Turns out there was something wrong w/ my jumpers on my slave - when I set the drives up it was pretty much guess and check cause I really didnt feel like pulling the drives out to read their jumper diagrams, and so I moved the jumper to a position I hadnt tried yet, and it booted right up =)

---

