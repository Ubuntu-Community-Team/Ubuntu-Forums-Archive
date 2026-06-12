---
title: "[SOLVED] Help - I've just mkfs-ed a partition I shouldn't have"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by gmjs on 2008-01-09
OK, I feel very very very stupid, but I've run mkfs -t vfat on device /dev/sda1 instead of /dev/sdf1 (while trying to format a USB flash drive).

This is a BIG problem as /dev/sda1 is (OK was) my Windows system partition with the Windows NTLDR that I used to boot both Windows and Linux.  My data's on another partition (thank goodness) but before I shut down Linux, reinstall Windows and all its software and replace the NTLDR settings, am I living in a dream world in hoping that I can reverse this?

I know everyone and everything in life hates me and that everything goes wrong for me if it can, but it's getting silly now!

Graham :cry:

---

### Post by gmjs on 2008-01-09
Everyone's just laughing at me, aren't they?  I'll reinstall Windows now.  I hate myself.

---

### Post by Mr. Altaco on 2008-01-09
We don't want to make you feel bad.  All we want to do is help man, we're not out to get you.  Someone here may be able to help you yet.

---

### Post by kinson on 2008-01-09
Don't be so hard on yourself man, we all make mistakes, if not we'd never learn.

Unfortunately I'm still rather new myself, and can't offer much to help. Look on the bright side though..**your data is fine**, and to me, thats the most important thing.. My computer (whom I love very much and wish she was a living hot blooded woman) could burst into flames for all I care(I seem to be contradicting myself here...), as long as my data is backed up somewhere, haha :P

But just to be extra sure, make sure you've backed up your data elsewhere (on another physical disk) before you try to reformat Ubuntu/XP again, just in case. I've had friends lost their data cause they accidently formatted their data drive in the process of trying to install Ubuntu.

Cheers,
Kinson

---

### Post by gmjs on 2008-01-09
Wow - everyone's so understanding.  That's the Ubuntu ethos is that!  I've reinstalled Windows.  I'd forgotten just how many updates etc (SP2) my copy needs!  Windows does nothing out of the box!  All data safe though (phew - I was most bothered about my sister's coursework; I can't reinstall that)!  How to learn the hard way...

And I second that - if only this PC was "a living hot blooded woman".  Think we're on the wrong forum for that!  Never mind.  (There might be girls out there into computers who don't mind their data going missing every now and then!)

Happier now,

Graham

---

### Post by kinson on 2008-01-09
Glad you've more or less got it sorted out, and are feeling better :)

Cheers,
Kinson

---

### Post by mdpalow on 2008-01-09
LOL...

I think I might have even done worse than you once before, but I'm not going to tell everyone what I did. Yours was a quick typo or maybe even a brain cramp - mine was plain stupid.

Anyways... when you get it all up and running again - make a back-up. I'll be putting out an update to my script (see link below) hopefully tomorrow or the next day and if you download it, you'll be able to back-up your Master Boot Record (MBR) and Windows partition right from Ubuntu. You'll even be able to restore them both with a click of the mouse from Ubuntu. That'll surely save you a lot of time if you do it again.

By the way, it's really not that stupid unless you make the same mistake twice! ;)

Live and learn; right?

take care...

---

### Post by Ionesco on 2008-03-18
Hoho. I just did exactly the same thing with my Vista/Boot partition. Only problem is my data is on that partition as well. Any ideas how to solve it? Please... Isn't there a nice little program one can use to fix it all with a click?=)

---

### Post by The Cog on 2008-03-18
I'm not aware of any way to recover from a formatted drive. mkfs is the same as **format C:** which is kind of brutal. There may be tools out there that can help, I don't know. Try goolging around for "rescue CD" or "recover formatted drive" and see if that turns up anything useful.

---

### Post by bodhi.zazen on 2008-03-18
You may be able to recover some data 

See these links :

After formatting : [http://ubuntuforums.org/showthread.php?&t=401093](http://ubuntuforums.org/showthread.php?&t=401093)

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) 

[http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk)
		How to testdisk : [http://www.debian-administration.org/articles/420](http://www.debian-administration.org/articles/420)
	[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)

[http://mirror.href.com/thestarman/asm/mbr/DataRecovery.htm](http://mirror.href.com/thestarman/asm/mbr/DataRecovery.htm)

---

### Post by Ionesco on 2008-03-18
Testdisk worked fine with the deepscan option! Found all my old partitions and got them back.:) Only problem is that the computer didn't boot so I started messing about with Grub. Sucessfully got up Grub booting again and Ubuntu booted just fine. Vista though didn't start and just restarted the computer when I picked that option. So I did some Grubbing again and put in 

root (hd0, 4)    // This is partition /dev/sd5 where my old Grub config files and everything seemed to be, on the linux drive

and after that I did
setup (hd0, 1)  // This is my Vista partition /dev/sda2

So I thought I was booting from the Vista partition, something I maybe read somewhere that I have to do if Vista should boot. Heh #-o. The latter command made the filesystem on the Vista partition faulty, I cannot longer read files from it. 

So...
Any idea how to undo the grubbing out of the Vista partition?



Here is all the partitions I got now (Sda1 is another ntfs partition that I grubbed over so that I can't read the files on it's filesystem):

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          14         275     2097152    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2             275       17800   140775416+   7  HPFS/NTFS
/dev/sda3           17801       19457    13309852+   f  W95 Ext'd (LBA)
/dev/sda5           17801       19381    12699348   83  Linux
/dev/sda6           19382       19457      610428   82  Linux swap / Solaris

---

### Post by dacorr on 2008-03-18
it should of just rewritten the partition entry for the windows partition, but the data is still intact, you need to look about recovering the partition. once recovered you may need to check the bootloader to make sure its pointing to the right place still.

Dac

---

### Post by Ionesco on 2008-03-18
Hmm. I didn't really know how to recover the partition so I booted with the Vista cd and did a startup recovery, that didn't work. Then I tried it again.  That didn't work. Then I had a backup of the partition table in testdisk since after I fixed it that I recovered. That ofcourse didn't work. Then I did a deep analyse with testdisk. Suddenly when testdisk is at 50% with the deep analyse the sda1 (extra NTFS) and sda2 (Vista OS) is readable again. No idea why.:confused:

Now I just have to get Vista booting again through Grub. So I tried the startup recovery thing from the Vista CD and that fixed the problem. Shouldn't have messed about so much in Grub before =D

So now approx 12 hours later after I mkfs-ed vfat-ed my entire hard drive I got both Ubuntu and Vista bootable again. :KS Thank you testdisk! And thanks for the help everyone!

---

