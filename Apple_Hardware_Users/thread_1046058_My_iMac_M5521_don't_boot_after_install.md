---
title: "My iMac M5521 don't boot after install"
date: 2009-01-21
forum: Apple Hardware Users
---

### Post by JujuLand on 2009-01-21
Hi,

I have installed Ubuntu 7.10 on an old iMac, the only reference I have is the model number M5521. It's a G3 400MHz

It seems that the install is complete, but when I boot, I just have the folder and the question mark.

Here are the disk parts:

08    Mo NewWorld
08.5 Go ext3 /
01    Go swap
11    Go /home

I must say that this iMac had OS 9.1 installed, and as I don't want to use it, I remove it.

Is-it possible to boot on Ubuntu without an installed mac OS, and how ?

I suppose yaboot ought to be in NewWorld part ?

Can somebody help a new user of an old machine ?

Thanks

A+

---

### Post by avtolle on 2009-01-21
You don't need a Mac OS installed to run Ubuntu. There was a problem with 7.10 installer, but you indicate that you believe the installation completed. Have you access to a later version of Ubuntu (8.04 LTS or 8.10) or could you download and try to install one of these? Finally, do you know how much RAM is in your computer?

---

### Post by avtolle on 2009-01-21
[https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot](https://wiki.ubuntu.com/PowerPCKnownIssues#Gutsy%20CDs%20will%20not%20boot) may have some information, too; while this will come up with the CD not booting section, scroll through the entire piece for information.

---

### Post by JujuLand on 2009-01-21
Thanks for the infos, 

I have upgrade the computer, and I have 20 Go on the HD and 256 Mo RAM

I'm happy to read that Mac OS(X) isn't needed, because I have tried now to install 9.2.2 with special parameter (it take less than 400 Mo), but now impossible to boot on the 7.10 alternate CD.

As I have 8.04.1 and 8.10 alternate CD, if I have understood, I can format my disk and install 8.10.

I have already tried to install 8.10, but after booting, when searching for devices, the install says that he don't find CD, and I must insert a driver for the CD-ROM.

Well, I don't know exactly what to do. First, as I can't now boot on a CD, I will format the disk (under Windows) to clear it (it was the only way I found to be able to install OS(x) there is some time).

A+

---

### Post by avtolle on 2009-01-21
For 8.10, during installation, when that error message comes up, do this: get to another virtual terminal by pressing Alt (or Option)+Ctrl+F2 together; press Enter as directed. Then, at the prompt type ```
sudo modprobe ide-scsi
```then return to the original screen by pressing Alt(Option)+Ctrl+F1 together at the same time. Then, if your install goes as mine, there will be a highlighted option, press the Enter key, and it should proceed. Good luck.

---

### Post by JujuLand on 2009-01-22
Thanks for all your advices, but I haven't yet been able to make it work.

1) I have created a dos partition that I have deleted. Result : the disk is blank for iMac > ok

2) I have tried to install with alternate 8.04.1 

install modprobe ide-core  >>> ok, but as I prefer to install 8.10, I have quit the install

3) I have tried to install with alternate 8.10 

install modprobe ide-core  >>> doesn't find cd

in new console :

modprobe ide-core  >>> module ide-core not found

>> this doesn't work

The problem now if that I don't know how to extract the CD, because it always boot on the alternate 8.10. 

I don't know if it's normal or if I have a problem ...

Thanks 

A+

---

### Post by avtolle on 2009-01-22
For 8.10, the command is```
sudo modprobe ide-scsi
```

---

### Post by JujuLand on 2009-01-22
ok, thanks

but, is there a key to extract a cd ?

A+

---

### Post by avtolle on 2009-01-22
If I understand your question, once the CD drive is found, the installer will extract the needed files and write them to the HDD as the installation process continues.

---

### Post by JujuLand on 2009-01-22
In fact, when I sent the last post, I hadn't the answer

For now, I can say yes, the CD is correctly detected, and the CD is browsed for install

