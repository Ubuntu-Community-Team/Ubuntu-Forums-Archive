---
title: "update manager keeps saying install linux-image-2.6.22-14-generic (version 2.6.)"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by neatokino on 2007-12-12
I installed gnome-do this morning and ran some updates, and now I keep getting the following message from update manager:  

linux-image-2.6.22-14-generic (version 2.6.22-14.46.cwi3) will be upgraded to version 2.6.22-14.46.cwi3

but when I click to install the upgrade and then restart, update manager comes back with the same request. 

I removed gnome-do and the repositories needed for it, but the message keeps coming  back from update manager.

How do I make this go away?

I'm on a Macbook Pro Santa Rosa,  Gutsy

---

### Post by spiderbatdad on 2007-12-12
try running```
sudo apt-get dist-upgrade && sudo apt-get update
```

---

### Post by neatokino on 2007-12-12
Thanks, spiderbatdad... unfortunately, the same thing happens after I run that update command in the terminal.

Any other suggestions?

---

### Post by philinux on 2007-12-12
Two things to look through

[http://www.linux.com/articles/48910](http://www.linux.com/articles/48910)

and

[https://help.ubuntu.com/community/AptGetHowto](https://help.ubuntu.com/community/AptGetHowto)

---

### Post by spiderbatdad on 2007-12-12
```
sudo apt-get -f install
```
```
sudo dpkg --configure -a
```

reboot

---

### Post by neatokino on 2007-12-12
Spiderbatdad-- those commands don't help, but thanks again.

Philinux--  I read through those posts and tried a few of the commands, but the update manager still continues to display this message.
 
So, what have I done to my system?????   Everything seems to be working ok, so why can't I just get rid of the 'install linux-image-2.6 22-14...etc'  message?  Is this never going to go away?

Any further help would be appreciated!

---

### Post by philinux on 2007-12-12
Run the update manager and click the 

details arrow. When its done its thing cut and paste the full messages

---

### Post by Seq on 2007-12-12
You are using my ppa for the macbook kernel. (I'm the cwi in cwi3). I am also experiencing this issue, and will be looking at it tonight. I had thought it was due to me having the package available in two repositories (my local one, and the ppa) as this issue only happened once I uploaded to the ppa. If you are also encountering it then I will investigate further, then.

Please note for other folks that the kernel package in question is the current ubuntu kernel, plus some patches to add macbook keyboard and trackpad support (for the new macbook), and omit building rt and xen kernels (they are not really needed for this). I did not do anything particularly funky when making this.

---

### Post by neatokino on 2007-12-12
Philinux:

This is what I get for details from the update manager:

This package contains the Linux kernel image for version 2.6.22 on x86/x86_64.
Also includes the corresponding System.map file, the modules built by the packager, and scripts that try to ensure that the system is not left in an unbootable state after an update.
Supports Generic processors.
Geared toward desktop systems.
You likely do not want to install this package directly. Instead, install the linux-generic meta-package, which will ensure that upgrades work correctly, and that supporting packages are also installed. 


SEQ:

Yes, I am running your kernel patches!  They were the only things I found that would make the trackpad and keyboard work with my Macbook Pro, so thanks for providing them.  Please tell me when you figure out how to fix this error message.   


Thanks!

---

### Post by Seq on 2007-12-12
> **neatokino said:**
> Yes, I am running your kernel patches!  They were the only things I found that would make the trackpad and keyboard work with my Macbook Pro, so thanks for providing them.  Please tell me when you figure out how to fix this error message.

I will update as soon as I figure out what is up.

Glad to hear that it works with the Pro model as well!

---

### Post by Seq on 2007-12-12
Are you also using my packages.cidesign.ca repository?

If I install from my packages.cidesign.ca repo, it works fine. If I install from the ppa, it constantly wants to update to the same version.

The only difference I can find is that for some reason the binary I build is different than the binary built in the PPA (from the same source). Could be different library versions or something, I'm not sure..

---

### Post by neatokino on 2007-12-12
My packages are from the ppa (chrisirwin, right?).... so should I remove the ppa from my repositories and replace it with    packages.cidesign.ca   ... and if so, how do I do that?  
Thanks  in advance!
Michael

---

### Post by Seq on 2007-12-13
> **neatokino said:**
> My packages are from the ppa (chrisirwin, right?).... so should I remove the ppa from my repositories and replace it with    packages.cidesign.ca   ... and if so, how do I do that?  
Thanks  in advance!
Michael

Don't :)

I may upload packages that break to packages.cidesign.ca (for my testing). After I test it, I upload to my PPA. This is because you can't split the PPA into stable or unstable. So I'd much rather figure out why the PPA builds a different kernel package and why it does not work properly..

I can not figure out why it does not work from the PPA. I'll have to go onto IRC and discuss with some devs there.

---

### Post by neatokino on 2007-12-13
Thanks, Seq.... please keep me informed... am standing by!

---

