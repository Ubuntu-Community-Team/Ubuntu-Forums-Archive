---
title: "CMOS Password Unknown"
date: 2006-12-23
forum: Absolute Beginner Talk
---

### Post by rbhigday on 2006-12-23
I found this program by chance and It peaks my interest and may intall it on one of my many extra hard drives to see how it functions.

But for now I have a few question. A co-worker husband passed away and left his laptop password protected, via cmos for the pc and the hard drive and now I am looking at a ubuntu password.  The logical password have been tried with no luck. Thus I tried to install the hard drive into my pc but while the pc see the hard drive none of the 4 partions on this laptop hard drive load to my pc.

Thus my questions. 1 I run windows xp (yes I hate windows but have bowed down to the greater evil) and am wonder if I would be able to see files on a hardrive with Ubuntu loaded.

Second is it possible for the person to encrypt the whole hard drive including access to any and all partitions.

is there a work around to get past the software password.

Any and all help will be greatly appreciated. as is where i can dl this program :)

---

### Post by kidders on 2006-12-23
Hi there,

> **rbhigday said:**
> A co-worker husband passed away and left his laptop password protected, via cmosThere should be a CMOS password reset jumper you can use to fix that :-)

> **rbhigday said:**
> the pc see the hard drive none of the 4 partions on this laptop hard drive load to my pc.What partitioning scheme is used, I wonder? Does your "dmesg" reveal anything useful?

> **rbhigday said:**
> I run windows xp (yes I hate windows but have bowed down to the greater evil) and am wonder if I would be able to see files on a hardrive with Ubuntu loaded.Do you mean Ubuntu is on the hard drive? If so, the answer is no ... at least out of the box.

> **rbhigday said:**
> Second is it possible for the person to encrypt the whole hard drive including access to any and all partitions.Yes, it is ... but it's unlikely that someone would do that, I'd say.

---

### Post by michaeljustman on 2006-12-23
Answers to two of your questions...

From Windows XP there is a program for mounting your Ubuntu partition (or hard drive)... can't remember the name of it. (Using Linux right now... (Actually... haven't been to windows for two weeks at least.))

Anyway... sorry.... Google for "mount EXT2 in windows" and you should find it.

Ubuntu will read your ntfs (Windows) harddrive when you first install it, but requires NTFS-3G for reading and writing.

Hope that helps.

---

### Post by rbhigday on 2006-12-26
I have gotten past the cmos and cmos hard drive password with help from DELL

I have installed the hard drive on my Windows XP

I looked for mount ent2 drives and I am now able to assign letters to all 4 and actually see files on 1 of the 4 partitions. The other three are label Linux and my only options are to format all 3 of these partions.

dmesg I am assuming is a unix command as it did not work in XP run funciton. (Hey I will try anything once, worst case reinstall :))

Any suggestion or did I miss a step?

---

### Post by rbhigday on 2006-12-27
Update.

I now have Ubuntu install on my laptop and have the other laptop hard drive connected via USB port.
I can see all the files without any problems, even the windows(BLEH) ones. :)

Thanks for all the help so far.

Now I am wondering if a few other things are possible.

I would like to know if it possible to undelete files that were deleted and how to do it. Files were deleted the day before the owner passed away. 

I am also wondering if there is anyway to determine the user name and password for Ubuntu on his hard drive? or if the file is editable to allow automatic login?

---

### Post by Sef on 2006-12-27
Check out [Trinity Rescue Kit]("http://trinityhome.org/Home/index.php?wpid=1&front_id=12").

---

### Post by rbhigday on 2006-12-30
ok dumb question 5 million and three :)

How do I change drives or directories trk I not even sure if it loading the USB drive either. My command promt expericance for unix is very little and about 5 to 10 years ago.

---

### Post by Malta paul on 2006-12-30
If your drives are mounted you will find them under 'Places'.
You may like to checkout [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) and [http://ubuntuguide.org/wiki/Ubuntu:Edgy](http://ubuntuguide.org/wiki/Ubuntu:Edgy) 
Hope this is of some help ;)

---

### Post by rbhigday on 2006-12-30
The drives load under Ubuntu with no problem but when your using Trinity Rescue Kit i had the impression that was a bootable software with it own OS. Does it use the same commands as Ubuntu I could not find any guild for TRK. Will look again ](*,)

---

### Post by msandersen on 2006-12-30
In answer to a question above... The Windows Ext2/3 Driver is here:
[http://www.fs-driver.org/index.html](http://www.fs-driver.org/index.html)
With it, you mount selected ext2/3 Linux partitions with Drive letters. Normally, you wouldn't mount the Root partition, but in this case you might.
It doesn't implement Unix permissions though, nor does it allow you to hide dot-files. And you must shut down Windows, not suspend, before switching over to Linux, or you may have trouble accessing. Also, I found trying to write to an ext2/3 partition in Windows when it is full, eg extracting a large archive, Windows will become almost nonresponsive, slowing down to the speed of molasses.

As for recovering a Windows password: Here's one how-to using a Linux rescue CD called Emergency Boot CD:
[http://www.elamb.org/hacked/ebcd.htm](http://www.elamb.org/hacked/ebcd.htm)

There would be others.

---

### Post by macogw on 2006-12-30
Pull out the battery.  The BIOS password will reset.

EDIT: the cmos battery, not the regular battery.

---

### Post by msandersen on 2006-12-30
> **rbhigday said:**
> The drives load under Ubuntu with no problem but when your using Trinity Rescue Kit i had the impression that was a bootable software with it own OS. Does it use the same commands as Ubuntu I could not find any guild for TRK. Will look again ](*,)
Having a quick look on their page:  Yes it's a LiveCD with its own OS. It is based on Mandrake (currently v10.2), so there are some differences. You'd have to read the FAQs, it is a bit of an expert tool.

This one might help:
[http://trinityhome.org/Home/index.php?wpid=7&front_id=12#winpass](http://trinityhome.org/Home/index.php?wpid=7&front_id=12#winpass)
It's an included script that will parse the Windows partition and allow you to reset the Administrator password. You may want to read the info on the chntpw command they link to and heed the warning.

MountallFS will mount all filesystems:
[http://trinityhome.org/Home/index.php?wpid=7&front_id=12#mountallfs](http://trinityhome.org/Home/index.php?wpid=7&front_id=12#mountallfs)

---

### Post by ragadanga63 on 2006-12-30
If you are recovering files while in Windows, try R-Studio.  It can recover files which have been deleted  and even from formated hard disks including those from Linux partition.

---

### Post by msandersen on 2006-12-30
On Windows, the best data recovery program I've seen is GetDataBack from Runtime software [http://www.runtime.org/gdb.htm](http://www.runtime.org/gdb.htm)
It's a comprehensive data recovery program that's also easy to use. Obviously, you shouldn't use the Windows partition in question until you've recovered any data you need, but then of course installing the said program would do just that if it was the System partition, which is likely in Windows, as having a separate partition for My Documents is rare. At least it is a small program.
If he had Norton Unerase or similar installed, you might already be able to do it.

---

