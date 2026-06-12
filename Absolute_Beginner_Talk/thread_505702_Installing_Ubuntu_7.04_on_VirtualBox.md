---
title: "Installing Ubuntu 7.04 on VirtualBox"
date: 2007-07-20
forum: Absolute Beginner Talk
---

### Post by sim085 on 2007-07-20
Hi,

I am having problems when I try to install Ubuntu 7.04 on Virtual Box. To install Ubuntu 7.04 I followed the step by step guide available from here:

[http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml](http://news.softpedia.com/news/How-to-Install-Ubuntu-7-04-Windows-User-P-O-V-52973.shtml)

However when I start the installation I get the following error message:

Failed to create a file system - The ext3 file system creation in partition #1 of IDE1 master (hda) failed.
(attached screenshot)

I have no idea what I have to do to complete the installation. I tried searching for the error on Google and even these forums but could not find anything I could understand. 

I am very new to the whole Linux world and would like to try and install it on a VirtualMachine so that I can learn how to use it. I am sure I am doing something wrong however I can not understand why. 

I would be glad for and comments regarding this.

Thanks and Regards,
Sim085

---

### Post by sim085 on 2007-07-20
Btw - I set the hard disk size to 8GB. Could the problem be because of this? What is the recommended hard-disk size for Ubuntu 7.04?

Regards,
Sim085

---

### Post by Majorix on 2007-07-20
> I am very new to the whole Linux world and would like to try and install it on a VirtualMachine so that I can learn how to use it.

I hate VMs.

Ubuntu comes as a LiveCD. So you could just put it in and try a few commands on it or check if your hardware is compatible etc. If you like it, install it on a PHYSICAL machine and use it that way.

PS: I also see that you have LowID on eMule. Lol, that was my nightmare back in the Windows days :p

---

### Post by sim085 on 2007-07-20
> **Majorix said:**
> Ubuntu comes as a LiveCD. So you could just put it in and try a few commands on it or check if your hardware is compatible etc. If you like it, install it on a PHYSICAL machine and use it that way.The thing is that there are some advantages for me. I am planning to create a base Ubuntu OS with all the tools for development on it so that when I start a new project I just need to copy this VM rather then having to format my computer (do not know if you get my point) > **Majorix said:**
> PS: I also see that you have LowID on eMule. Lol, that was my nightmare back in the Windows days :pWhat do you mean? :) and how did you get my emule ID? not that I bother or anything ... just cuirass :)

Regards and Thanks,
Sim085

---

### Post by steevols on 2007-07-20
> **sim085 said:**
>  how did you get my emule ID? not that I bother or anything ... just cuirass :)

Look at your system tray :)

---

### Post by sim085 on 2007-07-20
> **steevols said:**
> Look at your system tray :)Yes I have eMule open :) ... aaa ... Majorix told me that to show me windows is unsecure? ... sorry ... over here is already midnight ... guess I need another cup of coffee :) since I want to get Ubuntu installed by today .. that is yesterday! :)

Regards,
Sim085

---

### Post by jonsson on 2007-07-20
I have managed to install Ubuntu server 7.04 under VirtualBox on Kubuntu 7.04 but it won't boot. I get past Grub and then I get this (see screenshot). Any ideas?

---

### Post by scxtt on 2007-07-20
does the VM have a "virtual disk" assigned to it, and created? ... you mention an 8Gb disk (the file it uses as a disk) being created, but it seems like it can't be found when you go to install ...

i'd check your config for the VM itself ...

i use VMware, don't know what the equivalent *.vmx is for virtualbox ...

---

### Post by sim085 on 2007-07-20
> **scxtt said:**
> does the VM have a "virtual disk" assigned to it, and created? ... you mention an 8Gb disk (the file it uses as a disk) being created, but it seems like it can't be found when you go to install ..,I think it is recognizing it since I tried to actually do the partioning myself and correctly I only have 8GB of free space available (screenshot attached).> **scxtt said:**
> i use VMware, don't know what the equivalent *.vmx is for virtualbox ...The equivalent of *.vmx is *.vdi and in my case it is 8GB large.

