---
title: "Grub issue"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by ryn0 on 2007-01-13
I had two partitions on my hd. The first one was win2k, 14gb, and the second Ubuntu, 4gb. Recently i deleted win2k partition because i found it unnessesary. I used livecd then. Then i copied ubuntu partition on former win2k partition, deleted ubuntu partition. well, needless to say that i cant boot up now. so i need help

p.s. u r welcome to ask questions

---

### Post by bodhi.zazen on 2007-01-13
You have to restore your MBR.

See here:

[http://ubuntuforums.org/showthread.php?&t=303765](http://ubuntuforums.org/showthread.php?&t=303765)

And this: [http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php](http://www.eddieoneverything.com/windows-xp/uninstalling-the-ubuntu-linux-boot-manager.php)

---

### Post by confused57 on 2007-01-13
> **ryn0 said:**
> I had two partitions on my hd. The first one was win2k, 14gb, and the second Ubuntu, 4gb. Recently i deleted win2k partition because i found it unnessesary. I used livecd then. Then i copied ubuntu partition on former win2k partition, deleted ubuntu partition. well, needless to say that i cant boot up now. so i need help

p.s. u r welcome to ask questions
Do you see the grub menu when you boot up?  I think what happened is that your root partition changed when you moved Ubuntu to the first partition and grub is looking for root where it was before(hda2?), instead of hda1(hd0,0).

What you might want to do is bootup with the live cd, open a terminal, enter:
```
sudo fdisk -l
```
The -l is a small "L"

This will show your current partition table...if you're seeing the grub menu at system bootup, you could highlight the Ubuntu entry, press "e" for edit, and manually change the root to (hd0,0) and change the kernel line to root=/dev/hda1, if fdisk -l shows that is where your root is.  This change is only temporary, if you're able to boot you'd need to make it permanent in /boot/grub/menu.lst.

If your Ubuntu copied successfully to your 1st partition, this should work.

---

### Post by bodhi.zazen on 2007-01-13
> **ryn0 said:**
> I had two partitions on my hd. The first one was win2k, 14gb, and the second Ubuntu, 4gb. Recently i deleted win2k partition because i found it unnessesary. I used livecd then. Then i copied ubuntu partition on former win2k partition, deleted ubuntu partition. well, needless to say that i cant boot up now. so i need help

p.s. u r welcome to ask questions

Sorry, in reading your post I thought you deleted ubuntu and could not boot windows. My mistake :redface:

At any rate you can fix the situation easily with the live CD.

Mount the ubuntu partition:

```
sudo mkdir /media/ubuntu
sudo mount /dev/hda1 /media/ubuntu
```

Now you need only edit /etc/fstab and /boot/grub/menu.lst

You need to change both to point to the ubutnu partition.

In a terminal;

```
gksudo gedit /media/ubuntu/etc/fstab &
gksudo gedit /media/ubuntu/boot/grub/menu.lst
```

In fstab you need a line like this:

**/dev/hda1 / ** ...... (leave the rest of the line as is)

and in menu.lst you need to change the root and kernel lines ....

root (hd0,0)

kernel /boot/vmlinuz-xyz **/dev/hda1** .... (again leave the rest of the kernel line)

Save and exit both files.

reboot

should be good to go ....

If not, just reinstall grub as per my first post ....

---

### Post by ryn0 on 2007-01-14
It didnt work. But this did [http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html).
Thanks for help!

---

