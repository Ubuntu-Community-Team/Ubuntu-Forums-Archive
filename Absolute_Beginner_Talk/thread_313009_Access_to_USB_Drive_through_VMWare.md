---
title: "Access to USB Drive through VMWare"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by dkenny on 2006-12-05
I have VMWare server running and have created a Ubuntu Virtual Machine.

How do I allow this VM to see my USB drive?

Whne I connect the drive I can see it in my 'real' Ubuntu install, but it does not appear in the VM

---

### Post by |Syrius| on 2006-12-05
I guess you have to unmount it on Ubuntu and on starting up the Virtual Machine go to VM->Removable Devices->(Your USB Drive should be here)

hope that helped

---

### Post by Robor on 2007-02-14
I've got Ubuntu Edgy with VMWare Server 1.01.  I created a WinXP Pro virtual machine and when I plug my USB drive in it auto-mounts in Ubuntu but is not visible in VMWare.  I tried unmounting (Eject?) it and restarting the virtual machine and it's still not visible.  

I have another system with Ubuntu Edgy and VMWare Server 1.00 and a WinXP Pro virtual machine.  On that setup getting access to my USB thumbdrive is hit and miss - usually an unmount and replug will get it to appear in VMWare.  (Edit:  Note that in that setup I don't have to manually unmount it in Ubuntu - it auto unmounts when I import it into VMWare)

Any other suggestions on this?  :confused:

---

### Post by Robor on 2007-02-14
Problem solved here:

> **GorBo said:**
> Has anyone managed to get USB working on VMware (guest OS WinXP) after the upgrade to Ubuntu 6.10? Previous solution (worked under 6.06) was to:

add **usb.generic.skipSetConfig = "TRUE"** to .vmx file of the virtual machine.

Thanks GorBo!

---

### Post by ClarkM on 2008-05-06
OK, I tried both of these suggestions and my VM->Removable container still says "Empty". I'm on 8.04 Hardy Heron, using VMware server console v1.0.5-build 80187. My guest system is Windows XP/Pro, and I've tried having the VM in focus when I turn on the external drive and I've tried having the drive already powered up when I power on the VM. Same result; empty container. The USB controller correctly shows that I have 2 USB ports, but XP just doesn't seem to want to "see" my drive. Any hints?

---

### Post by dafallus on 2008-06-06
I'm having the same issue. I am also on Hardy 8.04 running vmware server 1.0.5 build-80187. No matter what I try, when I go to the VM-->Removable-->USB Devices the list remains empty.

I did however manage to find this link:
[http://ubuntuforums.org/showthread.php?t=779934](http://ubuntuforums.org/showthread.php?t=779934)

The relevant information would be:
sudo gedit /etc/fstab

Then, add this line:
# USB for vmware/vbox
none /proc/bus/usb usbfs devgid=46,devmode=664 0 0

I have not tried this yet. I just edited the file and am about to reboot. I'll try and let you know how it goes.

---

### Post by dafallus on 2008-06-06
I can confirm that the information above worked for me.

---

