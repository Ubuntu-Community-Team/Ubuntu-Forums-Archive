---
title: "How to setup virtual box in ubuntu 7.10 gutsy i386"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by famous3warriors on 2008-01-16
Ok I am a new and I would like to know how to install and use virtual box for the windows application.  I have some programs like cs2 and autocad programs that I need to run.  I do have inkscape, gimp, agave, blender and they work great.  I just haven't found a program that can change dwg files to eps yet.  Please Help.  Thanks I really do appreciate it.:guitar:

---

### Post by p_quarles on 2008-01-16
If you're using the latest version of Ubuntu (7.10) you can install VirtualBox OSE from the package manager. Open Synaptic and search, or run the command:
```
sudo apt-get install virtualbox
```
That's the first step. Once you get that installed, you'll need to make a new virtual machine and install Windows on it like you would on a real computer.

---

### Post by famous3warriors on 2008-01-16
ok cool thanks I give that a try I appreciate it.

---

### Post by matvrix on 2008-01-16
I don't mean to hijack - I'm at a point where I have a new vdi and I'm looking to install XP - SP2 using the "Reinstallation CD" that comes with Dell. Upon initializing the XP Professional Set Up, it is expecting me the format the "c:" drive. Since, this is a dual-boot system am tad worried as to how and where I should install the virtual OS.

Attach are some screen shots of my predicament.

---

### Post by p_quarles on 2008-01-16
> **matvrix said:**
> I don't mean to hijack - I'm at a point where I have a new vdi and I'm looking to install XP - SP2 using the "Reinstallation CD" that comes with Dell. Upon initializing the XP Professional Set Up, it is expecting me the format the "c:" drive. Since, this is a dual-boot system am tad worried as to how and where I should install the virtual OS.

Attach are some screen shots of my predicament.
Hmm. I'm assuming you specified "Windows XP" when Virtualbox asked what kind of OS you were installing, correct? If so, it should set up the VDI as an empty, unformatted partition. 

In any case, a virtual hard drive is essentially just an empty file, so don't be scared of "deleting" the existing partition. That is, unless you're using an existing NTFS hard drive partition as the VDI -- if that's the case, then you're definitely going about this the wrong way.

---

### Post by matvrix on 2008-01-17
When it presented me with c drive jut wanted to make sure that I wasn't anhiliating the ntfs partition.

Well, I got it installed and XP is up and running.


Cheers,
John

---

