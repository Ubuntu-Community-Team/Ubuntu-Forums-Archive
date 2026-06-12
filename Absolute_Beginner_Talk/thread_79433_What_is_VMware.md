---
title: "What is VMware"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by chrisblack on 2005-10-20
I've read on the frontpage about vmware free player... however I'm confused what vmware actually is and what a virtual machine is....

Can anyone either explain this, or point me in the direction of a site that does this in plain english.

Thanks

Chris

---

### Post by heimo on 2005-10-20
I'll give couple links (can't explain it myself in English):
[http://en.wikipedia.org/wiki/Virtualization](http://en.wikipedia.org/wiki/Virtualization)
[http://www.vmware.com/virtualization/](http://www.vmware.com/virtualization/)

:)

---

### Post by chrisblack on 2005-10-20
That is still as clear as mud.... put more simply, if i install vmware on either my windoze or ubuntu drive, what can i do????

Thanks

Chris

---

### Post by jbinc1 on 2005-10-20
VMware Workstation is powerful desktop virtualization software 								for software developers, software testers, and enterprise IT professionals. 								Workstation allows users to run multiple x86-based operating systems, 								including Windows, Linux, NetWare, and Solaris x86, and their applications 								simultaneously on a single PC in fully networked, portable virtual 								machines — no rebooting or hard drive partitioning required.(Taken from the VMware web site)

Read all about it here [http://www.vmware.com/products/ws/](http://www.vmware.com/products/ws/)

This is great software. I use it all of the time on my Windoze laptop to test different Linux distros.

---

### Post by chrisblack on 2005-10-20
so does this mean that if I install vmware player, that I can run/test linux distros direct from the cd, whether they are a live cd or not.... or do I have to do a HD install of the distro..... or are there only certain distro's available for vmware?

Thanks

Chris

---

### Post by jbinc1 on 2005-10-20
VMware Player is a free desktop application that lets you run a virtual machine on a Windows or Linux PC. VMware Player provides an intuitive user interface for running preconfigured virtual machines created with VMware Workstation, GSX Server, and ESX Server. On Windows hosts, the player also opens and plays Microsoft Virtual PC and Virtual Server virtual machines and Symantec LiveState Recovery system images. VMware Player makes your VMware virtual machines accessible to colleagues, partners, customers, and clients who do not own VMware products.

You would have to own the VMware Workstation software to actually do set up any virtual machines.

VMware only supports certain distros of Linux. I know that there are more distros that will work though. I have Kubuntu Breezy running right now.

---

### Post by pksings on 2005-10-20
VMware actually "boots" and runs an independent "PC instance" in a window. This window can be maximized to full screen or stay at whatever resolution(s) the host Operating System supports. This instance can be almost any x86 operating system. The "supported" ones have a matching version of "VMtools" which install virtual ethernet drivers, Display drivers and make the mouse and keyboard work smoothly between the virtual machines and host Operating System. I've never tried a non-supported one so I have no idea how they work.

VMware is proprietary expensive software. It works great. I use it to run Quicken to manage some finances.  There are other ways to run Windows programs, Win4Lin, which requires a kernel module, which for me was to big a pain to keep up, I kept not being able to get the module for the kernel I was running. This probably isn't as big a deal now as it was five years ago when the kernel was changing more rapidly. Win4Lin will run only Windows 95, 98 or ME.  The same company has now come out with Win4Lin Pro, which does not require a kernel module.  It runs Win2K and XP. Works okay, has blown up a few times during use. And was difficult to install at first. The latest version has a better installer. The newsgroups seem to show that XP support is less than stellar. Still, it's less than half the price of VMware.  Crossover Office is still around but was a dumb idea to start with and still is.

I highly recommend VMware workstation. Rock solid as long as you have more than 512 MB of RAM.  

VMware is RAM greedy. Win4Lin Pro

---

### Post by chrisblack on 2005-10-21
Thanks for the info...

What I get so far is that if I have vmware player installed, my pc will boot into vmware (rather than ubuntu), and from here I can run various supported OS's??  These OS's installed onto hard drive or from CD???

Chris

sorry for all the questions, but I want to know what to expect if I install vmware player... I don't want to find I can't boot into anything...

---

### Post by wishyjr on 2005-10-21
when your using VMware, it creates a file on your hard drive that represents a 'vitural drive' used by which ever vitual operating system your running. 

For instance, i run VMware as a program in ubuntu, its starts with a main menu type thing with an option to start a virtual version of XP -this runs in a window itself on my ubuntu desktop.

when i setup my virual XP system VMware asked me to create a file which it would use. This involved putting the file somewhere (i.e. /home) and assigning it a size (i.e. mine is about 3Gb).  So in my home directory i have a 3Gb file which is only used by my virtual XP when i run VMware

you see? :)

---

