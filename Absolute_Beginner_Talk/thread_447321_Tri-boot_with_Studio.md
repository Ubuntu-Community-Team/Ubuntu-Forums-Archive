---
title: "Tri-boot with Studio?"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by shaft350x on 2007-05-17
I am running Ubuntu Feisty on a Machine with XP on it already.  I would like to try out Ubuntu Studio (downloading it via torrent right now).  I want to be able to keep my Feisty the way it is and also be able to log into Studio either via GRUB or the GDM.

Is there an easy way to go about this?

---

### Post by shen-an-doah on 2007-05-17
What I did was just install all the Ubuntu studio parts from the repositories. This means my Ubuntu install is the same and then I just have the choice of my usual ubuntu kernel or the low latency one at start up.

Third post down in this thread:

[http://ubuntuforums.org/showthread.php?t=442506](http://ubuntuforums.org/showthread.php?t=442506)

---

### Post by Hobo Joe on 2007-05-17
I'm not positive, but I think all you need to do is make a separate partition and then install. GRUB should update accordingly.

---

### Post by Pollywoggy on 2007-05-18
Is it possible to login to Ubuntu via GRUB?  How does one do that?  I had not heard of this method.

---

### Post by rsambuca on 2007-05-18
> **shaft350x said:**
> I am running Ubuntu Feisty on a Machine with XP on it already.  I would like to try out Ubuntu Studio (downloading it via torrent right now).  I want to be able to keep my Feisty the way it is and also be able to log into Studio either via GRUB or the GDM.

Is there an easy way to go about this?

Why don't you just install the ubuntustudio packages?  They are all in synaptic!!

One-click install.

---

### Post by LE CHARBON on 2007-05-20
I agree to use synaptic. Just take what you want.;)

---

### Post by infoseeker on 2007-05-20
I have recently installed Ubuntustudio and the installation had no problems adding it into the GRUB list, and I now have the option of booting either Feisty or Ubuntustudio.

---

### Post by chatters on 2007-05-24
> **rsambuca said:**
> Why don't you just install the ubuntustudio packages?  They are all in synaptic!!

One-click install.

The kernels are different, Studio optimises the kernel for audio recording and playback at
the expence of stability.

I am glad to see that it is easy to set up Studio to run alongside Ubuntu and XP as this is
what I am doing as soon as studio has finished downloading.

---

### Post by shen-an-doah on 2007-05-24
> **chatters said:**
> The kernels are different, Studio optimises the kernel for audio recording and playback at
the expence of stability.

I am glad to see that it is easy to set up Studio to run alongside Ubuntu and XP as this is
what I am doing as soon as studio has finished downloading.

Your old Ubuntu kernel will still be in the GRUB menu for you to boot into whenever you like.

---

