---
title: "connection between nvidia driver and kernel?"
date: 2007-06-03
forum: Absolute Beginner Talk
---

### Post by kingmob on 2007-06-03
I don't think i actually qualify as a beginner, but i think this is definately a beginner question ;). Therefore, if you are kind enough to answer, you can be somewhat technical...
I'm just wondering why my Xorg always breaks after a kernel update. I know it has something to do with the drivers having to be compiled for the kernel, and i can see in the log that the modules cannot be found. I can fix this easily with apt-get, but i'm just wondering what is actually happening? I take it this should happen for any driver you use outside the kernel? And how do you go about fixing this yourself?
I guess i'm trying to understand the whole world of the modules and lsmod, modprobe, etc.
Basically i want a deeper understanding of the basic linux system so i can fix problems myself in the future and i can't find this info easily accesible through google.

---

### Post by sandwitch on 2007-06-03
For what i understand is the nvidia driver a proprietary driver. What means they are not GPL licensed. Therefor they are not allowed into a basic kernel, you have to compile them your self for every new kernel.

have fun!

---

### Post by kingmob on 2007-06-03
Yes, i think i understand that. I'm curious what makes it break after a kernel update. What happens that the system does not suspect?

---

### Post by BaffledMollusc on 2007-06-03
> **kingmob said:**
> Yes, i think i understand that. I'm curious what makes it break after a kernel update. What happens that the system does not suspect?

Okay, I'm just guessing here. When ATI or Nvidia compile the driver, they compile it against a specific version of the kernel. When a new kernel is put out, there is no guarantee that it is binary compatible with the previous one. So, for example, some kernel function calls may have been tweaked so they now have different arguments or return values. Thus, when the driver calls a function, that function no longer exists, or expects different parameters; hence the driver breaks.

If a driver is in the kernel (i.e. GPL drivers, not proprietary ones), then each time the kernel is changed that driver is also updated so it still works.

But, as I said, I'm just guessing here. I've wondered about this myself.

---

### Post by Bachstelze on 2007-06-03
While it is true that the nvidia driver is non-GPL and thus can't be included in the main kernel tree and must be compiled for every new kernel separately, it is not true thet you must do it yourself, at least not in Ubuntu. The Ubuntu team has already done it for you and precompiled modules are available for each and every Ubuntu kernel. To install them, do

```
sudo apt-get install linux-restricted-modules-$(uname -r)
```

---

