---
title: "Recommendation for Live USB with encrypted persistent file."
date: 2012-10-05
forum: Any Other OS
---

### Post by kircher on 2012-10-05
Hi all,

I am after recommendations and suggestions for a distro suited to a live USB. My requirements are the following:

[LIST]
[*]Must have encrypted persistence
[*]Persistence must be able to be larger than 4GB (limit imposed by FAT32)
[*]Must be fairly high performance
[*]Preferrably, but not essentially based on Debian. I know, and am used to the apt package management. I also know yum.
[/LIST]

Knoppix would appear to be ideal for this. I tried it, but could not get it to boot from a USB formatted in ext2/4. I could only get it to boot when using a FAT32 partition, but this restricted my .aes persistent file to only 4GB, which is unacceptable. I could not work out how to move this persistent file to another partition either, and the Knoppix documentation I found was very out of date. Apparently older versions of Knoppix easily allow the persistent file to be moved to wherever the user would like...

Any ideas, suggestions and recommendations would be greatly appreciated, even if it means something custom. I also tried a full-blown Ubuntu installation on a USB flash drive, but this proved to be too laggy whenever I was writing to the drive, since it is not optimised for live use.

---

### Post by kircher on 2012-10-08
I assumed this problem would have a simple solution that I had missed or over-looked. Am I asking in the wrong forum? Would I be better off asking the question elsewhere?

---

### Post by critin on 2012-10-08
> **kircher said:**
> I assumed this problem would have a simple solution that I had missed or over-looked. Am I asking in the wrong forum? Would I be better off asking the question elsewhere?

It  probably moved to the next page before those who have recommendations could see it.  You can bump the post if no reply in 24 hours to get it back on the front page--and you just did that.  :P

I don't have a proper answer but the forum is okay.  Someone will be along.  I assume you've tried googling with basically the same question?

---

### Post by kircher on 2012-10-08
I feel I've exhausted what google can provide. The searching of the knoppix forum doesn't seem to be of much help, either. I guess most people are happy with 4GB of storage space on an encrypted persistent live distro.

I did find some information, but it's for an older version of Knoppix which allows the user to move the persistent file to whichever location they want, but the utility the article describes doesn't exist in the newer version.

I guess an alternative would be to use an older version of Knoppix.

---

### Post by sidzen on 2012-10-08
Have you tried [Puppy Linux]("http://puppylinux.com/development/howpuppyworks.html")?  One is able to use a larger USB stick formatted to ext2 and encrypted.  Don't know exactly what you want or why, but puppy works.

---

### Post by kircher on 2012-10-09
Thanks Sidzen. I shall try Puppy Linux. I was already going to, but couldn't find any information to confirm whether it allowed for an encrypted persistence. Now you confirm it.

---

### Post by oldfred on 2012-10-10
I think these are full installs. If writes are minimized & you have a good amount of RAM system can be responsive even with USB flash.

It does not have to be encrypted BIOS based system:
Standard full install with screenshots to flash or SSD:
Ubuntu Encrypted Flash Memory Installation using alternative text based installer
[http://members.iinet.net/~herman546/p19.html](http://members.iinet.net/~herman546/p19.html)
More discussion Dec 2010, more SSD info
[http://ubuntuforums.org/showthread.php?t=1643591](http://ubuntuforums.org/showthread.php?t=1643591)
[http://ubuntuforums.org/showthread.php?t=1404664](http://ubuntuforums.org/showthread.php?t=1404664)

Backtrack persistent install to USB
[http://www.infosecramblings.com/backtrack/backtrack-4-bootable-usb-thumb-drive-with-full-disk-encryption/](http://www.infosecramblings.com/backtrack/backtrack-4-bootable-usb-thumb-drive-with-full-disk-encryption/)

You could use Lubuntu as it is lighterweight.

---

