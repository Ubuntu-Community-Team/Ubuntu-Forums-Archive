---
title: "ubuntu emulator for windows"
date: 2006-09-20
forum: Absolute Beginner Talk
---

### Post by mozkaynak on 2006-09-20
Hi,
Because of my job, I have to use 5-6 computers and only two of them have ubuntu the rest have to be windows or Mac. I try to learn phyton as programming language and scripting as kind of hobby and I am wondering whether there is a Ubuntu emulator that I can install to Windows machines. So far, I have been using Live CD when I wanna use Ubuntu on my Windows machine and this works fine however an emulator would be more convenient for me.
Any idea? Thanks...

---

### Post by hkgonra on 2006-09-20
Couldn't you run it in VMware?

---

### Post by mozkaynak on 2006-09-20
I think VMware runs in Ubuntu to use Windows. is the other way also correct? I am just wondering. Thanks...

---

### Post by Jose Catre-Vandis on 2006-09-20
Suggest you go for the free VMware Server. Installation on windows fights you harder than on Linux beleive it or not, and you need IIS installed, but it does the job. Less tricky than vmware player in terms of setting up and running/reconfiguring vms, IMHO :D

---

### Post by davec64 on 2006-09-20
Yep,

If you go to the VMWare site, you can download VMPlayer.
This allows you you run any OS Image in Windows.

If you have a look on the site you should be able to find some links to images of OS's which you can download and open with VM PLayer. 

Chances are, that someone has already created a Ubuntu image!!

If not you'll have to download an application to create it. 
VMWare do Workstation but you have to pay for it but there are free ones around.

---

### Post by alman15 on 2008-05-24
is there any way of running it without VMware ? :confused:

---

### Post by werries on 2008-05-25
vmware basically IS an emulator for any OS. 

another option is to install the essential parts to your computer in order to use python or scripting on windows. i have no experience with that though, as i dont use windows for my programming anymore.

Python installer for windows: [http://www.python.org/download/windows/](http://www.python.org/download/windows/)

---

### Post by alman15 on 2008-05-25
[SIZE="6"]I use vista:([/SIZE]

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **alman15 said:**
> [SIZE="6"]I use vista:([/SIZE]

**USE 32-bit compability mode while installing ur Program** in Vista, in case it doesn't get installed directly.:)

---

### Post by Sammi on 2008-06-25
> **alman15 said:**
> is there any way of running it without VMware ? :confused:
Yeah just use Virtualbox instead. It's open source and very easy to use :D

[http://www.virtualbox.org/](http://www.virtualbox.org/)

---

### Post by flaggh on 2008-06-25
If you're just using it for scripting and stuff, I think cygwin would work.  Probably better and less resource intensive than installing a virtual machine unless you are looking to run X apps.

---

### Post by joshdudeha on 2008-06-25
Couldn't you use Wubi? The one that comes with Hardy.
Would be easier I would have thought?

---

### Post by Canis familiaris on 2008-06-25
> **Sammi said:**
> Yeah just use Virtualbox instead. It's open source and very easy to use :D

[http://www.virtualbox.org/](http://www.virtualbox.org/)

I really dunno.
Virtualbox in Ubuntu rocks but The Windows version of Virtualbox did not really work though for me. It maybe an atypical case as well.

---

### Post by Canis familiaris on 2008-06-25
> **joshdudeha said:**
> Couldn't you use Wubi? The one that comes with Hardy.
Would be easier I would have thought?

I guess he wants to simultaneously run Linux programs with Windows ones.

---

### Post by lswest on 2008-06-25
Also, WuBI actually installs Ubuntu, into Windows, yes, but it requires a reboot to actually use the system, probably not what the OP is after.

I find VirtualBox works great for me in Windows.  However, give cygwin a try, I've used it before, offers a good range of things to employ (all terminal-based though).  Cygwin offers python compilers, and the python CLI system that Ubuntu uses.

---

### Post by DrMega on 2008-06-25
> **mozkaynak said:**
> Hi,
Because of my job, I have to use 5-6 computers and only two of them have ubuntu the rest have to be windows or Mac. I try to learn phyton as programming language and scripting as kind of hobby and I am wondering whether there is a Ubuntu emulator that I can install to Windows machines. So far, I have been using Live CD when I wanna use Ubuntu on my Windows machine and this works fine however an emulator would be more convenient for me.
Any idea? Thanks...

There are a number of options available to you, without killing Windows.

Firstly, you can install Ubuntu as dual boot with Windows. Your Windows installation won't be harmed as long as you go with the default options in the Ubuntu setup wizard.

Also, I believe you can use Python with Windows. If it is for web stuff, get Apache (which is available for Windows) and I believe you can configure that to link to various interpreters.

Then of course, as others have said, you can run Ubuntu in a virtual machine.

---

