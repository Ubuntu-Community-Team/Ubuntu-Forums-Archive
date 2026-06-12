---
title: "Running Windows XP in Ubuntu - need help"
date: 2007-12-11
forum: Absolute Beginner Talk
---

### Post by lmbrice on 2007-12-11
I'm new to Ubuntu (and the whole linux language). I installed Windows XP Pro in the virtual box of Innotek and I was successful except for my virtual XP does not recognize that I have any USB ports even though my mouse is USB. I tried to access my windows bios during startup, but haven't been successful as of yet. I would like to print from my xp side as I have yet to find a quality desktop publishing program for the linux side. Please tell me what to do.

Thanks.

---

### Post by c0mp13371331337 on 2007-12-12
I've used Innotek VM software before, unfortunately not on this install though, so I don't recall off the top of my head the exact way to get to where you need to be.  But there's an option in the VM software itself to configure your hardware for a particular VM, such as display adapters, networking devices, drives, etc.

When I installed it, USB support worked out of the box, so I didn't have to mess with that particular aspect, but I changed the drive configuration a bit, messed with the network settings, etc.  It read from USB drives just fine, and that's all I was using it for.

So I'd check there and make sure all the USB options are correct, and then, if you haven't already, try manually installing the printer through the Windows Add Printer wizard, see if it'll pick it up then.  Best of luck, and welcome to the Ubuntu community!

---

### Post by lmbrice on 2007-12-12
Thanks. The difficulty is that I'm not getting any options on the VM to enable the USB ports. When going to the add hardware in XP it says I don't have the ports at all.

---

### Post by 720iD on 2007-12-12
hi are you using the latest Innotek machine I used to used to have problems with network connections,usb and shared folders but after upgrading ot the latest version all is fine. although the latest version has a nag to register [for free].

---

### Post by omegamike3 on 2007-12-12
Is there a specific reason you're using Innotek? Personally, I prefer vmware server as I've never really had any trouble with it. Innotek has always been a bit flaky to me, sometimes working, sometimes not, sometimes just taking a lot of work to get functionality. There's a fine how-to on ubuntugeek if you're interested. [http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html](http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html)

---

### Post by Orbital75 on 2007-12-12
Hi.... If I am correct there are 2 version of Virtual Box.  The Open Source
version that is in the repositories and the Proprietary version that's on
Innotek site..... The Open Source version doesn't have USB support.
You will have to use the  Proprietary version that's on Innotek site....

Hummm.... I went and read some of the FAQ's for you and it seems
that they have taken USB Support out of their version as well. You can
get it to work by doing this below.

USB on Ubuntu/Gutsy: Ubuntu removed support for /proc/bus/usb/*. We will address this issue in the future. Until this, edit the script `/etc/init.d/mountdevsubfs.sh and activate the four lines around line 40 (Magic to make /proc/bus/usb work). Then execute

/etc/init.d/mountdevsubfs.sh start

From now on, there should be a directory /proc/bus/usb/ and the device entries below should be accessible by any user.

---

### Post by michaelzap on 2007-12-12
redacted

---

### Post by lmbrice on 2007-12-13
I'm using Innotek because when I went to acquire vmware it stated it wouldn't load because it didn't like that my machine was i386. I'm not quite sure what that's all about. 

Thank you Orbital75 for you're help. I'm totally new to linux/ubuntu so your directions have me stumped. I'm assuming I'm going into the terminal to make these changes, but I have no clue what to do from there or where to fine line 40. Would love more help.

Thanks

---

