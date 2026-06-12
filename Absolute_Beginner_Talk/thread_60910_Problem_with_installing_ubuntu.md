---
title: "Problem with installing ubuntu"
date: 2005-08-29
forum: Absolute Beginner Talk
---

### Post by Uzi on 2005-08-29
When i install ubuntu 5.04, after choosing language and keyboard ubuntu says it can't copy file from cdrom.


in expert mode it looks like this:

-I choose language, select keyboard, than select "detect and mount CD-rom" it shows me long list of kernel modules /I leave them all checked/

-than it says that "some kernel modules needed to drive some of your hardware are not avaible yet. Simply proceeding with the install may make these modules avaible later, missing modules :

ide-mod (linux IDE driver),
ide-probe-mod (linux IDE probe driver),
ide-detect (linux IDE detection),
ide-floppy (linux IDE floppy) "

-then it scans cd and display that ( LOL ) "CDROM detected, the cdrom autodetection was successful. Cdrom drive has been found and it contains CD ubuntu 5.04 [...]"

-when I load installer components from CD it says "there was a problem reading data from cdrom, please make sure it is in the drive, check integrity of cd bla bla bla failed copy file from cdrom"

-on "check the cdrom integrity" it says "the cdrom you have inserted is not valid ubuntu cdrom change disk "  :? 

i tried turning off acpi /linux acpi=off/ - doesn't help
tried installing on normal, server and expert - same problems
checked iso with md5 - it's ok
tried burning on other cds with slower speed - nothing changed

WTF   :?  HELP


p.s.
ecs k7s5a, athlon xp 1600+, 768 ram
hdd - seagate 20gb ata100, maxtor 40gb ata100, seagate 8gb ata33
cdrom - lite-on 16x/10x/40x multi word dma 2

p.s.2
whz i can't see ubuntu logo on cd boot? i see only black screen with text /boot/ I know it's not important but if you know why please tell me this too

---

### Post by byen on 2005-08-29
> when I load installer components from CD it says "there was a problem reading data from cdrom, please make sure it is in the drive, check integrity of cd bla bla bla failed copy file from cdrom"

-on "check the cdrom integrity" it says "the cdrom you have inserted is not valid ubuntu cdrom change disk " 
looks like a case of corrupted disc or a corrupted iso file or improper disc write. If you have already checked the integrity of the ISO and if you are sure the ISO has downloaded properly you might wanna burn the iso into the cd again (see "deepburner" at downloads.com(free))
goodluck.

Note: 1.there is a software called winMd5sum which helps check cd integrity of you are in Windows. and 2. I strongly suggest deepburner software for burning iso file. It is free and simple as can be.

---

### Post by Uzi on 2005-08-29
it seems that my problem is similar to 

[http://ubuntuforums.org/showthread.php?t=19228](http://ubuntuforums.org/showthread.php?t=19228)

[http://www.ubuntuforums.org/showthread.php?t=57122](http://www.ubuntuforums.org/showthread.php?t=57122)

[http://www.ubuntuforums.org/showthread.php?t=37916](http://www.ubuntuforums.org/showthread.php?t=37916)


what's going on??

---

### Post by byen on 2005-08-29
> link1:result:
After the reading of the Ubuntu Faq a have found that i have downloaded
the false ISO Image.
link2:result:
Maybe I spoke too soon. I just realized that the 'does not exist' files are there, but are 0 byte files. The third error relates to the file name being chopped off on my burned cd
link3:result:
So there's something consistently inconsistent about checking the md5 sums under Windows**.this is not Ubuntu's fault!**

did you check the md5sum of the iso you downloaded as suggested?

> "the cdrom you have inserted is not valid ubuntu cdrom change disk "

did you try re-writing the image?.Please remember that  99% of these issues arise due to the problems mentioned here...so instead of a "whats going on?" may be a little patience would probably improve the situation.Please let us know if it still doesnt work after that too...goodluck.

---

### Post by Uzi on 2005-08-29
I wrote in my first post :

[QUOTE=Uzi]
checked iso with md5 - it's ok
tried burning on other cds with slower speed - nothing changed

[/QUOTE]

md5 of iso image is ok, md5 of 3 files are corrupt :
/install/netboot/pxelinux.cfg/default
/install/netboot/pxelinux.0
and one is missing /pool/main/m/mozilla-firefox-locale-all/mozilla-firefox-locale-en-gb_1.0.1lang20050309ubuntu1-0ubuntu3_all.deb


 still can't install /even on vmware with install cd mounted as iso image/

---

### Post by myk on 2005-10-07
Im having these exact problems, anyone find a solution? Thanks

---

### Post by Uzi on 2005-10-07
I had some problems with nero changes in my windows registry. Try downloading  deepburner and burn image with default options - it worked for me

---

