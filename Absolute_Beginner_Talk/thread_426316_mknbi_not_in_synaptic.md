---
title: "mknbi not in synaptic"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by no.t on 2007-04-28
Is mknbi package missing in feisty?  I can't find it in synaptic. 

I try to make a kernel image for pxeboot (for diskless box). 
Where I am now:  I set up dhcp, tftp. I copied the "pxelinux.0" and "linux" kernel file to my /var/lib/tftpboot. I made a "default" file in /var/lib/tftpboot/pxelinux.cfg.
Diskless client contacts dhcp, successfully loads "pxelinux.0", then kernel, but it stops with "unable to mount root filesystem".  I think the next thing is mounting ramdisk as root filesystem, but I have to make a new kernel and ramdisk image. This should be done by mknbi.  Am I right?
(I am not absolute beginner: I am on linux for over 8 hours!! :))
Thanks,  Novak Tamas

---

### Post by Seisen on 2007-04-28
I did a package search for mknbi and its in their. I attached the package for you just double click on it and it should install.

---

### Post by no.t on 2007-04-28
> **Seisen said:**
> I did a package search for mknbi and its in their. I attached the package for you just double click on it and it should install.

Search?  I open Synaptic, on left panel I select "All", then the right main panel shows an alphabetic list. 
 "mknbi" should be between "mklibs-copy" and "mknfonts.tool", but I can't see that. I even tried to search (with top right icon), but found no "mknbi". How could you find it? 
Otherwise I just try the link -thank you.

---

### Post by no.t on 2007-04-28
> **Seisen said:**
> I did a package search for mknbi and its in their. I attached the package for you just double click on it and it should install.

I tried the file, but i am on "amd64" architecture, and I got an error "wrong architecture i386". Maybe I need another file on  64bit box and 64bit Linux, and that file is missing (yet)?

---

