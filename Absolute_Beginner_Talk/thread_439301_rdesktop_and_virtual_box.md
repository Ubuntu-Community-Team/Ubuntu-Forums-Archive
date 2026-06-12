---
title: "rdesktop and virtual box"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by thecomputingexpert on 2007-05-10
Hi there,
I have been running Windows XP in Virtual Box since installing Ubuntu. I have seen a lot of mention on rdesktop and terminal services which allow me to run windows programs on linux without having to boot up XP in the virtual machine, could anyone give me any assistance on how i can set this up, thankyou

Simon North

---

### Post by dca on 2007-05-10
Asides from using something like  WINE  ([http://www.winehq.org](http://www.winehq.org))  and seeing if the app works?

---

### Post by mazirian on 2007-05-10
I might be missing something here, but all rdesktop allows you to do, I think, Is connect to running server through the terminal services, er, service.  If you are trying to run certain windows apps under linux you may want to look at emulating them in wine.  If you are tyring to run a virtual machine running windows, you may want to look at vmware or the like.

---

### Post by dca on 2007-05-10
The only other thing I've used rdesktop or anything like that is:
 
*long story short*
 
We got this server w/ multiple processors performing secure FTP & Samba, etc.  A utility server per se...  The sales team got this high-speed app that they now want to share data or in other words store the data files in one location and multiple clients be able to access it instead of having it spread on multiple workstations.  Well, someone decided to only buy the client edition of the app because (price) the server install license plus client install license(S) would be out of the question.  In the meatime while they scrape up enough cash to buy into this solution, all the data files were migrated from the client workstations into the big box (Linux) which already had Windows w/ VMWare.  With the VMWare up, the clients running XP have a shortcut on their desktops w/ a preconfig remote desktop (includes IP/hostname, other connection info) icon that connects them to the server.  After clicking on it, remote desktop allows them to look at the VMWare'd Windows desktop on the server.
 
I know I'm probably off base, I just like telling stories...

---

### Post by Term1n4l on 2007-05-10
I am currently looking at doing the same thing, and this is where I found almost all the answers I needed...
[https://help.ubuntu.com/community/SeamlessVirtualization](https://help.ubuntu.com/community/SeamlessVirtualization)

When I run it with my rdesktop line as root:

rdesktop -rsound -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Windows\explorer.exe" localhost:3389 -u "admin" -p "password"

and receive......

Autoselected keyboard map en-us
ERROR: Failed to open display:

So far, I have another post regarding this on an old thread, but no responses yet... If anyone can help it would be greatly appreciated.

---

### Post by dca on 2007-05-10
Uh, hmmm, okay than I am off-base...

---

### Post by Term1n4l on 2007-05-11
I am still hitting a brick wall with this. I don't really know what other information is needed to help find the solution to this problem. I can give my computer specs and everything, but I don't see that helping. 

I have tried everything from notepad to cmd.exe and every one comes with the same error.

Has anyone else had this problem?

---

### Post by lazyart on 2007-05-11
According to the instructions, you should be entering an IP address for your Virtual Box ie. "192.168.0.xx:3389" and not "localhost:3389"

> rdesktop -A -s "c:\seamlessrdp\seamlessrdpshell.exe C:\Program Files\Internet Explorer\iexplore.exe" <IP of VM>:3389 -u administrator -p password
For QEmu, use 'localhost' for <IP of VM>. For VMWare and for VirtualBox, use the IP address noted down earlier. 

---

### Post by Term1n4l on 2007-05-11
I am currently using Qemu instead of VMware.
The instructions for Qemu is to use localhost instead of the IP of the Virtual Machine. I'll give it a try though.

I tried using the IP of the VM instead of using localhost and there is no change. the output is the same :-? 

Autoselected keyboard map en-us
ERROR: Failed to open display:

EDIT:
I was able to get it working. If you log into the VM then log out, leaving it open, you can then use the seamless virtualization. It doesn't work that well, and the only way to open more than one program you need to run CMD then open the others from there.

---