---

### Post by scxtt on 2007-07-20
did you click "format" before moving forward?

*.vmx is the script that sets up the VM when it's "executed", basically a config file ... *.vmdk is the actual "disk" ...

---

### Post by sim085 on 2007-07-20
> **scxtt said:**
> did you click "format" before moving forward?From were? I do not have that option when creating the partitions. Also it seems that it is by standard that it formats the drives since it tells me that I am going to loose any data in them.

Regards,
Sim085

---

### Post by scxtt on 2007-07-20
in your screenshot above, there's a checkbox to format the 8589mb disk ... you should check that box, then hit "forward" ... otherwise it'll try to install on a RAW disk, which it can't do ...

---

### Post by sim085 on 2007-07-20
> **scxtt said:**
> in your screenshot above, there's a checkbox to format the 8589mb disk ... you should check that box, then hit "forward" ... otherwise it'll try to install on a RAW disk, which it can't do ...Yes I have them both checked for the root and home however I can not check it for the swap (schreenshot attached).

With the above settings I still get the same exact error at the same exact time! (5%). 

Regards,
Sim085

---

### Post by sim085 on 2007-07-20
Btw - I tried installing Ubuntu 6.06 and had the same exact problem. So I think that this is more related to Virtual Box rather then Ubunutu, as scxtt has also sugested!

Regards,
Sim085

---

### Post by sim085 on 2007-07-20
I now created a new hard disk that is Dynamic rather the fixed size and it seems to be installing without any problems! (so far). However I can not understand what difference this setting could be making on the Ubuntu installation!

Regards,
Sim085

---

### Post by vexorian on 2007-07-20
The virtualbox page states that it is incompatible with Ubuntu as guest, and I can say that I tried so and it seriously did not work (not even the live-cd) vmware was way faster in windows XP host and a Xubuntu guest worked very well, until I messed up something when trying to install vmware tools on xubuntu...

---

### Post by sim085 on 2007-07-21
Yesterday it seemed to be working when installing on a Dynamic Drive and OS Type set to 'Other/Unkown'. I then aborted to try and install it on a fixed size drive and OS Type set still to 'Other/Unkown' however this did not work! I am now trying the first option again!

Regards,
Sim085

---

### Post by sim085 on 2007-07-21
I confirm on Dynamic Drive it installs (even OS Type set to Linux 2.6). I will make an another post when I have installed it completly.

Regards,
Sim085

---

### Post by sim085 on 2007-07-21
Just incase anyone comes across this post while trying to install Ubuntu on VirtualBox ... I did manage to install it using a Dynamic Drive (I set it to a maximum of 7.6GB but I think that is irrelevant).

Regards,
Sim085

---

### Post by sim085 on 2007-07-21
(I hope the mods will not see my too many post as spams) ... As I said before I did manage to install it. When I restarted the system exactly after the first installation I had no problems. However when I then switched the OS and off and started it again it freezed on the black screen with 'startup...' writen on it. I then restarted the OS for onne or two times and it is going up normally. So personally I believe it maybe some incompetibility with Virtual Box! 

Regards,
Sim085

---

### Post by muncrief on 2007-07-25
In order to install Ubuntu, and possibly other Linux guests under VirtualBox 1.4 you must check the "Enable IOAPIC " option in the "General->Advanced" tab of the virtual machine. This causes the virtual machine to run in a deprecated mode, but it is still more than fast enough.

You also usually have to use an ISO image of the CD instead of the CD itself. To do this go to the "CD/DVD-ROM" tab, click on "ISO Image File" and then the Folder icon on the right of the dropdown box to enter the path to your ISO file. Then you can select it in the dropdown box.

This works for me under Ubuntu Feisty 7.04 i386 and AMD64, Fedora 7 AMD64, and Suse 10.2 i386 and AMD64.

I hope it works for you.

---

