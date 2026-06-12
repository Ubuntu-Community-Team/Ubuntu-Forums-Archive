---
title: "Setting up a Virtual Machine for Windows XP"
date: 2007-09-22
forum: Absolute Beginner Talk
---

### Post by GISuser on 2007-09-22
Over the past year I have been thinking about switching over to Ubuntu.  But, I need to run ESRI's ArcMap 9.2 software that only runs on Windows and does not run on Wine, Crossover, etc.  Dual boot will not work, I need to access ArcMap, GIMP, and NVU at the same time as I am in Grad School and need to post maps generated from ArcMap to my webpage.  I am constantly updating and creating maps, rebooting will be highly inefficient.

Recently, I came across a discussion on VMware (more generically, Virtual Machines [VM]).  Now I am ready to make the switch.  But, I need help on conceptualizing the set-up.  

Additionally, I have Ubuntu working on two older laptops and have learned the basics over the past year.  I can't wait to have Ubuntu as my primary OS.  I am using my Gateway 200ARC right now with Ubuntu (7.04) on it.  Having one computer to run ArcMap and another to run Ubuntu will not work either, as I travel for my work and do not want to carry around two computers.  I cannot network them either, some areas I travel to do not have internet access.

Below is an outline on the process I plan on implementing to install Ubuntu with Windows XP running on a Virtual Machine.  I first discuss my current setup, then discuss what I want to do. Lastly, I posted a few questions.

Current hardware and software (paritial) installation :
  1.  OS - Windows XP SP2
  2.  Computer - Thinkpad T60 ( 2623-D6U); 80 GB HD (two partitions 40GB each [NTSF]; c:\ contains program files and d:\ contains all personal files); 1.5GB RAM; Intel 10/100/1000 ethernet, Intel ProWireless 3945ABG, bluetooth, ATI Mobility Radeon X1300 graphics card.
  3.  Shipped without Windows XP CD.  Preinstalled in a protected partition.
  4. I backup my D:\ to an external HD (NTSF) weekly.
  5. ArcMap 9.2 with the Spatial Analyst and 3D Analyst Extensions.

Notes: 
  1. I have been using the computer for 1.5 years (under WIndows XP) with no problems.
  2.  I have ran the T-60 from the Live CD (7.04).  Connected to the internet via wireless and wired.  Basic functions work.

**What I want to do:**

After reading numerous posts over the past year, I believe I know what I need to do.  Please notify me if I am about to do something that will not work, suggestions, or words of caution.

1.  During the installation of Ubuntu 7.04, repartion, and format, the hardrive (80GB) as follows:
    a.  preserve Windows XP preload (FAT32); 5 GB
    b.  allow 60GB for Ubuntu and the virtual machine (Windows XP)
    c.  partition the remaining 15GB to FAT32 so its accessible from Ubuntu and the VM (WIndows XP)
    d.  install Ubuntu
    e.  install VMware or another package that the group recommends

Now: 

1.  do I install Windows XP onto the VM using the preinstall or the recovery CDs I created before wiping out the system?
2.  Would it be better, or is it possible, to run the VM on a separate partition?

I also read about 3D graphics not working in VMs.  I wonder if this is true for the 3D Analyst Extension in ArcMap?

It has been wonderful reading the posts.  Everytime I got stuck with configuring my older laptops, reading the discussion groups solved my problems.   Thanks!!

---

### Post by HermanAB on 2007-09-22
You have two options:
a. Dual boot Linux/Windoze
b. Install Windoze in a VM

Graphics are not so hot in a VM.  If you need intensive graphics, then dual boot.

You can either use VMware (Server and Player are free) or Virtualbox/Qemu.

Don't worry about the Windoze data.  Linux can read/write Windoze NTFS without much of a problem.  In a VM, you can share a directory on the host system with the VM.

Before you start, backup your data to DVDs.

Cheers,

H.

---

### Post by GSF1200S on 2007-09-22
> **GISuser said:**
> Over the past year I have been thinking about switching over to Ubuntu.  But, I need to run ESRI's ArcMap 9.2 software that only runs on Windows and does not run on Wine, Crossover, etc.  Dual boot will not work, I need to access ArcMap, GIMP, and NVU at the same time as I am in Grad School and need to post maps generated from ArcMap to my webpage.  I am constantly updating and creating maps, rebooting will be highly inefficient.

Recently, I came across a discussion on VMware (more generically, Virtual Machines [VM]).  Now I am ready to make the switch.  But, I need help on conceptualizing the set-up.  

Additionally, I have Ubuntu working on two older laptops and have learned the basics over the past year.  I can't wait to have Ubuntu as my primary OS.  I am using my Gateway 200ARC right now with Ubuntu (7.04) on it.  Having one computer to run ArcMap and another to run Ubuntu will not work either, as I travel for my work and do not want to carry around two computers.  I cannot network them either, some areas I travel to do not have internet access.

Below is an outline on the process I plan on implementing to install Ubuntu with Windows XP running on a Virtual Machine.  I first discuss my current setup, then discuss what I want to do. Lastly, I posted a few questions.

Current hardware and software (paritial) installation :
  1.  OS - Windows XP SP2
  2.  Computer - Thinkpad T60 ( 2623-D6U); 80 GB HD (two partitions 40GB each [NTSF]; c:\ contains program files and d:\ contains all personal files); 1.5GB RAM; Intel 10/100/1000 ethernet, Intel ProWireless 3945ABG, bluetooth, ATI Mobility Radeon X1300 graphics card.
  3.  Shipped without Windows XP CD.  Preinstalled in a protected partition.
  4. I backup my D:\ to an external HD (NTSF) weekly.
  5. ArcMap 9.2 with the Spatial Analyst and 3D Analyst Extensions.

