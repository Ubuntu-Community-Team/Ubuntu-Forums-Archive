---
title: "bad blocks before data-area: cannot make fs..."
date: 2007-01-02
forum: Absolute Beginner Talk
---

### Post by masterjail on 2007-01-02
Hello, I'm very begginer on Ubuntu.

By the moment, I use windows xp.

A few weeks ago I was working with a USB hard disk when someone turn off the power. When I tried to use my USB hard disk, windows xp didn't recognise it...

I read on Internet that I could boot my computer with a live version of some linux system and try to recover my hard disk...

I own an Ubuntu Live CD for the version 5.04 and tried it. I found that my USB hard disk works well (except some corrupted blocks) and move the data to a FAT partition of the internal hard disk...

Then I tried to do **mkfs.vfat -F 32 -c /dev/sda1** to make a FAT filesystem on the USB device but I get the message: **bad blocks before data-area: cannot make fs**.

I kept searching info about how to solve that and then I did the following: **fsck -pcfv /dev/sda1** and tried again **mkfs.vfat -F 32 -c /dev/sda1** with the same result...

Could anyone help me to repair my disk so I can use it on windows xp? In the future I plan to use only linux but now I need to use win...

Thanks :(

---

### Post by smoker on 2007-01-02
sounds like you've damaged the drive, maybe you could check the manufacturers website, they may have an app you could download to repair. some of them do something similar to a low level format and may make the drive usable again.

---

### Post by az on 2007-01-02
Use

sudo cfdisk /dev/sda

to erase every partition on the device.  Then, start fresh and create a new msdos partition.

Also, some devices don't do well with 32 bit FAT.  Use the default (16 bit).

---

### Post by masterjail on 2007-01-02
Nothing... I tried **cfdisk** then **mkfs** again but get the same error message ](*,)

---

### Post by smoker on 2007-01-02
what's the make and model of your usb hard drive?

---

### Post by masterjail on 2007-01-05
Mmmm... I did something wrong... I did **cfdisk /dev/sda1** instead **cfdisk /dev/sda**...

I could delete the partition and tried to create a new one with **FAT 32** but... the same error message: **bad clusters...**

I tried deleting the partition again and booted with **Hiren's Boot Disk 8.6** and made a new partition with **Partition Magic** and tried to format it with **FAT 32** again but... it took more than 50 hours!! (that's why I haven't replied yet) and the same thing... there are bad sectors :(

I tried to use a tool to repair bad sectors which name I don't rememeber now but the progress bar was expected to fill next week and then aborted...

I don't know what to do... :(

The device is a Trekstor USB External Hard Disk 200GB.

---

### Post by alfo_uy on 2007-03-18
you could do a low level format. it should take a while... but it will clean those bad sectors or abort if not. if you do not have anything to recover, give it a try.

good luck

---

### Post by ikki_72 on 2008-05-25
any solution IF i wanted to recover the datas in it but whenever i copy anything from that disk with bad sectors, my machine hangs..

---

