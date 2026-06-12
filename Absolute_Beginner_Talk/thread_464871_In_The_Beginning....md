---
title: "In The Beginning..."
date: 2007-06-05
forum: Absolute Beginner Talk
---

### Post by rigadon on 2007-06-05
Hi guys and gals!

I've decided to use Ubuntu for my development box, so I have downloaded the server edition (this is for website development, so I think the server edition is best - please tell me if I am wrong) and I have written the ISO to a CD. But now I'm a bit confused :( I have two hard disks in my development box and I already have Redhat installed (on one hard disk) - I want to install Ubuntu on the other and have the option of which distro to start when I turn the box on. The first hard disk is mounted as /hda and has several partitions. The second hard disk is mounted as /hdb and has one partition. So I guess my questions are:

- where do I start?
- can I just install Ubuntu (on the second disk, somehow?) and it will work without disrupting my Redhat installation?
- is there any way to make the second hard disk not accessible from the Redhat installation, so I can't accidentally trash it?
- (see above) do I need to remove the /hdb mount so I don't trash the second hard disk?
- do I need to format the second hard disk before I can start using it?
- what about partitioning - I presume I am best to partition the second hard disk?

I think that's about it :) Any help would be appreciated! I've used Linux quite a lot, but only as a user, never as an administrator, so this is all new to me!

Thanks
Jay

---

### Post by Skrynesaver on 2007-06-05
> **rigadon said:**
> 
- where do I start?
- can I just install Ubuntu (on the second disk, somehow?) and it will work without disrupting my Redhat installation?

Yes, you'll have to add a stanza for the Redhat installation to your new /boot/menu.lst to make it available in the GRUB menu though
> 
- is there any way to make the second hard disk not accessible from the Redhat installation, so I can't accidentally trash it?

You could remove al reference to it from Redhat's fstab (/etc/fstab)
> 
- (see above) do I need to remove the /hdb mount so I don't trash the second hard disk?

Not at all, you can leave the mountpoint for use in the event of having to recover from an error
> 
- do I need to format the second hard disk before I can start using it?

The installer should deal with that for you
> 
- what about partitioning - I presume I am best to partition the second hard disk?

Not nesescary but if you are likely to upgrade or change distro then you'd be better off keeping all your development work on a non OS partition
I think that's about it :) Any help would be appreciated! I've used Linux quite a lot, but only as a user, never as an administrator, so this is all new to me!

Thanks
Jay[/quote]

---

### Post by rigadon on 2007-06-05
Hey, thanks for replying Skrynesaver!

> Yes, you'll have to add a stanza for the Redhat installation to your new /boot/menu.lst to make it available in the GRUB menu though

Ah okay, so where will the GRUB stuff be stored? On /dev/hda? How will it know about Ubuntu on /dev/hdb?

> You could remove al reference to it from Redhat's fstab (/etc/fstab)

Not at all, you can leave the mountpoint for use in the event of having to recover from an error

Okay that's cool - so remove it from /etc/fstab but leave the mountpoint in case of an error. That sounds easy enough :) I guess I'll be able to access /dev/hda (from Ubuntu) in the same way?

> Not nesescary but if you are likely to upgrade or change distro then you'd be better off keeping all your development work on a non OS partition

I guess I AM likely to change distro at some point - what do you advise in terms of partitioning? The partitions available through Redhat (not setup by me) are as follows:

```
[jay@tom jay]$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             15116836   6013088   8335844  42% /
/dev/hda2             30233928   3030872  25667244  11% /home
none                    240764         0    240764   0% /dev/shm
/dev/hda5             30566208     32828  28980700   1% /space
/dev/hdb              78786736  43613564  31171012  59% /hdb
```

Does that all seem reasonable? As a general rule what size partitions do you recommend for each section?

Thanks
Jay

---

### Post by Skrynesaver on 2007-06-05
> **rigadon said:**
> Hey, thanks for replying Skrynesaver! Np ;)