It seems that for 8.10, the modprobe command (which doesn't need sudo) only works in a console, not in yaboot. For 8.04.1, it works in yaboot, and probably in a console.

In fact, the last question I post was about the possibility when starting the Imac, to extract a CD which is already in.

Sometimes, when starting, the CD was ejected, but now, no more ejection at startup.

A+

---

### Post by avtolle on 2009-01-22
Yes, the modprobe command needs to be given at the console on 8.10, and while running from the live CD does not need sudo, although I always present it in that way as sudo is needed once the system is installed. 

To eject the CD, does your keyboard have an eject key? Press it if it does and see if that will work.

---

### Post by JujuLand on 2009-01-22
I'm not running Live CD, but alternate, and no sudo is needed during install.

How can I found the Eject Key ? What does it look like ?

For the modifications to do after install (adding ide-scsi in a file), I suppose that it's the file which is in memory, and that the update command will write it on the disk ?

Am-I right ?

A+

---

### Post by avtolle on 2009-01-22
Sorry; I meant the alternate install cd. The command itself is needed to install, but it is not written to any disk permanently. Once you get installed, the system finds the CD-ROM drive (in my experience) without anything further needed.

---

### Post by JujuLand on 2009-01-23
Hum ... I have finished the expert install, and I saw it updates yaboot, so I thought it was ok.

It was not, and at boot, impossible to boot 8.10 on the disk.

So I install again, but I took install instead of expert (it's quicker), and I let the install to finish.

When the setup eject and ask me to reboot, I don't do it, and open a new console.

When I tried to modify the file /etc/initramfs-tools/modules, the system doesn't find it. In fact it was in /target/etc/initramfs-tools which is the disk, and the mount point of the disk ubuntu install

I have modified the file located in it, but I'm not able to launch the command update-initramfs -u. I suppose it's normal

I suppose that the command is made to be able to correct the error and launch 8.10 correctly without booting again, and this after the boot at the end of install.

Am-I right ?
The previous installs  were bad and I don't want to setup again and again.
Will the modules modification be enough to launch 8.10 after a new boot?

A+

---

### Post by avtolle on 2009-01-23
I'm really not clear what you are doing or why you are doing it. After the CD ejects, then reboot.

---

### Post by JujuLand on 2009-01-23
In all previous install, after the reboot, the iMac just gives me an icon (folder + question mark) and impossible to do something, I just can install again.

A+

---

### Post by JujuLand on 2009-01-24
I have boot after install, and same problem.

I can just launch the alternate CD , and be at yaboot prompt.

I was reading a post on the bug 126337 page:

>                  I can confirm this bug on a b/w G3 which was upgraded from Gustsy 7.10 (kernel 2.6.22).
 Interestingly, the 2.6.24 kernel can be booted by specifying "Linux root=/dev/hda3" at the yaboot prompt. The system functions OK but without a CDROM.
 This lead me to consider that it was the secondary IDE controller that isn't being detected. I confirmed this by downloading the 28-Jan-08 build of the Kubuntu 8.04 install CD which gets as far as configuring the keyboard but then fails to detect the CD - even though it's just booted from it :-)

        

I thought it was perhaps possible to force the boot from yaboot to the hd part where the system is installed.

During expert install, I saw something about boot (if I remember) where it was asked to confirm a device, I'm not sure that this device was /dev/hda1, but I'm sure of hda1, and I think it was just before the setup put yaboot in place.

Even if the problem seems not to be exactly, it gives me an idea, and I have tried to boot from cd with the syntax :
linux root=/dev/hda1

but it fails, surely because the image hasn't this name.

I'm not sure also of the device, and of the syntax

I have tried too:

hda1,2 and a lot of combinations, and always the same message type:

hda1:2, /vmlinux : unable to find image or unknown device

Can-you give me the exact name and path of the image installed in your system ?
And also an help about the syntax to use ?

I hope this will be enough to boot with the hd image, and then been able to do the modifications I was not able to apply from within the setup.

A+

---

### Post by JujuLand on 2009-01-26
No idea about this type of problem ?

A+

---

### Post by JujuLand on 2009-02-04
I have now, with the help of a cool guy, found where was my problem.

I have choosen the manual partitionning, as I do on i386 machines, and the apple part wasn't created.

I ought to choose automatic partitionning, and before making the partitionning, choose to return back and modify the parts manually. It creates, like that, this little partition which allows to choose the boot.

I close this thread.

Thank for all the help I have found on the two threads I opened.

Hoping this can help others guys.

A+

---

