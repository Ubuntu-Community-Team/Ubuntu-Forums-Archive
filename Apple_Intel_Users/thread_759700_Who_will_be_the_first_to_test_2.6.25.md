---
title: "Who will be the first to test 2.6.25?"
date: 2008-04-19
forum: Apple Intel Users
---

### Post by Sunspark on 2008-04-19
Hi!

2.6.25 was released a couple days ago, and contains some interesting things that may be of value to Macs.. I noticed it has EFI x86-64 support, something about a soundcard for a "MacBook" and i915 video support, and a bunch of extra 'ACPI thermal support'.

This won't be in Hardy Heron, but I am curious to know what benefits it brings to the table for Macs, if someone who knows about kernels can look into it.

Looking forward to trying out HH on this 3,1 MacBook. Going to be really interesting to see if these sporadic slow-motion keyboard slowdowns in the web browser on my computer are OS X related, or hardware.

Have a great day!

---

### Post by sistoviejo on 2008-04-19
Well I don't have an Apple laptop but I'm going to try it.
I have already compiled the kernel and now I'm in the process of compiling the modules.
This is the first time I compile the kernel. 
It's fun! :lolflag:
If you want to try it I can give you directions.
:)

---

### Post by UnixBASHparty on 2008-04-19
double post

I am an idiot.

---

### Post by UnixBASHparty on 2008-04-19
I have tried to do this.  I am not building a RAM disk, so I built the needed kernels.  Unfortunately I am missing a drivers and the kernel panics as it can't mount root.  I don't remember the error, but it only reported the RAM drive present(I didn't load one, so who knows).
I know the problem is I forgot to load something for SATA to work.

:mad: Kernels are NOT fun.  I have made tons of kernels and laptops always kill me.

EDIT:  Does anyone have the .config file from vanilla Linux 2.6.24.x ?  That would help me so much.

---

### Post by Gen2ly on 2008-04-19
Hey, take a look at the faq.  There's a kernel config link there.

---

### Post by UnixBASHparty on 2008-04-20
> **Dirk.R.Gently said:**
> Hey, take a look at the faq.  There's a kernel config link there.

I said I need a .config file.  But thanks for helping!  The .config file needs to be configured for Macbook model 3,1.  

I wish I could get this kernel working.  I wonder what the problem is.

---

### Post by barutanseijin on 2008-04-20
Well, i tried it as soon as it came out.  It hangs on boot on my machine (Macbook 4,1).  I'm running x86_64.

---

### Post by cyberdork33 on 2008-04-20
> **UnixBASHparty said:**
> I said I need a .config file.  But thanks for helping!  The .config file needs to be configured for Macbook model 3,1.
He is talking about a kernel config... that is the same thing.

---

### Post by UnixBASHparty on 2008-04-20
> **cyberdork33 said:**
> He is talking about a kernel config... that is the same thing.

It was linked from the FAQ, so I didn't see it that the first time.  If anyone else wants it is here:
 [http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel")

---

### Post by Melcar on 2008-04-20
I had so much hopes for this kernel.  Apparently it suffers from the same as the 2.6.24 kernels on my machine, so it always hangs at the loading stage, and after a while gives me the same errors as the 2.6.24 kernels; either it's having problems with my drives or with the SATA controller on the SB600, which confuses me since the 2.6.22 and 2.6.23 kernels have no problems with my system.

---

### Post by cyberdork33 on 2008-04-20
This is a forum for Apple Mac support folks.

---

### Post by r.lopez.negrete on 2008-05-21
Hi sistoviejo,

Hey quick question, how did you get the source code for the kernel and the modules???

thanks.
 rodrigo

---

### Post by sistoviejo on 2008-05-21
> **r.lopez.negrete said:**
> Hi sistoviejo,

Hey quick question, how did you get the source code for the kernel and the modules???

thanks.
 rodrigo

From [http://www.kernel.org/](http://www.kernel.org/)
This link will let you download the latest version:
[http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.25.4.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.25.4.bz2)

---

