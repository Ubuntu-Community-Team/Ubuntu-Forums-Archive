---
title: "Trouble getting Ubuntu boot disk to work"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by Jameson_Styles on 2007-03-14
I downloaded Ubuntu 6.10 and burned it onto a disk using Nero Express 6. I specified that Nero create it as a boot disk, and burned the ISO to the CD without a problem. When I went to start up the computer, I inserted the disk and went to BIOS, specifying that only the CD-ROM drive was to be booted from. It got as far as recognizing the disk and starting Caldera DR-DOS, but then gave me this error:

EMM386: Warning: Address line A20 already enabled.

Stuck there still as I type this post. 

I thought that specifying the disk as a boot disk may have been the problem, so I burned one as just a plain old data disk which it refused to even try to boot from.

I have no idea what to do from here. What other programs work with burning the Ubuntu ISO image that people ahve used and know for sure that they work?

---

### Post by overdrank on 2007-03-14
> **Jameson_Styles said:**
> I downloaded Ubuntu 6.10 and burned it onto a disk using Nero Express 6. I specified that Nero create it as a boot disk, and burned the ISO to the CD without a problem. When I went to start up the computer, I inserted the disk and went to BIOS, specifying that only the CD-ROM drive was to be booted from. It got as far as recognizing the disk and starting Caldera DR-DOS, but then gave me this error:

EMM386: Warning: Address line A20 already enabled.

Stuck there still as I type this post. 

I thought that specifying the disk as a boot disk may have been the problem, so I burned one as just a plain old data disk which it refused to even try to boot from.

I have no idea what to do from here. What other programs work with burning the Ubuntu ISO image that people ahve used and know for sure that they work?

Hi and welcome but if you would use this link 
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
and burn the cd as slow as you can, it will work for you. Good luck!

---

### Post by orkim on 2007-03-14
And, just as a follow up.  You typically wont enable the "bootable cd-rom option" if you are buring a ISO.  Just burn the disc image and it should create a bootable cd-rom for you.  This special boot sector (el Torro) is already "in" the ISO.  Defining it again would be redundant.

By the way, when booting Ubuntu, you shouldn't see a DR-DOS prompt.  I'm assuming that is something that Nero had done to the image.

Hope that helps.

-orkim

---

### Post by Enginer on 2007-03-17
This is precisely the problem I was having.  I could not get the desktop or server version to boot.  I tried the desktop version, burned as an ISO to a CD-R disk at reduced speed (16x) to boot, so I told to make the disk bootable.

It comes up as drive A:/ in DR-DOS, and says it is booting from the 3.5 inch floppy, whereas it can only be booting from the CD-ROM because the floppy drive is empty.  Therrefore DR-DOS must be on the CD-ROM disk.   But...

DIR says the disk as A:\ has 142,848 bytes remaining, and no other (than DR-DOS) files show on the disk.  Putting the disk in a drive on an XP computer shows a file called ubuntu-6.06.1-desktop-i385.iso   at 715,172 KB  as an Image File.  I thought DR-DOS should be able to read Ubuntu files if they were on the disk.

I remember somewhere seeing that if this were a good burn then the individual files would show on the ISO image.

Please, I need help!

---

### Post by 3rdalbum on 2007-03-17
> **Enginer said:**
> This is precisely the problem I was having.  I could not get the desktop or server version to boot.  I tried the desktop version, burned as an ISO to a CD-R disk at reduced speed (16x) to boot, so I told to make the disk bootable.

In Nero, use the option "Burn Image to Disc". DO NOT choose "Make bootable CD" or whatever it's called; as the above poster said, this is incorrect. The ISO already contains everything it needs to be bootable. If you burn a disc and DR-DOS comes up, then you've done it wrong.

Also, when we say "burn at a lower speed", we're really talking about 8x here. And use the desktop version, not the server.

---

### Post by Enginer on 2007-03-17
Boy, that was fast!   As soon as I finished sending that last post, I burned the server edition as an ISO and it booted to ubunto just fine.

Fantastic results, guys!

---

