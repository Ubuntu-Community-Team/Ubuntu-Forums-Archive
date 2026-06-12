---
title: "Where did my hard disk space go?"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by chaplanger on 2007-01-08
I'm not certain what happened but all of a sudden my 80 GB HDD with Ubuntu Linux installed now only has 34 GB left open. ]  (*,) 

One thing has crossed my mind -- that somehow VMWare may have claimed this disk space -- below is my VMWare story:

I have installed VMWare, but WINT 2000 would not install.  However in the process I did try to create a WIN 2000 virtual machine.  This failed.  Thinking I did something wrong in my setup of the VM -- I tried a second install of WIN 2000.  (each of these installs was to set aside 10 GB "as needed" by the VM.  Both Failed and I thought I removed both of these VM installs.  Later, upon reading of a possible work around I sought to reinstall WIN 2000 in VMWare (failed for a thoird tiem with 8GB set aside).  Could this be where my HDD space has leaked too?  If so, is there a way to reclaim this space (short of fa full reinstall of UBUNTU)?

Thanks for any help.

---

### Post by Efwis on 2007-01-08
> **chaplanger said:**
> I'm not certain what happened but all of a sudden my 80 GB HDD with Ubuntu Linux installed now only has 34 GB left open. ]  (*,) 

One thing has crossed my mind -- that somehow VMWare may have claimed this disk space -- below is my VMWare story:

I have installed VMWare, but WINT 2000 would not install.  However in the process I did try to create a WIN 2000 virtual machine.  This failed.  Thinking I did something wrong in my setup of the VM -- I tried a second install of WIN 2000.  (each of these installs was to set aside 10 GB "as needed" by the VM.  Both Failed and I thought I removed both of these VM installs.  Later, upon reading of a possible work around I sought to reinstall WIN 2000 in VMWare (failed for a thoird tiem with 8GB set aside).  Could this be where my HDD space has leaked too?  If so, is there a way to reclaim this space (short of fa full reinstall of UBUNTU)?

Thanks for any help.

have you tried to completely remove VMWare? then gone and looked for all the files that VMware made, It could be as simple as that. Try the following to check:

```
sudo aptitude purge VMWare
```
that should remove all aspects of vmware.  then let us know what happens with your disk space.

---

### Post by jem7v on 2007-01-08
At the least, if you're running 6.10 (Edgy) you could check to see where all your disk space went with the Disk Usage Analyzer (aka baobab if run from the command line).  It should at least help you find the culprit and determine where your space is being eaten up!

---

### Post by chaplanger on 2007-01-09
Jem7v -- using baobab I discovered that 28 GB was being eaten up by VMWare in the three virtual machines I created.  After removing these VMs (which did not work and would not load WIN 2k) I gained those 28 GB back.

Thanks for the tip on the disk usage analyzer.

One of the really wonderful things about Linus (besides the Ubuntu community) is the ease with which one can correct bone-headed mistakes -- my guess is that if this was done in Windows I'd probably be going through Regedit to change some critical files. . .

Also a thank you to Efwis for the clear instructions on deleting VMWare -- maybe one day I'll figure out how to install my WIN virtual machine, so until then I'll probably keep VMWare around. 

Once again -- Thanks!

:D

---

