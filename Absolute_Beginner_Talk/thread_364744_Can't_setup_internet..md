---
title: "Can't setup internet."
date: 2007-02-18
forum: Absolute Beginner Talk
---

### Post by Matt1632 on 2007-02-18
I'm trying to decide whether to install Ubuntu on my pc(HP Laptop).  I'm just using the 6.06 LTS Live CD to test it out.  All my hardware seems to work great but I can't connect to my network to use the internet.  If I go to System>Administration>Networking it looks like my wireless card interface is not active, whereas my ethernet interface is active.  If I connect my computer to my router nothing happens.  I've never used linux before so I'm not sure how to set up network connections.  Can someone tell me or give me a link to a guide?  Ubuntu's web documentation didn't say much about the setup process. 
Thanks :)

---

### Post by mikewhatever on 2007-02-18
Do you know which wireless card you have? Look in Windows in the device manager and copy all there is about the wireless.

---

### Post by Matt1632 on 2007-02-18
Ok.

-Network Adapters.
  -1394 Net Adapter
  -Broadcom 54g MaxPerformance 802.11g
  -Realtek RTL8139/810x Family Fast Ethernet NIC
I don't need to use the wireless though, as long as I can connect to the network.  Also my router is a Linksys WRT54G Ver.2.

---

### Post by annda on 2007-02-18
the realtek ethernet card should just work. have you tried connecting to your router via cable and rebooting? that way, ubuntu will be able to load the appropriate modules/drivers and configure your network on boot.

from what i read, broadcom wireless might need some manual consiguration...

---

### Post by Matt1632 on 2007-02-18
Ok , I'll try booting ito ubuntu while it's connected.

---

### Post by mikewhatever on 2007-02-18
As I understand, you haven't installed yet, and tried live sessions. Not sure if that's gonna help, but you can try another one with the network cable pre-connected. There is a chance it might work. Broadcom cards are not too easy to setup though.

---

### Post by Matt1632 on 2007-02-18
Ok, that worked.  Thanks for the help.

---

### Post by annda on 2007-02-18
so now you can safely install! welcome and have (productive) fun!

---

### Post by Matt1632 on 2007-02-18
Well, i've got a few more questions.  I want to use it dual-boot with windows xp.  I have  74.5gb hard drive(48.9gb used) how big should I make the partition for Ubuntu when I install?  Also how easy is it to remove ubuntu and it's partitions if I decide I don't want it?  Also, say my computer gets messed up.  Can I use the Live CD(or some other bootable disk) to reformat my hard drive as NTFS and delete the partitions so I can use my hard drive backup software's boot disk to restore my computer. (To before I installed Ubuntu)

---

### Post by annda on 2007-02-18
i think 10 GB is a lot of space for ubuntu and lots of programs you will want to use and try out.

when you don't like it, you can use the liveCD or gparted liveCD ([http://gparted.sourceforge.net/](http://gparted.sourceforge.net/)) to delete the linux partitions and resize back your windows partition.

however, ubuntu will install GRUB - a boot manager to choose an OS to boot to. make sure you have some sort of windows install cd or floppy before you get rid of linux (in case you ever do). that's the easiest way to remove the boot manager.

also, if you have more questions, you will be more likely to get answers when you post another thread about dual booting - some people may not read threads about internet.

---

### Post by mikewhatever on 2007-02-18
> **Matt1632 said:**
> Well, i've got a few more questions.  I want to use it dual-boot with windows xp.  I have  74.5gb hard drive(48.9gb used) how big should I make the partition for Ubuntu when I install?  Also how easy is it to remove ubuntu and it's partitions if I decide I don't want it?  Also, say my computer gets messed up.  Can I use the Live CD(or some other bootable disk) to reformat my hard drive as NTFS and delete the partitions so I can use my hard drive backup software's boot disk to restore my computer. (To before I installed Ubuntu)

Well, it doesn't look like you have a lot of space left, but I'd suggest 10 GB for Ubuntu and about 512-1024 MB for swap. Before installing, defragment and run CHKDSK check from Windows.
Removing Ubuntu is not very hard, but you'll have to fix the MBR or restore it from backup if there is one. [Uninstall Page]("http://www.users.bigpond.net.au/hermanzone/p18.htm") has more.
If you PC gets messed up, you can use the lice Cd to restore GRUB, the boot loader, but I don't know about reformatting. Below are some useful links for reformating:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)  gparted live CD
[http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)         system resque CD

also, if you have Windows recovery CD/DVD by HP, you can reformat with them.

May I also suggest a few more links I found very useful:

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)
[http://users.bigpond.net.au/hermanzone/p15.htm](http://users.bigpond.net.au/hermanzone/p15.htm)
[http://users.bigpond.net.au/hermanzone/p5.htm](http://users.bigpond.net.au/hermanzone/p5.htm)
[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

I am sure there are more, but well, good luck with the installation.

---

