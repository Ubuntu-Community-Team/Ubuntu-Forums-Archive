---
title: "Which version to replace windows 98"
date: 2007-01-26
forum: Absolute Beginner Talk
---

### Post by GoneWithTheWind on 2007-01-26
I've a second computer with windows98 and would like to run Ubuntu on it, to run a program called RowIt via the USB port.  The w98 program asked me to insert the w98 disk for this, which I don't have as the computer is one someone was tossing away.  All I want to do at this point is to run the program RowIt to use while I'm rowing.

1)  Which version of Ubuntu should I download and install?

2)  Should I partition the HD the same as I did on the computer with wxp, then install the alt cd the same way?  I presume it's the same but want to make sure.

3)  Will the USB port work automatically or else what program would I need to add to run that.

I've done a search for windows98, found only 8 threads and none about installing ubuntu on it so please don't jump on me for asking a question that was probably asked before.  I also searched for "windows 98" but that didn't work.

I have looked for the processor speed but don't know how to find that with w98.

Thanks much.

---

### Post by meng on 2007-01-26
Ubuntu is a separate OS, you don't install it on WIndows 98. This program you're hoping to use sounds like a Windows program, and therefore will not run on Linux. Windows emulation is available for Linux but is primitive.

---

### Post by Sef on 2007-01-26
> 1) Which version of Ubuntu should I download and install?

Either Edgy 6.10 or Dapper 6.10.  Edgy is the latest Ubuntu.  Fairly stable, but could be some problems with the software as it is newer.  Dapper is the long term stable.   Very few conflicts if any, but upgrades are far and few between to new applications; hence, the app tend to be older than Edgy's.

> 2) Should I partition the HD the same as I did on the computer with wxp, then install the alt cd the same way? I presume it's the same but want to make sure.


How did you partition it before?

> 3) Will the USB port work automatically or else what program would I need to add to run that.

It should work automatically.

> I've done a search for windows98, found only 8 threads and none about installing unbunu on it so please don't jump on me for asking a question that was probably asked before. I also searched for "windows 98" but that didn't work.


If anyone jumps on you for askng you this or any question related to Ubuntu, contact a moderator to handle it.  Please provide a link to the thread and the post number, if you do.

Question for you:

How much ram does your computer have?

---

### Post by GoneWithTheWind on 2007-01-26
Yeah I know it's a separate os.

My question is if Ubuntu will run on an older win98 machine and what version to use.

RowIt runs on Linux or windows.  I want to run it with Linux.

---

### Post by pay on 2007-01-26
The usb drive should work fine. You could install a dual bootsetup, meaning that you make 3 partitions, one for Windows, and two for Ubuntu (one's a swap).

---

### Post by GoneWithTheWind on 2007-01-26
> **Sef said:**
> Either Edgy 6.10 or Dapper 6.10.  Edgy is the latest Ubuntu.  Fairly stable, but could be some problems with the software as it is newer.  Dapper is the long term stable.   Very few conflicts if any, but upgrades are far and few between to new applications; hence, the app tend to be older than Edgy's.

Thanks much.    :)   I have Dapper 6.06 on alt cd and presume that will work then.

> How did you partition it before?

I partitioned this wxp computer with a 0.3.1-1 gparted live cd.

> It should work automatically.

Wonderful!  :D 

> How much ram does your computer have?
I think it is 64 - not sure how to find the info with w98.

As always I am very impressed with the quick and helpful responses on this forum. 

Thanks much.

---

### Post by meng on 2007-01-26
With 64 MB, consider running Fluxbuntu or Damn Small Linux rather than any of the official Ubuntu flavors.

---

### Post by GoneWithTheWind on 2007-01-26
Pay,

Thank you.  I will do that.

---

### Post by GoneWithTheWind on 2007-01-26
Meng,

Okay thanks.  I will try and find out the ram.

---

### Post by meng on 2007-01-26
I seem to recall that Windows 98 control panel has a section called System, that should tell you how much RAM you have. But I may be thinking of ME or XP!

