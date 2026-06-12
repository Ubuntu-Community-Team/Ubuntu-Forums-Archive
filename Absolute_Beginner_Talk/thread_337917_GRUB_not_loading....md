---
title: "GRUB not loading..."
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by proginoskes on 2007-01-13
When I ran Dapper on my macbook off the live cd it worked like a charm - wireless, the works. But now that I've installed it, when I try to start Ubuntu the screen reads:

GRUB loading, please wait...

...and then nothing, not even an error number to let me know what's wrong. Could anyone tell me wat's going on? I've tried searching existing threads but couldn't find anything quite like this.

---

### Post by confused57 on 2007-01-13
Check out this link for grub errors:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#Grub_Errors)

The Gentoo Grub error link mentioned that setting your floppy drive to boot after your HD may be a fix.

---

### Post by proginoskes on 2007-01-14
Thanks for the link.

...How exactly would I change the order in which it boots? I'm pretty new at this.

---

### Post by confused57 on 2007-01-14
> **proginoskes said:**
> Thanks for the link.

...How exactly would I change the order in which it boots? I'm pretty new at this.

I've never used a Mac computer, so I don't if it's any different than an Intel-based pc.
On my pc's I can enter bios by pressing a key(or combination of keys) while the pc is booting up(it may be displayed which keys you'd need to press)...then there should be an option in your bios setup menu to select the order in which you would like your floppy, cd, hd's, USB, etc to boot...if you feel comfortable doing this, make sure you write down the initial settings and the changes you made so that you can go back into bios and change them back if there's problems.  There are no guarantees changing the boot order will correct your grub not working...you might first want to try to reinstall grub(see below).

You may want to wait on someone who has experience with a macbook to tell you exactly how to do this.

Another option would be to download the Super Grub Disk, it's a great tool for booting different OS(Linux & Windows...don't know about Mac OS):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

You might try installing grub, using the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub](http://www.ubuntuforums.org/showthread.php?t=224351&highlight=live+cd+grub)

You might want to do a search on the forums or google for grub problems & restoring the  mbr for a macbook computer...I really don't feel qualified to give you advice & hopefully someone with Mac & Linux experience can help you.
Added:  You might want to checkout this link:
[http://www.ubuntuforums.org/showthread.php?t=187465](http://www.ubuntuforums.org/showthread.php?t=187465)

---

