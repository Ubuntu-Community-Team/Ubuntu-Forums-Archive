---
title: "Mount / unmount"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by Jim_in_Germany on 2008-04-07
Evening all,

I have a Virtual Win XP running in Ubuntu Linux.
The only way to transfer data between it and the host is via usb stick.
When I put my stick into the usb port of my computer, Ubuntu recognises it and mounts it automaticcally.
When I want to use it for the VM XP I have to unmount it (right click - unmount) and then select vm - removeable devices in the virtual machine. 
Then it is mounted in VM and not in ubuntu.
When I have finished with Win XP I remove the stick (also via the gui: vm - removeable devices).
My question:
If I then want to use the stick in ubuntu again, I have to physically remove it and then reinsert it. The ubuntu recognizes it and it's all good.
Is there a shell command which will mount the device without me having to remove and reinsert it?

Thanks in advance
Jim

---

### Post by Berean on 2008-04-07
> **Jim_in_Germany said:**
> Evening all,

I have a Virtual Win XP running in Ubuntu Linux.
The only way to transfer data between it and the host is via usb stick.
When I put my stick into the usb port of my computer, Ubuntu recognises it and mounts it automaticcally.
When I want to use it for the VM XP I have to unmount it (right click - unmount) and then select vm - removeable devices in the virtual machine. 
Then it is mounted in VM and not in ubuntu.
When I have finished with Win XP I remove the stick (also via the gui: vm - removeable devices).
My question:
If I then want to use the stick in ubuntu again, I have to physically remove it and then reinsert it. The ubuntu recognizes it and it's all good.
Is there a shell command which will mount the device without me having to remove and reinsert it?

Thanks in advance
Jim

Jim,

I seem to remember that I had to download the VMware tools (which may be found in the tools tab: I'll check for you) and then I could just copy paste between VMware (XP) and Ubuntu without any problems whatsoever.  However, I personally can't get VMware to recognise my USB despite doing everything that should suggest otherwise.  Try the tools if you haven't already.

Regards,

---

### Post by Berean on 2008-04-07
> **Berean said:**
> Jim,

I seem to remember that I had to download the VMware tools (which may be found in the tools tab: I'll check for you) and then I could just copy paste between VMware (XP) and Ubuntu without any problems whatsoever.  However, I personally can't get VMware to recognise my USB despite doing everything that should suggest otherwise.  Try the tools if you haven't already.

Regards,

Sorry Jim,

I didn't give you all the information.  On my friends VMware I can simply insert the USB in Ubuntu, but it is recognised by XP (in VMware) BECAUSE he downloaded the tools.  Hope this is of help.  Regards,

---

### Post by Jim_in_Germany on 2008-04-07
Hi,

I had the same problem with the recognition of the usb device.
The steps described in this tutorial sorted the problem for me, perhaps they'll work for you:

[http://ubuntuforums.org/showthread.php?t=731001&highlight=usb+vmware#6](http://ubuntuforums.org/showthread.php?t=731001&highlight=usb+vmware#6)

I have the VM tools installed, I'll just power it on to see if I can indeed copy and paste between the two.

Jim

---

### Post by Berean on 2008-04-07
Sorry if I misunderstood the question, Jim, and hope I've not confused you!

---

### Post by Jim_in_Germany on 2008-04-07
Nope, just tried it.
Doesn't work.
Shame :-(

---

### Post by Berean on 2008-04-07
Try Edit>Preferences>input>enable copy paste to and from virtual machine.  If this doesn't work I don't know the answer to copy and pasting between Ubuntu and virtual machine.  I don't know of a terminal line that will mount / unmount your USB, but I'm still looking.

---

### Post by Berean on 2008-04-07
> **Berean said:**
> Try Edit>Preferences>input>enable copy paste to and from virtual machine.  If this doesn't work I don't know the answer to copy and pasting between Ubuntu and virtual machine.  I don't know of a terminal line that will mount / unmount your USB, but I'm still looking.

You'll need to restart VMware before any changes take effect.

---

### Post by Jim_in_Germany on 2008-04-07
Hi Berean,
Still doesn't work I'm afraid. Maybe it's a bug??
Thanks anyway.
Jim

---

### Post by Berean on 2008-04-08
Jim_in_germany,

Sorry, I don't know what else to suggest other than posting in Virtualisation in Other Community Discussions.  Good luck with this, and thanks for the tip on getting the USB recognised in VMware.  Regards,

---

### Post by zvacet on 2008-04-08
> The only way to transfer data between it and the host is via usb stick.

No it is not.Read [this](http://ubuntuforums.org/showthread.php?t=652640&highlight=sharing+files) and you will be able to transfer data from XP to Ubuntu and from Ubuntu to XP.

---

### Post by zvacet on 2008-04-08
> The only way to transfer data between it and the host is via usb stick.

No it is not.Read [this.](http://ubuntuforums.org/showthread.php?t=652640&highlight=sharing+files)

---

### Post by hums07 on 2008-04-08
> **Jim_in_Germany said:**
> 
Is there a shell command which will mount the device without me having to remove and reinsert it?
The usual mount command
```
sudo mount /dev/sdb1 /media/sdb1
```

---

