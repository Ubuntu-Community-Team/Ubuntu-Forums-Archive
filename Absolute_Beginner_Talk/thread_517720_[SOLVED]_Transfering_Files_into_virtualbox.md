---
title: "[SOLVED] Transfering Files into virtualbox"
date: 2007-08-04
forum: Absolute Beginner Talk
---

### Post by Specter043 on 2007-08-04
I installed Windows Vista into a virtualbox.  I cannot connect to the internet, because it doesn't have my ethernet card drivers.  I downloaded the driver in Ubuntu, and now need to know how to transfer it to my Windows Vista Virtualbox, if that is even possible.  BTW, the driver is on my desktop.

---

### Post by apswartz on 2007-08-04
Perhaps the easiest way would be to burn it to a cd from Linux, then copy it off of the cd into windows.

---

### Post by Specter043 on 2007-08-04
I had a feeling that was the most likely way, but I felt I should give the forums a try.  Does anyone know of any way at all?  If not, i'll just burn the drivers to a CD.

---

### Post by apswartz on 2007-08-04
There might be a way to have a shared folder, but I don't want to reads the manual for you to find out ;-)

---

### Post by apswartz on 2007-08-04
Wait a minute, go into virtual box and set your network connection to nat. you shouldn't need any drivers for that.

---

### Post by machoo02 on 2007-08-04
Head over to the Virtualbox website, and download the user manual.  The section you are looking for is 5.4 "Folder sharing", and has very simple instructions on how to set up a shared drive.

---

### Post by bodhi.zazen on 2007-08-04
LOL

You can transfer the file via many ways ...

Shared usb/flash drive, shared directories (files), shamba, nfs, ssh (scp) ... take your pick.

If you do not know any of these protocols, time to learn (you *should be able to bridge your network card without too much hassle)

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

---

### Post by Specter043 on 2007-08-04
I set it to NAT, and for some reason it won't work.  What do the other settings do?  Is it easy to set up networking with one of them?

---

### Post by apswartz on 2007-08-04
> **apswartz said:**
> Wait a minute, go into virtual box and set your network connection to nat. you shouldn't need any drivers for that.

Again, try this. It works for me w/o needing any driver installs.

---

### Post by Specter043 on 2007-08-05
> **bodhi.zazen said:**
> LOL

You can transfer the file via many ways ...

Shared usb/flash drive, shared directories (files), shamba, nfs, ssh (scp) ... take your pick.

If you do not know any of these protocols, time to learn (you *should be able to bridge your network card without too much hassle)

[http://doc.gwos.org/index.php/VirtualBox](http://doc.gwos.org/index.php/VirtualBox)

From that link I found this, [http://forums.virtualbox.org/viewtopic.php?t=224]("http://forums.virtualbox.org/viewtopic.php?t=224")

Which is exactly what I was looking for.
Thanks for the help.

---

