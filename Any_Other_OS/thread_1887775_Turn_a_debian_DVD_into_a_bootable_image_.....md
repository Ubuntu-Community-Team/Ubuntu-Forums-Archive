---
title: "Turn a debian DVD into a bootable image ...."
date: 2011-11-27
forum: Any Other OS
---

### Post by abnordude on 2011-11-27
I have a debian DVD with me.....i need to create a bootable image to store in my PC......any methods?

---

### Post by cariboo on 2011-11-28
If the dvd is bootable, all you have to do is create an iso file on your system, use brasero, K3B or from the command line:

```
sudo dd if=/dev/sr0 of=dvd.iso
```

---

### Post by abnordude on 2011-11-29
I tried doing that, but when i tried the image in a virtual machine, it doesnt boot......just a black screen...

---

### Post by dolphin194 on 2011-11-29
> **abnordude said:**
> I tried doing that, but when i tried the image in a virtual machine, it doesnt boot......just a black screen...
What software are you using for your Virtualization?

---

### Post by abnordude on 2011-11-30
> **dolphin194 said:**
> What software are you using for your Virtualization?


I used K3B for image creation..
And Oracle VM Virtual Box for virtualization.

---

### Post by haqking on 2011-11-30
Boot the VM direct from the DVD to see if it is an .iso issue.

Also check your VM machine settings like sata/ide HDD and also graphics settings.

Could be a few things,rule out the .iso first

---

### Post by abnordude on 2011-11-30
> **haqking said:**
> Boot the VM direct from the DVD to see if it is an .iso issue.

Also check your VM machine settings like sata/ide HDD and also graphics settings.

Could be a few things,rule out the .iso first

OKay....I deleted the image file.....am gonna try it again.....

---

### Post by jumpyjester on 2011-11-30
Depending on which version of Vbox you are using, would it not be best to change the virtual drive from the drive image to the actual host drive and just use the DVD. 
 
I use brasero myself for the image creation, hope this helps.
 
Regards,
 
Jumpy

---

