---
title: "kernel upgrade"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by stevieb on 2006-08-06
hello,

I've been thinking about upgrading to a different kernel than the one supplied with ubuntu.  is there any resource out there that can suggest the best one given my computer configuration?  I have a Lenovo 3000 C100.  If you can help, let me know what info I can post.

thanks,
-steve

---

### Post by 5-HT on 2006-08-07
Any reason why you don't want to stick with the Ubuntu kernel?
If you'd like the most recent kernel, you'll need to download it from kernel.org and compile it yourself. If you don't know how to compile a kernel, the following guides may be of help:[LIST]
[*][http://doc.gwos.org/index.php/Kernel_Compilation_Dapper](http://doc.gwos.org/index.php/Kernel_Compilation_Dapper)
[*]Using fakeroot: [http://www.ubuntuforums.org/showthread.php?t=219669](http://www.ubuntuforums.org/showthread.php?t=219669)[/LIST]If you're compiling your own kernel, there's no need to worry about the best one for your configuration as you'll be able to find tune the kernel to your specific hardware. The only caveat is that you'll need to know something about your hardware (well, you'll also be loosing the ability to recieve the easy to apply security updates for the kernel from Ubuntu)...

If you're not sure about all the specifics of your hardware, you can use the config from one of Dapper's kernels (look in /boot) that include support for a lot of different hardware. To do so, just copy the most recent kernel config you have to /usr/src/linux/.config, do a 'make oldconfig' at the appropriate time (the guides should let you know when), and use the recommended answers for any questions you're unsure about. You can then do a 'make menuconfig' or similar and fine-tune for things you know you don't want to get a leaner kernel.

HTH

---

### Post by stevieb on 2006-08-07
> **5-HT said:**
> Any reason why you don't want to stick with the Ubuntu kernel?

HTH

Well, I'm trying to get suspend to work on my laptop, and s2ram needs 2.17.  Also, the latest driver for my video card (Intel 915G) needs 2.17.

There are other problems I'm hoping to solve with this, namely: gaining access to my multicard reader and getting my palm tungsten E(which is running Card Export II) recognized as a USB drive.  I've come to dead ends in the forums on these 2 problems.

Do you think I'd be creating more headaches for myself by switching kernels?  

thanks for the reply,
-steve

---

### Post by 5-HT on 2006-08-09
If using 2.6.17 is required to sort out some of the problems you're having with your hardware, then it would definitely be worth a shot. Compiling a kernel isn't difficult once you get the hang of it. However,  you will loose the ability to use Ubuntu's restricted modules (some wireless drivers, video drivers, etc...) but there are work around for that (the easiest is just to compile those modules yourself if you need them. The first link in my previous post describes how.)

I would suggest using one of Ubuntu's kernel configs to get a nice base to work with that will enable support for a lot of hardware. My previous post briefly mentions how to do so, and the kernel compilation guides around should mention how to do it as well. Additionally, there is a help menu item for most kernel options (using *menuconfig/xconfig*) that briefly describes what the option does and if you should enable it in your kernel if unsure. Another thing that can come in handy if using one of Ubuntu's configs and *make oldconfig* is to press enter when prompted for decisions to make for new kernel options that weren't explicitly defined in Ubuntu's configs (as the options weren't present at the time)  to select the recommended option.

The whole process really isn't as bad as it seems, and you do end up learning a lot. Hopefully you can get 2.6.17 working without much hassel and cure some of the problems you're currently having if they have been addressed in the new kernel.

Also, there has been some talk about the possibly of backporting Edgy's (the devlopment version of Ubuntu) 2.6.17 kernel to Dapper. [http://www.ubuntuforums.org/showthread.php?t=200470](http://www.ubuntuforums.org/showthread.php?t=200470)
If it becomes feasible to backport 2.6.17, then it'll become only an apt-get away.

---