---

### Post by Pobega on 2007-01-26
> **meng said:**
> I seem to recall that Windows 98 control panel has a section called System, that should tell you how much RAM you have. But I may be thinking of ME or XP!

Actually, just right click My Computer and go to properties, or something similar. The information for your computer should be listed there :D

And run dxdiag to figure anything else out.

---

### Post by GoneWithTheWind on 2007-01-26
It is 64 ram and 160 mhz - dxdiag did the trick.

Yikes I thought it was faster than that so will give it away.

I've another with no OS and will install Ubuntu on that, provided it is fast enough.

Thanks for all the great responses.  :D

---

### Post by Pobega on 2007-01-26
You actually *could* run Ubuntu on that, but I would recommend the [Fluxbox Flavour of Ubuntu](http://fluxbuntu.org). If you can't get that to work, do an Ubuntu Server install and apt-get all of the needed packages to get a working GUI, then install Fluxbox.

Fluxbox is nice, customizable, skinnable, and lightweight. If it supported more keyboard shortcuts than it does I would use it myself.

---

### Post by GoneWithTheWind on 2007-01-26
Pobega, thanks much.

I've got two other tossaways and know one of them is 128mg/533mhz.

Is there any way to find the ram and processor speed on the one with no OS?

---

### Post by GoneWithTheWind on 2007-01-26
I clicked all the download links for dslinux, fluxbuntu, puppylinux and keep getting a bunch of directories, forums, and articles but nowhere to download.  When there is a download link it sends me to more directories, forums or articles - this is the beginner forum right.  :o 

Okay, I had a tooth pulled this morning and now I'm getting a headache.  Will take another look soon.

---

### Post by meng on 2007-01-26
[http://ftp.heanet.ie/mirrors/damnsmalllinux.org/current/](http://ftp.heanet.ie/mirrors/damnsmalllinux.org/current/)
[http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/)
[http://www.puppylinux.org/user/downloads.php?cat_id=1](http://www.puppylinux.org/user/downloads.php?cat_id=1)

You're looking for the iso (CD image) file.

---

### Post by GoneWithTheWind on 2007-01-26
> **meng said:**
> [http://ftp.heanet.ie/mirrors/damnsmalllinux.org/current/](http://ftp.heanet.ie/mirrors/damnsmalllinux.org/current/)
[http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/](http://modzer0.cs.uaf.edu/~hardwarehank/fluxbuntu/rev2/)
[http://www.puppylinux.org/user/downloads.php?cat_id=1](http://www.puppylinux.org/user/downloads.php?cat_id=1)

You're looking for the iso (CD image) file.

Okay I see need to burn the iso image like before.

Will do.  Thanks.

---

### Post by irish_flu on 2007-01-26
> **John Rupp said:**
> Pobega, thanks much.

I've got two other tossaways and know one of them is 128mg/533mhz.

Is there any way to find the ram and processor speed on the one with no OS?

You can find out the amount of RAM installed by going into the BIOS (sometimes called "Setup" screen right as the machine starts to boot.  Usually you have to press "Del" or "F2" or something to get there, your machine should tell you.

You might be able to find out exactly what the processor is from there too, it kind of depends on the computer.

---

### Post by GoneWithTheWind on 2007-01-27
> **irish_flu said:**
> You can find out the amount of RAM installed by going into the BIOS (sometimes called "Setup" screen right as the machine starts to boot.  Usually you have to press "Del" or "F2" or something to get there, your machine should tell you.

You might be able to find out exactly what the processor is from there too, it kind of depends on the computer.

Thanks, Irish.

I tried to plug in that computer tonight and got a spark from the wall plug.  :shock: 

So now I'm a bit reluctant to try it again.  The problem must be either the cord, the tower, or a makeshift trackball.

---

### Post by stevieb on 2007-07-16
John,

was there any luck getting rowit to work with ubuntu?

-steve (atheist on the C2 forums)

---

