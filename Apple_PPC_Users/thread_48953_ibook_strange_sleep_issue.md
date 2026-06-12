---
title: "ibook strange sleep issue"
date: 2005-07-14
forum: Apple PPC Users
---

### Post by sulobanks on 2005-07-14
I have a new (May 2005) ibook g4.  I understand a lot of people have had sleep problems with older kernels.  But the new kernels 2.6.11+ support sleep. I tried fedora core 4 first. But I don't like redhat-based distros very well and it was buggy. But sleep worked perfectly every time.

Now I have ubuntu hoary 5.04 and everything works great except sleep.  It goes to sleep just fine when I close the lid and if I open the lid within about 3 minutes, it wakes up exactly as expected.  But if it sleeps for more than 3 minutes or so, it powers down. Does the same thing with blank screen as well.  Surely there's a fix for this?  Any ideas would be appreciated. Thanks in advance.

---

### Post by DJ_Max on 2005-07-14
Have a look at this [http://ubuntuforums.org/showthread.php?t=2368&highlight=ibook+sleep](http://ubuntuforums.org/showthread.php?t=2368&highlight=ibook+sleep)
And do a search for ibook sleep

---

### Post by sulobanks on 2005-07-15
Thanks for the link. That's the issue everyone else seems to be having.  But my ibook wakes just fine even though it has the dreaded radeon 9600.  It just has no longevity.  About 3 minutes into sleeping, it completely powers down.  I searched google extensively before posting here.  I found only one site on google in hours of searching that mentioned this problem, but offered no solution.  ](*,) 

For now, I suppose I'll go on using os x when I'm in a situation that requires frequent sleeping.  That or switch back to Fedora if I find myself needing to use sleep that frequently.

---

### Post by pierba on 2005-07-15
I have the same problem.
With kernel 2.6.10-5 my ibook sleep and resume, updated to 2.6.11, don't sleep. I ha reinstalled kernel 2.6.10-5 now.
Pietro

---

### Post by pvz on 2005-07-16
I finally have sleep working properly on my iBook G4 12" now, no usb-issues or kernel-panics or whatever anymore, resume works fine, with the latest 2.6.12 kernel that I got here:

[http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-3-powerpc_2.6.12-3.3_powerpc.deb](http://archive.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.12/linux-image-2.6.12-3-powerpc_2.6.12-3.3_powerpc.deb)

You will have to get a newer initrd-tools from the archive as well to satisfy the dependency. Maybe this works on your iBook as well. Mine is from late 2004, I don't know what they changed in between.
Here is a working xorg.conf with the necessary lines added to try with it:
[http://www.petrvz.net/~pvz/xorg.conf](http://www.petrvz.net/~pvz/xorg.conf)

---

### Post by pierba on 2005-07-16
Thank you, I shall try
Pietro

---

### Post by pierba on 2005-07-18
Now my ibook sleep very well and it has a beatiful resume.
thank you
Pietro

---

