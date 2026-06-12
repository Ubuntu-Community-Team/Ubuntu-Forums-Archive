---
title: "Mounting a network share &amp; DosBox"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by Atomic Dog on 2007-01-13
Is there a folder location for a mounted Windows network share?  Something like /media/netshare ??? I am mounting the share with Nautilus, by specifying the server IP, share name and username.  lBut I can't seem to find a folder location like I would if I mounted a usb drive or cdrom.

I'm trying to use Dosbox to solve a problem with a very old proprietary program at work.  Dosbox will run the program (yay!), but I need to tell Dosbox to mount a folder as a drive (for instance I can say in Dosbox mount c /home/atomicdog/Desktop and c:/ would be my Desktop folder.  So I'm looking to use a command like mount d /mnt/mountedShare.

Not knowing where the folder for mounted shares in Nautilus is kinda my problem.

---

### Post by dann0 on 2007-01-14
Nautilus don't mount the share, it only connect to it.

Personally I use Samba and SMBFS to mount a network share to whatever folder I like.

**sudo apt-get install smbfs**

**mkdir /home/public**

**sudo mount -t smbfs //IP_to_host/Share_name /home/public -o username=YouAtHost,password=xxx,uid=YouAtUbuntuMachine,gid=YouAtUbuntuMachine **

Then you can browse the contents of /home/public/ as if it is a local folder.

Hope this helps...
There are plenty of information about Samba on the net.

---

