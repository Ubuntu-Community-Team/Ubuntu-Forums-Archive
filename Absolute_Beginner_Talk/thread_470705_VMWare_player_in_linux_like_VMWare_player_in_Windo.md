---
title: "VMWare player in linux like VMWare player in Windows?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by BHelts on 2007-06-11
I have a new toshiba laptop that came with xp pro installed, the first thing i did was wipe xp and put on feisty.  I'd like to put XP Pro in VMWare player.  Do I need VMWare Workstation like in windows, or can I make my own virtual machine in VMWare player for linux?

Thank you in advance for your time.

---

### Post by EndPerform on 2007-06-11
You'll need Workstation to create the image.

---

### Post by Nekiruhs on 2007-06-11
Or you could go with the free VMWare server to create the image! Right now I'm installing Vista into a VMWare server so I can sync my Zune.

---

### Post by BHelts on 2007-06-11
ok.  i think i'll give that a go.  Thank you both for your replies.

---

### Post by insane_alien on 2007-06-11
best thing is that there is a vmware-server .deb in the commerical repos now.

---

### Post by Seisen on 2007-06-11
You can also use VirtualBox which is similar to VMWARE.

---

### Post by BHelts on 2007-06-11
> 
You can also use VirtualBox which is similar to VMWARE.

yeah, i've been doing some reading about that......  hard to decide which is better.

> best thing is that there is a vmware-server .deb in the commerical repos now.

this may be a stupid question.... but which are the commercial repos?

---

### Post by Seisen on 2007-06-11
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

That is the commercial repository. Try VMWARE and if it doesn't work or you have problems try Virtual Box.

---

### Post by BHelts on 2007-06-11
very cool.... added that to my sources.list and there it is.  vmware-server.  thanks a lot.

i love this place.

---

### Post by anaconda on 2007-06-12
VMWare support for feisty isn't ready yet. It works, but is slow.

so currently Virtualbox will be a LOT faster, but I think vmware is going to fix that soon..

---

### Post by BHelts on 2007-06-12
thanks a lot for the heads up!!

---

### Post by jamaas on 2007-06-14
Relative noob here, I get as far as the installation and then get an error as such, is this common?  I have no idea what it means ... am I missing headers again?

Thanks

Jim

vmware-server: subprocess post-installation script returned error exit status 1


> **BHelts said:**
> thanks a lot for the heads up!!

---

### Post by deadlikeoscar on 2007-06-14
I second the Virtualbox suggestion. It runs better than vmware for me at least and I like the program better.

---

