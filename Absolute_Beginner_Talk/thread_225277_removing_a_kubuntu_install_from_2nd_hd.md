---
title: "removing a kubuntu install from 2nd hd"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by PhilJ on 2006-07-29
Hi all,
    aplogies if I have missed the answer when looking thru the forums. I installed Ubuntu to hda1 no problems . I then tried out Kubuntu which I installed on hdb1 no problems so far.  When I tried out Kubuntu it seemed a bit buggy ( could be me ) and I prefer Ubuntu. My question is how do I remove  Kubuntu which has moved itself to the top of the pile in grub? How do I get my original grub back ?  If I look at menu.1st in Ubuntu, Kubuntu isnt mentio ned, but in menu.1st under kubuntu , ubuntu is listed as other filesystems.

confused greyhaired one would appreciate any help

thanks

philj

ps installed Ubuntu on my son-in-law to be's computer cos he got the YOUR COPY OF WINDOWS IS ILLEGAL message and wasnt impressed cos he bought it pre installed. Mightily impressed so far ( but that might be cos it didnt cost him anything) :o)

---

### Post by catlett on 2006-07-29
Boot into your Ubuntu install. Open the terminal and enter this command to install an Ubuntu grub to the mbr.
```
sudo grub-install /dev/hda
```Reboot just to be safe and make sure there is a new grub. It should be easy to tell, ubuntu will be at the top of the list.
Once you know Ubuntu intalled grub, you can just reformat Kubuntu's partitions. Go to System<Administration<Gnome Partition Editor. This is the partitioner gparted. If it isn't in your menu, install it with this command ```
sudo apt-get install gparted
```

---

### Post by PhilJ on 2006-07-29
Thanks Catlett,
  much obliged.


Philj

---

