---
title: "usb persistent boot hanging"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by TJCIB on 2008-03-04
I installed Gutsy on a 2GB pen drive.  It worked great.  I followed the pendrivelinux.com howto with some modifications that I read from here and other places.  It worked.

I booted up into persistent mode and did apt-get update and upgrade and all to get the updates.

Now my usb stick will only boot in Live Mode, it will not boot in Persistent Mode.

When booting, it loads the kernel and then finally gets to the "flesh colored" screen where it hangs forever.

So I restarted and hit alt+ctrl+f2 to see what was going on and everything was okay except I got a FAIL on etc/default/linux-restricted-modules-common

I've read some other similar threads, but nothing has helped to this point.  I mounted the usb stick to another system and made sure syslinux.cfg was correct, and it seems to be.

Any help would be great.

Thanks

---

### Post by thewho? on 2008-03-08
Sounds like a reload.  Be careful when getting update, you can't always just let it update everything.

---

### Post by TJCIB on 2008-03-08
I am careful when I do anything.  I know enough fix some things and little enough to really mess stuff up. 

but how do I know what to update and what not to?  Especially when there are 255 updates...just go through them one-by-one and find stuff that affects the changed files?

---

### Post by thewho? on 2008-03-18
I know what you mean.  You just have to watch out because apt will update everything, including your kernel.  Which could be bad news.  Something like that probably happened to you.

---

### Post by TJCIB on 2008-03-19
i tried rolling my own Live CD using remastersys, but I couldn't get it to load.  It kept saying "kernel not found" when trying to boot.

I then used the standard Live CD with the exact same steps and it worked fine.  I guess I missed something in setting up my own distro...

i think i need to set up my own CDFS and then create the iso rather than going straight to the iso.  I then mounted the iso and copied the files as per the instructions on the various pages (pendrivelinux.com, etc.)

---

