---
title: "Running OS X inside Ubuntu"
date: 2008-09-19
forum: Apple Hardware Users
---

### Post by afrowildo on 2008-09-19
Hey. I've been lurking on these forums for a while now, slowing getting the hang of ubuntu, and linux/unix in general. But the time has come where, having failed to find a solution on the forum, I must now seek the wisdom of the aged ubuntu masters.

I have a mactel running both Ubuntu and Leopard, and what I want to do is boot one up from within the other, the order isn't an issue. Now I know there are several tools out there that can do this, and I even own a Parallels desktop licence.

My problem is that I want to boot up a preinstalled OS, rather than install it into a virtual machine. I've tried with Parallels, but that doesn't seem to be ablt to do it. Does anyone know if there's a program out there that can do this, for either linux of the mac?

Thanks in advance.

---

### Post by dsmoot on 2008-09-19
I don't think that VMWare or parallels will let you do as you describe because technically that is not allowed by the OSX license (they let you do it with OSX server, but not desktop).

I have not done what you describe but I will eventually try it too.  I think you might want to look at virtualbox from Sun.



David

edit:
This is in theory possible according to the virtualbox documents.  I tried to boot my linux partition from inside OSX and failed but the really geeky options seemed to be supported from a linux host.  I will try this today or this weekend and let you know how it goes.  The hard part is going to be the bootloader if it fails.

---

### Post by cyberdork33 on 2008-09-19
vmware fusion can do this, but it is basically undocumented. parallels may also be able to. There is sparse information out there, but I think you have to edit the VM config by hand.

VirtualBox under OSX is kind of crippled (a lot further behind in development) so if it supports this, then it may not work on the OSX side anyway.

Also, about the licensing issue... No, Apple does not allow for OSX to be run in a VM (except the server version) and because of that, even if it was possible, it cannot be discussed here in these forums. Just FYI.

---

### Post by timcredible on 2008-09-19
> **cyberdork33 said:**
> Also, about the licensing issue... No, Apple does not allow for OSX to be run in a VM (except the server version) and because of that, even if it was possible, it cannot be discussed here in these forums. Just FYI.

what? we can't discuss things that violate a eula?  talking about something isn't illegal or against any eula or license.

---

### Post by cyberdork33 on 2008-09-19
> **timcredible said:**
> what? we can't discuss things that violate a eula?  talking about something isn't illegal or against any eula or license.
You can talk to the mods about it.

---

### Post by dsmoot on 2008-09-19
> **cyberdork33 said:**
> vmware fusion can do this, but it is basically undocumented. parallels may also be able to. There is sparse information out there, but I think you have to edit the VM config by hand.

You lost me here...  VMWare Fusion runs on OSX and has no problem running linux.  Do you mean VMWare Player running on Linux could in theory boot a OSX VM?

> 
Also, about the licensing issue... No, Apple does not allow for OSX to be run in a VM (except the server version) and because of that, even if it was possible, it cannot be discussed here in these forums. Just FYI.

I am not a lawyer but is that a EULA violation?  I think the EULA forbids running OSX on non Apple hardware, I don´t think it explicitly forbids virtualization.  Ironic if an Apple EULA prevents you from running an Apple OS on Apple hardware.

David

---

### Post by Ripfox on 2008-09-19
Discussing illegal activity is against COC, plain and simple.

---

### Post by dsmoot on 2008-09-19
Again I am not a lawyer and I am the new guy too.  Not trying to start any trouble but here is the exact language from the EULA posted on Apple´s own website at images.apple.com/legal/sla/docs/macosx105.pdf:

> 2. Permitted License Uses and Restrictions.
A. Single Use. This License allows you to install, use and run one (1) copy of the Apple Software on a single Apple-labeled computer at a time. You agree not to install, use
or run the Apple Software on any non-Apple-labeled computer, or to enable others to do so. This License does not allow the Apple Software to exist on more than one
computer at a time, and you may not make the Apple Software available over a network where it could be used by multiple computers at the same time.


No where in the EULA does it specifically forbid virtualization that I can see.  AFAIK, it is completely legal to virtualize a copy of OS X as long as that virtual copy is running on Apple hardware.

