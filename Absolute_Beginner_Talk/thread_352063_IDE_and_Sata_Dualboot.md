---
title: "IDE and Sata Dualboot"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by Razer on 2007-02-02
I have 3 hard drives which consists of 2 IDE and 1 SATA. The 60GB IDE has Windows on it, the 160 IDE is storage, and the 160 SATA is brand new with a few files on it. I want to dual boot with Windows on the 60GB IDE as the master and Ubuntu on the 160 SATA. I've read the posts on how to do this without messing with the Windows MBR but I just wanted to make sure that I've got it correct. First I will select the SATA drive as the primary HD in bios and install Ubuntu on that (which should install grub on that HD right?). Then adjust the grub configurations and when I start up my computer it should give me the option of windows or Ubuntu right? I'm sorry if this thread seems repetitive but all the posts got confusing after a while and I just want to make sure that what I'm doing is correct. Thanks!

---

### Post by mikewhatever on 2007-02-02
Yes something like that. The main point is that GRUB is installed to Ubuntu HD MBR. They even advice to disconnect other HDs to prevent possible confusions.

---

### Post by logos34 on 2007-02-02
> First I will select the SATA drive as the primary HD in bios and install Ubuntu on that (which should install grub on that HD right?).

That should work...If you're using the live cd what you'll see when you get to the 'Ready to install' screen is 'Grub will be installed to (hd0)'...As long as the sata is first hard disk in bios boot priority it should be hd0, although grub may see the primary master as hd0 in which case the sata would hd1 0r hd2...You can try it, the worst that can happen is that grub will overwrite the windows bootloader and you'll then have to restore it with 'fixmbr', then use the live cd to setup grub on sda, or use Supergrub disk.  

One way to be sure grub goes to the target disk is to disconnect the others during install.  Of course that means you'll have to add them manully to menu.lst and fstab.

---

### Post by Razer on 2007-02-02
Thanks for the responses. Another quick question; is it better to use Fat32 or ext3 for communication between windows and ubuntu?

---

### Post by logos34 on 2007-02-02
> **Razer said:**
> Thanks for the responses. Another quick question; is it better to use Fat32 or ext3 for communication between windows and ubuntu?

Well, you can use fs-driver in windows to read and write to ext3.  Fat32 is probably the most popular way, although it fragments more easily than ntfs and there is a 4gb file size limit.  NTFS-3G, which allows you to read and write to windows from linux, is another option (i've been using it for a short time now and haven't encountered any problems whatsoever).

---

### Post by ckaspereli on 2007-02-02
Can Ubuntu 6.XY be installed on a USB connected hard drive as a bootable partition?

---

### Post by Razer on 2007-02-03
Ok I've just installed ubuntu 6.10 on my 160 SATA drive and a couple of weird things has happened. Before the install, it said that grub will be installed on hd0. I put the SATA drive as my primary drive and clicked continue and took a leap of faith because I was not 100% sure that hd0 was my SATA drive. Now after the install, I reboot and instead of giving the choices, it simply said ,"Can't find OS" or something to that extent. At this point, I change the boot settings to my 60GB IDE with Windows and a message comes up and says "Grub loading..please wait. Error 22" and it freezes. At this point, I thought that my computer was kaputt so I reach for my windows CD and try to repair it. But the windows CD gives me the BSOD and says that it has to shut down the computer. So I restart give the following boot options: 1.DVD Drive 2.Windows Drive 3. Ubuntu Drive. This actually brought me to the menu where I can select the OS that I want and everything works perfectly. If someone could tell me if GRUB is loaded onto my windows MBR or Ubuntu HD that would be really helpful. Thanks for reading!

---

### Post by mikewhatever on 2007-02-03
hd0 should be the first HD. Have you edited the grub menu yet?

---

