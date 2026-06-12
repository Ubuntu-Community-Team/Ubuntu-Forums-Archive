---
title: "gedit of grub menu.lst"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by fxyefx on 2008-03-07
I'm using xubuntu on an older laptop, running hardy alpha 5 (with all the updates that come up in the manager thus far installed).  Of course, with all the constant updating that's taking place, my grub boot menu is now populated with a bajillion different kernel options.  I wanted to get rid of the older ones using

gksudo gedit /boot/grub/menu.lst

but the terminal just moves on to the next $ line as though it worked, but no text editor opens up!!  This has never happened to me before - how can I get the text editor to open up with the terminal command in xubuntu?  Is this a problem specific to xubuntu? :confused:

Thanks!!

---

### Post by forestpixie on 2008-03-07
if you've not installed gedit - try using mousepad - I think - have a look and see what text editor it has

or use nano in the terminal, Ctrl+O to save, Ctrl+X to exit

---

### Post by steveneddy on 2008-03-07
```
sudo apt-get install gedit
```

---

### Post by fxyefx on 2008-03-07
Ahh thanks for the fast response; I hadn't realized that gedit was its own package... thought it was some kinda command built into linux!

---

### Post by steveneddy on 2008-03-07
> **fxyefx said:**
> Ahh thanks for the fast response; I hadn't realized that gedit was its own package... thought it was some kinda command built into linux!

It is, if you install it first.

Linux is the kernel, or the insides, the rest is just multiple applications that talk to the kernel.

The kernel talks to the hardware.

---

### Post by stchman on 2008-03-07
> **fxyefx said:**
> I'm using xubuntu on an older laptop, running hardy alpha 5 (with all the updates that come up in the manager thus far installed).  Of course, with all the constant updating that's taking place, my grub boot menu is now populated with a bajillion different kernel options.  I wanted to get rid of the older ones using

gksudo gedit /boot/grub/menu.lst

but the terminal just moves on to the next $ line as though it worked, but no text editor opens up!!  This has never happened to me before - how can I get the text editor to open up with the terminal command in xubuntu?  Is this a problem specific to xubuntu? :confused:

Thanks!!

Remove the kernels via Synaptic and the menu entries will disappear.

---