Now the sticky part... If I post instructions on how to do under Linux, it will work with any linux box, not just one running on Apple hardware.

Moderators, this is your playground, what is your decision?  Is virtualization of OSX on Apple Hardware a discussable topic?  I think it is pretty clearly not a violation of the EULA.

David

---

### Post by cyberdork33 on 2008-09-19
> **dsmoot said:**
> You lost me here...  VMWare Fusion runs on OSX and has no problem running linux.  Do you mean VMWare Player running on Linux could in theory boot a OSX VM?No, I was talking about the reverse... Install Ubuntu on a partition, then running that install in a VM under OS X as the host OS.

> **dsmoot said:**
> I am not a lawyer but is that a EULA violation?  I think the EULA forbids running OSX on non Apple hardware, I don´t think it explicitly forbids virtualization.  Ironic if an Apple EULA prevents you from running an Apple OS on Apple hardware. It is a grey area. It tends to get skirtted every now and again here.

> **dsmoot said:**
> No where in the EULA does it specifically forbid virtualization that I can see.  AFAIK, it is completely legal to virtualize a copy of OS X as long as that virtual copy is running on Apple hardware.and it is the only copy installed on that machine as well...

> **dsmoot said:**
> Now the sticky part... If I post instructions on how to do under Linux, it will work with any linux box, not just one running on Apple hardware.

Moderators, this is your playground, what is your decision?  Is virtualization of OSX on Apple Hardware a discussable topic?  I think it is pretty clearly not a violation of the EULA.This has been discussed in the past, and the staff here has decided not to allow it. That is why I brought up the fact that it should not be discussed.

---

### Post by LaRoza on 2008-09-19
> **timcredible said:**
> what? we can't discuss things that violate a eula?  talking about something isn't illegal or against any eula or license.

Not usually, no.

EULA's are not binding under most laws, but we act like they are. This is the official Ubuntu forums owned by Canonical.

I don't think violating EULA's of other products is fitting material for this forum and the Code of Conduct supports that.

Closed. If you wish to contest this closing, post in the Resolution Centre. I am not a lawyer.

---

### Post by LaRoza on 2008-09-19
> **afrowildo said:**
> 
My problem is that I want to boot up a preinstalled OS, rather than install it into a virtual machine. I've tried with Parallels, but that doesn't seem to be ablt to do it. Does anyone know if there's a program out there that can do this, for either linux of the mac?

Thanks in advance.

Ok, upon review I see there aren't any concerns unless one wants to be really picky. OS X is (presumably, because it is a Mac) legally installed and Ubuntu is also installed next to it. 

The issue is running OS X which is legally installed on Apple hardware in a VM on a dual booted OS. (Right?). I am not a lawyer, and now I don't want to be.

Thread opened...

---

### Post by cyberdork33 on 2008-09-19
> **LaRoza said:**
> Ok, upon review I see there aren't any concerns unless one wants to be really picky. OS X is (presumably, because it is a Mac) legally installed and Ubuntu is also installed next to it. 

The issue is running OS X which is legally installed on Apple hardware in a VM on a dual booted OS. (Right?). I am not a lawyer, and now I don't want to be.
yes that sounds right. as long as there is only one install of OSX, this seems to abide by the EULA.

---

### Post by DoubleClicker on 2008-09-19
> **afrowildo said:**
> Hey. I've been lurking on these forums for a while now, slowing getting the hang of ubuntu, and linux/unix in general. But the time has come where, having failed to find a solution on the forum, I must now seek the wisdom of the aged ubuntu masters.

I have a mactel running both Ubuntu and Leopard, and what I want to do is boot one up from within the other, the order isn't an issue. Now I know there are several tools out there that can do this, and I even own a Parallels desktop licence.

My problem is that I want to boot up a preinstalled OS, rather than install it into a virtual machine. I've tried with Parallels, but that doesn't seem to be ablt to do it. Does anyone know if there's a program out there that can do this, for either linux of the mac?

Thanks in advance.

Does it matter to you which is the Host OS and which is the Guest?   

There is no legal way to do it with Ubuntu being the host OS and Mac OS X being the guest OS, running in the virtual machine.   However if you run Mac OS X as the host OS, you can use VMware fusion to run Linux off a bootable partition in the virtual machine. This is the way I have my Machine set up.     

