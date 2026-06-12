---
title: "Can't see a partition on my hardive"
date: 2006-10-04
forum: Absolute Beginner Talk
---

### Post by sKuarecircle on 2006-10-04
Before I start please let me tell you that i searched at length for this answer but......nothing.

I have just installed Ubuntu about 8 hours ago so I am completely green. I have a 80G hardive and a 160Gig on my Computer. I partined ot so that i can dual boot,and there was 130 Gig's unused, this I want to use for Ubuntu exclusively. If I look under System,Administration,Disks I see the hardrive but I can't enable it. At this piont it there was 130 gig paritioned but not formatted, I formatted it through the format function (little button next to the paths box) but it still won't enable. I really need this space but I don't know what to do.

Thanking you in advance for your help.
PS
I realise you may need some information other than what i have here posted so please go ahead and let me knowo what post.

[Please excuse my English, not my first language]

---

### Post by Jose Catre-Vandis on 2006-10-04
I don't quite understand. You say you want the 130gb for Ubuntu, yet you write as if you are booting into Ubuntu, hence the partition is your root partition for Ubuntu.

Run these two commands in a terminal and post the output:

1.  fdisk -l > fdisk.txt

2.  df -h -T > df.txt

(the "> *.txt" bit saves the output to a text file in your home directory)

I would guess that, because you have two hard drives, Ubuntu doesn't automagically spot the second drive, so you will have to manually mount it and then set up your fstab file to get it to mount each time on boot. Once we have your outputs and you can determine what is what, we can get this sorted :D

---

### Post by uk_sphinx on 2006-10-04
the partition will be a folder in your filesytem.
if you labeled the partition as "second partition" for example, you will have a folder in your filesystem called second partition. if you go inside this folder it will tell you how much space you can use in this folder.

thats how mine works anyway.
my second harddrive is a folder in my first harddrive.
i wanted my second hard-drive as a second filesytem but i gave up trying.

---

### Post by sKuarecircle on 2006-10-04
I do boot into Ubuntu but the separate 130 gig isn't used for it.

I ran the codes, fdisk gives me no info and df gives me the following:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3     18G  2.5G   15G  15% /
varrun       tmpfs    506M  132K  506M   1% /var/run
varlock      tmpfs    506M  4.0K  506M   1% /var/lock
udev         tmpfs    506M  132K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hda1     ntfs     21G  4.2G   17G  21% /media/hda1
/dev/hdb1     ntfs     40G   66M   39G   1% /media/hdb1

---

### Post by sKuarecircle on 2006-10-04
Here is a screen shot

---

### Post by aysiu on 2006-10-04
If you formatted it as Ext3, follow these instructions:
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

If you formatted it as NTFS or FAT32, follow these:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by Jose Catre-Vandis on 2006-10-04
> **sKuarecircle said:**
> I do boot into Ubuntu but the separate 130 gig isn't used for it.

I ran the codes, fdisk gives me no info and df gives me the following:

Filesystem    Type    Size  Used Avail Use% Mounted on
/dev/hda3     ext3     18G  2.5G   15G  15% /
varrun       tmpfs    506M  132K  506M   1% /var/run
varlock      tmpfs    506M  4.0K  506M   1% /var/lock
udev         tmpfs    506M  132K  506M   1% /dev
devshm       tmpfs    506M     0  506M   0% /dev/shm
lrm          tmpfs    506M   19M  488M   4% /lib/modules/2.6.15-27-386/volatile
/dev/hda1     ntfs     21G  4.2G   17G  21% /media/hda1
/dev/hdb1     ntfs     40G   66M   39G   1% /media/hdb1


Sorry, I should have told you to sudo the fdisk command, e.g.

```
sudo fdisk -l
```

This gives good info about the state and formatting of all your hard drives

So if I figure that /dev/hda1 is your XP partition (first partition-hda1, first hard drive-hda), what is the ntfs partition-hdb1 on the second hard drive-hdb, and yourUbuntu installation is "3rd" partition-hda3 on first hard drive-hda? It maybe that your missing 130gb isn't formatted? Look at Aysiu's lnks for mounting guidance though...

---

### Post by jaboua on 2006-10-04
You pirate, you're busted because of the azureus popup ;)

Now back on topic: The partition you selected is listed as an "Extended" partition - in other words it's just a container partition, a partition that you could put other partitions inside. Try running fdisk again like mentioned above, if you have created a partition inside this "extended" partition, it should be listed as hdbX where X is a number above 4.

---

### Post by Jose Catre-Vandis on 2006-10-04
> **jaboua said:**
> You pirate, you're busted because of the azureus popup ;)

LOL @ jaboua :lol:

---

### Post by sKuarecircle on 2006-10-05
Cool, I have reformatted that drive as Ext3 and will n ow attempt to mount as per the link that wasgiven to me.

---

