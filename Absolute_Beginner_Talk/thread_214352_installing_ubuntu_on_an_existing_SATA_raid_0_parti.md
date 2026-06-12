---
title: "installing ubuntu on an existing SATA raid 0 partition"
date: 2006-07-12
forum: Absolute Beginner Talk
---

### Post by nismo on 2006-07-12
note:  This is the first time I've ever used any incarnation of linux before in my life, though I am a very experienced windows/mac OS user.  However, I know very little or nothing at all about linux terminal commands.  It'd be helpful if any help you can give me regarding the terminal to solve this problem is more or less guiding me by the hand.

Anyway,  I have 2 300gig maxtor SATA drives on a RAID 0 stripe set, via my onboard raid controller (sil 3112) on my a7n8x deluxe 2.0.  These are the only drives in my system, I have no other IDE hard drives.

I'm not sure whether you guys would classify this as hardware raid or fakeRAID, but the stripe set was setup during boot up directly after the bios (press alt-k to set up raid devices).

When I run ubuntu off the latest 6.06 live CD, open the synaptic package manager, and download dmraid off of the repositories previously unchecked, the ubuntu install program will see the partitions I've already created using the windows XP initial blue screen installation.  When I go to install Ubuntu on the partition I had set aside for it, I choose "Erase entire partition" or whatever, and it gets to 15% before it gives me the error "Failed to create file system".  I've tried formatting the partition with gparted, and wiping the partition of any filesystem whatsoever.  No matter what I do, I still get the error "Failed to create file system" at 15%.


Anybody have any ideas?

---

### Post by araz on 2006-07-12
I hade the same error and solved it by compiling a custom kernel. Before adopting such a radical move try install the ubuntu using a alternate cd.

---

### Post by nismo on 2006-07-12
how exactly do I compile a custom kernel?

---

### Post by araz on 2006-07-12
Thats the wrong question:(. Look at one of this [How-to]("http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16")    maybe it will change your mind. But first you'l have to put some linux OS working to compile the new kernel (may not be a solution for you).

---

### Post by nismo on 2006-07-12
Well I booted off the alternate install CD, and I tried both the text install and the OEM install, and neither would recognize my raid set nor its partitions (just like live mode won't until I install dmraid).  Also I see no way of loading dmraid in the alternate install for it to be able to recognize the partitions.

---

### Post by nismo on 2006-07-12
> **araz said:**
> Thats the wrong question:(. Look at one of this [How-to]("http://ubuntuforums.org/showthread.php?t=157560&highlight=2.6.16")    maybe it will change your mind. But first you'l have to put some linux OS working to compile the new kernel (may not be a solution for you).

So I can't recompile a kernel in live mode or from windows?

---

### Post by araz on 2006-07-12
> **nismo said:**
> So I can't recompile a kernel in live mode or from windows?
I hope some one help you with this, cause i don't know:???: .

---

### Post by nismo on 2006-07-12
eh forget it, I guess I'll just try SuSe, my frend says SuSe has better SATA and RAID support.  Maybe when I get comfortable with compiling kernels I'll recompile for ubuntu with better support for my raid controller.

---

### Post by kspades on 2006-07-17
If Im not mistaken the a7n8x deluxe 2.0 uses software raid....the bios level stuff is mis-leading because its really only a pointer to the drives for the Asus RAID software that only runs under windows. I had a simular issue with my MSI board...I was sooo excited when I got it cause it said it supported RAID 1...only to find out its RAID1 for winblows...oh well.

To answer your ? I dont know why your filesystem format bombs at 15%, however I do know that when I had the "Raid" thingy enabled in the bios I got all types of odd detection issues both during install (of a few different distro's) and after while the kernel was running. 

I havent used suse since ver. 10 and to tell you the truth its not much better at raid. Actually I think Dapper does a much better job at Raid than Breezy did. Case in point Im currently typing this from the Dapper LIVE CD. My boot drive failed 4 days ago and my home directory is stored on my RAID 1 sata drives (same MSI mobo with that BS bios raid nonsence turned off). I booted from the Dapper LIVECD, mounted my raid 1 volume and aside from the annoying occasional CDROM drive read its performing great...I've been running like this for 3 days now, and will be till newegg deliver my new drives....this is why Im a linux user!

---