Notes: 
  1. I have been using the computer for 1.5 years (under WIndows XP) with no problems.
  2.  I have ran the T-60 from the Live CD (7.04).  Connected to the internet via wireless and wired.  Basic functions work.

**What I want to do:**

After reading numerous posts over the past year, I believe I know what I need to do.  Please notify me if I am about to do something that will not work, suggestions, or words of caution.

1.  During the installation of Ubuntu 7.04, repartion, and format, the hardrive (80GB) as follows:
    a.  preserve Windows XP preload (FAT32); 5 GB
    b.  allow 60GB for Ubuntu and the virtual machine (Windows XP)
    c.  partition the remaining 15GB to FAT32 so its accessible from Ubuntu and the VM (WIndows XP)
    d.  install Ubuntu
    e.  install VMware or another package that the group recommends

Now: 

1.  do I install Windows XP onto the VM using the preinstall or the recovery CDs I created before wiping out the system?
2.  Would it be better, or is it possible, to run the VM on a separate partition?

I also read about 3D graphics not working in VMs.  I wonder if this is true for the 3D Analyst Extension in ArcMap?

It has been wonderful reading the posts.  Everytime I got stuck with configuring my older laptops, reading the discussion groups solved my problems.   Thanks!!

Im going to jump around a bit in my answer. Because of a relativly new program called ntfs-3g, you would be able to have your Windows partition in NTFS, and create a seperate ext3, reiserfs, or xfs partition for Ubuntu (no FAT32 necessary). The VM is on a .vdi file, so its sandboxed from the OS that hosts it. To share files between the VM and the host OS, you would need to create a network drive in the VM linking it to a folder in Ubuntu. 

You could store the .vdi file on the NTFS partition, that way you could access the VM with Linux or your hard drive install of Windows.

Installing Windows will be tricky... ill be back with more-

---

### Post by GISuser on 2007-09-22
I just read about ntfs-3g a few days ago!  I need to test it out with my backup drive from my Gateway 200ARC running 7.04.

Also, I still have my WIndows XP CD for the Gateway.  Maybe I will test the VM concept first.  Then I could test the graphics as well.  The Gateway is my test machine.

The Gateway has a 60GB HD, 500MB RAM, and the Intel Centrino chip.  I would partition it the same way I would the T-60 but with NTSF.

I am just too anxious to dump Windows!

---

### Post by GSF1200S on 2007-09-23
> **GISuser said:**
> I just read about ntfs-3g a few days ago!  I need to test it out with my backup drive from my Gateway 200ARC running 7.04.

Also, I still have my WIndows XP CD for the Gateway.  Maybe I will test the VM concept first.  Then I could test the graphics as well.  The Gateway is my test machine.

The Gateway has a 60GB HD, 500MB RAM, and the Intel Centrino chip.  I would partition it the same way I would the T-60 but with NTSF.

I am just too anxious to dump Windows!

Sorry, I had some important stuff to do or I would have finished my reply earlier...

ntfs-3g will work without an issue. No need to test it really. Once you install it through synaptic, you install the ntfs config tool from synaptic too. Then you run it as root (alt+f2), and set it up for read-write access. This way Ubuntu could write files to your hard drive install of Windows. There is also a program out there (do a goole search) that allows Windows to read ext3 partitions, so all three OS' (Ubuntu, Windows hard drive install, Windows VM) could communicate. You would store the Windows VM .vdi file on the NTFS partition so that Windows can use it, and set up 2 network drives on the VM (say X: and Y: drives). You would then throw a command into both Ubuntu's terminal and Windows command prompt. Then in your VM, you could choose whether to make the file available to Windows on your hard drive, or Ubuntu on its partition, or both, and you could do it from Ubuntu or Windows.  You could also share freely files from Ubuntu to windows or vice versa. Complete freedom :)

As far as installing Windows... this is where stuff gets crappy. Its not because of Linux, but rather because of greedy licensing laws on Microsoft's part. Technically, its illegal to use an OEM windows CD to install Windows on a hard drive AND on a virtual machine: you legally need 2 copies of Windows for that. That said, there are ways around it, but i couldnt say any of that here. Best bet.. check to see if every 3d program will work for you in your Virtual Machine, and then possibly consider either a) purchasing another copy of XP before Jan 1, 2008 (thats when Microsoft will stop selling XP and only offer Vista), or b) figure out a workaround. Now.. if you have already PURCHASED an XP cd, than you can use it on a different computer, as long as only 1 computer has it installed. You may have to call and get a new activation code, but its still legal because you own the Windows XP CD, and therefore can always use it, so long as its only on one machine (if you guys out there know more or disagree, let us know). I researched this too, because I run a VM myself.

Now, you have to choose which Virtual Machine you want to use. This usually starts a flame war between the VMWare and VirtualBox fans. I myself use VirtualBox because of its Guest Additions option, which allows automatic mouse capture, automatic resizing of the VM when you change the window size, etc, but VMWare has its own merits. If I were you, I would do a little research as to which VM software offers the best 3d support, and go that route to see if it will run all your software.

Let me know if you need any more help, and good luck :)

---

### Post by funrider on 2007-09-23
FYI, i did use Norton Ghost recovery image to clone my old windoze desktop into a VM with vmserver, on my fiesty fawn. Performance is great (better actually since i have a better physical machine now which i can allocate 1GB of ram to windoze and with dual processor).

---

### Post by GISuser on 2007-09-24
Just a quick update.  

Installed Ubuntu 7.04 on T60.  No more Windows XP.  Not even a dual boot.  I am slowly customizing the install to meet my needs.

Over the next few days, I will work on installing VMware server and load Windows XP and see if I can run ArcMap.

Thanks again for the support.

---

