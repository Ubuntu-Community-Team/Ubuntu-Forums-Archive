---
title: "Ubuntu Fiesty Virtualization"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by ZeroWing on 2007-04-19
I've always wanted to be able to virtualize windows on Ubuntu, just to be able to run some programs, but I've never been able to. Can anyone tell me how to run Virtualization software with feisty? What do I need to run it?

---

### Post by LaRoza on 2007-04-19
Search the forums.

You could use many different tools, Wine, VMware, and VirtualBox are frequently discussed on this forum. Search for them for specifics.

---

### Post by ZeroWing on 2007-04-19
> **LaRoza said:**
> Search the forums.

You could use many different tools, Wine, VMware, and VirtualBox are frequently discussed on this forum. Search for them for specifics.

 Wine is not virtualization, it is emulation, and I think that VMware and VirtualBox cost money, which I have very little of. Anyways, you need the actual install CD for what you're trying to emulate, right? Well, I don't have any install CD's, so I suppose I have to use Wine....

 thanks, anyways..

---

### Post by LaRoza on 2007-04-19
Sorry, I never used them and only know of them.

---

### Post by Zuph on 2007-04-19
> **ZeroWing said:**
> Wine is not virtualization, it is emulation, and I think that VMware and VirtualBox cost money, which I have very little of. Anyways, you need the actual install CD for what you're trying to emulate, right? Well, I don't have any install CD's, so I suppose I have to use Wine....

 thanks, anyways..

Neither VMWare nor Virtual box cost a dime.  You do have to have an install CD or ISO image to put an OS on there, though.

VMWare Server needs a patch to install on feisty as of right now, but this process is pretty well documented in the forums.

---

### Post by compiledkernel on 2007-04-19
With the fiesty release KVM driven Qemu is a valid way to address this issue. 

[https://wiki.ubuntu.com/ScreencastTeam/HowToSetupQEMU](https://wiki.ubuntu.com/ScreencastTeam/HowToSetupQEMU)


Alternately you can also consider the use of VirtualBox -- which has prebuilt Debs that install very easily on feisty and edgy. 

[http://virtualbox.org](http://virtualbox.org)

---

### Post by veloce on 2007-04-20
> **Zuph said:**
> Neither VMWare nor Virtual box cost a dime.  You do have to have an install CD or ISO image to put an OS on there, though.


VMWare also have a free (as in beer) tool to convert an existing physical machine into a virtual machine.

---

### Post by docshawnc on 2007-04-20
Can someone steer me to the patch to make VMWare Server work with Fiesty?  A quick search didn't come up with anything for me - thanks

---

### Post by the8thstar on 2007-04-21
Hey guys, I have a few questions before I take the deep plunge:

1. With the virtualization solution, will I be able to use DirectX?

2. Can I update Windows and the programs running in it through Windows Update and custom program-run updates or is the system fixed forever?

3. Can I use drag-and-drop function for files and documents between Ubuntu and the virtual machine?

4. Can I use my system restore partition as a source file instead of a Windows CD, which I don't have since my install was OEM?

5. Can I install the Vista Upgrade on top of Windows XP running in a virtual machine in Ubuntu?

---

### Post by veloce on 2007-04-22
> **docshawnc said:**
> Can someone steer me to the patch to make VMWare Server work with Fiesty?  A quick search didn't come up with anything for me - thanks

[http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz](http://knihovny.cvut.cz/ftp/pub/vmware/vmware-any-any-update109.tar.gz)

(Just had to do the same myself.)

---

### Post by veloce on 2007-04-22
> **the8thstar said:**
> Hey guys, I have a few questions before I take the deep plunge:

1. With the virtualization solution, will I be able to use DirectX?

2. Can I update Windows and the programs running in it through Windows Update and custom program-run updates or is the system fixed forever?

3. Can I use drag-and-drop function for files and documents between Ubuntu and the virtual machine?

4. Can I use my system restore partition as a source file instead of a Windows CD, which I don't have since my install was OEM?

5. Can I install the Vista Upgrade on top of Windows XP running in a virtual machine in Ubuntu?

1. No.  Well, the (not free) vmware workstation has experimental support for 3d acceleration.

2. yes.  You just need to set up virtual networking to allow internet access through the host.

3. No.  Or Yes.  Think of the machines as being two physically different machines - use samba to share a directory and you can drag and drop to / from it.

4. I don't think so.  For OEM, use the vmware tool to create a vm from a physical distribution.  You will probably have to re-authenticate your windows as well.  

5. Maybe - you could be breaking new ground there, I haven't heard of anyone doing it.  (Though we have installed a fresh copy of Vista as a vm at work).  You'd also have to check the license for the copy of Vista.  They specifically exclude virtualisation for some versions and severely restrict it on others.

---

### Post by heimo on 2007-04-22
> **ZeroWing said:**
> Wine is not virtualization, it is emulation, 

[**W**ine]("http://www.winehq.com/") **I**s **N**ot an [**E**mulator]("http://en.wikipedia.org/wiki/Emulator").

It's more like [compatibility layer]("http://en.wikipedia.org/wiki/Compatibility_layer").

---

### Post by the8thstar on 2007-04-22
Apparently, someone has been able to their partition as a source disk: [http://ubuntuforums.org/showthread.php?p=2510162#post2510162]("http://ubuntuforums.org/showthread.php?p=2510162#post2510162")

Any ideas on how to do that?

---

### Post by ZeroWing on 2007-04-23
Now  would you be able to install Windows XP into a virtual disk using VMware from, say, an HP system restore disk...?

---

