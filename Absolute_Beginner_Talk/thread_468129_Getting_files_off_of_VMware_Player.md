---
title: "Getting files off of VMware Player"
date: 2007-06-08
forum: Absolute Beginner Talk
---

### Post by kyrhash on 2007-06-08
I am using VMware Player to virtualize Ubuntu Edgy and i decided to use Ubuntu on my new desktop PC.  I have two PDF files that i downloaded and want to get them onto my XP system.  Has anyone had experience doing this.

---

### Post by hyper_ch on 2007-06-08
There are various ways...

if you have a usb stick, have it assigned to vmware... ubuntu should auto-recognize and auto-mount it... then you can put the pdfs on there...

Depending on there size you could also email them to you...

Or you could setup a shared fat32 partition and put them on there

Or you could share a folder from ubuntu and access it from windows

Or you could save them to a disk or cd(rw) or dvd(rw) or or or ;)

---

### Post by starcraft.man on 2007-06-08
> **kyrhash said:**
> I am using VMware Player to virtualize Ubuntu Edgy and i decided to use Ubuntu on my new desktop PC.  I have two PDF files that i downloaded and want to get them onto my XP system.  Has anyone had experience doing this.

Easy way to get it is to switch to [Virtual Box]("http://www.virtualbox.org/"). They offer shared folders and a whole host of great customization features for free.

They also now directly support reading the VMware vmdk format. Great product. That should do it :).

I second the email idea if your planning on sticking with them, Gmail has 20 MB limit now no? Use an archiver if its larger and split em.

---

### Post by kyrhash on 2007-06-08
I cant figure any of that out, i tried to burn the files to a cd but Xp refused to recognize them.  All email programs i use refuse to attach the files but anyway how would i assign a USB flash Drive to Vmware so i could access in Ubuntu.  I am completely new to this, so go step by step please.

---

### Post by hyper_ch on 2007-06-08
well, USB needs to be enabled in your machine configuration...then once it's booted there's a menu atop where you can add specific usb devices to the virtual machine (at least in the server version....)

---

### Post by kyrhash on 2007-06-08
The Version i have doesnt allow me to use do basically anything, i don't think i have the option to add a usb device.  Virtual box refuses to boot my Ubuntu it never even gets to the welcome screen.

---

### Post by Wicca on 2007-06-08
You can easily add a USB-device to VMWare, even in Player.
Just at the top of your VMPlayer screen you see this buttons 'CD-ROM 'Ethernet' etc? Just put in a USB stick and you'll see that a button is added with the name of the USB device. Just click on it to make it available inside your VM.
If you don't see this button try restarting VMPlayer with the USB-stick attached to your PC.
If you don't see any buttons at all you'll have a menu, in that case look under 'devices'.

---

### Post by kyrhash on 2007-06-08
No matter What i do I cant get it to show the USB drive up top and the linux system refuses to recognize my CD drive, so the USB should appear somewhere around the Ethernet adapter?

---

### Post by Wicca on 2007-06-08
> **kyrhash said:**
> No matter What i do I cant get it to show the USB drive up top and the linux system refuses to recognize my CD drive, so the USB should appear somewhere around the Ethernet adapter?
This USB thingy can only show up in VMWare if it's recognized by Ubuntu. Same goes for the CD-drive: if Ubuntu doesn't see it, it can't get passed through to VMware. Are you sure the USB-drive is working properly?

But, to go back to your original question, you can also mail yourself :idea:

---

### Post by kyrhash on 2007-06-08
USB Drive Works fine on my XP Box, how would i get it to work in Ubuntu (that or the CD Drive), and email doesnt seem to want to work the files simply refuse to attach themselves.  this crap is drivin my nuts

---

### Post by Acglaphotis on 2007-06-08
With qemu i just start my ftp server and exchange files with firefox + fireftp. Just get pure-ftpd, start it and you are good to go... dont worry, pure-ftpd is in the repository...

---

### Post by Mazehero55 on 2007-10-12
At first using my usb drive worked great,but now whenever I try to use my usb drive it makes the noise but doesn't come up and it says "Unsafe drive removal error". But when I un-enable it it works fine in ubuntu. 

thanks

---

### Post by Shazaam on 2007-10-12
kyrhash...
Go to the folder that has the VMware vmx file. Open (right click) the vmx file in a text editor, and post a copy of it here. If your wondering what file I need to look at it's the .vmx file you click to start the virtual machine.

---

### Post by Mazehero55 on 2007-10-13
here you go:

```
#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
memsize = "452"
ide0:0.present = "TRUE"
ide0:0.fileName = "OS.vmdk"


ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"

floppy0.fileName = "/dev/fd0"
ethernet0.present = "TRUE"
ethernet0.connectionType = "nat"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "Test OS"
guestOS = "other24xlinux"
nvram = "testos.nvram"
scsi0:0.redo = ""
ethernet0.addressType = "generated"
uuid.location = "56 4d 41 87 12 c7 a4 1b-00 3a 02 39 ec 22 fd e6"
uuid.bios = "56 4d f3 a5 03 8c cb b9-ed bb 8f 10 a3 de b0 10"
ide1:0.autodetect = "TRUE"
ethernet0.generatedAddress = "00:0c:29:de:b0:10"
ethernet0.generatedAddressOffset = "0"
checkpoint.vmState = "OS.vmss"
tools.remindInstall = "TRUE"
ide0:0.redo = ""

extendedConfigFile = "OS.vmxf"
virtualHW.productCompatibility = "hosted"
tools.upgrade.policy = "manual"

isolation.tools.hgfs.disable = "FALSE"

usb.autoConnect.device0 = ""
```

---