> 
Ah okay, so where will the GRUB stuff be stored? On /dev/hda? How will it know about Ubuntu on /dev/hdb?

Up to you but the Ubuntu install will want to put it on /dev/hdb (ie. It's own partition)

> 
Okay that's cool - so remove it from /etc/fstab but leave the mountpoint in case of an error. That sounds easy enough :) I guess I'll be able to access /dev/hda (from Ubuntu) in the same way?
Yup
> 

I guess I AM likely to change distro at some point - what do you advise in terms of partitioning? The partitions available through Redhat (not setup by me) are as follows:

```
[jay@tom jay]$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/hda1             15116836   6013088   8335844  42% /
/dev/hda2             30233928   3030872  25667244  11% /home
none                    240764         0    240764   0% /dev/shm
/dev/hda5             30566208     32828  28980700   1% /space
/dev/hdb              78786736  43613564  31171012  59% /hdb
```Does that all seem reasonable? As a general rule what size partitions do you recommend for each section?

As your working on web server development I'd add a /var or /var/www partition to keep that work safe, after that it depends on how much data is sitting where ;) This can be hard to gauge at the beginning of a project but really no one knows better than yourself where the data is going tp be held, so set your partition sizes to suit.

Best of luck with the project

---

### Post by rigadon on 2007-06-05
Hmmm, in that case I am still slightly confused. How can GRUB work if I have a config file on both /dev/hda and /dev/hdb??

Would it help at all if I created a /boot partition on /dev/hdb? Would that be a more logical place for grub.conf to be kept?

---

### Post by Skrynesaver on 2007-06-05
A boot partition at the start of the drive isn't a bad idea but whether you do this or not it is the new boot directory that grub will be pointed at from the new boot sector.

---

### Post by rigadon on 2007-06-05
Okay cool. Thanks again for your help Skrynesaver - enjoy the craic :)

---

### Post by Dylnuge on 2007-06-05
> **rigadon said:**
> Hmmm, in that case I am still slightly confused. How can GRUB work if I have a config file on both /dev/hda and /dev/hdb??

Would it help at all if I created a /boot partition on /dev/hdb? Would that be a more logical place for grub.conf to be kept?

Your red hat actually installed something to the MBR (Master Boot Record) which tells it to access GRUB on /dev/hda. If GRUB or LILO is not yet installed, when you install it, you will be installing it to the MBR. Now, changing the /boot/grub/menu.lst file (or whatever it is called on a Red Hat system) will change what GRUB shows to the MBR when it accesses it. Therefore, it does not matter where GRUB is installed. If you don't have GRUB yet, Ubuntu will not only auto-install it, but also auto-detect your Red Hat install.

---

### Post by rigadon on 2007-06-05
Hi Dylnuge!

Ah okay - thanks for your help! I'm just going through the setup process now - wish me luck :)

Cheers
Jay

---

### Post by rigadon on 2007-06-05
Okay - I've got everything installed and it all worked perfectly without me having to think - huzzah :)

Except ... is the server edition just a text version - ie - no GUI provided? If there IS a GUI can someone please tell me how to access it. I intend to use this box for development purposes, so a GUI is kind-of vital!?!

If not I guess I'll have to start again :( Does anyone know - if I download and install the desktop edition will it do *the right thing* and overwrite the server edition I have just installed?

Thanks
Jay

---

### Post by Skrynesaver on 2007-06-05
You can add the desktop environment with
```

apt-get install ubuntu-desktop

```

---

### Post by rigadon on 2007-06-05
Awesome - thanks so much for your help again! I would have spent hours trying to sort this out otherwise :)

---

### Post by Dylnuge on 2007-06-05
The server edition is just text based. Doing what Skrynesaver is telling you is right, but you could have done that just by downloading the LiveCD.

---

### Post by rigadon on 2007-06-06
Thanks guys - all up and working now. Wish I'd downloaded the desktop edition first time round, but we got there in the end :)

---

