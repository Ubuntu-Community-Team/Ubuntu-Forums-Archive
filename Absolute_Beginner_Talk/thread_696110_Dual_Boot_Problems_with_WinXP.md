---
title: "Dual Boot Problems with WinXP"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by gemmala on 2008-02-13
Hi,

I just installed Gutsy on my computer - using the LiveCD to partition my hard drive. First installation I managed to screw up - didn't work. So I started installing again - this time I could only access the partition I'd set aside for the failed installation previously, but using that I managed to successfully install Ubuntu - leaving 3.5GB left to the failed installation in a separate partition. It loads up alright, however when I select that I want to boot from Windows, it goes to a black screen saying "Starting up..." and stays there. I can still access the data in the Windows partition, but that's it.

Any suggestions?

---

### Post by LRT on 2008-02-13
if you don't care too much about your data, or can easily back it up, i would start all over again following this [HOWTO]("http://www.howtoforge.com/dual_boot_windows_xp_vista_ubuntu_feisty")... i followed it and it worked very nicely for me. (it uses ubuntu feisty but should also work for gutsy).

---

### Post by Ek0nomik on 2008-02-13
You can still probably avoid all the hard work of reinstalling.  Can you post the output of this command so we can get a better look at your hard drive:

```
sudo fdisk -l
```

---

### Post by carverj on 2008-02-13
If the problem is GRUB related, the link in my signature may help!

---

### Post by Tylazene on 2008-02-18
Hi,

I just wanted to revive this thread because I seem to be having the exact same problem. When I choose windows XP it shows "Starting up" in a black screen but never does. Ubuntu comes up no problem. It can even see all the files in the windows partition. I am probably using Ubuntu now more than windows but I have a lot of stuff on that partition and would hate to loose it all. 

sudo fdisk -l

Disk /dev/hda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x02cc02cb

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       19414   155942923+   7  HPFS/NTFS
/dev/hda2           19415       38073   149878417+  83  Linux
/dev/hda4           38074       38633     4498200    5  Extended
/dev/hda5           38354       38633     2249037   82  Linux swap / Solaris
/dev/hda6           38074       38353     2249037   82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x12345678

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       30401   244196001    c  W95 FAT32 (LBA)


Can anyone help? :confused:

Thanks,

---

### Post by Kwisniew on 2008-02-20
I am interested in this problem as well, I have the same exact simples when going to Windows in the GRUB menu,  Starting up ... and nothing happens. Can't get an answer?

---

### Post by HoLLyw00dGT on 2008-02-26
Also having the same problem.

---

### Post by oedha on 2008-02-26
can you boot into windows from safe mode ?
or you can fix the windows mbr but after that you have to fix the grub

---

### Post by HoLLyw00dGT on 2008-02-26
Well, i'm not really sure what I should do. I don't understand why its doing this in the FIRST place. I follow write ups and they just don't work. I partitioned with option one. Moved the slider down a little bit because i didn't want that much hd space for ubuntu, slid it down 2 like 100 gig. instaled, seemed fine, but starting...

---

### Post by gemmala on 2008-02-26
I heard from someone that the problem was caused by a problem with the Master Boot Record, so I tried fixing that. Big mistake - everything broke - had to set my hard drive as slave to a friend's, back everything up then format the drive. Reinstalled everything from scratch. The moral as far as I see is - touch the master boot record with care. Don't know if that was the problem in the first place though.

---

### Post by darkworld on 2008-02-26
ok this is a very common issue. Ive seen people screw up from various different angles.

Basically on your windows Hard drive you have a MBR, master boot record, this is where the machine goes to after bios has spread life  at startup. Ok you just have windows  then MBR directs windows to boot.

Newbie with Ubuntu disk boots off live cd, nice Ubuntu, ok install. 

Ubuntu see MBR on windows disk and writes into or over this to add grub. This is where some problems seem to occur.

It can be ironed out. 

However Mr Newbie is now faced with  tasks. He has to quickly learn some stuff to get Grub/MBR sorted and there are no immediate sign posts. 

LINUX HILL this way. :)

This is a shock because windows normally babysits your brain. LOL. Nothing personal meant to anybody!

So now newbie is hunting for command line terminal, next he needs to sudo, ????, something else to learn, then get menu.lst into editor, what editor and where?  and sort out stuff using google and forum. Of course remembering to make back up first of menu.lst. So some command line commands too.

sudo gedit /boot/grub/menu.lst 

And so the climb up the hill begins, but let me tell you, when you get up that hill you will have a great view and a smile. :)

---

### Post by HoLLyw00dGT on 2008-02-26
I typed in 
sudo gedit /boot/grub/menu.lst  into terminal. The list comes up and idk what to do from there. All you said was use google and forums. IDK what to search for. IDK what is wrong with the menu.lst or whatever.

-Justin
sudo gedit /boot/grub/menu.lst

---

### Post by HoLLyw00dGT on 2008-02-27
Ok, on the last screen....it gives you a summary and what not, there is an advanced button. What do i need to do to NOT screw up my MBR again? UNCHECK install boot loader? CHANGE device from hd0? I'm gonna leave it at that stage until i get the correct answer lol thx

---

### Post by lucasl on 2008-02-27
For my installation (XP SP2 and Ubuntu 7.10), all you do is install Windows first (leaving some space for Ubuntu), then Ubuntu second. When installing grub, it said "The following OSs were detected: Microsoft Windows XP". If that is all..." or something like that. Install GRUB and all worked fine!

---

### Post by HoLLyw00dGT on 2008-02-27
Well it's not working fine for me. I tried the guided partition and obviously ****** myi MBR, now i'm trying manual, mounted ext3 partition to "/" like i read. deleted ext2, left with NTFS, unallocated, swap and ext3.

At the end of the installation process, I am presented with the screen that had the advanced button on it, Gives me the option of checking or unchecking the box that says install boot blah blah, then there is a space that says (hd0) i believe in it. I changed that to the name of the ext3 file, apparently screwed up something again, got a disc read error, so i restored windows again, deleted partitions andi'm back at zero. I'm so close to saying **** linux but i really want to play with it.But its been days...i just CAN'T get the answer:mad:

---

