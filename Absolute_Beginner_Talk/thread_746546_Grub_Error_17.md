---
title: "Grub Error 17"
date: 2008-04-05
forum: Absolute Beginner Talk
---

### Post by antarantar on 2008-04-05
I am complately new to ubuntu and not a saavy computer user as you will see...
I urgently needed space and, working from windows just deleted the installed ubuntu partitions (terribly stupid, I know)
now I am getting the grub error 17 message.
I want to recover ubuntu but have had problems with this.
I tried installing super grub on a usb, went through all the steps but when I boot from usb I only get this:

_


Do you know why this happens? Can you help?
Many thanks!

---

### Post by upthelum on 2008-04-05
[http://ubuntuforums.org/showthread.php?t=442945](http://ubuntuforums.org/showthread.php?t=442945)

---

### Post by antarantar on 2008-04-05
Thanks, I read the link, but it seems I got myself into a much deeper trouble. 
I have  grub working it gives me the error 17 but I have only one drive with two partitions (one with vista, the other one hp recovery disc).
I can´t create more partitions to install ubuntu again using the tools from ubuntu cd and I can´t boot from usb with supergrub disc...

---

### Post by bubba_169 on 2008-04-05
In the install process of Ubuntu you can choose to shrink your vista partition to make room for ubuntu so you could probably create more partitions that way...

---

### Post by antarantar on 2008-04-05
I have tried that.
It doesn´t let me shrink the partition through ubuntu install or the gnome (the partition tool, ithink this is how it´s called)
I could only format the whole drive, which I can´t do because I have a couple of years worth of e-mails in outlook which I can´t access through ubuntu and copy

 :(

---

### Post by JoshuaRL on 2008-04-05
In the Live CD theres a tool called GPartEd, see if you can change partitions with that.

---

### Post by bubba_169 on 2008-04-05
In the ubuntu install choose custom partitioning, click on your vista partition and then click the edit button. You can usually change the size of the partition from there so make it small enough to add your linux partitions then create your new partitions in the newly created space.

---

### Post by waspbr on 2008-04-05
gparted should definately allow you to  shrink the vista partition, unless it detecs file system errors, which happened to me once, something about vista no shutting down properly, so I ran vista once and had it shut down properly, problem solved

---

### Post by antarantar on 2008-04-05
Thanks Joshua and bubba.
None of these simple solutions work for me. 
It doesn´t let me resize using gparted

during install when I get to edit partion it does not have a resize option. only use as and mount point.

---

### Post by antarantar on 2008-04-05
Thanks, well I can´t run vista. that´s the problem. and it doesn´t let me shring anythng anyway. strange, isn´t it?

---

### Post by antarantar on 2008-04-05
some other strange things are happening
This is what I get on mount command with the usb drive on



proc on /proc type proc (rw)
sysfs on /sys type sysfs (rw)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
tmpfs on /lib/modules/2.6.20-15-generic/volatile type tmpfs (rw,mode=0755)
/dev/bus/usb on /proc/bus/usb type none (rw,bind)
fusectl on /sys/fs/fuse/connections type fusectl (rw)
varrun on /var/run type tmpfs (rw,noexec,nosuid,nodev,mode=0755)
varlock on /var/lock type tmpfs (rw,noexec,nosuid,nodev,mode=1777)
udev on /dev type tmpfs (rw,mode=0755)
devshm on /dev/shm type tmpfs (rw)
devpts on /dev/pts type devpts (rw,gid=5,mode=620)
tmpfs on /tmp type tmpfs (rw,nosuid,nodev)
binfmt_misc on /proc/sys/fs/binfmt_misc type binfmt_misc (rw)
/dev/sdb1 on /media/disk type vfat (rw,nosuid,nodev,shortname=mixed,uid=999,utf8,umask=077)
/dev/sda1 on /media/disk-1 type ntfs (rw,nosuid,nodev,umask=222,utf8)



but then when I go into grub and check disc geometry only the usb drive is listed ????

---

### Post by bubba_169 on 2008-04-05
I'm not 100% but I think what you said in your last post is pretty normal. Its just listing all the different mount points I think and you shouldn't really bother with it. I don't know what to suggest? Have you tried opening GParted from the System->Administration->Partition editor on the live cd and working from there?

If it doesnt exist connect to the internet, open a terminal and type 'sudo apt-get install gparted' then it should appear.

Once opened you should be able to right click your vista partition and choose resize? If not im at a blank :confused:

---

### Post by antarantar on 2008-04-06
In sum, I tried that you have suggested: resizing windows partition in gparted or during install (both using ubuntu cd)
I installed super grub disc on a usb drive but the computer doesn´t boot from it.
I am stuck both trying to partition the disc and booting. Any other thoughts you may have? I'd appreciate it greatly!

---

### Post by upthelum on 2008-04-06
> **antarantar said:**
> Thanks Joshua and bubba.
None of these simple solutions work for me. 
It doesn´t let me resize using gparted

during install when I get to edit partion it does not have a resize option. only use as and mount point.

It might be a good idea to defragment your windows partitions first before using a partition manager or altering other partitions.

---

### Post by antarantar on 2008-04-12
Well, this must have been a rather unusual problem. I solved it by a brute force - formatting the entire disk and installing the ubuntu anew. This can´t be treated as solving the specific problem though.

---

### Post by windows-killer on 2008-04-12
I had the same problem.
I took my BIOS instructions manual and followed all instructions and reinstalled XP first and then ubuntu and it worked.
hope it helped.:lolflag:

---

