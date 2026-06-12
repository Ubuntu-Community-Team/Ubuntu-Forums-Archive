---
title: "VMWare player fault"
date: 2006-02-02
forum: Absolute Beginner Talk
---

### Post by bartbes on 2006-02-02
I have installed VMWare Player, but when I want to run configure, It says that /etc/vmware/locations is missing. Does anyone knows how to fix it?

---

### Post by skopas on 2006-02-02
LOL,,,its funny i just came from your situation.  A couple of days ago i was trying to install Ubuntu on VMware and had so much probs:confused: 
I kept getting errors on certain files not showing up.  So i installed Parallel workstation which is like Vmware.  And i had no problem installing.

They have a trial basis ed of parallel.  Try it..it cant hurt.

---

### Post by bartbes on 2006-02-04
I can't even start it, and where can I find Parellel?

---

### Post by bartbes on 2006-02-05
I really need this, my windows XP is too slow to really do something with VMWare Player.

---

### Post by bartbes on 2006-02-05
just tried to put an empty file in /etc/vmware named locations, it then says that LIBDIR is not declared

---

### Post by skopas on 2006-02-06
Try this...

[http://www.parallels.com/]("http://www.parallels.com/");) ;)

---

### Post by GreyFox503 on 2006-02-06
I've never installed VMware *Player*, but I have done Workstation.  Just for that I had to download and apply a patch and I had to have my kernel sources installed.  Every time I changed the kernel, I had recompile the VMWare module (which really wasn't too often).

If you post the exact message(s) from the terminal, maybe someone will have a better idea.

---

### Post by bartbes on 2006-02-07
where can I download that patch? (I'm going to search teh VMWare site now) I posted the whole error message at first it was only that /etc/vmware/locations was not found now it says (I have made the file, it's still empty) that LIBDIR is not declared in /etc/vmware/locations

---

### Post by kenweill on 2006-02-07
I have installed VMware Player succesfully without any troubles.
Just follow the procedure at:
[https://wiki.ubuntu.com/VMwarePlayerAndQemu?highlight=%28VMware%29](https://wiki.ubuntu.com/VMwarePlayerAndQemu?highlight=%28VMware%29)

Everything works just fine.
Im using Windows XP inside Ubuntu to connect to the internet. I have a modem that depends on accelerator/driver which is Windows based only.

VMware Player works for me.

Edit:
The procedures on the link have been updated. It was different during the time I installed VMware Player in my machine. I even have a different vmx configuration file with the one posted in the link.

---

### Post by bartbes on 2006-02-07
I have sortof a problem here.. I can't install it because I have already instaleled it with rpm and now it says already installed, while I removed it..

---

### Post by bartbes on 2006-02-07
It's installed and working!!!!!!! I used checkinstall and now it's working \\:D/
I think I also now why the other installation was incorrect.. it was someway installed in /usr/bin/usr/bin/ and I think the locations file was in /usr/bin/etc/vmware/locations or something

---

### Post by GreyFox503 on 2006-02-07
That's cool that they have a guide for installing the player.  I didn't know that you could create VMware-compatible images with QEMU!!  That is freakin' sweet, because the main disadvantage of using the free Player is that it doesn't create new machines.

I have used QEMU, and while a good piece of software, the wiki is right:  It was about 1/3 the speed of VMware during emulation.

---

### Post by bartbes on 2006-02-08
You can as well create your own files I have an empty disk and an .vmx file ( you can edit it to your wishes and remember the current names are dutch)

---

### Post by kenweill on 2006-02-08
Heres my .vmx file. Im using 2 virtual Network Adapter

#!/usr/bin/vmware
config.version = "8"
virtualHW.version = "3"
ide0:0.present = "TRUE"
ide0:0.filename = "Starband360.vmdk"
memsize = "324"
MemAllowAutoScaleDown = "FALSE"
ide1:0.present = "TRUE"
ide1:0.fileName = "auto detect"
ide1:0.deviceType = "cdrom-raw"
ide1:0.autodetect = "TRUE"
floppy0.present = "FALSE"
ethernet0.present = "TRUE"
ethernet1.present = "TRUE"
usb.present = "TRUE"
sound.present = "TRUE"
sound.virtualDev = "es1371"
displayName = "StarBand 360"
guestOS = "winxppro"
nvram = "Starband360.nvram"
MemTrimRate = "-1"

ide0:0.redo = ""
ethernet0.addressType = "generated"
ethernet1.addressType = "generated"
uuid.location = "56 4d a3 9c a6 17 38 ff-00 58 ff 30 26 15 ff 78"
uuid.bios = "56 4d a3 9c a6 17 38 ff-00 58 ff 30 26 15 ff 78"
ethernet0.generatedAddress = "00:0c:29:15:ff:78"
ethernet0.generatedAddressOffset = "0"
ethernet1.generatedAddress = "00:0c:29:15:ff:82"
ethernet1.generatedAddressOffset = "10"

tools.syncTime = "TRUE"
ide1:0.startConnected = "TRUE"

uuid.action = "create"

checkpoint.vmState = ""

tools.remindInstall = "TRUE"
usb.autoConnect.device0 = ""
usb.autoConnect.device1 = ""

ethernet1.connectionType = "bridged"
ethernet0.connectionType = "bridged"

---

