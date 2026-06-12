---
title: "Help install a harddrive"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Oki on 2007-01-08
Hi 

I just installed a new harddrive, downloaded gparted and formatted it as etc2. But I cant open it? Doing so I get this message;

Unable to mount the selected volume

Show more details

error: device /dev/sdc2 is not removable
error: could not execute pmount


What can I do?

Thanks

---

### Post by harmegido on 2007-01-08
How are you mounting it? What commands are you using?

---

### Post by confused57 on 2007-01-08
You might want to use ext3, instead of ext2...see this thread with a similar question:

[http://www.ubuntuforums.org/showthread.php?t=333055](http://www.ubuntuforums.org/showthread.php?t=333055)

---

### Post by Oki on 2007-01-08
Hmm, no commands from me – I thought Ubuntu automatically mounts all partitions. Thanks for the links, very good explained. 

Etc2 because I am going to use the fs-driver so Windows can read Etc partions (and it cant read etc3). Will change this to Etc3 when I am finished ( [http://fs-driver.org/)](http://fs-driver.org/)).

I used gparted, but when I now look at the new harddrives in Norton partion magic(in Windows) it stands “BAD”, and I cant use it? Any ideas? 

Thanks

---

### Post by hal10000 on 2007-01-08
> Etc2 because I am going to use the fs-driver so Windows can read Etc partions (and it cant read etc3). Will change this to Etc3 when I am finished ( [http://fs-driver.org/)](http://fs-driver.org/)).

You can (and usually should) format it with ext3, it is completely downwards compatible with ext2.

---

### Post by Oki on 2007-01-09
What am I doing wrong?
I am following this guide: [http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

I have a new physical hard drive, and I want to add one of the partion on it to Ubuntu. 

1. I made a mount point with &#8220;sudo mkdir /musikk_hele&#8221;
2. I opened gparted(gksudo gparted) and saw that it is called /dev/sdc4
3. Then: &#8220;sudo nano /etc/fstab&#8221; and added /dev/sdc4/musikk_hele ext3 defaults 0 0 at the bottom. 
4. Save, confirm, then exit. 

When I run &#8220;sudo mount -a&#8221; I get this one; &#8220;mount: mount point /musikk_hele does not exist&#8221;


Edit; If I go to the folder with Nautilus I can find it, so it dos exist.

---

### Post by hal10000 on 2007-01-09
> 3. Then: &#8220;sudo nano /etc/fstab&#8221; and added /dev/sdc4/musikk_hele ext3 defaults 0 0 at the bottom

I guess it's just mistyped, but the correct syntax for fstab is:
```

/dev/sdc4 /musikk_hele ext3 defaults 0 0

```
with a blank (or <TAB>) between /dev/sdc4 and /musikk_.....

But if the mount command says that this mount point does'nt exist, then you must have be done something wrong when creating this directory.
Verify if it really exists by typing ls -ld /musikk_hele

---

### Post by hal10000 on 2007-01-09
Also, if you put th [COLOR="Red"]defaults [/COLOR]option to this partition, you night not be able to create files (or directories) as a normal user.
I'm not sure if this is what you want.

---

### Post by Oki on 2007-01-09
Thanks for your help hal10000!

I guess that I am doing some stupid mistake, but I dont know witch...  Dos this tell you anything?

steffen@steffen-desktop:~$ sudo mkdir /media/musikk
steffen@steffen-desktop:~$ sudo nano /etc/fstab
steffen@steffen-desktop:~$ sudo mount -a
mount: mount point /musikk does not exist
steffen@steffen-desktop:~$ ls -ld /media/musikk
drwxr-xr-x 2 root root 4096 2007-01-09 23:39 /media/musikk
steffen@steffen-desktop:~$


For the sudo nano /etc/fstab command look at the screenprint. 

Thank you so much!

---

### Post by hal10000 on 2007-01-09
yes, you made a stupid mistake, just make your fstab line look like
```

/dev/sdc4 /media/musikk_hele ext3 defaults 0 0

```
What you did is creating a subdirectory /media/musikk_....., but in your fstab you referred only to /musikk.....

if you like to have write permissions for non-privileged user (non-root) then make the line look like:
```

/dev/sdc4 /media/musikk_hele ext3 rw,user 0 0

```
(note there is **no space** between the comma)

This makes the partition (un)mountable and writeable for normal users.

---

### Post by Oki on 2007-01-10
It worked -  Thank you so much for your help hal10000 :-D

And yes, that was a stupid mistake'; time to feel stupid and blame that I was tired LOL   But I am happy – now I have music (the partion is full of music). I changed it so “none sudo” also can write to it. Thanks again! 



(Btw; notice sudo mkdir /media/musikk   So not musikk_hele, I changed it to musikk since I tried it all from the beginning).

---

### Post by Oki on 2007-01-10
I have to ask:

I made the mount point(the directory) in the /media , and not in the  /mnt cus I have read that this gives you a icon on the Desktop. But there is no icon here &#8211; no biggi cus I can make one, but I am wondering.

EDIT:
After rebooting the disk showed up as an icon on the desktop - so everything as it should be. Thanks again

---

