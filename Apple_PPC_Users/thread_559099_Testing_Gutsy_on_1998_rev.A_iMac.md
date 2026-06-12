---
title: "Testing Gutsy on 1998 rev.A iMac"
date: 2007-09-24
forum: Apple PPC Users
---

### Post by roazena on 2007-09-24
Gutsy doesn't recognize some IDE drives by default so when experimentally upgrading from Feisty to Gutsy on my ancient 1998 iMac, I was dropped into busybox.

```
modprobe ide_core
exit
```

loaded the rest of the kernel and got me to a graphical boot. The bug is already noted [here]("https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/126146") and I updated the /etc/initramfs-tools/module to add ide_core to the list of modules loaded at boot.

```
sudo update-initramfs -u
```

and reboot. This time your (E)IDE drive will be detected properly and the system will boot.

---

### Post by Calash on 2007-09-27
I saw this same issue on my iBook G3 when I was playing around with the upgrade to Gutsy.  Never had the time to look into it.

I will try this solution tonight.  Thanks for posting the information

---

### Post by Calash on 2007-09-28
Between the link and what you posted it worked perfectly.  Thanks :)

Now I got Xubuntu Gutsy on my iBook Blueberry.  Gnash still does not work though, but I have given up on that anyways.

---

### Post by roazena on 2007-10-17
[Bug filed in Launchpad, Importance changed to high]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/126337")

The solution does work but as one person posted, this is a showstopper.

---

### Post by kwiter on 2007-10-20
Ahh this fixed the trouble on my G4 iMac but still unable to boot the 7.10 disc to install on my Powerbook G3 Wallstreet with 512 meg of RAM. On that it finds the Hard Drive, then goes back to initramfs

I type exit and says 

cp unable to open /root/var/log no such file or directory 

then

runs some mounts

then 

I get the error

Target Filesystem doesn't have /sbin/init

:-(

Thanks

---
[http://www.urbanskinz.com](http://www.urbanskinz.com)

---

### Post by fuoco on 2007-10-24
> **kwiter said:**
> Ahh this fixed the trouble on my G4 iMac but still unable to boot the 7.10 disc to install on my Powerbook G3 Wallstreet with 512 meg of RAM. On that it finds the Hard Drive, then goes back to initramfs

I type exit and says 

cp unable to open /root/var/log no such file or directory 

then

runs some mounts

then 

I get the error

Target Filesystem doesn't have /sbin/init

:-(

Thanks

---
[http://www.urbanskinz.com](http://www.urbanskinz.com)



i have the same problem starting the livecd, what do we do?

---

### Post by pyre on 2007-10-25
Have you verified the checksum/gpg signature on the ISO you downloaded?

If that checks out, try re-burning the disk.  Make sure that you tell your burning software to 'verify disc' or 'check integrity' to make sure there were no errors burning.

I had to reburn my Gutsy Alternate PPC CD because it wouldn't even start the boot process.  (OpenFirmware acted like the CD wasn't there, but the disc could mount and read on another Ubuntu install)

---

### Post by Tommy on 2007-10-25
> **kwiter said:**
> still unable to boot the 7.10 disc to install on my Powerbook G3 Wallstreet with 512 meg of RAM. On that it finds the Hard Drive, then goes back to initramfs

There is at least one other module the Oldworld machine will need -- try also making sure the mesh module is loaded, and if that doesn't work, try scsi_mod 

(this is from memory & from a ssh into my Wallstreet running Dapper -- I haven't tried loading Gutsy on it yet)

P.S.: If you're using the serial port(s) for anything -- IRdA, the internal modem, a serial printer, or your Palm Pilot, you'll also want to load pmac_zilog   -- but that can happen after boot (doesn't need to be in the initramfs). In dapper I have the following in my /etc/modules file :

```

# /etc/modules: kernel modules to load at boot time.
#
# This file should contain the names of kernel modules that are
# to be loaded at boot time, one per line.  Comments begin with
# a "#", and everything on the line after them are ignored.

mesh
bmac
snd-powermac
apm_emu
mousedev
ide-cd
ide-disk
ide-generic
genrtc
pmac_zilog


```(mesh HAS to be in the initramfs if you want to boot so it's redundant here, but it doesn't hurt anything. Genrtc is the "real time clock" which makes ntpdate work but the clock accuracy has been TERRIBLE under Dapper and I have to set the clock several times per day or it goes way off.)

---

### Post by ajt on 2007-11-23
[QUOTE=roazena;3421176]Gutsy doesn't recognize some IDE drives by default so when experimentally upgrading from Feisty to Gutsy on my ancient 1998 iMac, I was dropped into busybox.
[...]

Just used this info to boot 7.10 on my iMac: BTW, the 'old' boot image from Feisty was still working on my iMac, so I edited /etc/initramfs-tools/modules after booting the 'old' kernel.

Thanks :)

---

### Post by roazena on 2007-11-27
Honestly, at this point the main thing preventing me from ditching Ubuntu for the PPC platform is the fact that Fedora switched to DVD install media and these iMacs don't have DVD drives.

---

### Post by mirak63 on 2007-12-14
funny I tried to install fedora once and never managed to log in either from console or gdm, so I dumped it

---

### Post by king_arthur on 2007-12-25
> **fuoco said:**
> i have the same problem starting the livecd, what do we do?

You can add me on a iMac G4 flat-screen.

Exactly same problem and error output.

BTW Ditto CD works fine on the iBook (well, provided the necessary tweaks) so there is nothing wrong with the ISO image I guess.

This Gutsy live CD is a major regression from the previous releases that worked flawlessly.

/P

---

