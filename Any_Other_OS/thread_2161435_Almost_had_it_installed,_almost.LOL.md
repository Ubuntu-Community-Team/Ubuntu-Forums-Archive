---
title: "Almost had it installed, almost.LOL"
date: 2013-07-10
forum: Any Other OS
---

### Post by TNFrank on 2013-07-10
I've been trying to install an op system(Back Box Linux) onto my external hard drive since I took it off of my computer and went back to Ubuntu 12.04LTS.  There were just too many Tools that I had no idea how to use yet but hopefully with some schooling I'll be able to use them in a future job but I digress.
  Anyway, I set up my BIOS so that it'll ask me what to boot to on start up, that solves the slow hard drive spin up problem with auto detect when it's plugged into USB.  So, I figure I'll use one of the DVD's I burned to keep things simple, that way there's only one thing in the USB port, my external hard drive.   Anyway, I choose "Something Else" and set things to "sdg" and set the boot record to "sdg" and do the install but when I tried to run it I ran into a problem.  So, I figure I'll reinstall it and all is going well then I get an "Installer failure" message after just about everything is installed. I wonder if I have a corrupt copy of the .iso?  I guess I need to check the md5 key or whatever that was to make sure my copy of the .iso is right.  Just hadn't got around to it yet. Funny thing was that I could install the DVD and boot to it and everything would run fine from the Live DVD, it's just when I tried to install it to the external hard drive where I ran into problems.  I formatted it Ext4 Journaling, and set the root "/" deal so I know I did that right.  Just not sure what the problem is.

---

### Post by oldos2er on 2013-07-10
Moved to Other OS/Distro Support.

---

### Post by TNFrank on 2013-07-11
Not really sure why this was moved over here since it is an Installation problem regardless of which Distro it is. That's why I posted it under the " [Installation & Upgrades]("http://ubuntuforums.org/forumdisplay.php?f=333")" section but if you think my question as to what went wrong during install can be answered over here then that's fine I guess.:confused:
  Also, just to throw this out there for future ref., Back Box Linux is Ubuntu 12.04LTS based or more precisely Xubuntu since it has an  Xfce Desktop environment.

---

### Post by BreezyBrooke on 2013-07-11
You were put here because only Offical Ubuntu Derivitives are allowed in the "Ubuntu General Support" area. Even Mint and Bohdi Linux are put here.

---

### Post by oldfred on 2013-07-11
We have no idea what changes other distributions have made, even if based on Ubuntu or Debian.

Have you tried running Boot-Repair? Is system UEFI? Not many have secure boot issues resolved yet.

       Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)
Full Ubuntu 13.04 liveDVD or USB Install with Boot-Repair included (for newer computers) 
[https://help.ubuntu.com/community/LinuxSecureRemix](https://help.ubuntu.com/community/LinuxSecureRemix)

---

### Post by TNFrank on 2013-07-11
I seriously don't think it's UEFI since it's an old HP NC8230 from around 2005 with a single core Pentium "M", 1.86GHz processor.  I couldn't even finish install so Boot Repair doesn't even enter into it at that point. I need to see about checking the md5 checksum of the download to see if it's all there(but it does run fine in "Live" mode, go figure) or maybe just re-download the Distro or maybe another Distro and install it to see if it'll work.  I'm sure I'll get it figured out eventually. ;)

---

### Post by oldfred on 2013-07-11
If it is a Pentium M, you may be into the issues of PAE. Since cpu not supporting PAE are now so old and cannot run Unity/Ubuntu, Ubuntu does not have a kernel that works with those systems. You probably need 12.04 Lubuntu or may Xubuntu for non-PAE support.

 [http://ubuntuforums.org/showthread.php?t=1951653](http://ubuntuforums.org/showthread.php?t=1951653)
Ubuntu, Kubuntu, and probably Edubuntu will ship with the PAE kernel in 12.04, but both Lubuntu and Xubuntu will ship with non-pae



 [http://en.wikipedia.org/wiki/Physical_Address_Extension](http://en.wikipedia.org/wiki/Physical_Address_Extension)
PAE is provided by Intel Pentium Pro and above CPUs, including all later Pentium-series processors (except most 400 MHz-bus versions of the Pentium M)
[non-pae] Anybody with an old ThinkPad who wants to do a small experiment? 
[http://ubuntuforums.org/showthread.php?t=2113826](http://ubuntuforums.org/showthread.php?t=2113826)

---

### Post by TNFrank on 2013-07-11
It's a later Pentium "M" with the 533MHz bus so the PAE flag is enabled. I've double checked it three times and there's no problem with PAE. All of the 700 series Pentium "M"'s have the PAE flag enabled, mine is a 750, 1.86GHz chip so I'm fine as far as PAE goes. That's NOT the problem.  If there was a problem then I'd not be on the Interweb right now running Firefox under Ubuntu 12.04.2LTS. 
I personally think it's an md5sum problem but since that's pretty much "magic" to check it(trust me, I've looked up what's involved and I'm no where near skilled enough yet) then I guess I'll just download it again and give it a try again.

---

### Post by benerivo on 2013-07-11
> **TNFrank said:**
> ...I personally think it's an md5sum problem but since that's pretty much "magic" to check it(trust me, I've looked up what's involved and I'm no where near skilled enough yet) then I guess I'll just download it again and give it a try again.

The md5sum check is only a command like...```
md5sum /mnt/Storage/Downloads/debian-7.1.0-amd64-netinst.iso
```

---

### Post by TNFrank on 2013-07-11
That's not what I saw. There was a GUI I could download that'd find the md5sum of the .iso that I had downloaded then I'd have to hunt down the actual md5sum from a list then cut and past it into the GUI and do a "compare" and if all was well it'd tell me that the download was ok.

---

### Post by benerivo on 2013-07-12
> **TNFrank said:**
> ...I'd have to hunt down the actual md5sum from a list then cut and past it into the GUI and do a "compare" and if all was well it'd tell me that the download was ok...

The md5sums are within [here]("http://cdimage.ubuntu.com/releases/"). Then just use a terminal window run the md5sum check.

---

