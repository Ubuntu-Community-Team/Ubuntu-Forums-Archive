---
title: "Need Help, NTFS3g and Fuse"
date: 2006-08-13
forum: Absolute Beginner Talk
---

### Post by Chazall1 on 2006-08-13
I have installed NTFS3g and fuse current, I am using Ubuntu 6.6. I went to configure /etc/fstab and here is what I put in as my hda2 NTFS line
(/dev/hda2       /media/windows  ntfs-3g silent,umask=0,locale=en_US.utf8 0 0) Is spacing an issue in the fstab file???? I need help, I know it is simple, but I am new to this I can not get my NTFS drive to mount on startup, my other drives from my windows partition are auto mounting, just not hda2 my ntfs files
Frustrated

---

### Post by Joeak on 2006-11-02
All I had to do was # rem out the old /media/hda1 entry, then add:

/dev/hda1 /mnt/windows ntfs-3g silent,umask=0 0 0

Spacing is important in that you need at least one space in between the parameters, as your example did and mine does.  More than one space is fine.

I also had to create my mount point (sudo mkdir /mnt/windows, or sudo mkdir /media/windows in your example).  I also ran a command to add fuse to /etc/modules so that it would load at startup.

The full procedure I used (stolen from the comments on [http://lunapark6.com/?p=1710]("http://lunapark6.com/?p=1710")):

> Download Fuse from here [http://prdownloads.sourceforge.net/fuse/fuse-2.5.3.tar.gz?download](http://prdownloads.sourceforge.net/fuse/fuse-2.5.3.tar.gz?download)
tar -xvf fuse-2.5.3.tar.gz
cd fuse-2.5.3.tar.gz
sudo apt-get install build-essential
sudo apt-get build-dep fuse
./configure
make
sudo make install

Then download NTFS-3G from here [http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz](http://mlf.linux.rulez.org/mlf/ezaz/ntfs-3g-20070714-BETA.tgz)
tar -xvf ntfs-3g-20070714-BETA.tgz
cd ntfs-3g-20070714-BETA
./configure
make
sudo make install

Then add it to your fstab
/dev/hda1 /mnt/windows ntfs-3g silent,umask=0 0 0

Check to see if you have write permissions
sudo modprobe fuse && sudo umount -a && sudo mount -a

Now to make fuse load at bootup
echo fuse | sudo tee -a /etc/modules

Done. 

---

### Post by givré on 2006-11-02
If you want the latest version of ntfs-3g, go there :
[http://www.ntfs-3g.org/](http://www.ntfs-3g.org/)
Or use the ubuntu specific instruction :
[http://ubuntuforums.org/showthread.php?t=217009](http://ubuntuforums.org/showthread.php?t=217009)

Thanks

---

