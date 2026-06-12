---
title: "Ubuntu 8.04 won't boot on Powerbook G4"
date: 2008-05-02
forum: Apple Hardware Users
---

### Post by ombra on 2008-05-02
Hi.
I recently installed the new Ubuntu on my Mac. There were no errors or anything during the installation. But when I try to boot, the following error message appears:

/pci@4000000/ata-6@d/disk@0.4,/boot/vmlinux:Unknown or corrupt filesystem

:confused:What does this mean and how can I get rid of it?

thanks very much in advance!

---

### Post by razinjap on 2008-05-07
was it a clean installation or an upgrade?

---

### Post by ombra on 2008-05-07
It was a clean installation, as upgrading from 7.04 to 7.10 didn't work, and you can't upgrade from 7.04 to 8.04.

I found a kind of solution: i moved my mac partition from the harddrive to the firewire device and installed heron on the harddrive.

If someone has an idea how to boot heron from a fw device please reply.:(

thanks very much in advance!

---

### Post by stream303 on 2008-05-07
Here's how I got my external firewire drive to boot:

[http://ubuntuforums.org/showthread.php?t=314237&highlight=firewire](http://ubuntuforums.org/showthread.php?t=314237&highlight=firewire)

Basically after installation, you need to go back in and find your ofpath to the drive.  Using that, you modify your /etc/yaboot.conf file, and run ybin on it.

The instructions were for Edgy, but it still works on Hardy.  I don't think you need the "ofboot" line that I listed there.

Another option if you feel up to it is to just install Hardy to the internal drive, and put OSX on the external firewire - now you won't have to deal with anything special.

---

### Post by OqiQi on 2008-05-08
I have the same problem when i try to install hardy to my ibook with 1.33G G4 CPU, 1.5G RAM, bcm43xx wireless card and bluetooth card. And it cause a crash. When Hardy is installed and the system is reboot from hard driver, the system shutdown after showing the message "PCI: cannot allocate resource region 0 of device 0001:10:18.0 \n
PCI: cannot allocate resource region 0 of device 0001:10:19.0"
Does anybody can give me some help info?

---

