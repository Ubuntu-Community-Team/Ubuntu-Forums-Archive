---
title: "[SOLVED] Mounting an Ubuntu ISO file in windows"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by JohnMac on 2008-02-21
I am a newb.(will become obvious)Bought a new AMD64 with a dual core , 2GB and XP. My plane was to instal UBUNTU in a virtual drive to allow me to install/uninstall Ubuntu easily. I used a PC mag DVD with all the software on it including Ubuntu. I was going Ok until I found I couldn't run Ubuntu from the DVD, I tried copying the file but I couldn,t get the PC to boot from it either, despite checking my bios settings.

Plan B was to use Daemon Tools Lite to mount the ISO file. I downloaded the App but when I ran it, I got a windows message " not a win32 program etc" The App is said to be 32/64 bit.

Does anyone know of another App which will mount the ISO for me?

TIA

---

### Post by swoll1980 on 2008-02-21
I use magic disc [http://www.magiciso.com/tutorials/miso-magicdisc-overview.htm](http://www.magiciso.com/tutorials/miso-magicdisc-overview.htm)

---

### Post by Squizz on 2008-02-22
If you want to install Ubuntu from inside Windows, you could try using [Wubi]("http://wubi-installer.org/").

I'd suggest that you download a Live-CD and boot your computer from that first of all though, as it will let you try Ubuntu without changing your system at all.  You can download it [here]("http://www.ubuntu.com/getubuntu/download")

---

### Post by ubuntu-freak on 2008-02-22
You mean you want to burn it to another disc? Ubuntu recommend [InfraRecorder](http://infrarecorder.sourceforge.net/). Always worked well for me.
 
Nathan

---

### Post by JohnMac on 2008-02-22
No, not much use burning another CD if I can't get the DVD to read it. I can take the file of the original CD, I need to mount it as a virtual drive.

---

### Post by asmoore82 on 2008-02-22
If you want to install Ubuntu, you must burn a physical disc to boot your system from.

If you want to virtualize Ubuntu, you need virtualization software such as VirtualBox or VMWare;
in this case, the virtualization software would facilitate mounting the disc image in a virtual drive.

---

### Post by northern lights on 2008-02-22
Nowadays, there is an excellent way of installing Ubuntu without a CD/DVD, actually.

Check out [unetbootin]("http://sourceforge.net/project/showfiles.php?group_id=198821&package_id=243411"). Download the .exe, and run it from within Windows. It adds an "Install Ubuntu" entry in your bootmenu. Reboot, and instead of choosing the default "Boot Win" option, select the installer. Make sure you're connected to the net (wireless did not work for me, the CAT5 had to be plugged in) choose a few options, wait some 20 minutes and you're done. When prompted for further software you should select "Ubuntu Desktop", otherwise you will only have a commandline after installation. All the other software I'd install from within Ubuntu.

---

### Post by JohnMac on 2008-02-23
Yeah thanks asmoore82 and others who offered assistance. I managed to to get it up and running using VMWARE.  Thanks again.

---

### Post by ubuntu-freak on 2008-02-23
Glad you got it working.
 
Nathan

---

