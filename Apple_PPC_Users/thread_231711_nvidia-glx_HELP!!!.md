---
title: "nvidia-glx HELP!!!"
date: 2006-08-07
forum: Apple PPC Users
---

### Post by gamgee911 on 2006-08-07
Ok, I've searched the forums finding no help and now I'm at my wits end :confused:  Someone Please Help?!

I entered in the sudo apt-get install nvidia-glx and got the package not found error.  I've enabled all sources in synaptic and in my apt list and still nothing.  I dug around online and found the package "linux-restricted-modules-2.6.15_2.6.15.11.orig.tar.gz" so I downloaded it and opened it but I don't know what to do with it.  I'm such a n00b, I'm sorry :???: 

I'm running dapper on my PowerBook G4 12" (GeForce4 MX 32 MB) 867 MHz PPC

Please help? ](*,)  thanks

---

### Post by avtolle on 2006-08-07
I am totally not familiar with what you are trying, but before you go further with the tarball, what kernel do you have? type at terminal uname -r and post back.

---

### Post by gamgee911 on 2006-08-07
Wow, that was quick.

2.6.15-23-powerpc

thanks

---

### Post by avtolle on 2006-08-07
When I run the same command, the response is: 2.6.15-26ppc, which is the current most-updated kernel. Just a thought: could you run update manager from the System>Administration menu, and see if it gives you an update to that kernel, and then install it and see if that helps?

---

### Post by gamgee911 on 2006-08-07
update again.. :P  Ok, I'll try it tonight  thank you

---

### Post by avtolle on 2006-08-07
While updating your kernel will be beneficial, my bad on not really noticing that you are trying to install the appropriate nvidia driver. May I suggest trying to use automatix or easy ubuntu to install the driver? Many on the forum think this is the way to go, so I offer this to you for your consideration. Again, I would install the update first, then run either script to see if that helps. You can find the links under the third party forum. HTH.

---

### Post by rasec on 2006-08-07
gamgee911, you can't get the nvidia glx driver to work because it doesn't exist for the powerpc. Nvidia only makes drivers for the i386 and amd64 platforms.

---

### Post by KFASheldon on 2006-08-07
HEy rasec is correct same goes fro ATI accel drivers - and I so wanted to have XGL stuff on my iMAC.

Sorry Mac guys you just miss out at the moment.

---

### Post by gamgee911 on 2006-08-07
Crap, I was wondering that when I saw the drivers labeled x86 :(  So there's no way to get the acceleration I want?

---

### Post by 3rdalbum on 2006-08-08
> **gamgee911 said:**
> Crap, I was wondering that when I saw the drivers labeled x86 :(  So there's no way to get the acceleration I want?

Sorry it took so long for you to get the correct reply, and sorry that there's no way for you to get proprietry acceleration.

---

### Post by gamgee911 on 2006-08-08
That's ok, thanks guys for helping.

---

