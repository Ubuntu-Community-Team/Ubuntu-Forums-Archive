---
title: "NTFS to FAT32"
date: 2006-05-11
forum: Absolute Beginner Talk
---

### Post by morequarky on 2006-05-11
I haven't tried, but I have heard that a person can only install XP twice without spending hours on the phone trying to get another working CD key from tech support.  To remedy this I would like to backup my NTFS partition and just copy it to another computer and have it boot. :)

I have read access to my NTFS partition.  Can I copy everything and output it to a FAT32 partition on another computer and have it boot?  How do I copy the MBR?
(FAT32, because it is such a hassle to write to NTFS)

Would it even boot after copying the MBR?

(I have already installed XP twice, don't really want to try a third time.)

Thanks for any advice.

---

### Post by Sef on 2006-05-11
> I have heard that a person can only install XP twice without spending hours on the phone trying to get another working CD key from tech support.

It is true about calling though I don't know if it is hours, but I am sure it can take that long at times.

> Can I copy everything and output it to a FAT32 partition on another computer and have it boot?

Try this, it has captive which can read and write to NTFS.

[http://trinityhome.org/trk/]("http://trinityhome.org/trk/")

---

### Post by NeghVar on 2006-05-11
Ive installed XP about 7 times and never had to call for myself, I did one for my father brand new and I had to call on the very first try.

You can convert an NTFS drive to FAT32 by using partition magic, its not guaranteed to suceed but I did it without a problem on my 40 gig. Symantec ghost, from 2002, will copy it all over and make it work perfectly, all you need is the floppy. It may take a while if you have alot of data but on a basic Win2000 install with a few programs I can have 10 computers all booted perfectly with about 10 min each and the 1st 1 just taking the time to originally load everything.

Unfortunatly I'm not sure how well XP would work, I think you would have to reactivate and it doesn't take hours once your into the process it only takes about 15 minutes.

---

### Post by cgjones on 2006-05-11
I've installed XP more then twice without having to get a new Product Key issued. It will happen eventually though. That's one of the reasons I finally switched completely to Ubuntu.

To move your XP install to another drive, I would look into some kind of disk imaging program. Norton Ghost, the **dd** command in Linux, etc.

---

### Post by Jim Hill on 2006-05-11
I had a similar problem.  I bought a Dell computer at a swap meet, XP pro and Windows Pro were installed, but no software was supplied.  If serious problems occurred, presumably I would need to buy XP and Office, plus finding all the drivers (not easy with Dell computers, I can assure you!).  The hard drive supplied with the computer was too small, so I bought another hard drive.

I used Casper XP to transfer the entire contents of the drive supplied with the computer to the new drive, and kept the original drive in a drawer as backup.  I don't remember what I did regarding formatting the drive; maybe the software supplied with the drive did the job.. If not, use Partition Magic, another great program.

Try Casper XP.  If you have any question, contact me.  I'll look for my  old notes  JJan-3atcox.net
Jim

---

### Post by morequarky on 2006-05-11
Could I "tar" hda1(ntfs) and the MBR, then output the file on a new computer?
I don't need to change my NTFS to FAT because I can already read the NTFS.  I want the new partition on another computer to be FAT32.

Issue.  I don't know how to copy the MBR.  I think "dd" can do it, but I am not sure how?  I don't want to mess up a harddrive with "dd".  Rumor has it that "dd" stands for "delete disk" or "destroy disk".  And no one wants that to happen.

I have "tar"-ed my whole system already, but it threw some errors at the end of the process and I don't know if the errors are serious or can be ignored.  I am not too excited about going through the whole "tar" process with -w option.  It would take to long, but I might need to make sure what the error was, unless there is an output file somewhere.

Let's try to stay away from paying for software.  I ain't rich.  And the linux tools are probably superior anyways.

Thanks.

---

### Post by Sef on 2006-05-11
> If not, use Partition Magic, another great program.

Partition Magic is not advised with GNU/Linux.  They tend not to get along too well.  If you want to use a proprietary partitioner, system commander works much better.

---

### Post by Clay85 on 2006-05-11
[QUOTE=cgjones]I've installed XP more then twice without having to get a new Product Key issued. It will happen eventually though. That's one of the reasons I finally switched completely to Ubuntu.
[/QUOTE]

I do a lot of hardware work as a hobby, switching hardware on windows makes it freak out. Although, I've never had to call tech support. (I have OEM versions, which may allow the keys to be used an infinite number of times, I'm not sure. OEM WINXP versions come with two CPU keys anyway.)

 If I swap my ubuntu hard drive into another machine will it freak out over all the new hardware, like windows does? (obviously there's no key, but I mean will it be okay with the change?)

---

### Post by morequarky on 2006-05-11
**[COLOR="Red"]@clay85[/COLOR]**

What do you mean by windows freaking out?  I would guess it would bounce the "new  hardware" message a bunch of times wanting to know about the new hardware.  Is that such a bad thing?

---

### Post by Clay85 on 2006-05-12
morequarky,

Most of the time when I switch my main HDD to another windows box as Primary Master Windows crashes. Hard. Two or three times I've had to hurry and burn as much stuff as possible to CD before the HDD corrupted itself beyond its capacity to keep running Windows. Then I reformat the HDD and re-install windows. (fool me once...haha! You can bet I'm not doing that anymore!)

If I switch my HDD as Primary Master to another Ubuntu box, will it corrupt my hard drive disk?

---

### Post by jdusablon on 2006-05-12
The problem is the hard drive controller. If you move an XP install to a new computer, chances are very high that it will blue screen and give you a "INACCESSIBLE_BOOT_DEVICE" error. This is because it can't find any device(s) attached to its systemroot harddrive controller driver. Unless you can load the new HDD controller driver into the XP system before moving it, you won't have much luck.

Personally, I use a pci HDD controller, get SP to recognize it, reboot with the HDD connected to this controller, shutdown. Then I move the HDD and the pci controller to the new machine and boot. Once XP has detected all its new gear, I shutdown and move the HDD onto the local (built-in) controller in the new machine. If all goes well, XP will now run on the new machine. This does fail 20% of the time, though.

It is possible to get lucky enough for the HDD controller in the new box to be close enough to the old one that XP will boot.

---

### Post by Clay85 on 2006-05-15
Is that an XP specific problem?

---

