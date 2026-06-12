---
title: "Just installed.....  (sorry)"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by az on 2006-06-26
In regards to this thread ([http://ubuntuforums.org/showthread.php?t=204187)](http://ubuntuforums.org/showthread.php?t=204187)),

[QUOTE=acht]
i just reinstalled my ubuntu and i just need to know something. how do i get to my files that were on my previous install. there are some very important things and i dont know what directory ubuntu put them in after the reinstall. thanks!

it was all on my 40 gb partition. it should all be there after the install. if it only installs 2 gb of stuff it should erase it all. what i want to know is where it put my files. would it be in a hidden folder?
[/QUOTE]

I have had success using foremost to recover data from a formatted partition.

[http://foremost.sourceforge.net/](http://foremost.sourceforge.net/)
Here is the manpage:
[http://foremost.sourceforge.net/foremost.html](http://foremost.sourceforge.net/foremost.html)

You probably can recover most of your files.

You need to use the version from the site, since the version of foremost in the repositories is a little old and not very easy to use.

foremost -i /dev/hda1 -o /mnt

where hda1 is your erased partition and /mnt is another hard drive you own that you have installed and mounted under /mnt which will host the files that foremost can recover.  Yes, run it from a live cd so that you don't have to use your hard disk that is the one you need to recover.  Classicaly, you would use dd (data dump) to make an image of the partition and use that file as source, but you can just use the device straight AFAIK.

Anyway, good luck!

---

### Post by nalmeth on 2006-06-26
That's cool

What kind of data were you able to recover with it? Any music / pictures? Were any of the files damaged or corrupted?

---

### Post by az on 2006-06-26
I recoverd a usb drive that some guy at work formatted to ext using the ubuntu live cd.  So there is residual data when you format to ext3 - it does not blank the partition.

He had written to it but most files were recovered fine.

---

### Post by az on 2006-06-27
I just did the same exercise over again.  I formatted a usb drive to vfat, copied a bunch of stuff there and then formatted it to ext3.  Using Foremost, I then recovered about 40 megs worth of the original 62 megs that I put there.  I also recovered about 12 megs of stuff from previous formats (not the stuff I wanted, but still intact files).

Now, I would expect that you can recover more data from a partition that was originaly ext3 and then reformatted to ext3.  As well, since the installation of ubuntu would rewrite the same areas as the first time, most of the other 38 gigs of data should be more or less intact.


emma@ubuntu:~$ sudo umount /dev/sda1
Password:
emma@ubuntu:~$ sudo mkfs.vfat /dev/sda1
mkfs.vfat 2.11 (12 Mar 2005)
emma@ubuntu:~$ mkdir example
emma@ubuntu:~$ ls /media/usbdisk/
00001.jpg  00010.jpg  00022.jpg  00031.jpg  00064.jpg  00076.jpg  00100.jpg
00002.jpg  00011.jpg  00023.jpg  00032.jpg  00065.jpg  00077.jpg  00101.jpg
00003.jpg  00012.jpg  00024.jpg  00033.jpg  00066.jpg  00078.jpg  00102.jpg
00004.jpg  00013.jpg  00025.jpg  00034.jpg  00067.jpg  00079.jpg  00103.jpg
00005.jpg  00014.jpg  00026.jpg  00035.jpg  00068.jpg  00080.jpg  00104.jpg
00006.jpg  00015.jpg  00027.jpg  00036.jpg  00069.jpg  00081.jpg  00105.jpg
00007.jpg  00019.jpg  00028.jpg  00061.jpg  00070.jpg  00097.jpg  00106.jpg
00008.jpg  00020.jpg  00029.jpg  00062.jpg  00071.jpg  00098.jpg  00107.jpg
00009.jpg  00021.jpg  00030.jpg  00063.jpg  00072.jpg  00099.jpg  manual.pdf
emma@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on


/dev/sda1              62M   61M  1.2M  99% /media/usbdisk
emma@ubuntu:~$ sudo umount /dev/sda1
emma@ubuntu:~$ sudo mkfs.ext2 -j /dev/sda1
mke2fs 1.38 (30-Jun-2005)
Filesystem label=
OS type: Linux
Block size=1024 (log=0)
Fragment size=1024 (log=0)
15744 inodes, 62896 blocks
3144 blocks (5.00%) reserved for the super user
First data block=1
8 block groups
8192 blocks per group, 8192 fragments per group
1968 inodes per group
Superblock backups stored on blocks:
        8193, 24577, 40961, 57345

Writing inode tables: done
Creating journal (4096 blocks): done
Writing superblocks and filesystem accounting information: done

This filesystem will be automatically checked every 31 mounts or
180 days, whichever comes first.  Use tune2fs -c or -i to override.
emma@ubuntu:~$ ls /media/usbdisk/
lost+found
emma@ubuntu:~$ time sudo foremost -i /dev/sda1 -o example
foremost: /usr/local/etc/foremost.conf: Not a directory
Processing: /dev/sda1
|*|

real    1m9.807s
user    0m1.296s
sys     0m0.360s
emma@ubuntu:~$ sudo chmod -R +rwx /home/emma/example/
emma@ubuntu:~$ du example -h
53M     example/jpg
152K    example/gif
356K    example/png
53M     example

---

