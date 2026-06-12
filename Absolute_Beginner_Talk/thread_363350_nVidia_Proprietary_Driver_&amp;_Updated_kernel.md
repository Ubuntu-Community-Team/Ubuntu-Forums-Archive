---
title: "nVidia Proprietary Driver &amp; Updated kernel"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by edwardLS on 2007-02-16
Running ubuntu (Dapper) with kernel 2.6.15-27-386.  Have installed and configured the Proprietary nVidia Driver per [http://albertomilone.com/instructions.html](http://albertomilone.com/instructions.html).  All of this was working fine and the Xserver was great.

I recently installed 'upgrades' which included a new kernel (kernel 2.6.15-28-386)  and booting that kernel gives me an Xserver failure to start.  Booting the kernel 2.6.15-27-386 from the GRUB menu still works perfectly.

I believe that I read someplace that when you upgrade the kernel, the nVidia driver must be reinstalled with the new kernel.  This is a bit above my head; could someone please give me an overall outline of what I have to do, and in what order.

---

### Post by sardion on 2007-02-16
Should be as simple as:

sudo aptitude install --reinstall nvidia-glx

assuming you followed what those instructions call "method 1".  the link you posted talks about kernel upgrades and what you have to do.

---

### Post by kpkeerthi on 2007-02-16
Whenever you upgrade your kernel, you should also upgrade the linux-restricted-modules to the corresponding version of the kernel. Both these packages are usually kept in sync in the standard ubuntu repository. 

When you upgraded your kernel, your linux-restricted-modules was not upgraded as you have used an external repository for nvidia driver. This caused Xorg to fail. You can try a couple of things

Option 1:

1. Boot by selecting your new kernel in GRUB. Press ctrl + alt + f1 after you get to see xorg error.
2. Type 
	sudo aptitude update
	sudo aptitude install linux-restricted-modules-`uname -r`
	(NOTE: copy/paste the above command)
	
3. If aptitude complains of a non-existent package, it means that linux-restricted-modules is not available for your kernel yet (and thats why xorg failed). You may try option 2, which worked for me.


Option 2:

1. Boot by selecting your old kernel in GRUB
2. Download envy from [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
3. Remove nvidia driver
	sudo aptitude remove nvidia-glx
4. Install envy by double clicking on the .deb	file or sudo dpkg -i envy****.deb
5. Go to virtual terminal one by pressing ctrl + alt + F1
6. Login and type envy

More information about envy can be found at the website above.

---

