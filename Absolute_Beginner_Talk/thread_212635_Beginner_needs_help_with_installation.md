---
title: "Beginner needs help with installation"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by timofthec on 2006-07-10
Hi all - this is my first post in these forums and I am looking to install Linux on my current system so that it dual boots, however, I have held off because I do not want to get it wrong - hence I need someone to let me know what I plan to do is going to work.

At present, my computer is already set up to duel boot to Win98 and Winxp home.  There are 3 partitions on the hard drive as follows: -

1. 30gb fat32 partition for win98
2. 60gb ntfs partition for winxp
3. 30gb ntfs partition for the kids to download their stuff to and not clutter my winxp partition.

I have read some of the posts in the forums and printed of a pretty thorough installation guide from [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm).  However, I can find nothing about whether tampering with an already established duel boot will work or not.

I am hoping to install ubuntu into 15gb of partition 3 but, as I mentioned earlier, I am not sure that this is possible.  

Any advice / reassurance would be welcome

---

### Post by Crosbie on 2006-07-10
If you're using Windows XP's bootloader (NTLDR?) to handle your current dual boot, I reckon it *should *work fine.

Grub successfully identified and included the two Windows XP bootloaders on my (3-drive) system and preserved them intact.

Perhaps you can copy your bootsector to a backup file ready to reinstall?  (You'd have to find a more experienced user than me to advise you on this though.)  You should be able to reinstall a Windows XP bootloader with a 'fixboot' command from a Windows install cd, or reinstall Grub from a Linux CD too.  I've knackered my bootsector more than once, and been able to restore it after a bit of panic. :)

---

### Post by raldz on 2006-07-10
Yes, it should work.. as long as you install Ubuntu's bootloader called "GRUB" in the MBR.. if, in any way that you could not see the other Windows in the boot menu, you could always add them by editing "/boot/grub/menu.lst" from within Ubuntu after the installation.. 

here is a guide how to edit menu.lst:

[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)

---

### Post by Kyran on 2006-07-10
> **timofthec said:**
> I am hoping to install ubuntu into 15gb of partition 3 but, as I mentioned earlier, I am not sure that this is possible.

The installion gives you the option of resizing paritions, however I have never been able to do it (files were probably all over the partition, never was bothered to defragment before hand) if however you were planning to delete that third partition all together and have the setup replace it theres no reasion why that wouldn't work.

---

### Post by diepruis on 2006-07-10
> **Crosbie]You should be able to reinstall a Windows XP bootloader with a 'fixboot' command[/QUOTE]

You might need "fixmbr" as well if things go really pear shaped. Don't ask why I know that  said:**
> I am hoping to install ubuntu into 15gb of partition 3 but, as I mentioned earlier, I am not sure that this is possible.

I wouldn't reccomend resizing it, if that's what you're asking. I used partition magic to resize and gparted to create some new partitions for linux, and that killed my NTFS partition. I'd backup the files on partition 3 , delete it and create some new ones. Just thought I'd warn you.

Also, I've read that you want at least 20GB for your root parition on ubuntu. Personally I don't agree at this point because I've been using Dapper for ~2 weeks now and I'm only using 3.5G of my root partition and 200M of my home parition. Again, just thought I'd mention it.

Otherwise your plan seems solid. GRUB **should** handle the 3 OSes fine.

---

### Post by Herman on 2006-07-10
>  1. 30gb fat32 partition for win98
2. 60gb ntfs partition for winxp
3. 30gb ntfs partition for the kids to download their stuff to and not clutter my winxp partition.

I have read some of the posts in the forums and printed of a pretty thorough installation guide from [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm).  However, I can find nothing about whether tampering with an already established duel boot will work or not.

I am hoping to install ubuntu into 15gb of partition 3 but, as I mentioned earlier, I am not sure that this is possible.   Hello, timofthec, if those partitions are all 'Primary' partitions, you will need to install Ubuntu on all 'Logical' partitions, which is a small difference from what the install page you linked to suggests. Otherwise you might 'paint yourself into as corner' partitionwise.
As you may already know, we can only have four Primary partitions per disk, or three primaries plus one 'extended' partition. The 'Extended' partition can contain as many logical partitions as we like. (Well quite a few anyway).
Ubuntu does not really care whether you install it on Primary or Logical partitions. it will work just the same. 

So make all your new partitions 'Logical', and you'll be fine.

All the best, and good luck with it, Regards, Herman :D

---

### Post by timofthec on 2006-07-10
Thanx for the quick responses and the info guys :D 

Herman - honestly can’t remember how I did the partitions now, gona have to check that when I get home from work but thanx for the point out.

I have a further question if that’s ok - is the GRUB programme included with the unbutu cd that I’ve burned or do I need to download it separately?  If it is a separate programme, do I run that before I install unbutu?

Sorry if these are a bit noobish or covered elsewhere but there is a looottt of info in the forums to digest:-({|=

---

### Post by Jagot on 2006-07-10
GRUB will be installed at the end of the installation of Ubuntu - you don't need to do anything separately.

---

### Post by raldz on 2006-07-10
> **timofthec said:**
> 
Sorry if these are a bit noobish or covered elsewhere but there is a looottt of info in the forums to digest:-({|=

Please don't call yourself as noobish or newbie.. it's better to ask questions and remove all doubts than never ask a question and be dumb forever.. we are glad that you asked questions.. that's the purpose of this forum..

---

### Post by timofthec on 2006-07-11
first off guys - many thanx for the responses and the info it’s a great help and is much appreciated :KS .

I've decided to wait till the weekend to install ubuntu so I can do it in a relaxed state with plenty of time to resolve any probs that may arise (well, at least that’s the theory).

Herman - had a check and I have partition 1 as a primary partition and partitions 2 & 3 are logical partitions within an extended partition so hopefully that should be ok.

> I wouldn't recommend resizing it, if that's what you're asking. I used partition magic to resize and gparted to create some new partitions for linux, and that killed my NTFS partition. I'd backup the files on partition 3 , delete it and create some new ones. Just thought I'd warn you.

Thanks for that advice diepruis, I've already cleared out partition 3 and am gona delete it and repartition it. When I'm done, ubuntu will be on partition 3 and the kid’s stuff with be on a new partition, surprisingly called partition 4.

Well that’s that for now, just wanted to thank you for the advice and hopefully I should be the proud user of ubuntu by Monday :D

---

### Post by diepruis on 2006-07-11
Good luck, and let us know how it turns out.

---

### Post by timofthec on 2006-07-14
lo guys

just to let ya know that ubuntu is now up and running and i can now dual boot to win98 winxp or ubuntu :-D 

i did have a littlie glitch with the install in that b4 i started i created the partitions that i wanted under the drive manager in xp, however, the ubuntu installer didn’t like it.  i had to go back out delete the partitions that i had made under xp and then re-do them under ubuntu - everything was a breeze after that.

many thanks for the help it was very useful to me.  the next project is to get me wifi working but that’s the subject of another post that can be seen here if ur interested.[http://www.ubuntuforums.org/showthread.php?p=1255215#post1255215](http://www.ubuntuforums.org/showthread.php?p=1255215#post1255215)

anyways, this post was just to let ya know how i got on and to say thnx - so thnx:-D

---

### Post by UbuntuniX on 2006-07-14
Do you really need Windows 98 when you have XP?

Extra space is always good when you're running windows,
but with just linux anything will do :)

Anyway good luck :D

---

### Post by diepruis on 2006-07-14
Good luck with WiFi! Only these forums saved my wireless card from a creative death ;)

---

