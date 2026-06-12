---
title: "(initramfs) - Xubuntu doesn't install -DESPERATE!"
date: 2007-11-22
forum: Absolute Beginner Talk
---

### Post by verraeter on 2007-11-22
Hello,

After unsuccessful install of ubuntu I tried Xubuntu hoping it would work my old laptop.

I burned the disc, copied the check sum and compared it, but when trying to install it comes up with the following message:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7)
Built-in shell (ash)
Enter 'help' for a list of built in commands
(initramfs)_

I found a thread with the same message

> **chillifrost said:**
> Hi there,

I looked up what initramfs does here:[http://linuxdevices.com/articles/AT4017834659.html](http://linuxdevices.com/articles/AT4017834659.html)

Then I poked around with commands in the initramfs shell. I saw that the directory called 'cdrom' in the OS ubuntu install booted into was empty. So I figured that it wasn't finding the "root". So the next time I booted from the Live CD, I specified an additional boot option (by pressing F6 when the ubuntu install menu comes up; each item in the install menu has a different set of options. You want to add in the options line for the install option) root=/dev/cdrom and hit install.  

Viola!

I am writing from my newly installed Ubuntu. Hope this helps someone.

Chill.

I have done that, now I have the following error:

[  392.462006] SQASHFS error: Unable to read page, block ca1ca68, size 3c6a

etc. etc. Now the entire screen if filled with these messages...

Help, please!

Kai

Toshiba Satellite 1620 with 40GB Hard Drive and 160MB Ram, System memory 640KB

---

### Post by overdrank on 2007-11-22
Hi and the live cd requires 256mb ram you may try and install with the alternate cd found here
[http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimage.ubuntu.com/xubuntu/releases/feisty/release/)
And yes that is Feisty, Gusty Xubuntu seems to be a little resource hungry. :)

---

### Post by verraeter on 2007-11-22
I changed from Ubuntu to Xubuntu because some one in the forum said it might require less memory. I have tried Mandriva which apparently requires 256MB of RAM , but that installed ok, it ran slowly and I didn't like its interface.
I will try this and most certainly report back!

Thank you,
Kai

---

