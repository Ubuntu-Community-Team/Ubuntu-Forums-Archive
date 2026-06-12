---
title: "Virtual Machine?"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by RyanZec on 2007-10-04
I am trying to trying out some Virtual Machines for windows on linux.  2 main thing i need windows for is Web Development(PhpED & IE7) and Windows Development(Visual Studio).  Can you give give em a list of solid VM programs i should try.  Right now i am trying Parallels(PhpED and recently partnered with them with is how i found out about them.

Also i am currently using Wine to game(right now only WoW), if any of these VM program you suggest can support game just as good or better then Wine, please let me know.

---

### Post by Hossie on 2007-10-04
Why do you use IE for web development? Shouldnt you use some "modern" browser for that? Nevertheless, IE should run with wine. There a quite a few native Editors for Web-Dev, e.g. Quanta or Komodo Edit.

---

### Post by bodhi.zazen on 2007-10-04
VMWare is the most mature

Virtualbox is also nice :

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

[http://doc.gwos.org/doku.php/doc:office:virtualbox](http://doc.gwos.org/doku.php/doc:office:virtualbox)

---

### Post by nowshining on 2007-10-04
i use VirtualBox - nice, quick, etc.. I still got the older version. :P and it doesn't support some linux version, but does support XP, etc.. few if any problems so far and VB is FREE. :) - altho u need to take some to set it up and it does take a bit of time to set permissions, etc..

---

### Post by Incense on 2007-10-04
VirtualBox has my vote. Seamless mode is fantastic!

[http://www.virtualbox.org/wiki/Downloads]("http://www.virtualbox.org/wiki/Downloads")

---

### Post by RyanZec on 2007-10-04
The ones you talked about are designed for "gerenal" web development.  One major feature on PhpED i need to code complete becuase i would with large files will many variable and classes that can be large so auto complete increases my productivity a lot.

Another thing i forgot to ask it would it be safe to development something use Visual studio in a VM program and say for sure it will run in windows?

---

### Post by nowshining on 2007-10-04
anyting in a VM envirnment will work if the Operating installed in the VM program wil allow it, :) in other words if you had installed windows - just windows and used it on the main computer without the VM envirnment - in a VM envirnment it will just be the same, it's a Guest operating system on the Host computer that's all - :) Anything windows will support on it's own, will support the same in a VM program. Well except restore disks at least in the VB version I have :P it needs activation even tho it worked without the need to do so when it was insalled by itself and not in a VM.

---

### Post by bodhi.zazen on 2007-10-04
~ LOL ~ VMWare server is also free, but not open source.

Virtual box is abailable as an open source edition, see the DL page.

Seamless : [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

---

### Post by RyanZec on 2007-10-04
> **bodhi.zazen said:**
> ~ LOL ~ VMWare server is also free, but not open source.

Virtual box is abailable as an open source edition, see the DL page.

Seamless : [https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

I though VMWare costed about 180?

---

### Post by nowshining on 2007-10-04
I did to thought it costs however that might be for whe Windows version. VB does come in a open source editons, however it omits usb support, etc.. :) I'm using the closed one with USB support and the ability to write to disks on the Host itself.

---

### Post by Malibu Illusion on 2007-10-04
**@Hossie**:

> **Hossie said:**
> Why do you use IE for web development? Shouldnt you use some "modern" browser for that? Nevertheless, IE should run with wine. There a quite a few native Editors for Web-Dev, e.g. Quanta or Komodo Edit.

Web developers have to cater for a wide scope of browsers, entailing a broad spectrum of parsing and output methods.  To create a web solution centric to a specific browser, no matter which browser this happens to be, is poor development and atrocious from an accessibility standpoint.  This is a very valid reason to view content in IE, seeing as this is still what the majority of browsers are on the Internet statistically speaking.

That said, there are other methods of reviewing your page in a multitude of other browsers without installing them.  Anyone interested in this should check out sites such as [browsershots.org](http://browsershots.org)

**@RyanZec**:For a VM solution, I personally use VMWare.  It's solid, although the others mentioned in this thread such as Virtualbox work equally as well.

For gaming I'd suggest checking out the Cedega fork of WINE.

Take care.

---

### Post by n3tfury on 2007-10-04
> **nowshining said:**
> I did to thought it costs however that might be for whe Windows version.

wrong.  they have free versions for both OS's.  

> **nowshining said:**
>  VB does come in a open source editons, however it omits usb support, etc.. :) I'm using the closed one with USB support and the ability to write to disks on the Host itself.

huh?  vb is ALL open source.  and no, it does NOT omit usb support "etc".  if you meant VMware, well guess what?  you're wrong again:

>  Windows NT and Linux kernels older than 2.2.17 do not support USB.

---

### Post by nowshining on 2007-10-04
Actually Those Useragent strings can be changed to look like one another - This site thinks I'm using IE7 on Windows Vista which Is why the drop-downs don't work - :) figured that is why, anyway i'm going to keep it that way.

---

### Post by RyanZec on 2007-10-04
Where can i get the free version of VMware?  what is the difference fromt he free version of VMware and the 180 dolar version?  

I tried to install VirtualBox two times but if frozen my system and i had to reboot.

---

### Post by n3tfury on 2007-10-04
> **nowshining said:**
> Actually Those Useragent strings can be changed to look like one another - This site thinks I'm using IE7 on Windows Vista which Is why the drop-downs don't work - :) figured that is why, anyway i'm going to keep it that way.

