---
title: "install GRUB2 on MAC"
date: 2014-03-22
forum: Apple Hardware Users
---

### Post by flamant on 2014-03-22
Hello
I try to install ubuntu on my MAC book pro. I have a Mac book 9,2 (mid 2012) and try to install ubuntu 12.04.4

I installed reflt and created a 50 GO partition formated in hsf+

I passed successfully the stage of burning the MAC version   "ubuntu-12.04.4-desktop-amd64+mac.iso" to a DVD and getting the   installation menu. I succeded in getting the menu to format my 50GO with  ext4 where I am going to install Ubuntu

But a pop-up appear saying 

The partition table format in use on your disks normally requires you to  create a separate partition for boot loader code. This partition should  be marked for use as a "reserved BIOS boot area" and should be at least  1MB.
If you do not go back to the partitioning menu and correct this error,  boot loader installation may fail later, although it may still be  possible to install the boot loader to a partition

If I well understood, I need to install a boot loader like GRUB2

I have several questions:

1) visibly reflt is a menu to switch on a OS choice. Should I use it plus the installation of GRUB2 ? What is the link between them ?

2) Is it dangerous to install GRUB2 on MAC OS X ? is there any risk ?

3) from what I read, you haven't to choose a partition when you install GRUB2. Is it possible to choose the partition for installing it ? If so, on which partition should I install it ? The one where OS X is or the one where ubuntu is going to be install ?  a priori, I would say on the ubuntu partition (see the message above) !! So how to do it ?

4) I found GRB2 documentation on this link [http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB](http://www.gnu.org/software/grub/manual/grub.html#Obtaining-and-Building-GRUB)
When I download by the link [ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz](ftp://ftp.gnu.org/gnu/grub/grub-2.00.tar.gz) , and I try to configure (./configure), the program stops with the following log

```

MacBook-Pro-de-xflamant:grub-2.00 xflamant$ ./configure
checking build system type... i386-apple-darwin12.5.0
checking host system type... i386-apple-darwin12.5.0
checking target system type... i386-apple-darwin12.5.0
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... build-aux/install-sh -c -d
checking for gawk... no
checking for mawk... no
checking for nawk... no
checking for awk... awk
checking whether make sets $(MAKE)... no
checking for cmp... cmp
checking for bison... no
configure: error: bison is not found

```

4-a) first remark: it seems that the version GRUB2 is for i386 architecture. Do you know if there is a amd64 release ? If so, do you know the link ?
4-b) When I try afterwards > make install, the system tels "make: command not found". I didn't suceed in going furthet

Thanks in advance for your answers

---

### Post by PartisanEntity on 2014-03-25
What you can try to do is leave the 50GB partition unformatted as free space.

Then you can choose the option "Install ubuntu side by side with Mac OSX". The installer will select the free space (but double check that it is the correct partition anyway).

This way the installer will take care of swap and bios boot partition for you.

That is how I installed Ubuntu 12.04 on my iMac as a dual boot option.

---

### Post by andy10 on 2014-03-25
I have a MacBook Pro 9,1 (Mid 2012). I have installed Xubuntu 14.04 on it (I have tried Ubuntu 14.04 as well). I used the OS X Boot to recovery system to resize the OS X Lion partition to half of the 500gb disk space and left the other half blank. I then installed rEFInd on the OS X partition. 

I put the Xubuntu 14.04 image on a usb stick and booted it using rEFInd.  I selected “something Else” as the install choice and set up the free space with 10gb for the “/” partition 16gb for the swap space as I have 16gb RAM, probably overkill, and the remainder as “Home.” 

I also selected the Xubuntu partition as the location for the GRUB installation location. REFInd provides the boot choices for you now and you can choose Linux or OS X at boot time. Everything is working fine on my machine. I do use a script called “control” in a cron job as described on this web page ( [http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/](http://unencumberedbyfacts.com/2013/08/16/linux-on-a-macbook-pro-101/) ) to control the fans and have better control of the heat.

Hopefully, this will be of some help to you.

Andy

---

