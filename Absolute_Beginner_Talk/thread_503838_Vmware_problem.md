---
title: "Vmware problem"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by Mekanto on 2007-07-18
I have seem quiet a few tutorials for using vmware to use windows within Ubuntu, 
but i can't understand/get it to work.

Wine doesnt work for some applications.
***1. Does wine work better or worse than Vmware?

I only have Ubuntu on this computer (no duel boot)
***2. Would making a partion for vmware work better?

Ok so I have VMware player which will only open .vmx files.
***3. Where do i get this .vmx file? from converting my winXP CD?

In some tutorials Vmware server was mentioned
***4. Do I need the server or player?

I seem to already have a "windows" folder in my "home folder" but its empty.
 I don't know what im doing at all here could someone help me out?

---

### Post by testube_babies on 2007-07-18
> **Mekanto said:**
> I have seem quiet a few tutorials for using vmware to use windows within Ubuntu, 
but i can't understand/get it to work.

Wine doesnt work for some applications.
***1. Does wine work better or worse than Vmware?

I only have Ubuntu on this computer (no duel boot)
***2. Would making a partion for vmware work better?

Ok so I have VMware player which will only open .vmx files.
***3. Where do i get this .vmx file? from converting my winXP CD?

In some tutorials Vmware server was mentioned
***4. Do I need the server or player?

I seem to already have a "windows" folder in my "home folder" but its empty.
 I don't know what im doing at all here could someone help me out?

1)  Wine only runs certain programs, whereas VMware runs the whole OS.  Wine will have better performance, but not every app will work with wine.

2)  No, you don't have to worry about partitions with VMware; it creates virtual hard drives as files.

3 + 4)  You have to make your own vmx if you want to use Windows, which has to be done with VMware Server, not Player.  Once you install VMware Server, it should be pretty self-explanatory to use.

---

### Post by wormser on 2007-07-18
Wine doesnt work for some applications.
***1. Does wine work better or worse than Vmware?
[I]
It depends on what you are trying to run.[/I]

I only have Ubuntu on this computer (no duel boot)
***2. Would making a partion for vmware work better?

*VMware runs in your OS (Ubuntu) so there is no need for a new partition.*

Ok so I have VMware player which will only open .vmx files.
***3. Where do i get this .vmx file? from converting my winXP CD?

*The VMware site has .vmx files you can download.  They do not have them for Windows since it is not free and you need a license.  VMware Server can create .vmx files.  Just create a new VM in VMware server and go into properties and change the CD to use the host and it will boot the install CD when you start the VM.*

In some tutorials Vmware server was mentioned
***4. Do I need the server or player?
[I]
Server will allow you to create new VMs (.vmx).[/I]

---

### Post by desicratn on 2007-07-18
It sounds like you installed the Vmware Player. try installing the VMwware SERVER. Im at work so I dont have the link in front of me but if you search my posts i think I posted a link to a tutorial in regards to VMware Server before. Also it is in Automatix as well but I have not tried it, but I assume it would work as well.

I have the server set up and it works great. Just no 3D acceleration. Just throw in  your windows CD and it creates the imageand off you go, no need to partition it just creates a file that  VMware sees as a windows drive. I use it for the 1 or 2 programs I havent figured out how to use in Wine or a Linux version yet.

Good Luck and please ask questions if you need more help.

---

### Post by b20963a2 on 2007-07-18
[How to install Vmware server From Canonical commercial repository in Ubuntu Feisty]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html")

You can download some vritual machines [here]("http://www.vmware.com/vmtn/appliances/directory/"), but not windows ones (because of licensing).

---

