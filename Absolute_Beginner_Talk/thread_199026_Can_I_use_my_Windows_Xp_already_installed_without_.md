---
title: "Can I use my Windows Xp already installed without reboot?"
date: 2006-06-18
forum: Absolute Beginner Talk
---

### Post by gogunused on 2006-06-18
I 've installed Ubuntu and I am charmed by it. However, I want use my preinstalled Xp without rebooting (inside Ubuntu), if something like that is possible. I mean, could be used for that some apps like Vmware, Samba or anything else?

---

### Post by u.b.u.n.t.u on 2006-06-18
VMware can do that but at a performance hit to XP.

Samba is a networking tool.

---

### Post by gogunused on 2006-06-18
Thanks. Could you tell me more about that? Or send me to a source where could I learn more about that?
I know what Samba is, but I've express my intention unhappily. I intend to use Samba for networking betwen my two machines (the real one and the virtual one). Sorry for my bad English.

---

### Post by u.b.u.n.t.u on 2006-06-18
VMware runs XP in a virtual environment. That means that XP may only run at 70% of normal speed - something like that.

[http://en.wikipedia.org/wiki/VMware](http://en.wikipedia.org/wiki/VMware)

---

### Post by gogunused on 2006-06-18
Thanks again, u.b.u.n.t.u. Now, I've seen some threads on install VMware and Windows, but I have no ideea about making a **preinstalled **Windows to run on top of Ubuntu. There is hope for me?

---

### Post by u.b.u.n.t.u on 2006-06-18
A dual boot is a better way in my view. You can set up a shared FAT32 partition that both ubuntu and XP can read and write to it.

As far as I know, the virtual environment installs the operating system. I don't think you can nominate an existing operating system to operate inside a virtual environment.

---

### Post by JurB on 2006-06-18
[QUOTE=gogunused]I have no ideea about making a **preinstalled **Windows to run on top of Ubuntu. There is hope for me?[/QUOTE]

Look [here]("http://macrolinz.com/macrolinz/index.php/2006/01/09/physcial-to-virtual/")
...

---

### Post by gogunused on 2006-06-18
I think sharing a FAT32 partition is a very good idea. Thanks again, u.b.u.n.t.u.

JurB, that HowTo seems great, except I believe it works only for a Windows host with a Windows guest. Maybe I'm wrong.

I will format a big partition and I'll share it between Windows and Ubuntu - that for use my big library in both OSs. As for those Windows apps, I'll use Wine. I hope it's a satisfying solution.

Thanks both of you.

---

### Post by gogunused on 2006-06-18
In fact I'll share an ext3 partition. For that, I need *Ext2 Installable File System for Windows*, a file system driver that permit Windows to read and write ext2/3 formatted partitions. I hope it will work. 

In case others are interested, this link may be useful: [http://fs-driver.org/](http://fs-driver.org/).

---

### Post by catlett on 2006-06-18
That driver allows you to read and write to ubuntu from windows but it will not allow you to read and write to windows from ubuntu. So if all you want is to have read only access between windows and ubuntu then the ext2 driver is fine. But if you want to freely read and write to an area of your computer from either OS you'll need a FAT32 partition.

There is fuse and captive for ubuntu that will allow you to readf/write to ntfs but it is still not considered a 100% stable.

Plus if you get into ext2fs a little more you will see that it doesn't retain the benefits of ext3 when you use it. So the filesystem will be usable in windows but it will   have the attributes of ext2. What does that mean? It means that the benefits and advances that ext3 has over ext2 will not be available. To put it in windows terms, it would be like having a driver that allowed you to read/write to ntfs but the ntfs filesystem would act like fat32.

So, why use a driver made for ext2 on your ext3 parrtition? Why risk your data by using beta drivers to access your ntfs? There really isn't a good why when the alternative is more stable and safe.

As long as you have disk space. You should place data that you want to have access to, no matter what OS you have, in a FAT32 partition. Both windows and linux have the ability to read and write to the filesystem with NO danger or possibility of corruption. It is stable in both OSs. Some people will say ntfs and ext3 are faster and better systems. Yes but you are not going to keep your program files on it, just data that you want access to.

Since you didn't ask and since I'm rambling already:) Set your system up with 4 more partitions. A swap, an ext3, another ext3 and a fat32 partition.

The swap is for virtual memory (it is like widows swap file) The rule of thumb for size is twice your ram i.e. 256mb ram = 512mb swap.

The first ext3 is for /  (/ is the synbol for root) This is the partition that will hold the install. It is similar to your windows and program files folders in windows. 5gb is more than enough space. You can add a few more gb if you have plenty and want a cushion but I have never gone over 4gb.

The second ext3 is for home. Home is like  my documents in windows. It will hold all your personal data. The size of this can be unlimited but you should have at least 5gb. 10 is plenty since you are going to make a fat to share with windows. This partition is not needed. It can be inbstalled in root's partition but it is advisable. If you have a home partition you can reinstall the OS without loosing your data. This way if something goes wrong and you need to reformat root and reinstall your home is safe.  Sometimes upgrades don't go smoothlly when done through the update manager, this way allows you to upgrade with a fresh install from cd and still keep your data untouched.

The FAT32  is for sharing with windows. Again this not needed but advisable. The size depends on what your interests are. Are you into movies and want your dvd collection here? Or your mp3s? Do you have lots of files from work? Obviously it depends on your disk space available but I would make it at least 10gb and if I had space I would go 20gb.

I set my partitions up ahead of time with gparted live. [http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)  That way I don't have to make partitions at install. You just select to manually set up your partitions and label the partitions accordingly (swap,/,home,data)

---

### Post by gogunused on 2006-06-18
Thanks, Catlett, that is some answer! The reason to choose ext3 and not FAT32 for the shared partition between Windows and Ubuntu is that on a FAT32 partition I cannot have a file bigger than 4 Gb and that there is some waste of space on a big partition FAT32 (I could have many little and very little files on that partition).

Well, I won't write on my NTFS partition from Linux, but that doesn't matter, if anything I'll write on ext3 can be read from Windows with that ext2fs driver. So I will be able "to freely read and write to an area of my computer from either OS", to use your words.

Anyway, I appreciate a lot your well conceived answer and I'll follow your advice about having a partition for / and another for /home. Maybe I'll add one for /usr.

Thanks!

---

### Post by catlett on 2006-06-18
[QUOTE=gogunused]Thanks, Catlett, that is some answer! The reason to choose ext3 and not FAT32 for the shared partition between Windows and Ubuntu is that on a FAT32 partition I cannot have a file bigger than 4 Gb and that there is some waste of space on a big partition FAT32 (I could have many little and very little files on that partition).

Well, I won't write on my NTFS partition from Linux, but that doesn't matter, if anything I'll write on ext3 can be read from Windows with that ext2fs driver. So I will be able "to freely read and write to an area of my computer from either OS", to use your words.

Anyway, I appreciate a lot your well conceived answer and I'll follow your advice about having a partition for / and another for /home. Maybe I'll add one for /usr.

Thanks![/QUOTE]
Yeah I got the writing bug. I started to use more partitions myself. I finally ended up with a / ( root), var, usr,tmp, home and swap. The only one I didn't do that was recommended was boot. I have never had a problem with grub booting all my OS's but I guess maybe I should do it next time. Any ways this is one source I used. If you want some light reading :D  it came from this html doc under What partitions Do I need? [http://www.tldp.org/HOWTO/Partition/](http://www.tldp.org/HOWTO/Partition/)
> Everything in your linux file system can go in the same (single) partition. However, there are circumstances when you may want to restrict the growth of certain file systems. For example, if your mail spool was in the same partition as your root fs and it filled the remaining space in the partition, your computer would basically hang.

/var - This fs contains spool directories such as those for mail and printing. In addition, it contains the error log directory. If your machine is a server and develops a chronic error, those msgs can fill the partition. Server computers ought to have /var in a different partition than /. 

/usr - This is where most executable binaries go. In addition, the kernel source tree goes here, and much documentation. 

/tmp -  Some programs write temporary data files here. Usually, they are quite small. However, if you run computationally intensive jobs, like science or engineering applications, hundreds of megabytes could be required for brief periods of time. In this case, keep /tmp in a different partition than /. 

/home - This is where users home directories go. If you do not impose quotas on your users, this ought to be in its own partition.

/boot - This is where your kernel images go. See discussion above for placement on old systems. 

---

### Post by gogunused on 2006-06-18
Well, thanks again, Catlett. That link seems very usefull to me. I'm confused a bit about the Linux world, but I promise to learn. I have all the time in the world (because jobless for a while :( ), so I will use it for learning. I'll learn English, too. :)

---

