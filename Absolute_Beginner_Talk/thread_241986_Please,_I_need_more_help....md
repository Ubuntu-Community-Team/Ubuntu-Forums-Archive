---
title: "Please, I need more help..."
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by doodsangel on 2006-08-23
I have tried gparted, but it didn't work, thereafter I tried fdisk as birdbrain suggested. I was able to create and format the partitions. 
[I]/dev/hda5 <- suppose to be root "/"
/dev/hda9 <- swap space
/dev/hda10 <- planning on making this home.[/I]

Ran Ubuntu 5.10 installlation again. Once again the Ubuntu partition tool was unable to pick up any partitions, only giving me the option to destroy my complete harddrive and start from scratch. I tried professional installation next, and skipped the partition bit. When I told it to install, it said noe "/target" specified. I then ran the shell tool, and did a "mount /dev/hda5 /target", and tried the install again. I was quite excited to see Ubuntu install, only to be dissapointed after restarting.

GRUB came up, and gave me all the choices I wanted, but when I tried to boot into Ubuntu, I got the following:

[B]Booting 'UBUNTU, kernel 2.6.12-9-386'

root(hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash

Error 17: Cannot mount selected partition.

Press any key to continue.[/B]

Now, I can clearly see that "root=/dev/hda1" must be wrong as it is supposed to be /dev/hda5. Now how do I fix this and how do I specify the operating system to use /dev/hda10 as "/home", as I suppose that will also be wrong. :!: 

Previous problem: [http://www.ubuntuforums.org/showthread.php?t=241274](http://www.ubuntuforums.org/showthread.php?t=241274)

---

### Post by deadgobby on 2006-08-23
Are you trying to dual boot windows and Ubie?
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)

---

### Post by doodsangel on 2006-08-23
Yes, windows installation is on /dev/hda1.

I cannot seem to edit my partitions from LVM... It gives me the option to delete my whole drive and start over, and that won't do. Did it manually from FDISK.

I would like to rebuild my complete box, with Linux and windows, but the wife is currently doing her Thesis for MBA, and will hang me if I loose any of her data....... Or if I take 5 hours to reinstall everything...... 'cause then she can't work.

Cannot watch video's at work sorry, currently almost capped @home.

Other help would be appreciated.

---

### Post by gils0040 on 2006-08-23
you will have to edit your /boot/grub/menu.lst file, and as you said change your root partition to the correct one.

---

### Post by deadgobby on 2006-08-23
To save you from time out in bed you will need to save every thing to some format to other. I remeber I was screwing around on the puter and lost my wifes home work. It was a dry spell for me. Perhaps you need to wait it out and let finish her stuff. Cause if you dual boot you may hose your HD and loose your fun for a month. 
Gobby

---

### Post by doodsangel on 2006-08-23
Mmm, yes... But I'm also part (in my part time) of a web-hosting and web/graphic-design company. And need to script and can't get Mandriva to connect with my sierra wireless... Everyting with Mandriva is so easy to install, but so hard to get it to work. That one time @ configuring the dialup took me five hours and worked beautifully. The next day when I tried to connect, it just refused and I wasn't able to connect since.

---

### Post by deadgobby on 2006-08-23
Eh ya I tried Mandriva and did not like the o/s. It was better when it was Mandrake. Mandrake was good O/S before they decided to go pay for.
Gobby

---

### Post by doodsangel on 2006-08-23
Agree, 

Ah, well, Microsoft is making money, why not Mandriva and RedHat as well... 

I user to be sold on Mandrake, but the above reason is why I'm moving towards an alternative.

Maybe I should just bite the bullet this weekend, and if the "snoepie" is closed for a few days. Then so be it. :p 

BTW. I like your pic...

---

### Post by anaconda on 2006-08-24
> **doodsangel said:**
> 
GRUB came up, and gave me all the choices I wanted, but when I tried to boot into Ubuntu, I got the following:

[B]Booting 'UBUNTU, kernel 2.6.12-9-386'
root(hd0,0)
Filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda1 ro quiet splash
Error 17: Cannot mount selected partition.
Press any key to continue.[/B]

Now, I can clearly see that "root=/dev/hda1" must be wrong as it is supposed to be /dev/hda5. Now how do I fix this and how do I specify the operating system to use /dev/hda10 as "/home", as I suppose that will also be wrong. :!: 


title  Ubuntu, kernel 2.6.12-9-386
root  (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

This should be more correct grub -entry (in menu.lst -file) And if /home is correctly defined in /etc/fstab -file then it will be used automatically (it has nothing to do with grub). You might want to check that your fstab-file has the /home corretly assigned to hda10

eg. it has a line starting like
/dev/hda10 /home ......

And you can try if it works before modifying menu.lst.. just boot your machine, and when in grub select 'e' (=edit) and correct the lines..

---

### Post by doodsangel on 2006-08-25
> title Ubuntu, kernel 2.6.12-9-386
root (hd0,4)
kernel /boot/vmlinuz-2.6.12-9-386 root=/dev/hda5 ro quiet splash
initrd /boot/initrd.img-2.6.12-9-386
savedefault
boot

Thanks. This worked perfectly, now back to home folder....

>  You might want to check that your fstab-file has the /home corretly assigned to hda10

eg. it has a line starting like
/dev/hda10 /home ......

I checked this out... The fstab has absolutely nothing in it. It starts of with a hashed line, and thereafter it is empty.

It looks something like this when I **vi fstab**.
```
#Some text intorducing the fstab file
~
~
~
~
~
~
```

---

