---
title: "[SOLVED] how to mount an external hard drive in recovery mode?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by Korrontean on 2008-03-24
Hi, this morning for some unknown reason the system wouldn´t boot normally. After the Ubuntu logo came a dreadful black screen.
I tried typing gdm for recovery mode and it is working fine, but I want to copy my personal data to an external hard drive in order to try a re-install.
However, I don't know how to mount it... can anyone help?
THANK YOU!!! :)

---

### Post by kpkeerthi on 2008-03-24
Are you sure you want to re-install? 

Why not try recovering X before you reinstall the whole thing?

Boot into recovery mode and at the prompt, type
```
dpkg-reconfigure -phigh xserver-xorg
```
and select the driver and resolutions your monitor supports. If your are not sure what driver to choose, select **vesa**. Type **reboot** and boot into normal mode. Post back the result.

---

### Post by kpkeerthi on 2008-03-24
Plugin your external drive and post the output of ```
fdisk -l
```

---

### Post by Korrontean on 2008-03-24
Thanks kpkeerthi!
In fact, :oops: I was not very precise in the use of the terms: "a dreadful black screen". I get a black screen in text mode, full of weird error messages. So it is not a screen problem.
I re-booted to enter recovery mode. I typed gdm and everything looks quite normal... the language is set back to English and not my native Basque, but no problem. The thing is that my external hard drive is not mounted automatically and I don't know how to do it manually. I've been trying to do it with no success, although I imagine it is a pretty easy process. :oops:
As my last fresh install is quite recent (not lots of programas, customization yet) and I need to get back to work as soon as possible, I thought a re-install after recovering my personal data was the most sensible thing to do. :oops:
Thank you very much for your attention and help!!! :D

---

### Post by kpkeerthi on 2008-03-24
OK... Plugin your external drive, wait for a few seconds and post the output of
```

fdisk -l

```

---

### Post by Korrontean on 2008-03-24
Sorry had not read your last message. I'll try to post it, but I'm typing from another computer (the network does not allow my laptop to connect to the internet), so without the possibility to bring the text to this computer by an external memory (which I can't mount) will be a little slow. I'll be right back!

---

### Post by kpkeerthi on 2008-03-24
> **Korrontean said:**
> Sorry had not read your last message. I'll try to post it, but I'm typing from another computer (the network does not allow my laptop to connect to the internet), so without the possibility to bring the text to this computer by an external memory (which I can't mount) will be a little slow. I'll be right back!

Can you tell me what is the partition type of your external drive, if you remember from the top of your head? NTFS? FAT32?

---

### Post by Barrucadu on 2008-03-24
This will work in 99% of all cases, if not, we'll need the output of fdisk -l to help further.

```
sudo mkdir /media/usbdrive
sudo mount -t vfat /dev/sda1 /media/usbdrive
```

I have yet to find a removable drive that isn't located at /dev/sda1, and with a filesystem other than fat32.

---

### Post by Korrontean on 2008-03-24
OK, the output of fdisk -l is:
```

Disk /dev/sdc: 2056 MB, 2056257536
16 heads, 32 sectors/track, 784 cylinders
Units=cylinders of 512 * 512 = 262144
Disk identifier: 0x4f8f1e77

Device Boot       Start         End              Blocks             Id          System
/dev/sdc1                1          7844             2008048        e          W95   FAT16 (LBA)
```

---

### Post by Barrucadu on 2008-03-24
Well, I'll be damned, it's NOT at /dev/sda1.

Try this:
```
sudo mkdir /media/usbdrive
sudo mount -t vfat /dev/sdc1 /media/usbdrive
```

---

### Post by kpkeerthi on 2008-03-24
OK here are the steps...
```
sudo mkdir /media/sdc1
```
```
sudo mount /dev/sdc1 /media/sdc1 -o umask=000
```

You should see an icon on the Desktop. If not open nautilus and navigate to /media/sdc1

The filesystem type on the external drive is FAT16 which is way [dated]("http://www.microsoft.com/technet/prodtechnol/windows2000serv/reskit/core/fncc_fil_blpd.mspx?mfr=true"). Consider upgrading it to a better filesystem like ext3 or atleast FAT32.

---

### Post by Korrontean on 2008-03-24
Thank you very much, kpkeerthi and Barrucadu!!! It worked!:guitar:
```
Well, I'll be damned, it's NOT at /dev/sda1.
```
Maybe I misled you because, although I was talking about a portable external hard drive at the beginning, I finally tried a USB memory stick because it was easier to bring along with me to the computer where I'm typing from. ;)
THANKS!!!! \\:D/

---

### Post by Korrontean on 2008-03-24
> The filesystem type on the external drive is FAT16 which is way dated. Consider upgrading it to a better filesystem like ext3 or atleast FAT32.
How can I do that? I use this USB memory stick as a constant bridge to exchange data with many different Windows computers.

---

### Post by kpkeerthi on 2008-03-24
1. Boot with ubuntu live cd
2. Plugin your flash drive
3. Press ALT + F2 and type **gparted** or System -> Admin -> Disks & Partitions
4. Click on the partition you want to format. Right-click and unmount*. Now click Delete from toolbar.
5. Right-Click and select New. In the popup that opens, select the partition type as ext3. 
6. Click OK and Apply.

* If the drive automounts, Go to System -> Preferences -> Removable Drives and Media and then uncheck the first two boxes on the storage tab

---

### Post by lswest on 2008-03-24
also, if you pop it into windows you can right-click the drive and choose "format" and i do believe XP (not sure about vista) will ask you what filesystem type you want to format it as, and FAT32 is what you want to choose, in case you're more comfortable using windows for that.

---

### Post by Barrucadu on 2008-03-24
> **kpkeerthi said:**
> 1. Boot with ubuntu live cd
2. Plugin your flash drive
3. Press ALT + F2 and type **gparted** or System -> Admin -> Disks & Partitions
4. Click on the partition you want to format. Right-click and unmount*. Now click Delete from toolbar.
5. Right-Click and select New. In the popup that opens, select the partition type as ext3. 
6. Click OK and Apply.

* If the drive automounts, Go to System -> Preferences -> Removable Drives and Media and then uncheck the first two boxes on the storage tab

Before you do that, back up everything on it. Also if you use this with Windows computers you should format it to NTFS or FAT32, as Windows can't read Ext3 without installing a third party driver, which will not be on every computer you need to use the flash drive with.

---

### Post by Korrontean on 2008-03-24
Thank you!!!

---

### Post by rosegarden78 on 2008-03-24
If you use gparted, cfdisk or mkdosfs to format/partition in Linux, chances are it will destroy the boot sector and master boot record.  Windows can only read drives formatted with a Microsoft boot sector and/or MFT.  If your drive works in Windows convert it to NTFS and leave it alone.  Run disk defragmenter from time to time.

Related articles:
[http://ubuntuforums.org/showthread.php?t=277684&page=2](http://ubuntuforums.org/showthread.php?t=277684&page=2)
[http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format](http://ubuntuforums.org/showthread.php?t=708426&highlight=ntfs+format)
[http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361](http://ubuntuforums.org/showthread.php?p=4579361&posted=1#post4579361)

---

### Post by Korrontean on 2008-03-24
Thanks everyone for your great support. You've been extremely patient and helpful!!! :)

---

