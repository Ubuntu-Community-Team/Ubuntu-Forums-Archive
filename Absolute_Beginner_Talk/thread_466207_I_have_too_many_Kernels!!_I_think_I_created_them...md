---
title: "I have too many Kernels!! I think I created them...."
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Brightbelt on 2007-06-06
Hi,
I am on Ubuntu Studio and I may have gotten myself into a beginner's mess. I happened to be looking through the Synaptic Package manager and saw some Linux Modules for Restricted Drivers that seemed relevant to installing the advanced ATI graphics driver. And I saw they were uninstalled. And I was thinking maybe I could (yet again) give it another try to install the accelerated driver for my Ati X1650. 

So I installed them, and when I restarted, I saw a whole page of kernels to choose from in my boot menu. I already had 6 kernels or so before this mess which seemed too much already. This is somewhat what it looked like I installed the modules. I'm improvising: 

Kernel 26.20-16 Low latency
Kernel 26.20-16 generic
Kernel 26.20-15 Low latency 
Kernel 26.20-15 generic

But now there's about 5 to 8 more lines on top of these !! Some have the number 386, which seems like they were the recent ones I installed. I've already removed a few through the Synaptic Package Manager that seemed from my memory to be ones I installed today by mistake. But beyond that, I'm sacred I'll delete something important.

Please help me get this under control, if it is still possible. I appreciate any help. 

Many Thanks, Frank B.

---

### Post by Bachstelze on 2007-06-06
The kernels all havea package for them in Synaptic, called linux-image-VERSION. Just remove the packages for the kernels you don't need :)

---

### Post by Brightbelt on 2007-06-06
Thanks HymnToLife ! I was hoping it would be that easy. 

I appreciate your quick response,...Frank B.

---

### Post by Inxsible on 2007-06-06
There are 3 packages of importance for each kernel 
```

linux-headers-VERSION
linux-headers-VERSION-generic
linux-image-VERSION-generic

```
 
where VERSION could be for eg. 2.6.20-15 or 2.6.20-16
Remove the ones that you dont require. I dont know if there are any additional ones for 64-bit architectures. So if you use the 32-bit Ubuntu, you can un-install the above 3 packages.
 
Hope that helps.

---

### Post by Brightbelt on 2007-06-06
Thanks Inxsible !! I'll save that information,Frank B.

---

