---
title: "Ubuntu installation hangs on Macbook Pro"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by agiveon on 2006-11-13
ok... I am very close to giving up on Linux... I tried Fedora.... and hit a wall... now the same with Ubunto... 

It seems like all the instructions everywhere assume you have used UNIX / Linux sometime... not very newbie freindly...

I have a MacBook Pro, and I want to have dual boot with the OSX.. I downloaded the CD image... burned it... I installed rEFIt and using bootcamp I set aside 20GB...

I started the installation of ubuntu... and it hangs...

now what?

---

### Post by aysiu on 2006-11-13
Your original title "About to give up on Linux..." may get a lot of attention, but it won't get you the help you deserve. I've changed the title to be more appropriately descriptive.

If your Ubuntu installation hangs, it probably has to do with one or more of the following:

1. Bum CD (either corrupted during download or during burning process)
2. Hardware failure
3. Insufficient RAM

Considering you have a Macbook Pro (relatively new), I doubt it's #2 or #3.

So it's probably a bad CD.

This thread may help:
[Cannot burn iso](http://ubuntuforums.org/showthread.php?t=11266)

Unfortunately, in terms of "instructions everywhere assum[ing] you have used UNIX / Linux sometime," I'm afraid the documentation for Macbooks or Mac anything-related-to-Linux is pretty scant and does make a lot of assumptions.

Documentation for switching from Windows to Linux is abundant and very user-friendly. Not much on using Disk Utility to do checksums or burn ISOs, not much on EFI instead of BIOS, etc.

---

### Post by agiveon on 2006-11-13
I agree regarding the title :)

As for the ISO. I downloaded it in Windows... I have no clue how to use the checksum thing... can it be used in Windows?

---

### Post by aysiu on 2006-11-13
> **agiveon said:**
> I agree regarding the title :)

As for the ISO. I downloaded it in Windows... I have no clue how to use the checksum thing... can it be used in Windows?
Oh, you have Windows, too? Great!

I wrote some detailed instructions with screenshots on how to burn an ISO correctly. There are three parts to it: downloading, checking the integrity, and then burning. Skip the first part, but play close attention to the second part, and keep in mind that for burning, the slower you burn it, the more likely it will keep the integrity of the ISO:
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by bodhi.zazen on 2006-11-13
Two links that may help:

[md5sum](http://ubuntuforums.org/showthread.php?t=290339)

[Install Ubuntu on a MacBook](http://doc.gwos.org/index.php/InstallUbuntuMacBook)

---

