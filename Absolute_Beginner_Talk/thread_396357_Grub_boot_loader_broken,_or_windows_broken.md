---
title: "Grub boot loader broken, or windows broken?"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by BeastlyKings on 2007-03-29
My WinXP partition will not boot.
I had WinXP then I added ubuntu and everything worked for awhile but then the windows partition would not boot, telling me "Error 13: Invalid or unsupported executable format".
Please help, I need windows for work but I don't want to dish out $99.99 for a new WinXP Cd.

Oh, here is some other info:
[http://paste.ubuntu-nl.org/11954/](http://paste.ubuntu-nl.org/11954/)
[http://paste.ubuntu-nl.org/11956/](http://paste.ubuntu-nl.org/11956/)

PLEASE HELP?


-BK

---

### Post by undertherift on 2007-03-29
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

Check that thread out and see if it works.  You might just need to trick grub.

Alternatively, if you have a rescue disk or partition or something, you could run fixmbr ( which would wipe out grub) and give you a working windows.  

Then you could reinstall grub and see if it works.

---

### Post by psusi on 2007-03-29
Do you get this error before, or after choosing windows from the grub menu?

---

### Post by BeastlyKings on 2007-03-29
I have already tried that, it says drive does not exist or something along those lines.
I think I have to change the drive names, but I do not know what to change them to or where to put the changes.

---

### Post by BeastlyKings on 2007-03-29
@psusi
after choosing windows

---

### Post by confused57 on 2007-03-29
> **BeastlyKings said:**
> I have already tried that, it says drive does not exist or something along those lines.
I think I have to change the drive names, but I do not know what to change them to or where to put the changes.
Did you recently add the sda drive or change the hard drive boot order in bios?
You might want to make sure that your IDE drive (hda) is selected to boot before your sda drive.

---

### Post by BeastlyKings on 2007-03-29
I checked and it was selected to boot before hda, I changed it but still no luck.

WILL this work if I change some stuff around for a 1 HDD system?
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

if so, how do I do that?
I'm a newb so please go easy on me.

---

### Post by confused57 on 2007-03-29
> **BeastlyKings said:**
> I checked and it was selected to boot before hda, I changed it but still no luck.

WILL this work if I change some stuff around for a 1 HDD system?
[http://ubuntuforums.org/showthread.php?t=282545](http://ubuntuforums.org/showthread.php?t=282545)

if so, how do I do that?
I'm a newb so please go easy on me.

If you're able to boot into Ubuntu or have access to another pc, you might want to burn a copy of the Super Grub Disk(500 kb download):
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
SGD is capable of booting Windows or Linux & restore your mbr

Do you get a grub menu when you boot first to your SATA drive?  What you could try at the boot grub menu is highlight your Window's entry, press "e", change the root to (hd1,0), then press "b" to boot...if this doesn't work, you could try adding the mapping lines mentioned in the link you listed.

I think the Super Grub Disk may be your best option to get back into Windows.

---

### Post by BeastlyKings on 2007-03-30
Even with super grub disk (which I'm not all that sure how to use) I couldn't boot windows, it gave me the same error when trying with the grub disk.
Then I tried what you said about changing the root boot line in grub, same error.

---

### Post by BeastlyKings on 2007-03-30
Please don't stop replying, even if you could just guess at the problem.
I REALLY NEED HELP!

---

### Post by confused57 on 2007-03-30
Haven't been on the forums for the past several hours, just saw your reply.  Here's a description of error 13:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#13](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html#13)
from reading this you "might" need to get your hands on a Window's install cd & run recovery mode with the command FIXBOOT.

Here's a link that would be worth trying:
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
read the section "Boot Windows using the Command Line" (CLI).

Another link from the same website:
[http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP](http://users.bigpond.net.au/hermanzone/p6.htm#A_Birdss_eye_view_of_Windows_XP)

The homepage for the above links is the first one in my signature...hopefully this will help.

Added:  See reply #10 about Tom's boot disk in this thread:
[http://www.ubuntuforums.org/showthread.php?t=236471](http://www.ubuntuforums.org/showthread.php?t=236471)
Creating a boot disk for NTFS:
[http://support.microsoft.com/kb/305595/EN-US/](http://support.microsoft.com/kb/305595/EN-US/)
[http://tinyempire.com/notes/ntldrismissing.htm](http://tinyempire.com/notes/ntldrismissing.htm)

Sorry I can't offer you a specific solution since I haven't actually had to repair my Window's boot sector...I hope some of the links I've provided will help...good luck.

---

### Post by confused57 on 2007-03-31
Probably won't work, but you could try this Window's entry:
```
title		Microsoft Windows XP Home Edition
rootnoverify    (hd0,0)
makeactive
chainloader	+1
```

---

### Post by BeastlyKings on 2007-04-01
Thank you for the links but I kinda re-installed Ubuntu in a feeble attempt to make grub load windows, While partitioning the table I noticed that Gparted could not detect the file system used on hda1, my windows partition.
What does this mean?
I tried doing this because someone on the #ubuntu channel over at irc.freenode.net server said this could work.

I guess I'm screwed now and I have to buy a new XP cd?

---

### Post by undertherift on 2007-04-02
Since your #1 priority is to get back into windows, i would say make a best effort to run fixmbr.  This will wipe out grub, and atleast you'll be able to get back into windows no problem.

Don't have an XP cd, right?  So check this out. 
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/) 
I've never used it, don't know if it works, so use at your own risk.

Also, this one looks a little more appropriate, but im not sure whats happening on the download page.
[http://ubcd4win.com/index.htm](http://ubcd4win.com/index.htm)

See how far you can get.  I did some cursory reading and it seems like it might help you.

After that, we can reinstall grub, and see what happens.

---

### Post by psusi on 2007-04-02
Yea, it sounds like your windows partition got screwed up.  Try the fixboot and fixmbr commands from the recovery console ( borrow a windows cd if you need to ) and see if that fixes it.  

By the way, if the computer came with windows on it, it should have come with a windows install cd as well.  If not, call the vendor and demand one.

---

### Post by BeastlyKings on 2007-04-03
I'm still working on it, I will fill you in later thanks all for the replys.

---

### Post by BeastlyKings on 2007-04-04
Well I tried ubcd and nothing couldn't download that other thing.
So now, I'm going to have to find a XP cd?
I think I'll ask one of my friends , they might have one.
So just get the XP CD and run FixMBR?

---

### Post by psusi on 2007-04-05
Yes, and you should call the vendor who sold you the pc and make them send you the install cd.

---

### Post by LaurelLynn on 2007-04-05
Dear BeastlyKings,

The very first thing I would do is make sure Windows is still there. Boot to Ubuntu (the Live CD if you have to).  From there you can mount your Windows partition and browse through the files.

If the filesystem is intact **then** it´s a bootloader problem. If it´s gone I´m afraid reinstalling may be the only option :( 

Laurel Lynn

---

### Post by BeastlyKings on 2007-04-06
Well, when I use Gparted it says the filesystem is unknown.
How would I go about mounting it if it WAS still intact?

---

### Post by BeastlyKings on 2007-04-06
@psusi
This PC is old and I got it at staples.
Its a hp pavilion ze4300, I don't know if they would still do that for me.

---

### Post by BeastlyKings on 2007-04-22
Nevermind guys, I bought a new WinXP cd, installed ubuntu then installed WinXP in VMware player.
All is fine again.

---

