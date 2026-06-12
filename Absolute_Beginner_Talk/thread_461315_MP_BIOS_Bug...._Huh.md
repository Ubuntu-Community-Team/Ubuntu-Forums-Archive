---
title: "MP BIOS Bug....???? Huh ??????"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by mike23 on 2007-06-01
Hey all just installed 6.06 (dual boot XP). Allthough i have used and installed ubuntu last december with no problems with installation, this time i came across something weird for me. Everything installed properly, duallboot screen appears and everything, but when i load ubuntu i get this:

....Uncompressing Linux, OK.......
.....MP BIOS bug:8254 timer not connected to IO-APIC
.....Kernel Panic - not syncing: IO-APIC + timer doesnt work!....
......bla bla bla..........

Unlike kernel, im not panicing coz i know u guys can help me fix this :):)
Probably something i did wrong due to NO experience LOL :)

Thanx !!!!

---

### Post by greenstar on 2007-06-01
I recently had this same problem with a new motherboard I had just built a Athlon X2 Dual core system around. It was a Biostar mobo. I'm through with Biostar because I've had 5 defective mobos over 2 different models from them since Feb. The problem was a defective mobo in my case, but you may be experiencing something with a different cause. Fwiw, the BIOS was junk on that board. I went into the BIOS and disabled APIC to no avail.

Good luck. HTH
Greenstar

---

### Post by nickpaton on 2007-06-01
Hi Mike

I believe you need to disable apic via your grub menu.

The problem I have is I don't know how to access grub from recovery mode!

To access grub menu in normal mode paste the command below into a terminal:

```
gksudo gedit /boot/grub/menu.lst
```

Find the section similar to this (this is from feisty - yours is slightly different):

> ## ## End Default Options ##

title		Ubuntu, kernel 2.6.20-16-generic
root		(hd0,5)
kernel		/boot/vmlinuz-2.6.20-16-generic root=UUID=49bfa7bc-de95-4593-8ee0-69f6ac5a234c ro quiet splash
initrd		/boot/initrd.img-2.6.20-16-generic
quiet
savedefault

and at the end of the quiet splash add (without "") "noapic".

Save and restart.

When someone else tells us how to get into grub from recovery mode, try this.

For more information on apic see [this]("http://ubuntuforums.org/showthread.php?t=228499").

Alternatively, you could try a reinstall.  When you get to the inital selection screen select F6 and add "noapic" (no "") to the end to the command line and continue on from there.

---

### Post by nickpaton on 2007-06-01
To amend your grub menu from recovery mode:

Select 6.06 Recovery from start up menu.

When it eventually ends up at the root prompt type:

```
sudo nano /boot/grub/menu.lst
```

This opens your grub menu list in a terminal like window.

Scroll down to the kernel options section which will look similar to the one in my last post.

To the end of line 

```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=49bfa7bc-de95-4593-8ee0-69f6ac5a234c ro quiet splash
``` 

add noapic, so that it now looks like this:

```
kernel /boot/vmlinuz-2.6.20-16-generic root=UUID=49bfa7bc-de95-4593-8ee0-69f6ac5a234c ro quiet splash noapic
```

Ctrl x to save, y (for yes to save changes), enter key to exit grub menu list .

When back at root type:

```
exit
```

and enter key

Should hopefully boot into Ubunutu.

---

### Post by mike23 on 2007-06-01
the thing is that last december when i installed ubuntu on my pc i didint have this problem...!! anyways ill try what u told me :)

greenstar: its an asus motherboard..:(

---

### Post by greenstar on 2007-06-04
> **mike23 said:**
> greenstar: its an asus motherboard..:(

Well, at least you had the good sense to buy Asus. Stay away from Biostar. I was building a couple of budget rigs and found out the hard way about Biostar quality control... it doesn't exist. My experiences with Asus are top-notch. Good luck.

Greenstar

---

