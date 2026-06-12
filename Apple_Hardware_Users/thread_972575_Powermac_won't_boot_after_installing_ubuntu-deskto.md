---
title: "Powermac won't boot after installing ubuntu-desktop"
date: 2008-11-05
forum: Apple Hardware Users
---

### Post by heluani on 2008-11-05
Hi there, I installed 8.10 server powerpc CD and everything was fine, I got wireless working and apt-get was working fine with no graphical interface. I did ```
sudo apt-get install ubuntu-desktop
``` and after a few hangs and retries, it finished installing the gnome applications, but when tried rebooting in the new systems it just hangs after "loading please wait"... I can't even boot in console mode as before. Any thoughts are welcomed, I'm running on a powermac dual G5

R.

---

### Post by meg23 on 2008-11-05
You might try putting in a livecd and check out the partitions with gparted. I have had a lot of problems in the past with bootstrap loaders for ppc. The install of ubuntu-desktop might have hosed your bootstrap loader. When you get to the actual loader press escape and see if you can get it to run in recovery mode. If it runs in recovery mode it be a problem with x, assuming it was properly installed. Post any results you have.

---

### Post by pxwpxw on 2008-11-05
Are you getting the yaboot welcome and boot:?
If so, just boot: Linux single.

---

### Post by heluani on 2008-11-05
Thanks for the quick answers, I'm back at home so I won't be able to try until tomorrow. I'll get back to you tomorrow early. But just in case, I'll burn now a Live Hardy CD and try installing that tomorrow if I can't fix quickly the 8.10 I already have.

---

### Post by pxwpxw on 2008-11-05
The intrepid 810 powerpc64 version has a revised yaboot ofpath, which fixes problems that were in in hardy804 and earlier, with G5 dual sata and external drives - that should not be the issue, and hardy is not a good idea.

If you restarted into command line with just the server install, that says the bootloader install was ok before the desktop install.

The desktop install would not normally have anything to do with yaboot - but anything is possible. 
I have just installed the same way (server first then + xubuntu-desktop), all ok and running(*). (G5 single cpu dual drives)

*edit  I am having some problems here with desktops, but not affecting booting.

---

### Post by heluani on 2008-11-07
Well, yesterday I decided to start the installation again, I did the same as the first time, server then apt-get ubuntu-desktop, and to my surprise everything worked absolutely fine. I left the computer running all night, and today I decided to shut it down (I'm leaving for a trip tomorrow).  Just as the first time, it fails to shut-down, the screen goes black and the fan control is lost I guess cause they start spinning full-blast. I turned it off completely holding the power-button, now it doesn't boot any more. I get to the Yaboot welcome and boot prompt, and there with both Linux and Linux single, the screen flashes, the a message "loading please wait", then black and hang, fans full blast and that's it. Well, I'll have to try something in a couple of weeks when I come back. In the meantime any thoughts will be appreciated. 

R.

---

### Post by palmdalian on 2008-11-13
I had the same exact problem.  I don't know too much about Linux, but I'm pretty sure it has to do with initrd.  The last line when installing ubuntu-desktop is "Generating initramfs" or something similar.

The way I fixed it was replaced my /boot folder with the original files from the fresh server install.  Hopefully someone here with more knowledge can figure out what is going on.

I am happy to try/test anything that is suggested.

---

### Post by IQRules on 2008-11-13
> **palmdalian said:**
> 
The way I fixed it was replaced my /boot folder with the original files from the fresh server install.  Hopefully someone here with more knowledge can figure out what is going on.

I am happy to try/test anything that is suggested.

Can you explain your fresh server install? Is it another working box?:)

---

### Post by palmdalian on 2008-11-13
I meant that I copied over the /boot folder to an external thumb drive before I installed ubuntu-desktop.  It is the same exact machine, with the same exact install (without the gui).

The computer reboots fine before installing ubuntu-desktop, but fails to boot immediately after.

Hope that helps.

---

### Post by heluani on 2008-11-25
Ok, this sucks, I'm still in the same situation. I can boot with the install CD and chroot into my Intrepid installation, all the files are well there. Is there any way of replacing the initrd files with the correct ones without reinstalling everything? (This assumes that palmdalian is right in his solution). I tried ```
update-initramfs -u
``` and exited fine, but no luck, also I checked with ```
ybin -v 
``` that the yaboot installation was fine, but still can't boot even in single mode. The worst part is that the yaboot.conf file has an entry to an initrd.old file that I guess was a backup of the fresh server install, but that file is not around in /boot/ so I can't boot that image!.

R.

EDIT Holy! I tried a ```
 update-initramfs -c -k 2.6.25-2-powerpc64-smp
``` and at least now I can boot with "video=ofonly" I can't use Nautilus (due to an unexpected error) and stuff but this is something!

---

### Post by stream303 on 2008-11-25
You might find the following useful when doing using the DIY approach of building it up step by step like that from the server install:

[https://help.ubuntu.com/community/Installation/LowMemorySystems](https://help.ubuntu.com/community/Installation/LowMemorySystems)

It is targeted at low-memory systems, and also seems to be for Intel only, but the instructions work just fine for those with PPC and large-memory who just want to do it that way as well.

The use of a bootable usb stick may be part of the problem if it isn't really stable yet with Intrepid on PPC.

Also, even though you may get it to work, you will still be using a kernel tuned for server needs.  Not that this makes it unusable, but it is a little bit different than the kernel designed for the desktop.

If your objective is to have a full-blown Ubuntu desktop instead, it may just be easier to download and install from the "alternate" text-based installer.  Same great taste during install as the server / DIY approach, albeit with a kernel tuned for the desktop. :)

Are you trying to install *from* a usb stick, or put an installation on it?  I know these can be a bit tricky for ppc, even if your model supports that.  (many don't, but it appears yours does perhaps)

---

