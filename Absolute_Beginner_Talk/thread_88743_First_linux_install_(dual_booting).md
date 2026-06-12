---
title: "First linux install (dual booting)"
date: 2005-11-11
forum: Absolute Beginner Talk
---

### Post by BurningToad on 2005-11-11
Hey, I'm wanting to learn some about linux.

I figure the best way is to just try an install and get it all set up and then play with that.

So my plan is to dual boot XP with some linux distro. So far i've only really looked at unbuntu.

One of the main reasons I want to start learning linux is that most of the computers in my CS program here at university use it. I think most are Debian but some newer ones are Unbuntu.

Anyways, at first i'll just use it for basic stuff, plus maybe some java programming.

It seems like Unbuntu should do me fine... any reason to go with Breezy over Hoary? (edubuntu over unbuntu)

Also, as I plan on dual booting, what is the best setup?

I have two hard drives, should I put windows on one and linux on the other? Is a swap partition for unbuntu really needed? I guess my initial thoughts about a setup are...

200gb drive - SATA
one huge NTFS partition for windows xp + installed programs + storage

120gb drive - IDE
10-20 gb partition for unbuntu (ext3? not sure what that means)
2gb partition for swap? I have 2gb RAM
the rest FAT32 for dual storage?


What are the benefits of NTFS? Should I just make my XP partition FAT32 to maximize my storage flexability?

Also, if I setup my drives like the above, how would it go about booting when I turn on my computer? Would I get an option to pick which OS, or would I need to go into my bios to pick a certain drive for boot priority?

Oh, and I'm actually going to try WinXP 64 bit edition if that makes any difference.

I'll probably be adding a 3rd hard-drive soon for backup purposes... not for disk images or anything, just for saving stuff that I don't want to lose should something go bad.

---

### Post by aysiu on 2005-11-11
Read these links in this order:
[http://www.psychocats.net/essays/linuxguide.php](http://www.psychocats.net/essays/linuxguide.php)
[http://distrowatch.com/dwres.php?resource=major](http://distrowatch.com/dwres.php?resource=major)
[http://www.zegeniestudios.net/ldc/](http://www.zegeniestudios.net/ldc/)
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Manny C on 2005-11-11
> **BurningToad]Hey, I'm wanting to learn some about linux.

I figure the best way is to just try an install and get it all set up and then play with that.

So my plan is to dual boot XP with some linux distro. So far i've only really looked at unbuntu.[/quote]

You mean Ubuntu.  said:**
> 
One of the main reasons I want to start learning linux is that most of the computers in my CS program here at university use it. I think most are Debian but some newer ones are Unbuntu.

Anyways, at first i'll just use it for basic stuff, plus maybe some java programming.

It seems like Unbuntu should do me fine... any reason to go with Breezy over Hoary? (edubuntu over unbuntu)

Breezy is the newest version of Ubuntu and probably has the best hardware support. You probably want Ubuntu over Edubuntu as it probably targets you better. Unless you a school child you probably don't want Edubuntu.

[quote=BurningToad]
Also, as I plan on dual booting, what is the best setup?

I have two hard drives, should I put windows on one and linux on the other? Is a swap partition for unbuntu really needed? I guess my initial thoughts about a setup are...

200gb drive - SATA
one huge NTFS partition for windows xp + installed programs + storage

120gb drive - IDE
10-20 gb partition for unbuntu (ext3? not sure what that means)
2gb partition for swap? I have 2gb RAM
the rest FAT32 for dual storage?
[/quote]

For installation questions, please read [this]("https://wiki.ubuntu.com/Installation"). Any questions that are unanswered, do not hesitate to ask here.

[quote=BurningToad]
What are the benefits of NTFS? Should I just make my XP partition FAT32 to maximize my storage flexability?

Also, if I setup my drives like the above, how would it go about booting when I turn on my computer? Would I get an option to pick which OS, or would I need to go into my bios to pick a certain drive for boot priority?

Oh, and I'm actually going to try WinXP 64 bit edition if that makes any difference.

I'll probably be adding a 3rd hard-drive soon for backup purposes... not for disk images or anything, just for saving stuff that I don't want to lose should something go bad.[/quote]

You can't install Linux on NTFS.  And yes one does ideally need SWAP. 

I think it is best that you first read the wiki entry and then ask any unanswered questions.

---

### Post by spin1078 on 2005-11-11
as far as windows goes, NTFS has file security and fat32 doesnt.  theres more to ntfs but thats the biggest difference.  

dual booting linux can be fun.  i tried it just recently and i dont know anything bout linux.  waht i did was use partition magic to do some things.

Linux needs to a swap partition, preferably before the partion you install it on.  I created a 50mb partion at the beginning of the harddrvie, before the windows partition, for the /boot area.  KNOW THIS, the bootloader oyou choose (i used GRUB) installs itself on the MBR.  this was not fun to fix the first time i botched a linux install.

ok so i have 4 partitons, i used Partion Magic 8.0 to make.  one small one for the boot (i think the actually reccomended size is at least 75 MEGS) then my windows Primary partion, and a 1.5GB swap partion (should be 2-3 times your RAM amount) and a partion for the Root install.  Ubuntu will convert the Root partion to EXT3 which is a linux filesystem and the swap is a Linux Swap format and i think my boot is EXT3 aswell.  has to be.

do all that and dont forget to make a recovery CD for XP, if you screw up the MBR its not fun to fix.  FIXMBR didint work for me.

oh im running windows 2000/ubuntu 5.10 dual boot.  ibm p3 733 mhz 300PL (jacked from old job hehe)

good luck man!
brad

---

### Post by BurningToad on 2005-11-11
I'm working on checking out those links

A quick question though, can Windows XP read the ext3 partitions?

---

### Post by aysiu on 2005-11-11
[QUOTE=BurningToad]I'm working on checking out those links

A quick question though, can Windows XP read the ext3 partitions?[/QUOTE] Not without some kind of helper program.

---

