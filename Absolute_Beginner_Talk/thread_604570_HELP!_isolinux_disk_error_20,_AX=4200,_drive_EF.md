---
title: "HELP! isolinux: disk error 20, AX=4200, drive EF"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Muad Dib on 2007-11-06
Hi,
I have read through numerous threads trying to find the answer to my latest installation error.  Most of them stop before a conclusion.  There's some back story to this.  My apologies for being long winded.  I have burned seven or eight iso images to date.  The first was a copy of Fiesty Fawn that got me to an "I/O Error: reboot".  I tried downloading again and again.  I finally did a bit torrent download of Gutsy Gibbon.  My first burn left me with a blinking cursor.  The current burn gets me an "isolinux: disk error 20, AX=4200, drive EF".  It seems that with each burn, I get a different error message or problem.  I have ordered the disks from Ubuntu, but would like to know if I can overcome this error message somehow by adjusting something in the computer.  Any suggestions?  Please dumb down your recommendations.  I am not a techie.

Thanks,
Cam

---

### Post by nickbooker on 2007-11-06
First, try burning the discs at a lower speed, and check the maximum speed the discs themselves can cope with.  Burning at higher speeds may produce coasters.  Make sure you've got Burnfree enabled if your drive supports it.

It's also worth checking the MD5 checksum of the image you download against the one listed in the MD5SUMS file on the download server.  On Linux, you can do this by typing at the command line: ```
md5sum downloaded.iso
```  If the file gets corrupted during download, it won't work.

If the image verifies, you may be using poor quality discs -- try burning a disc from a new pack.

Failing that, it might be either your cd writer or cd reader -- try burning and booting from a different machine.

---

### Post by Muad Dib on 2007-11-06
I checked the Md5sums.  I went out when I first started trying to burn a disk and got Memorex High Speed CDR/W instead of the store brand I was using.  Then, I burned at 4X.  After that I tried a few more downloads of Ubuntu and even some other Linux systems to no avail.  When I boot up the Windows OS and see if it recognizes the disk, it sees the Ubuntu 7.10 disk and I can open it with explorer and see all the files.  The burn LOOKS good.  I just can't seem to get it to install.  Is there a setting on the PC that I am missing or some other more technical issue that I am not doing?  I'm infuriatingly stumped.  Please bring on the suggestions.  I know that if I can make the switch and learn to use Linux, I'll be much better off.  Thanks.

---

