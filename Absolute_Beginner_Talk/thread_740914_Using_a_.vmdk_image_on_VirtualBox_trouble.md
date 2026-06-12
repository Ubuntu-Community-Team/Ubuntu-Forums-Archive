---
title: "Using a .vmdk image on VirtualBox trouble"
date: 2008-03-31
forum: Absolute Beginner Talk
---

### Post by TMcKSmith on 2008-03-31
I'm trying to get a Windows XP virtual image to run on VirtualBox.  The image was given to me by a co-worker, originally created with VMWware.  I clicked "New", selected "Windows XP", left the default memory size at 192MB, then selected "Existing..." on Boot Hard Disk.  Here are the files in the directory that I can choose from when I try to 'add'a Virtual Disk image in the "Virtual Disk Manager":
Windows_XP_Professional-s001.vmdk
Windows_XP_Professional-s002.vmdk
Windows_XP_Professional-s003.vmdk
Windows_XP_Professional-s004.vmdk
Windows_XP_Professional-s005.vmdk
Windows_XP_Professional.vmdk
I selected the "Windows_XP_Professional.vmdk" file, tried to fire up the Virtual Machine and it ends up just sitting at a blank screen.  So I deleted the image and started from scratch, tried to start it again and it brings me to the "We apologize for the inconvenience, but Windows did not start successfully" screen.  I chose "Start Windows Normally" and it just freezes.  Any idea what's going on here?  Thanks

---

### Post by abhiroopb on 2008-03-31
Firstly to the best of my knowledge a vmdk file is used for VMware NOT virtualbox ([http://www.extremetech.com/article2/0,1697,1156367,00.asp](http://www.extremetech.com/article2/0,1697,1156367,00.asp)), and it won't work with the latter. It needs to be converted first, follow the guide here (scroll to where it talks about converting: [https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

When you say you "deleted the image and started from scratch" what does this mean? Did you follow the entire virtualbox process and install Windows XP with an install CD?

Also I recommend setting the default memory to about 256mb, it runs a lot better (do this only if you're PC has at least 1gb RAM)

---

### Post by TMcKSmith on 2008-03-31
> **abhiroopb said:**
> 
When you say you "deleted the image and started from scratch" what does this mean? Did you follow the entire virtualbox process and install Windows XP with an install CD?


No I just meant I deleted the VirtualMachine I had created in VirtualBox and went through the setup process again, using the same image.

---

### Post by abhiroopb on 2008-03-31
OK, well use this guide (which contains practically everything, including combining multiple vmdk files): [https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool](https://wiki.ubuntu.com/UbuntuMagazine/HowTo/Switching_From_VMWare_To_VirtualBox:_.vmdk_To_.vdi_Using_Qemu_+_VdiTool)

and it should work fine.

Good Luck!

---

### Post by TMcKSmith on 2008-03-31
This command is giving me trouble:

 sudo LD_LIBRARY_PATH=/opt/VirtualBox* ./vditool DD Windows_XP_Professional.vdi Windows_XP_Professional.bin
[B]
sudo: LD_LIBRARY_PATH=/opt/VirtualBox*: command not found[/B]

Searched around google and found an alternative method, BUT:

sudo vboxmanage convertdd Windows_XP_Professional.bin Windows_XP_Professional.vdi
[B]
VirtualBox Command Line Management Interface Version 1.5.0_OSE
(C) 2005-2007 innotek GmbH
All rights reserved.

Converting VDI: from DD image file="Windows_XP_Professional.bin" to file="Windows_XP_Professional.vdi"...
Creating fixed image with size 512Bytes (1MB)...
Failed to create output file (VERR_INVALID_PARAMETER)!
[/B]


blah

---

### Post by abhiroopb on 2008-03-31
did you naviagte to the directory that vditool was downloaded to? The .bin file should also be in this directory.

---

### Post by TMcKSmith on 2008-03-31
Yes, I did...

---

### Post by Pridkett on 2008-04-28
The issue is that VirtualBox only understands how to handle monolithic disk images where everything is in a single file.  However, most installations of VMWare split virtual disks into multiple 2GB files.  For example, on my system I have a virtual disk called "WindowsXPProfessional.vmdk" which is an 8GB virtual disk.  Looking at the file, we see it is quite small and is actually comprised of many smaller disks -- WindowsXPProfessional-s001.vmdk through WindowsXPProfessional-s007.vmdk.  These files are the actual data.

Before using the disk, you'll need to combine these using the vmware-vdiskmanager command, which comes with vmware-server but not with player.  In my case it was as simple as:

```
vmware-vdiskmanager -r WindowsXPProfessional.vmdk -t 2 single.vmdk
```

The -t 2 flag tells the program to create a single preallocated disk image.  If you'd like the image to grow, use the -t 0 option instead.

---

