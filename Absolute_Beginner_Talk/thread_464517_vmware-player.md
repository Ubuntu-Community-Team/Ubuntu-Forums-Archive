---
title: "vmware-player"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-06-04
What exactly is vmware-player?  I assume it is some sort of  'virtual machine'.  I've seen some YouTube demos but not sure if it is something that is useful.

Does vmware-player allow one to run say Windows XP applications in a window?  If so, how does wine and CrossOver compare?

Thanks

Carl

---

### Post by mojo123 on 2007-06-04
VMware is a virtual machine like you said, you could run another os on it not just a application
I wouldnt say vmware is a good way to subsitute.
After all rule #1 is
Linux isnt windows

---

### Post by cwmoser on 2007-06-04
What can one do with vmware-player?  Is it practical or more so some proof of concept?

In other words, can vmware be used to run Windows XP in a window and be able to install software like one would do with a real Windows XP PC?

Carl

---

### Post by RedRover1 on 2007-06-04
It is very practical.  I use it currently to run Ubuntu as a virtual machine running XP as a host.  In the future I hope to reverse that and run Ubuntu as the host and XP as the guest.

Good link that explains alot.  If you don't use a pre made virtual machine it may be easier to start with VMServer.

[https://help.ubuntu.com/community/VMware?action=show&redirect=InstallingVMware](https://help.ubuntu.com/community/VMware?action=show&redirect=InstallingVMware)

---

### Post by cwmoser on 2007-06-05
What then are the pros and cons of Wine and CrossOver versus vmplayer?

I currently have CrossOver and wine and wonder if vmplayer is a better player of Windows programs.

Carl

---

### Post by lazyart on 2007-06-05
Wine/Crossover will run quite a bit of stuff without installing WIndows.

VMware server will let you create an virtual computer inside of your operating system and you can install Windows there and get near 100% compatibility (it doesn't do 3D well).  It's handy if you just gotta have something.  Quite frankly dual booting gets old, especially if there are only a couple things you need.

The price is that there is a performance hit as you are using your system resources to run two machines at once-- so you'll want a decent processor and plenty of RAM to pull it off.  But we've reached a point with technology that it's quite affordable.  With a 2 ghz P4 and 1.5 gb ram I ran two virtual machines inside my linux installation.  And now I just upgraded to 4 ghz. :D

vmplayer will "play" previously created virtual machines.

---

### Post by cwmoser on 2007-06-05
How do I get started with VMPlayer?  Say I want to install VMPlayer on my Ubuntu installation with the intent of running Windows XP in a window so I can run Quicken and Quick Books?  Do I use a Windows XP installation CDROM to get XP loaded?

Thanks for the insight.

Carl

---

### Post by MxGB on 2007-06-06
If you can install the vmware-player and you can load the app from your menu (it's in System Tools) you're well on your way. Next to go [www.easyvmx.com/easyvmx.shtml]("http://www.easyvmx.com/easyvmx.shtml") to configure and create a virtual machine. When you are configuring network devices you will probably want to use a bridged connection which will "join" the VM with your real network (be it wired or wireless). If you use dialup or a USB modem you might have to use the NAT network type to create an internal emulated network. You'll need your XP cd or an ISO image of an XP install cd to install Windows, choose your CD drive options accordingly. You end up with a zip file containing the necessary files. Download it and extract it to your home directory and point VMware player at the vmx file in that directory. Without a bootable OS on your new virtual machine Vmware will try to boot from it's emulated CD drive, which will either be linked to your real CD drive or to a bootable iso file. You can then install Windows just as with a real PC install.

---

