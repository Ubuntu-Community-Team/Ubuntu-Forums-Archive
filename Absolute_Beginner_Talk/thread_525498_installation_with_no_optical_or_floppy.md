---
title: "installation with no optical or floppy"
date: 2007-08-14
forum: Absolute Beginner Talk
---

### Post by cwm33 on 2007-08-14
If I'm trying to install Ubuntu to a system with no Optical/Floppy drive...would I be able to copy the contents of the CD to the hard drive, reboot, and have it recognize properly? or is there a better way without using a floppy/optical?

---

### Post by divague on 2007-08-14
if you have windows installed you could try wubi
[http://wubi-installer.org/](http://wubi-installer.org/)

---

### Post by Alterax on 2007-08-14
Will be difficult without Wubi.  Best bet if you don't have that option is to yank the harddrive, install it as the only hard drive on a machine with an optical drive t(if you are using a laptop, there's an adapter you can get to attach a 2.5 ide laptop drive to a 3.5 ide cable).  Install Ubuntu using that, and configure the X11 server to use the standard VESA driver.  Then shut it down and put it back into the machine you are wanting to install it.  Should work fine after that, though you may have to poke around to get the correct video driver for your driveless computer. (Hence changing the driver to VESA, which is a fallback)

---

### Post by cwm33 on 2007-08-14
The laptop itself does not have anything installed for an operating system (hence the problem) but I do have my main tower that I can do all these lovely operations from.  I even have an enclosure that allows me to yank out the hard drive and run it as an external hard drive.

Would it work to boot into a virtual environment (such as virtual box), and install it to the hard drive through the USB connection? or would I have to do some form of drive ghosting for it to work?

Also how does one configure the X11 server to use the VESA driver?

Thanks for the help!

---

### Post by logos34 on 2007-08-14
do you have windows on this thing and broadband internet connection?  if so use Wubi or this guide:
[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29)

edit: ok so no OS...

---

### Post by cwm33 on 2007-08-14
> **logos34 said:**
> do you have windows on this thing and broadband internet connection?  if so use Wubi or this guide:
[https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29](https://help.ubuntu.com/community/Installation/FromWindows?highlight=%28installation%2Ffromwindows%29)

edit: ok so no OS...

nope no OS, but I can take the hard drive out of the laptop, and hook it up to my main computer as an external hard drive, if that helps. :)

I should also mention that my main tower is an Athlon 64, while the laptop is a Pentium 4.  I've got a dual boot of Ubuntu 7.04/Win XP running on my main tower.

---

### Post by logos34 on 2007-08-14
looks like you'll have to install it using another machine then transfer the drive back.  

After install run 
sudo dpkg-reconfigure xserver-xorg

change to 'vesa' driver

run through the interactive, accepting defaults on most but you may want to substitute your laptop monitor settings

---

### Post by logos34 on 2007-08-14
> **cwm33 said:**
> nope no OS, but I can take the hard drive out of the laptop, and hook it up to my main computer as an external hard drive, if that helps. :)

**I should also mention that my main tower is an Athlon 64, while the laptop is a Pentium 4.  I've got a dual boot of Ubuntu 7.04/Win XP running on my main tower**.

good luck, not sure how that's gonna work (amd to intel platform)

**EDIT:** oh, and when you install to it in a usb enclosure, your /boot/grub/menu.lst will probably end up pointing to the kernels on '(hd1,0)' -- i.e the first partition on the second drive' (the main internal hard disk is (hd0)) -- you will have to change that to (hd0,0) since it will be the only drive when you put it back in the lappy.  change /boot/grub/device.map too to show only (hd0) /dev/hda.  reinstall grub to the mbr when you're done so it will look for menu.lst on hd0 instead of hd1.

---

### Post by cwm33 on 2007-08-14
> **logos34 said:**
> good luck, not sure how that's gonna work (amd to intel platform)

Should I do it through a virtual machine environment? Think that might work better?

I should also note that I didn't go for anything other than a standard Ubuntu install for my main tower, I used the ubuntu-7.04-desktop-i386.iso file.  I wanted my first run with the system to be as problem free as possible, so I followed what the majority of users would go with, as I don't really need my ubuntu install to be a racehorse, just a stable system. :)

---

### Post by logos34 on 2007-08-14
> **cwm33 said:**
> Should I do it through a virtual machine environment? Think that might work better?

I should also note that I didn't go for anything other than a standard Ubuntu install for my main tower, I used the ubuntu-7.04-desktop-i386.iso file.  I wanted my first run with the system to be as problem free as possible, so I followed what the majority of users would go with, as I don't really need my ubuntu install to be a racehorse, just a stable system. :)

Can't help you on the VMWare part, but as for the second question, it's basically a hardware configuration issue--you'll be installing/setting up on a completely different platform, then transferring the hard disk back to the laptop as the internal drive.  Even if you get the video part right, the rest of the OS (network,  sound, chipset, storage controllers, etc) wlll be setup to run certain drivers with certain hardware.  It may work in the end--the proper modules will be loaded.  But you may have problems.  OTH you don't have any other choice so give it a shot

---

### Post by cwm33 on 2007-08-14
How good is ubuntu with detecting the installation of new hardware?  Would it be able to successfully discover that there's a brand new EVERYTHING and reconfigure properly? or would it more or less just pop up with a bunch of cryptic errors?

Also, what's the best way to reinstall Grub to the MBR like you suggested? or if I install directly to that external drive, would I only have to modify the paths?

---

### Post by jordanmthomas on 2007-08-14
cwm33, does your computer have PXE (network boot)?  If so, that's always an option.  I'm pretty sure you can run the tftp server needed from Windows or a *nix so your other computer should be able to host it for you.

[https://help.ubuntu.com/community/Installation/WindowsServerNetboot](https://help.ubuntu.com/community/Installation/WindowsServerNetboot)  <-- a little old, but should still help
[https://help.ubuntu.com/community/Installation/LocalNet](https://help.ubuntu.com/community/Installation/LocalNet) <-- up to date

> Also, what's the best way to reinstall Grub to the MBR like you suggested?
I would attach it to another computer (with Linux installed or at least a LiveCD running) and install GRUB to the disk there.  
```
grub
root (hdx,y)
setup (hdx,y)
quit

```
Then, you would just need to edit the paths later.

---

### Post by cwm33 on 2007-08-14
The last time I snooped at the network boot option (that the laptop DOES have), it didn't seem to have any options for asking where it should look to find an image to boot off of.  I'm hoping that the up to date article you linked does provide a solution to that, or at least a reason why, but trying to read that while working is more or less making me go all crosseyed.  If you could dumb it down a wee bit at least enough for me to have an 'OHHH COOL!' type moment, and clarify it enough for me to figure it out I would much appreciate it. :)

---

### Post by jordanmthomas on 2007-08-14
I've actually never set up a net boot, so I can't really help you have one of those moments.   I pretty much know they exist and that's the extent of my expertise on the subject.  :)  

Maybe someone else can give you a quick 'n dirty rundown?

I was just tossing the idea out there.

---

### Post by cwm33 on 2007-08-14
Managed to get the operating system installed.  I actually wound up jury-rigging up an optical drive into a workable condition so that I could do things the old fashioned way.  Was more in a hardware mood I guess. :guitar:

Thanks for the help though folks. :)

---

