---
title: "is this method of installation correct?"
date: 2011-08-20
forum: Any Other OS
---

### Post by vikash_chandola on 2011-08-20
Still now i have installed windows 7 ultimate and Ubuntu 11.04(using wubi). I am thinking to install linux mint xfce 201104. It is very fast really!!.. I wan to install this also. But neither it has thing like wubi nor installation seeming simple. I fear that it will delete (format) my whole HDD(biggest fear for my computer) so i put all the installation images here.I want to ask will it cause any problem if i install with these steps.
see all attachments one by one.
what these images show
//I did not put step 1 step 2 and step 6 images i think they doesn't matter. 
step 1   select language
step 2  time zone
step 3  keyboard layout       I make no changes in first three steps   
[COLOR=red]step 4  show my hard disk status/partitions
step5  what i make change for installation. I just right click on /dev/sda 6 and select that option in which there is arrow like this '**\**'.
[/COLOR]
step 6 user name password and other things.
[COLOR=red]step 7 boot loader info(I did not know anything about this)  as you can see there is /dev/sda selected it is by default. If i click on that there were 7 options dev/sda2, dev/sda3 and so on. Also i can un check install GRUB option.
step 8 all the things i do.
[/COLOR]

My main concern is on hard disk i don't want to format my whole hard disk. just tell me if i install with these settings then will any harmful changes made to my computer(specially HDD).All of my data is in /dev/sda 5.** Why that is marked as red**.
I may want to remove it in future so tell me how to set boot loader so that if i remove Linux mint in future then it still boots without any boot time error
boot loader problem is not seeming harmful. I have already solved this problem when i install fedora and then remove it. after removal , i run boot rec.exe (win 7 command) and this problem was solved.

I hope i provide all the information that i can.
If you think it is not fair to ask Linux mint question of Ubuntu forums then sorry!!

---

### Post by sanderd17 on 2011-08-20
This seems good, the only reason for that being in red is because random colors are chosen to distinguish the partitions.

You will format sda6 and lose all data on sda6. You also didn't set up a SWAP partition, so you need at least 2 GB memory and you won't be able to hibernate to disk.

You have to install GRUB to boot to Mint, but if you uninstall Mint, you will also have to repair the Windows bootloader. There is no other possibility since the Windows bootloader can't boot any Linux system. Grub needs to be on the hard disk (sda) and not on a partition (sda1..6).

---

### Post by vikash_chandola on 2011-08-20
> **sanderd17 said:**
> This seems good, the only reason for that being in red is because random colors are chosen to distinguish the partitions.

You will format sda6 and lose all data on sda6. You also didn't set up a SWAP partition, so you need at least 2 GB memory and you won't be able to hibernate to disk.

You have to install GRUB to boot to Mint, but if you uninstall Mint, you will also have to repair the Windows bootloader. There is no other possibility since the Windows bootloader can't boot any Linux system. Grub needs to be on the hard disk (sda) and not on a partition (sda1..6).


thanks for reply.
How to create swap partition. I have only 1 GB RAM.
The only thing i have to change is set up swap. Am i correct?

---

### Post by Perfect Storm on 2011-08-20
Moved to Other OS/Distro Talk.

---

### Post by sanderd17 on 2011-08-20
> **vikash_chandola said:**
> thanks for reply.
How to create swap partition. I have only 1 GB RAM.
The only thing i have to change is set up swap. Am i correct?

Just create an extra partition, 1 to 2 GB should be enough and select to use it as swap (just like you did to use the other partition as /).

The rest is OK, but don't blame me if you lose data, you should make a backup anyway.

---

### Post by vikash_chandola on 2011-08-20
> **sanderd17 said:**
> Just create an extra partition, 1 to 2 GB should be enough and select to use it as swap (just like you did to use the other partition as /).

The rest is OK, but don't blame me if you lose data, you should make a backup anyway.

I also try to do so. but i did not found swap like word
when i right click->edit there was a screen as like in attachment and there were following options in front of mount as 

/ 
/boot 
/tmp 
/home 
/srv

And also what is format of swap memory(ext 3, ntfs msdod......).
which should  i select.

---

### Post by sanderd17 on 2011-08-21
Oh, than it seems that if you format something as swap, mint will automatically mount it as swap too. I thought you needed to select it yourself to mount it as swap.

---

