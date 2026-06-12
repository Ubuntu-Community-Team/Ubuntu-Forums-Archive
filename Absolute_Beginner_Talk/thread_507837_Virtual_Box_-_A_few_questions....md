---
title: "Virtual Box - A few questions..."
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by ryanVickers on 2007-07-23
I am using Virtual Box (as said in the title) and have a few questions.  Everything is working great, it has basically 100% performance of a native OS, but there is 2 things I would like to ask:

1. In my win XP virtual machine, how would I setup a folder that I can use to exchange files between the VM and Ubuntu? (networking required == false or true ok with me!)

2. Does anyone know how to make a VM running Mac OS X to work using virtual box or something else?  I know they are usually not able to run on anything except a actuall mac computer, but I got a new regular computer much newer than the mac I had and want to get it going!  To cut to the chase, my theory is that since the  virtual box handles all the hardware interactions, it should work, right?  I know this is true for my windows VM because a real installation on my particular setup will not work without a 3rd party driver, but the VM runs fine with nothing!
I've looked around and found nothing really that will run OS X on linux, so what's up with that? :confused: Does anyone know a way?

---

### Post by dca on 2007-07-23
I generally have Samba installed on the Linux host, then when MSWinXP opened in VM, 'right-click' on 'My Computer, select 'Map Network Drive' and put in the IP and path of Samba share on Linux host...

---

### Post by aks44 on 2007-07-23
1. No need to use a Samba network, VirtualBox is way smarter than that... Select the VM, menu Machine -> Preferences -> Shared Folders. Mouse over the listbox in the right pane and read the instructions ;) You will have to install the VirtualBox tools in the guest OS (XP for instance), this option is available in some menu when the VM is up and running and XP is booted.

2. I guess you'll have to tinker with Mac OS X. I know it is possible to make it run on any hardware, but I have no idea how exactly. The thing is, VirtualBox exposes a virtual hardware to the guest OS, that's why you don't need specific third-party drivers for XP. But installing the VirtualBox tools in XP will install anyway some drivers that better fit the virtual hardware than Microsoft's generic drivers. The same applies to Mac OS X, but it seems that VirtualBox doesn't have drivers for it so you'll have to use Apple's generic ones when (if) you manage to install OS X despite the hardware lock-in.

---

### Post by ryanVickers on 2007-07-23
> Mouse over the listbox in the right pane and read the instructions :wink:
I would have figured that out if they made any sense!  It seems like such an easy to use product except for this feature!  So lets say I have a VM named "vmxp" and a shared folder on ubuntu at "/home/shared" and I wanted to be able to get files out of (and possibly into) the VM.  how **exactly** would I do this? :)

---

### Post by aks44 on 2007-07-23
> **ryanVickers said:**
> I would have figured that out if they made any sense!

Sorry, I assumed you just overlooked that...

> **ryanVickers said:**
> ISo lets say I have a VM named "vmxp" and a shared folder on ubuntu at "/home/shared" and I wanted to be able to get files out of (and possibly into) the VM.  how **exactly** would I do this? :)

The two fields when you create a shared folder under the VM's preferences are :
- Folder path = path to the shared folder on the host OS (ie your Ubuntu)
- Folder name = name of the shared folder as it will appear to the guest OS. In XP's case, it will be presented to XP as a Samba share, even though you don't have to use Samba on the host side.

Let's assume the folder *name* is UbuntuShare in this case.

1. Boot your VM, wait for XP to be fully loaded, then install VirtualBox tools (in the "Devices"? menu, last item "Install client tools"? - not sure about the exact names as my VBox installation is in french).

2. Once it's done, open the Explorer, menu "Tools", item "Connect a network disk"? (again, my XP install is in french so I'm not sure of the exact name).

3. Use \\vboxsvr\UbuntuShare as the remote folder name, and you're done.

---

### Post by ryanVickers on 2007-07-23
Wow, thanks alot!  By the way, if you care, it's Map Network Drive and Install Guest Additions.

For anyone else reading this, I'm still interested in the Mac problem...

---

### Post by aks44 on 2007-07-23
> **ryanVickers said:**
> By the way, if you care, it's Map Network Drive and Install Guest Additions.

Good to know, I'll try to remember that ;)

---

