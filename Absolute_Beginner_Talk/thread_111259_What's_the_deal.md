---
title: "What's the deal???"
date: 2006-01-01
forum: Absolute Beginner Talk
---

### Post by Jukey on 2006-01-01
I want to install Ubuntu or Kubuntu on an existing Windows ME system. when i go through the guided partitioning portion and say "resize IDE Master 1" or something like that, it asks me to allocate 15.5GB to Ubuntu. no matter what amount i suggest, it says something like could not get enough free space. every time i try to defrag the drive it stalls and won't even start defraging. any suggestions? i know this may be a stupid question but i really want to get Ubuntu running and keep my files from Windows.

any reason why it asks for 15.5 GB?

---

### Post by mazelado on 2006-01-02
Not sure why it's suggesting the 15.5 GB, but as far as the defrag goes, try booting Windows in Safe Mode and then running defrag. Windows ME was horrible about defragging. I remember systems that would start and then restart and then restart again... Maybe when you get the defrag working and have a larger continuous free space you'll be able to configure the partition the way you want.

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=Jukey]I want to install Ubuntu or Kubuntu on an existing Windows ME system. when i go through the guided partitioning portion and say "resize IDE Master 1" or something like that, it asks me to allocate 15.5GB to Ubuntu. no matter what amount i suggest, it says something like could not get enough free space. every time i try to defrag the drive it stalls and won't even start defraging. any suggestions? i know this may be a stupid question but i really want to get Ubuntu running and keep my files from Windows.

any reason why it asks for 15.5 GB?[/QUOTE]

The only way I have successfully resized a Windows drive so that I could put Ubuntu on the free space is when I used Partition Magic. I know this does not help you much....but I honestly have never gotten anything else to work.

If messing with closed (aka pay-for) software is too much for you I suggest buying another hard disk. Seriously. 20 gig drives can be had for REALLY cheap and then you problems will be solved.

---

### Post by Rinzwind on 2006-01-02
[QUOTE=mazelado]<..> then running defrag. Windows ME was horrible about defragging. I remember systems that would start and then restart and then restart again... <..>[/QUOTE]
That's normal behaviour when you have something running that changed the files on the harddisc (mosttimes when I saw that happen it was virusses (yeah, not 1 but dozens...). Thing is I often could allready tell that by listening to the drive :X ) 

I've seen it also happen where someone had kazaa running at the same time...


En regarding the queston:

you need partition magice.
Oh and this is 1 reason where I consider it perfectly acceptibale to download PM and use a serial from the web. Just delete the program after you used it :)

---

### Post by diggs on 2006-01-02
[QUOTE=Jukey]I want to install Ubuntu or Kubuntu on an existing Windows ME system. when i go through the guided partitioning portion and say "resize IDE Master 1" or something like that, it asks me to allocate 15.5GB to Ubuntu. no matter what amount i suggest, it says something like could not get enough free space. every time i try to defrag the drive it stalls and won't even start defraging. any suggestions? i know this may be a stupid question but i really want to get Ubuntu running and keep my files from Windows.

any reason why it asks for 15.5 GB?[/QUOTE]
Do yourself a favour and download a copy of 2000. seriously. then set up your partitions in disk managment and then set up ubuntu. Oh, and when you are installing 2000 set up your 2000 partition to be fat32. give that a shot. 

there's a reason why you can still buy a copy of win 98 and you can't buy a copy of ME.

---

### Post by poofyhairguy on 2006-01-02
[QUOTE=Rinzwind]

Oh and this is 1 reason where I consider it perfectly acceptibale to download PM and use a serial from the web. Just delete the program after you used it :)[/QUOTE]


I hate to admit it, but thats what I did. Partition Magic also helps turn NTFS drives into FAT drives without losing data. Thats is great since Ubuntu can read and write to FAT drives but only read NTFS drives.

---

### Post by az on 2006-01-02
Partition magic is notorious for eating partition tables with linux filesystems on it.

The partitioner will offer to shrink your partition and suggest the smallest ammount to which it can shrink your windows partition.  What happens when you put in a smaller number (We are talking about the size of the new partition, and not the size of the old one!) when asked?

---

### Post by iand675@gmail.com on 2006-01-02
wouln't it be an option to resize the partition from the ubuntu installation?

---

### Post by Jukey on 2006-01-02
Thanks for the help, i'll try your suggestions.
any idea where i can get a serial from the web???

---

### Post by pmaury on 2006-01-02
what about this; download a live CD iso, burn it to disc then reboot with the live CD in the CD drive then you can partion the hard drive using Qparted. Make sure the CD-rom is first in order in the BIOS boot order to boot from live CD. I used Qparted to load linux on my hard drive with m$ XP ,it wasnt easy for me to figure out how to make a dual boot system but it all works now! I think it might be called Gparted in Gnome

---

### Post by Jukey on 2006-01-02
sounds easy enough. the only problem may be that the CD takes too long to load up. i tried a live CD session and once it was running I tried to use OOo calc. the file took about an hour to show the splash screen and the program never opened. i'll give it a try, but i'm new to linux. if it is complicated can someone please give me step-by step instructions?

thanks a million

---

### Post by Iandefor on 2006-01-02
[quote=poofyhairguy]Seriously. 20 gig drives can be had for REALLY cheap and then you problems will be solved.[/quote] I can't even *find* a 20 gig drive anymore. Where do you see these cheap drives?

---

### Post by Jukey on 2006-01-02
[QUOTE=diggs]Do yourself a favour and download a copy of 2000. seriously. then set up your partitions in disk managment and then set up ubuntu. Oh, and when you are installing 2000 set up your 2000 partition to be fat32. give that a shot. 

there's a reason why you can still buy a copy of win 98 and you can't buy a copy of ME.[/QUOTE]

that defeats the purpose. i want to keep the partition of windows ME because it has all my files

---

### Post by Sef on 2006-01-02
> that defeats the purpose. i want to keep the partition of windows ME because it has all my files


Can't you just back up your files by burning them to a CD-R/RW or another way?

---

### Post by Jukey on 2006-01-02
tried that, my main computer can't seem to read the files. when i try to copy everything to my hard drive i get an error message

---

