---
title: "RAID problem with GRUB (dual boot)"
date: 2005-07-30
forum: Absolute Beginner Talk
---

### Post by Larkki on 2005-07-30
Hello. First I'd like to say "yes, I've searched this forum and done a lot of searching and experimenting with google, but I just haven't got this to work".
So I decided to register here and maybe some gurus can help me in this problem.

Ok, here's the deal:
I had Windows XP on my SATA RAID1 and I installed Ubuntu 5.04 (32bit) on an empty HD (slave). In installation, it didnt ask me where to install the grub boot loader. (it asked that on previous installations, but this time it didn't). Well, now it finds the grub fine and Linux boots fine (after I edited the /boot/grub/menu.lst) but I can't boot windows using grub.

I had problems with the linux installation before, so I decided to switch off my SATA drives during the installation. This way it didnt find Windows XP already installed in the system, so it made the grub only for linux. That was the only possible way I could even make linux work.

Now I'd like to edit the /boot/grub/menu.lst somehow in such a way, that I could boot my windows XP with the Grub loader. And I need your help.

My system:
AMD64 (shouldn't have anything to do with this)
Motherboard: MSI K8N Neo Platinum (Nvidia Raid controller for SATA and IDE)

Hard drives:
Primary Master IDE: Sony DVD-RW
Primary Slave IDE: Samsung 80GB (1 partition: just files on this drive)
Secondary Master IDE: IBM 60GB (1 partition: just files on this drive)
Secondary Slave IDE: Samsung 80GB (3 partitions: linux, swap and Fat32)
SATA RAID ch3 and ch4: Windows XP (mirroring, 1 partition)


When I have all drives connected and SATA is on, and in BIOS I change the primary boot hard drive to Secondary Slave IDE (samsung), it shows me the grub and I can boot to Ubuntu.

CORRECTION: When I change the boot order in BIOS so that NVidia Mirroring is first, it fails to boot to Windows. It just restarts when windows should start loading.
BUT, when I enable IDE raid for all my IDE drives (and SATA of course), then it boots to Windows. This just causes problems in windows, because those hard drives are not in use, but they are as spare disks for the raid. Also some program loadings failed, which is odd, because all my programs were in the SATA Raid.

I'd like to do this so that I can boot to windows using the Grub loader. The linux might have already messed up my windows so that it'll won't work properly, but if there's things I can do, i want to try.

I add some screenshots of my configuration:
[Device Manager](http://www.geocities.com/laurilarjo/Sisapiiri/Devicemanager.png) 
[dmesg from terminal]("http://www.geocities.com/laurilarjo/Sisapiiri/dmesg.png")
[fdisk -l from terminal]("http://www.geocities.com/laurilarjo/Sisapiiri/fdisk-l.png")
[/root/grub/menu.lst]("http://www.geocities.com/laurilarjo/Sisapiiri/grubmenu.lst.png")

The problem here is that I don't know which hard drive eg. (hd0,0) I must add to grub menu.lst for windows to boot properly. All the combinations don't seem to work. I tried things like sd0,0 as well, but doesn't seem to work.

Hope some of you knows how to do this.
Thanks for your time.

---

### Post by Larkki on 2005-07-30
UPDATE:
I threw in a Windows XP Installation CD and started system recovery. There I gave a command "FIXMBR" which definitely did something, because now I can boot into Windows normally.

So in BIOS, I have NVidia Raid as 1st boot drive, and all IDE Raid are disabled. And Windows works totally normally.

The issue now is only to tell grub how to boot this windows and after that I can change in BIOS the 1st boot drive to be that Samsung drive, where Linux is located.

---

