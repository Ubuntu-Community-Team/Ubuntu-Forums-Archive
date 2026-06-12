---
title: "Please Help - VMware Shared Folders"
date: 2007-10-26
forum: Absolute Beginner Talk
---

### Post by luckylucky on 2007-10-26
Hi, I did my due diligence homework, googled around & all, spending numerous hours trying to get this to work, but I am stumped.  Can someone please help out?

I am trying to make a virtual machine of Ubuntu guest on an XP host.  Making the VM in either VMware & VirtualBox is easy... where I am having trouble is getting shared folders to work.  

Ok, let's stick with VMware, how do I get shared folders working?
*  I've added code to the vmdk config file
*  Of course vmtools is properly installed inside guest
*  I've activated shared folder "alway on" in the vmplayer settings
*  I've looked in the folder /mnt/hxxx (I don't remember the actual path right now)
*  I've tried knocking my head against brick wall ](*,)

Has anyone actually got shared folders working in vmware?  I would appreciate a life-line of help here.  Thanks in advance.

---

### Post by stijngysemans on 2007-10-26
Just a question, maybe this will work?
Can you drag a file from the virtual desktop to the XP desktop? This can maybe be a work-around!

---

### Post by luckylucky on 2007-10-26
Actually that only works between two windows machines (host & guest = windows).  If you have a mix of windows & linux that won't work.  It will be nice once VMware builds in that feature!

Thanks for trying... **[COLOR="Red"]still looking for other suggestions.[/COLOR]**

---

### Post by luckylucky on 2007-10-26
[COLOR="Red"][B][SIZE="5"]Anybody Help Please Please PLEASE!!!
[/SIZE][/B][/COLOR]
Ive even turned off my firewall in desperation... nothing at all is working.  Please help

---

### Post by stijngysemans on 2007-10-27
please don't get frustrated:)
:guitar:

what you can do is set up a network connection in both the vm and the host.
I do not know it's possible to setup multiple ip adresses for one physical network card?
have you tried some howto's already?

---