The secret is to use **vmware-rawDiskCreator** :
In VMWare Fusion, create a new virtual machine called MyUbuntu. Under “Settings” for that vm, you can change or add a new IDE hard drive. This will make life easier, since you won’t have to worry about having the right SCSI driver if you are running a minimalistic Linux distro. MyUbuntu is really a directory called **MyUbuntu.vmwarevm** (yes, vm appears twice in that extension).
Close MyUbuntu in VMWare Fusion, so you can edit it directly.
In a terminal:
```
cd "/Library/Application Support/VMware Fusion/"
```
List the partitions on your hard drive.
```
./vmware-rawdiskCreator print /dev/disk0
```
Create a file that points VMWare at your partition. (for exampe if your Ubuntu partition is number 3, you would use  number three 3 in the following command.)
```
./vmware-rawdiskCreator create /dev/disk0 3 /Users/USERNAME/MyUbuntu.vmwarevm/bootcamp_partition ide
```
Add or edit these lines in the text file /Users/USERNAME/MyUbuntu.vmwarevm/MyUbuntu.vmx
```
ide0:0.present = "TRUE"
ide0:0.fileName = "bootcamp_partition.vmdk"
```
Run MyUbuntu in VMWare Fusion. You will be asked for your administrative password, because VMWare Fusion must be granted access to read and write to your bootcamp partition.

---

### Post by cyberdork33 on 2008-09-19
> **DoubleClicker said:**
> However if you run Mac OS X as the host OS, you can use VMware fusion to run Linux off a bootable partition in the virtual machine. This is the way I have my Machine set up.     

The secret is to use **vmware-rawDiskCreator**.
Thanks, this is helpful. I think you are the first to summarize this in the Apple Users forum.

---

