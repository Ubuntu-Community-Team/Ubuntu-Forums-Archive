---
title: "How to backup/restore an entire disk"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Nikko963 on 2008-02-15
My server has a single, bootable drive with just Ubuntu server 6.06 LTS.

I need to be able to backup this disk and restore the contents in the same way I might use Norton Ghost to create/restore a disk image. Essentially, in the case of a problem, I want to restore the drive to a known good state. Since this state contains all of my server application settings, files, states, etc., I don't want to go the "reinstall Ubuntu server from scratch" route.

Ideally, this image would be kept on a CD/DVD or USB/Firewire external HD. I suppose it would need to be bootable.

Would rsync be the correct tool (it seems to be the one other threads recommend for similar applications)? Or another app?

Thanks for your help.

---

### Post by Medieval_Creations on 2008-02-15
I've only started playing with it, but PartImage seems to be a good app for imaging an entire drive.

---

### Post by .nedberg on 2008-02-15
Partimage, g4l or clonezilla would all do the job. Or Ghost if you have the $...

---

### Post by Het Irv on 2008-02-15
I like QuickStart because it has a few other options for rebuilding a computer.  See Sig.

---

### Post by Nikko963 on 2008-02-25
Thank you for your advice. I'll look into these.

---

### Post by HermanAB on 2008-02-25
You can use netcat and dd.

On server:
nc -l -p 5000|gunzip|dd of=file.img

On PC:
dd if=/dev/sda|gzip --fast|nc serveripaddress 5000

---

### Post by stooshbunutu on 2008-02-26
Another option that is good is [http://www.remastersys.klikit.org/](http://www.remastersys.klikit.org/) it creates a bootable live CD so you can reinstall easily, hope you like this

---

