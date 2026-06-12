---
title: "VMware Question"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Lvcoyote on 2007-12-07
Hi !!,

My computer has two hard drives, one houses Ubuntu 7.10, and the other XP SP2.  How would I go about using VMware to use WindowsXP while booted in to Ubuntu?.  I've read up on how to install VMware, but I dont want to do so if I cant use it to access my XP install on the other hard drive.

Thanks  in advance!

---

### Post by nikoPSK on 2007-12-07
A bit confusing... You want to run vmware in xp to emulate linux? or the other way round....

---

### Post by CaptainInsaneO on 2007-12-07
He wants to run VMWare on Linux to use Windows from.

And you can access your physical disks from VMWare, to answer your question. Search around Google for a guide on it, there's lots!

---

### Post by Lvcoyote on 2007-12-07
Yes, while booted in to Ubuntu I want to use WIndows XP via VMware.  What confused me is while reading up a little, its seems most people use VMware to access a Windows computer over a network, but my XP install is on a hard drive attached to the same system.  It may be that I am completely off base as to what VMware does, which wouldnt suprise me......LOL

---

### Post by Dr Small on 2007-12-07
You have it correct. VMware installs on your Ubuntu installation, and then you install Windows XP with VMware, or VirtualBox, all on the same hard drive.

---

### Post by CaptainInsaneO on 2007-12-07
I actually have VMWare running right now as I type this, I'm using it for three servers running Windows Server 2003 and one XP client. None of these OS's are actually installed on this machine, I'm just using the .iso image of each one to run it. Hope this helps you understand it a little bit better.

---

### Post by Lvcoyote on 2007-12-07
Ok, great.....now we are getting places.... LOL.  One more question before I dive in.  When you say I install XP with VMware, do you mean like a fresh install or will VMware pull its XP install from the hard drive that XP is already installed on??

---

### Post by Dr Small on 2007-12-07
VMware will read a file (well, virtualbox does) that the OS has been installed to. You must make a clean install of the OS on VMware in order for it to function. VMware can not read a current installation somewhere else on the hard drive at another partition, that is not what VMware does.

Dr Small

---

### Post by Lvcoyote on 2007-12-07
Ok, now I got it.....  I'm sure this will require activation again by the turds at M$....LOL.  Yet another reason why I'm trying like hell to say goodbye to Microsoft!!

Thanks again fellas, these forums are the best Linux forums around..... bar none!!

---

### Post by PilotJLR on 2007-12-07
Lvcoyote - it sounds like you want to boot your Windows partition as a VM while in linux. Check this out:

[http://oopsilon.com/Running-a-Windows-Partition-in-VMware](http://oopsilon.com/Running-a-Windows-Partition-in-VMware)

---

### Post by scxtt on 2007-12-07
> **Dr Small said:**
> VMware will read a file (well, virtualbox does) that the OS has been installed to. You must make a clean install of the OS on VMware in order for it to function. VMware can not read a current installation somewhere else on the hard drive at another partition, that is not what VMware does.

Dr Smallthat's not true ... you can create another hw profile in a HDD-installed Windows partition, point the virtual disk for the virtual windows at the physical install, then boot a virtual version of that installed Windows ...

which is what PilotJLR is getting @ ...

---

### Post by Dr Small on 2007-12-07
> **scxtt said:**
> that's not true ... you can create another hw profile in a HDD-installed Windows partition, point the virtual disk for the virtual windows at the physical install, then boot a virtual version of that installed Windows ...

which is what PilotJLR is getting @ ...
Oh sorry. I didn't know that. See, I learn something new everyday :)

---

### Post by scxtt on 2007-12-07
> **Dr Small said:**
> Oh sorry. I didn't know that. See, I learn something new everyday :)it happens, i sure didn't know about it til i saw it randomly somewhere - probably wouldn't have even thought to do it (don't think i ever will, for @ least 2 reasons :p) ...

---

### Post by Lvcoyote on 2007-12-07
I went ahead and used VMware server, works like a champ.  I appreciate all the help guys....!!

---

### Post by Lvcoyote on 2007-12-08
> **scxtt said:**
> that's not true ... you can create another hw profile in a HDD-installed Windows partition, point the virtual disk for the virtual windows at the physical install, then boot a virtual version of that installed Windows ...

which is what PilotJLR is getting @ ...

Can you be a little more descriptive on how I might accomplish that???

---

### Post by Lvcoyote on 2007-12-08
I got the VMware working fine other than I cant get any sound.  I downloaded the creative drivers but it says it cant find any supported devices....????

---

### Post by scxtt on 2007-12-08
vmware emulates the hardware, so you'd have to get the 2nd-ary hw profile to think there's a creative sound card - don't know if that's possible ...

i've never felt the need to do this myself - i run vmware, but in the traditional way.

---

### Post by Lvcoyote on 2007-12-08
Ok, got the sound working, I just had to add it to the hardware in VMware settings.....

I just have one more problem...

While using WindowsXP inside the VMserver as the guest OS, it will not let me do the windows updates. I get to the windows update site and it appears to be searching for the appropriate updats, then finally I get a screeen saying that windows update can not display the requested page....

Any ideas on this???

---

