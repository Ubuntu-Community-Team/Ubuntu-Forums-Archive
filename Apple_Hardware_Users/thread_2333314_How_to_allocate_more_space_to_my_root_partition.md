---
title: "How to allocate more space to my root partition?"
date: 2016-08-09
forum: Apple Hardware Users
---

### Post by aldo82 on 2016-08-09
I've  a macbook running with snow leopard. I 've recently  installed LTS 16.04 on dual boot.
In the last few days hoverer, I have been  not able to manage this system because I do not  have any root 
space at all. So, how to allocate more space to my root folder?

Many thanks in advance

Aldo

[ATTACH=CONFIG]270630[/ATTACH]

---

### Post by howefield on 2016-08-09
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by ajgreeny on 2016-08-09
It will not be easy as there is no available space next to your root partition.

What is currently in sda4, sda8, sda9, sda10 and sda11, none of which are immediately available or next door to the root partition, so will require some moving and messing about.  Why so many small ext4 partitions; it is not normal for a Ubuntu installation?

It looks to me as if the easiest way to proceed might be to boot to a live Ubuntu and using gparted, delete the current swap and sda8 if it is empty, then combine the free space with sda6, which I assume is your root.

Come back with some answers to my queries and we can try to go a bit further with this.

---

### Post by aldo82 on 2016-08-09
So I deleted the current swap and sda8. But how to combine the free space  to my root and 
how to  create a new swap?

Unable to upload  the new screenshot, but the files are next door above and beneath
my root folder.

---

### Post by ajgreeny on 2016-08-09
You presumably still have the 128MB free space above root, and now about 8.33GB free space below root?

If I'm correct I would ignore the 128MB partition above root as it is not worth the bother of incorporating unless it is possible to add it to the HFS+ sda5.  I know nothing about apple filesystems so will leave you to search that yourself if you really want to.

You should now be able to use gparted in the live ubuntu system to extend the right hand end of root into the free 8.33Gb space but leave another 2GB in which you can create another swap partition.  Once started do not interrupt the process or you will lose everything.

When you now reboot you will get an error about swap being unavailable and will have to edit swap's UUID showing /etc/fstab in order to get swap working again.  You can find the correct UUID to use by running ```
sudo blkid -c /dev/null
```

---

### Post by aldo82 on 2016-08-10
No, above root I've now 2,03Gib because I deleted the HFS sda5. My problem is: I don't how to combine this unallocated  
space to my root. Unfortunately I can't upload the current screen folder, but my description is correct.
Maybe someone can  give me  a step by step instruction . I've  been using  Mac OS since 1994  but I'm completely new in terms of  using  Ubuntu

---

### Post by ajgreeny on 2016-08-10
OK, now it makes most sense to me to use that 2GB by creating a new swap partition there, and then extending the root partition into all of the available free space after it.

From gparted in your live ubuntu system click on sda6 as you show in your picture and click the orange coloured icon for Move/Resize (in English).

Now in the window that appears grab the right hand end of the partition and drag it all the way into the free space using all the 8.33GB.  Click the green tick mark to accept the action and wait for it all to finish.  Once again, **DO NOT INTERRUPT THIS ONCE STARTED.**

Make sure you have backups of important files before doing anything in gparted as things can go wrong;  I've used it many times and never lost anything but mistakes or power failures can happen and it's good to be prepared.

---

### Post by aldo82 on 2016-08-11
I resized the root to 15,29GB I entered  the code you posted before.  The result was/ dev/sro: UUId=2016-04-22-15-53-22 -00 Label=US_02_2016. Type Iso 9660 But there is an error message too* broken account.*
Furthermore there is no new swap in the g-parted window

---

### Post by ajgreeny on 2016-08-11
> **aldo82 said:**
> I resized the root to 15,29GB I entered  the code you posted before.  The result was/ dev/sro: UUId=2016-04-22-15-53-22 -00 Label=US_02_2016. Type Iso 9660 But there is an error message too* broken account.*
Furthermore there is no new swap in the g-parted window
Well, I have no idea what exactly is going on here, nor why there is no swap shown in gparted.
Is that output you show what you get from the blkid command I suggested? If so then you definitely did something wrong somewhere; Type Iso 9660 is a CD or DVD filesystem, as is /dev/sr0.

Does your system still boot to Ubuntu now or does in just throw an error about the old swap not being available and stop?

---

### Post by aldo82 on 2016-08-12
Yes, I can boot to Ubuntu. The Problem is, I suppose, the broken count. I can't install nor disable third party's software.

When entering the  command : sudo apt-get install---fix-broken, I got" invalid command.".
 
the blkid command results in: directory  was not found, type  iso 9660 was my live DVD.

---

### Post by ajgreeny on 2016-08-12
It should be ```
sudo apt-get install -f
``` or ```
sudo apt-get install --fix-broken
```You used too many **---** in your version and missed the space before **--fix-broken**, but if you have a broken account (I assume you mean user account, but I'm not sure exactly what you mean) that is not going to help as that command fixes any installed broken packages that are stopping the package management system from working as it should.

I do not understand why the **blkid** command did not give you a full output, but just to make sure can you please run that from your running installed Ubuntu OS, not from a live system, if that is what you were using previously.

Did you use the old HFS space together with the previously unallocated space to create a new swap as I suggested using gparted, and after doing so did gparted show it on the disk?  I begin to wonder if you carried out the final action of accepting it with a click on the green tick-mark.

---