### Post by mfox on 2008-09-19
[Here comes a rant.] Ironically, you can run MacOSX within Linux without an additional installation of MacOSX on a PowerPC!  This is one of the beauties of the program Mac-on-Linux (MOL).  You can do the same with OS9 on MOL even where you can't run OS9 on your Mac (other than from Classic).  That's why I'm so miffed that Ubuntu hasn't yet patched MOL to run on the latest versions. :(  As I have noted in other posts, openSUSE has patched MOL so it will run on their latest version (11.0).  More recently, Debian has patched it so MOL will run in Lenny and Sid.  (It could always run in Etch because of the older kernel.)  I hope that MOL won't be a casualty of the loss of official support by Canonical for the PPC platform.

---

### Post by dsmoot on 2008-09-20
Good stuff Double Clicker!  I'll be giving that a shot today once I finish setting up my linux partition.  The same thing is in theory possible from virtualbox according to the manual BUT I could not get it to work with virtualbox running on a OSX host booting my Linux partition.  I plan to try running my OS X partition from a linux host under virtualbox soon.

Stupid question but does your Linux partition have to be formatted in a way os X can read?  I've never had much luck with the ext driver software on OS X.

David

---

### Post by dsmoot on 2008-09-21
Your instructions worked great for my Ubuntu partition, booting just fine inside Vmware.  However, because of the screwy way I partitioned, my XP partition is #5 and the IDE can't handle a partition number of 5.  So I've got to screw with using scsi or just re-partition.  I may try to buy a bigger hard drive and start from scratch.

Thanks again, I'll play with it and post detailed instructions later.

David

---

### Post by dsmoot on 2008-09-22
Ok, thought I would share what I learned playing with vmware...

If you use the older vmware (1.xx) then doubleclicker's instructions are perfect with two comments:
[LIST=1]
[*]Because you are telling VMware to treat your partition like an IDE device, then you can only use this with a partition number of 4 or less
[*]The vmdk file name does not have to be bootcamp_partition, it can be anything that does not conflict with the vmdk you had to create with the VM.
[/LIST]

If you decide to do the free upgrade to VMWare 2.xx then doubleclicker's instructions have to be tweaked slightly.
[LIST=1]
[*]Don't create a Virtual Machine inside vmware first.  Instead follow Doubleclicker's step to create the virtual disk and store it in your virtual machines folder.
[*]Now create a new virtual machine in vmware.  Select the "Continue without installation disk".
[*]You will then be presented with some options about what kind of virtual disk to use.  Tell it you want to use an existing disk image and point it to the *.vmdk file you created in step 1.
[*]The rest should be straight forward...
[/LIST]

Maybe I'll play with virtualbox now that it is not a forbidden topic and make an Apple virtualization FAQ.

David

---

### Post by cyberdork33 on 2008-09-23
> **dsmoot said:**
> Ok, thought I would share what I learned playing with vmware...
You might check in the virtualization forum as there might be something similar there (and I think it is more appropriate there). Then I can make a link in the FAQ here to point to that how-to / faq.

---

### Post by ubuntoplebe on 2008-11-12
> **dsmoot said:**
> Ok, thought I would share what I learned playing with vmware...

If you use the older vmware (1.xx) then doubleclicker's instructions are perfect with two comments:
[LIST=1]
[*]Because you are telling VMware to treat your partition like an IDE device, then you can only use this with a partition number of 4 or less
[*]The vmdk file name does not have to be bootcamp_partition, it can be anything that does not conflict with the vmdk you had to create with the VM.
[/LIST]

If you decide to do the free upgrade to VMWare 2.xx then doubleclicker's instructions have to be tweaked slightly.
[LIST=1]
[*]Don't create a Virtual Machine inside vmware first.  Instead follow Doubleclicker's step to create the virtual disk and store it in your virtual machines folder.
[*]Now create a new virtual machine in vmware.  Select the "Continue without installation disk".
[*]You will then be presented with some options about what kind of virtual disk to use.  Tell it you want to use an existing disk image and point it to the *.vmdk file you created in step 1.
[*]The rest should be straight forward...
[/LIST]



I just installed Ubuntu 8.04 on a 3rd internal hard drive on a mac pro.
I have a dual boot using rEFIt, everything is peachy. I'm eager to use vmware fusion (2.xx) now
along the lines discussed here, but keep getting the "no bootable device" error.

Here's the rawdiskCreator print output for me:

me> ./vmware-rawdiskCreator print /dev/disk0
Nr      Start       Size Type Id Sytem                   
-- ---------- ---------- ---- -- ------------------------
 1          1     409639 BIOS EE Unknown
 2     409640  976101344 BIOS AF HFS+

me> ./vmware-rawdiskCreator print /dev/disk1
Nr      Start       Size Type Id Sytem                   
-- ---------- ---------- ---- -- ------------------------
 1          1  976773160 BIOS EE Unknown

me> ./vmware-rawdiskCreator print /dev/disk2
Nr      Start       Size Type Id Sytem                   
-- ---------- ---------- ---- -- ------------------------
 1         34  964742188 BIOS 83 Linux
 2  964742222   12030913 BIOS 82 Linux swap

I believe I want the 1st of disk2 (the 3rd internal disk), so I've tried

me> ./vmware-rawdiskCreator create /dev/disk2 1 "/Users/me/Documents/Virtual Machines.localized/bootcamp_partition" ide

and then followed the 2nd set of doublecliker's instructions (for VMF 2.xx) for using VMF 
off of a virtual disk, but no go. It tries to start up, but within a minute or so I get the
"no bootable device found" error.

I'm wondering if there's something about my linux installation that prevents it
from being usable in VMF along these lines. Does the output of my rawdiskCreator print 
command above look normal?

Thanks for any help!

---

### Post by the Arbiter on 2008-12-09
try mini vmac it may not be osx ... but it is cool

---

### Post by nil0z on 2008-12-10
Is there also an answer to the original question?

**Disclaimer**: I have a MacBook with a legal MacOS X, but my OS of choice is Ubuntu. To stay EULA compliant, i would either boot the nativly installed MacOS inside a VM, or i would wipe the native installation and install MacOS into a VM image. In any case, **there would be only ONE MacOS installation and it would run on Apple hardware**.

I am a network and system admin and work all day with Linux, but i need to run MacOS apps to test our services. And i am tired of rebooting all the time ...

Cheers, n

ps: i would prefer OSS software like KVM or virtualbox or xen, but vmware would be ok, too

---

