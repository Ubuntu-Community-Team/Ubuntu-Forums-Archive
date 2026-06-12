---
title: "mac at school want to use ubuntu"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2008-01-30
I have a ubuntu cd. It won't boot on the schools computer, nor do i want it to.

I want to be able to run the ubuntu live cd virtually. How can I do this by not installing any programs on the mac. i can't install to the applications folder, but I can install to my own folder.

What do i need to do?

virtualbox won't work unless i am missing something that lets me install to a optional folder.

---

### Post by rubbsdecvik on 2008-01-30
Are the macs running on Intel processors, or PowerPC processors.  

It makes a difference.

---

### Post by rubbsdecvik on 2008-01-30
[http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/](http://www.pendrivelinux.com/2008/01/11/run-ubuntu-710-from-windows/)

here is a link on how to do it with Windows...

If you can do the same process with QEMU for Mac... you might have some luck.  

Virtualbox only works on the new Intel Macs

---

### Post by tdrusk on 2008-01-30
It's an intel

---

### Post by rubbsdecvik on 2008-01-30
[http://www.kju-app.org/kju/](http://www.kju-app.org/kju/)

You could try Q.  It's based off of QEMU.  It looks like its a little harder to use, but might be more customizable.

I'll look into seeing if virtualbox will install in other directories.

---

### Post by yousufinternet on 2008-01-30
try to use bootcamp to install ubuntu 
i have done this with my macbook

---

### Post by rubbsdecvik on 2008-01-30
> **yousufinternet said:**
> try to use bootcamp to install ubuntu 
i have done this with my macbook

The problem is, i think, that he wants to only do it temporarily.  it's not his computer.  He doesn't want to permanently change anything

---

### Post by dark_harmonics on 2008-01-30
if you dont mind sacrificing a usb drive (because of the multiple read-write operations) you can install to a flash drive. The install process takes a LOOONNNNGGG time but it worked for me to test ubuntu on laptops that dont have native graphics support.'

I've never done this with a PPC install though. I would assume you would need to use a PPC to boot the installer and point it towards the usb drive. It should work. Just be careful not to wipe your local HD... btw you will need to use the PPC installer for that arch.

Edit:
Also now that i think of it. I think that you can add parameters to the live cd to have it use a usb drive to write changes to.I dont remember how to do this. If i find the post i will edit it in here.
Edit Edit:
Yes found the information here:  [http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/](http://www.pendrivelinux.com/2007/09/27/making-ubuntu-710-casper-persistent/)

The important part is to "To boot persistently, at the boot menu press F6 to enter a custom boot option. Add persistent to the end of the boot string"

Oh and i noticed that you said its an intel so a default gutsy install to a USB or the above use of live CD and USB drive should work.

---

### Post by rubbsdecvik on 2008-01-30
Couldn't find anything on how to install in a different directory sorry.  And I don't have a Mac handy right now sorry.

Hopefully you can find something that will help you out.

---

### Post by tdrusk on 2008-01-30
q worked. It's loading the live cd right now.


I will probably put this on a flash drive to speed it up.

Can I put it on my iPod and not ruin it?

---

### Post by dark_harmonics on 2008-01-30
type free at a command prompt

---

### Post by rubbsdecvik on 2008-01-30
> **tdrusk said:**
> Can I put it on my iPod and not ruin it?

Not sure.  You'd have to do some research on that.  I can't see why you wouldn't be able to.  If you just use part of it as storage.  I can still use my flash drive as normal and I have [SystemRescue Linux]("http://www.sysresccd.org/Main_Page") on it.  So my preliminary guess is, yes you probably could put it on your iPod.

Glad to hear you got it working!

---

### Post by tdrusk on 2008-01-30
hmm. Can I install ubuntu to a folder? That is the purpose of vmware right?

They are going to reformat the computer soon, so it's all good.

---

### Post by tdrusk on 2008-01-31
> **tdrusk said:**
> hmm. Can I install ubuntu to a folder? That is the purpose of vmware right?

They are going to reformat the computer soon, so it's all good.

anybody?

when i install it with the mac qemu can I install it to a folder or what? What's the fastest way to run this off the hard drive?

---

### Post by rubbsdecvik on 2008-01-31
You could probably install it with QEMU using a virtual hard drive, which can be in a folder.

---

### Post by jrothwell97 on 2008-01-31
1. Put your disk in.
2. Reboot the computer and wait for the startup chime (the loud bong the machine plays when it boots).
3. Press and hold C when you hear the chime, and wait. As soon as something appears on the screen, release the key.

If this doesn't work, then chances are your administrator has enabled EFI Password Protection. In this case, your best bet is using QEMU (Q is a rather nice GUI port).

---

### Post by tdrusk on 2008-01-31
> **rubbsdecvik said:**
> You could probably install it with QEMU using a virtual hard drive, which can be in a folder.

hmm.

when i booted ubuntu with the mac qemu it didn't show any available "partitions" how can i get around that?

EDIT: I just saw in qemu preferences that I can have a 4 gig compressed hard drive. Awesome.

---

### Post by jrothwell97 on 2008-01-31
You need to create a disk image first, either using dd or qemu-img. I still suggest using either Q or booting directly from the CD.

---

### Post by rubbsdecvik on 2008-01-31
> **jrothwell97 said:**
> ... booting directly from the CD.

The problem is that he doesn't want to restart the computer.  This is a school computer and he is only allowed to do things to his user (at least that's what I'm guessing because that's how it worked at my school).  Restarting the computer and booting from the CD is not a good option for a couple of reasons.

1) School Sys Admins don't know what's going on.  They tend to freak out at the slighted deviation from their normal "working" setup and truly detest students messing with their set up.

2) You can't save the work.  All he can do is mess with it a little and all his work is lost.  I'm guessing he wants a semi permanent, but easily reset system.  Hence a VM.  

> **tdrusk said:**
> I just saw in qemu preferences that I can have a 4 gig compressed hard drive. Awesome.

I'm glad you found that preference, but is it going to be enough?

---

### Post by tdrusk on 2008-02-01
> **rubbsdecvik said:**
> The problem is that he doesn't want to restart the computer.  This is a school computer and he is only allowed to do things to his user (at least that's what I'm guessing because that's how it worked at my school).  Restarting the computer and booting from the CD is not a good option for a couple of reasons.

1) School Sys Admins don't know what's going on.  They tend to freak out at the slighted deviation from their normal "working" setup and truly detest students messing with their set up.

2) You can't save the work.  All he can do is mess with it a little and all his work is lost.  I'm guessing he wants a semi permanent, but easily reset system.  Hence a VM.  



I'm glad you found that preference, but is it going to be enough?

It should be. I just want to install ubuntu and do little things.

---

