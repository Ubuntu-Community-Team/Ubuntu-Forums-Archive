---
title: "refit issue"
date: 2009-04-05
forum: Apple Hardware Users
---

### Post by norma on 2009-04-05
Having some issues regarding a refit install.

What I've done: downloaded the refit iso on my linux system, burned the rEFIt.cdr as an image to a cd-R disk. When I attempt to boot with the rEFIt cd I get the flashing gray screen with the question mark folder. I can't open it on my desktop.

Problem: I have installed linux prior attempting to install rEFIt. My buddy and I installed it the same way he installed it on his new PC - which turned out to be a bad idea on our part. Anyway we didn't partition correctly for one, so I am unable to boot without the live CD in the disk drive. 

Any suggestions?

Thanks,

-Norman

---

### Post by pxwpxw on 2009-04-05
> **norma said:**
> Having some issues regarding a refit install.

What I've done: downloaded the refit iso on my linux system, burned the rEFIt.cdr as an image to a cd-R disk. When I attempt to boot with the rEFIt cd I get the flashing gray screen with the question mark folder. I can't open it on my desktop.

Problem: I have installed linux prior attempting to install rEFIt. My buddy and I installed it the same way he installed it on his new PC - which turned out to be a bad idea on our part. Anyway we didn't partition correctly for one, so I am unable to boot without the live CD in the disk drive. 

Any suggestions?

Thanks,

-Norman

 You can download a linux refit package and run gptsync from ubuntu desktop to update the MBR. (Dont think the package is available for amd64, only i386)
```

sudo apt-get update
sudo apt-get install refit
sudo gptsync /dev/sda

```
(might not be /dev/sda)

---

### Post by cyberdork33 on 2009-04-06
> **pxwpxw said:**
> (Dont think the package is available for amd64, only i386)
that is correct, but the i386 package will install / run in amd64 ;)

You really only need the gptsync package... You can also just download it here:
[http://packages.ubuntu.com/jaunty/gptsync](http://packages.ubuntu.com/jaunty/gptsync)

---

### Post by pxwpxw on 2009-04-06
> **cyberdork33 said:**
> that is correct, but the i386 package will install / run in amd64 ;)

You really only need the gptsync package... You can also just download it here:
[http://packages.ubuntu.com/jaunty/gptsync](http://packages.ubuntu.com/jaunty/gptsync)

The i386 gptsync wont run in my jaunty amd64.

Anyway, I posted attachments for both the i386 and amd64 gptsync debs in a separate thread -
[http://ubuntuforums.org/showthread.php?t=1117464](http://ubuntuforums.org/showthread.php?t=1117464)

---

### Post by cyberdork33 on 2009-04-06
> **pxwpxw said:**
> The i386 gptsync wont run in my jaunty amd64.

Anyway, I posted attachments for both the i386 and amd64 gptsync debs in a separate thread -
[http://ubuntuforums.org/showthread.php?t=1117464](http://ubuntuforums.org/showthread.php?t=1117464)
oh well, I keep the debs on a thumbdrive and use them. Seemed to always work OK for me, but maybe that has changed...

---