that wasn't directed at me, was it?

---

### Post by n3tfury on 2007-10-04
> **RyanZec said:**
> Where can i get the free version of VMware?  what is the difference fromt he free version of VMware and the 180 dolar version?  

I tried to install VirtualBox two times but if frozen my system and i had to reboot.

how did you try and install VB?  from synaptic or from the .deb on the website?  i had no issues with several installs using the .deb

---

### Post by RyanZec on 2007-10-04
from the .deb on there site.

Let me clear something up, the install on VB is good but when i try to install Windows XP it freezes on the format partition stage around 0 or 20%

---

### Post by n3tfury on 2007-10-04
uh, yeah, that's a COMPLETELY different issue.  im not sure why that wouldn't work. i've got XP and Vista ultimate installed on my VB.  hopefully someone can chime in to help you out further.

---

### Post by RyanZec on 2007-10-04
my mistake, i was giving the VM 1024MB on memory and that is the total in my computer.

---

### Post by RyanZec on 2007-10-04
i got XP installed but it gets aborted while i am on it randomly

---

### Post by nowshining on 2007-10-04
mine works fine, i just did an update to the newer one, i used the feisty deb and i'm on Gutsy and all works well, altho sound is a bit off at first when it starts up :P oh tho it's quicker.

Why did you chose a partition there is no need to, to create new VMs and install new operating systems just select new. :) yes XP worked fine for me on feisty.

---

### Post by nowshining on 2007-10-04
oh and my xp is FAT and 2GB edit: NTFS last time before I deleted it - just re-installed last night..

---

### Post by bodhi.zazen on 2007-10-05
:lolflag:

For those looking for VMWare :

> VMware Server is a proprietary virtualization software package made available for no cost from the [WWW] VMware website. VMware Server allows you to run entire operating systems in a virtual machine, which runs on top of Edubuntu, Ubuntu or Xubuntu. This guide provides instructions on installing, configuring and running VMware Server and VMware Server Console on (Ed/K/X)Ubuntu.

[https://help.ubuntu.com/community/VMware/Server](https://help.ubuntu.com/community/VMware/Server)

[http://www.howtoforge.com/ubuntu_vmware_server](http://www.howtoforge.com/ubuntu_vmware_server)

VMWare server is free of charge, you must register with VMWare to obtain a serial number (free of charge)

==================================
:guitar:                 :guitar:
==================================

For those interested in VirtualBox, there are two editions :

> Proprietary version vs. free and open source edition

There are two versions of the VirtualBox software. The full VirtualBox package comes under a proprietary license which allows using the software free-of-charge for personal and educational use and evaluation of the product.[8] Licenses for commercial use of the full VirtualBox package can be purchased from innotek.

A second version called the VirtualBox Open Source Edition (OSE) was released under the GPL, from which a number of features are missing, which are:[9]

    * The built-in Remote Desktop Protocol (RDP) server.
    * USB support (see above) and the combination of running the RDP server with support of remote USB devices.
    * USB over RDP, which permits connecting USB devices to a remote virtual machine.
    * The iSCSI support for virtual hard disks (see above).

The open source edition got accepted in Debian unstable on 30 August 2007.

[http://en.wikipedia.org/wiki/VirtualBox](http://en.wikipedia.org/wiki/VirtualBox)

---

### Post by RyanZec on 2007-10-05
> **nowshining said:**
> mine works fine, i just did an update to the newer one, i used the feisty deb and i'm on Gutsy and all works well, altho sound is a bit off at first when it starts up :P oh tho it's quicker.

Why did you chose a partition there is no need to, to create new VMs and install new operating systems just select new. :) yes XP worked fine for me on feisty.

Not sure what you mean by this.  I created a new virtual disk and then installed XP like i would normally.

---

### Post by RyanZec on 2007-10-05
Another thing is do i have to install the video/audio driver for the guest OS for virtualBox?

---

### Post by nowshining on 2007-10-05
no exit out of the xp and go into settings once there you can chose to use the audio ALSA however u must disable all audio program from the HOST operating system first (i was playing music which then it spit out a warning to me about that - no sound exited - exited out of rythmbox and restarted XP and sound was available. Just check out the settings on the side in settings and it should say sound ,etc.. there also somewhere in there an option to allow to from the host, guest to host or bidirectional clipboard access.

did you read the manual incl. on the program. :P

---

### Post by Incense on 2007-10-05
> **RyanZec said:**
> Another thing is do i have to install the video/audio driver for the guest OS for virtualBox?

Yes, you will want to do this for better mouse and video support. Also I beleive you need this to use seamless mode. It's under one of the menus when your guest os is running. ( don't have it in front of me right now)

---

