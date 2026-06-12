---
title: "Linux-PHC: How to rebuild kernel?"
date: 2006-12-07
forum: Absolute Beginner Talk
---

### Post by kilou on 2006-12-07
Hi,

I'd like to undervolt my laptop with Linux-PHC. This requires to patch the kernel and then rebuild it. As a newbie, I really don't understand what rebuilding a kernel means. I could only find these informations:
[https://www.dedigentoo.org/trac/linux-phc/browser/trunk/doc/User.Documention/release_doc/patching.procedure.txt](https://www.dedigentoo.org/trac/linux-phc/browser/trunk/doc/User.Documention/release_doc/patching.procedure.txt)

The problem is that the rebuilding step is left uncommented...

Anybody could explain how to install Linux-PC or rebuild the kernel in Ubuntu Edgy?

Thanks

---

### Post by pay on 2006-12-07
Try this ```
wget http://www.kernel.org/pub/linux/kernel/v2.6/linux-2.6.19.tar.bz2
sudo tar jxvf linux-2.6.19.tar.bz2 /usr/src
sudo ln -s /usr/src/linux-2.6.19 /usr/src/linux
```Then patch it. Now you need to compile it```
cd /usr/src
sudo make menuconfig
sudo make clean && sudo make && sudo make modules_install
sudo mount /boot && sudo make install
sudo module-rebuild rebuild
```Now reboot and hopefully it will work. That is an example for the latest kernel using a generic installation. There are different ways to compile the kernel. Before you compile the 2.6.19 kernel I suggest you look at this [http://forums.gentoo.org/viewtopic-t-521199-highlight-.html](http://forums.gentoo.org/viewtopic-t-521199-highlight-.html) (doesn't apply for older kernels). Goodluck

---

### Post by kilou on 2006-12-07
Thanks a lot Pay! I'll try that :) Just another question: after patching it's recommended to "configure, build and install your kernel as you are used to". I guess the commands you proposed in your last post are to rebuild and install the kernel but what does it mean to configure the kernel??

Also I don't want to use the 2.6.19 kernel, I need to use the one that is included in Edgy (2.6.17). Is there a way to backup the kernel in case anthing goes wrong during the patching? Any "HowTo" to backup and restore the kernel? 

Thanks

---

### Post by pay on 2006-12-07
When you type make menuconfig it will give you a bunch of configuration options. That's what I meant by configure your kernel. You don't need to back up your kernel if you install a new kernel version because the old kernel will still be installed and you can pick it from the grub menu, but if you recompile the old one then you won't have that option. To use the kernel that Ubuntu is using just start the compile from here after you patch it```
cd /usr/src
sudo make menuconfig
sudo make clean && sudo make && sudo make modules_install
sudo mount /boot && sudo make install
sudo module-rebuild rebuild
```I also recommend that you have a thourough read of this [http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu) which is more Ubuntu specific than my little guide. Also look at this [http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html](http://www.cyberciti.biz/tips/build-linux-kernel-module-against-installed-kernel-source-tree.html)

---

### Post by kilou on 2006-12-08
Thanks for these links (especially the first one which is exactly what I need!!!). I switched my mind: I'll install the latest 2.6.19 kernel because my SD card reader (Ricoh RL5c476 II rev ac) is not working in Edgy and I read somewhere that it "may" work with the latest kernel. Moreover as you mentioned there is no need to backup my current kernel if I install a new one so this is even better. Now my last question is how can I remove the old kernel if I'm happy with the new one? Or how can I remove the new kernel if it doesn't work properly? I understand I can choose which kernel to start with during boot in Grub but I like keeping things clean and don't want to keep a non-working or obsolete kernel in the system if the new (or old) one works better. Any way to remove one kernel or the other when 2 are installed?

---

### Post by pay on 2006-12-08
> **kilou said:**
> Now my last question is how can I remove the old kernel if I'm happy with the new one?
That would depend on the method that you install it with. I'm not a Ubuntu user but I think that you can remove the older kernel with a command like this```
sudo aptitude --purge remove linux-image-generic
```But make sure that you read carefully what kernel you are removing before you remove it. If you compilled a kernel with the method that I showed in my first post then to remove it type ```
sudo rm -r /usr/src/linux-2.6.19
```Then link the kernel source to the kernel you want to use```
sudo ln -s /usr src/linux-2.6.xx /usr/src/linux
```Also to remove the kernel with a method showed in the link that I gave you try "sudo aptitude --purge remove linux-image-generic" (or if that doesn't work type up to linux-image- and then press tab) of if apt can't remove it then type in```
sudo dpkg -r linux-image-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb
sudo dpkg -r linux-headers-2.6.18.1-custom_2.6.18.1-custom-10.00.Custom_i386.deb
```Good luck with the kernel hacking. After removing the obsolete kernel then there maybe still a grub entry for it. Remove the files from /boot that you don't need as root and then edit the grub file and remove the old kernel from the list (sudo nano /boot/grub/grub/conf) Do this with caution and I recommend only commenting out the lines you don't need incase you make a mistake (#).

---

### Post by kilou on 2006-12-08
Thanks for this help. I'm now compiling the new kernel and just saw another thing to do to make the linux-phc patch work. The linux patch procedure recommends to enable CPUfreq debugging in the kernel configuration. I did this but it's also written that "To enable these debug messages you also have to add "cpufreq.debug=3" to your kernel boot parameters." How do I do this? Do I have to add this in the GRUB's menu.lst??? Where should this line be added?

Thanks again for your help :D

PS: kernel 2.6.19 is now working, reboots OK and the patch seems to have been applied (I still need to configure it though). However the SD card is still unsuported :( (mine is a RICOH RL5c476 II rev ac and it's not compatible with SDIHC apparently)

---

### Post by pay on 2006-12-08
> "To enable these debug messages you also have to add "cpufreq.debug=3" to your kernel boot parameters." How do I do this? Do I have to add this in the GRUB's menu.lst??? Where should this line be added?Yeah I believe you have change your grub.conf ```
gksudo gedit /boot/grub/grub.conf
```Then change something like this```
title LINUX
root (hd1.0)
kernel /vmlinuz root=/dev/hdb1

```to this```
title LINUX
root (hd1.0)
kernel /vmlinuz root=/dev/hdb1 cpufreq.debug=3
```But before you edit this file back it up```
sudo cp /boot/grub/grub.conf /boot/grub/grub.conf_bak
```

---

### Post by kilou on 2006-12-08
I have no grub.conf file :confused:  I added the parameter in the menu.lst file in /boot/grub/, looks similar to what you propose.

I could successfully undervolt the CPU, now my 800Mhz voltage is 700mV vs 988mV previously!

Thanks ALOT for your help Pay! Greatly appreciated ;)

---

### Post by pay on 2006-12-08
> **kilou said:**
> I have no grub.conf file :confused:  I added the parameter in the menu.lst file in /boot/grub/, looks similar to what you propose.I guess that Ubuntu does things alittle different than Gentoo. Since that you decided upon the 2.6.19 kernel, I hope that you took the time to look at my post here [http://forums.gentoo.org/viewtopic-t-521199-highlight-.html](http://forums.gentoo.org/viewtopic-t-521199-highlight-.html) if you are planning on using ati drivers. Congratulations on getting the kernel to compile:)

---

### Post by kilou on 2006-12-08
Yes I looked at this link but it doesn't apply to me since I have intel 915 graphics, no ATI. Everything works great (except the SD card reader is still not working as before...). But I have some troubles installing lm-sensors to get the sensors info (CPU temperature etc) on the taskbar. As you know a lot of things and if you are interested you can check the thread I started on this topic at [http://www.ubuntuforums.org/showthread.php?t=314844](http://www.ubuntuforums.org/showthread.php?t=314844)

Thanks for the great HowTo! I'm a newbie and now I can say that I have compiled my first Linux kernel :cool: well just done some copy/paste from your posts and from the link you provided so I shouldn't feel that proud :-#

---

