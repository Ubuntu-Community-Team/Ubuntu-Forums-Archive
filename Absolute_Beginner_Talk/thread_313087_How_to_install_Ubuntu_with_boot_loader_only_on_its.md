---
title: "How to install Ubuntu with boot loader only on its partition"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by rjmichaelson on 2006-12-05
This has to be an easy question to answer, but I have been searching/Googling for over an hour without finding the answer, so....

I want to install Ubuntu with the boot loader placed only on the / partition and not on the master boot record. The distro I use 99% of the time is Xandros, and Xandros, along with most other distros I have tried, gives one the option NOT to install the boot loader on the MBR.  If this option is available for Ubuntu, and I assume that it is, it is not immediately evident. 

I started using Ubuntu because, for whatever reason, it was the only live or hard drive install distro that worked on my newly-built dual-core PC:
 
[http://www.extremetech.com/article2/0,1697,2002778,00.asp](http://www.extremetech.com/article2/0,1697,2002778,00.asp)

(only Ubuntu recognized the hard drives or the CD/DVD drives). 

Then, Xandros came out with a beta version of Xandros 4 Professional, and the darn thing worked. Despite a number of screwy error messages, the Xandros boot loader also loaded Ubuntu, along with both Windows XP Pro and Windows XP 64 bit. 

Xandros just released Xandros 4.1 Professional Business Edition, and I bought it & installed it, and now Ubuntu will not make it through its boot routine, even though it is still listed as a choice under the Xandros boot loader. 

I am not confident that the Ubuntu boot loader will correctly take over the job of the Xandros boot loader, and that is why I want to reinstall Ubuntu, but with its boot loader only on its respective partition. 

Thanks!

---

### Post by bodhi.zazen on 2006-12-05
Use the alternate CD. This will give you the option of where to install grub.

The boot loader should be grub and should work to boot Xandros and Ubuntu. It likely needs to be re-configured. 

Can you post /boot/grub/menu.lst form xandros and ls /boot from Ubuntu if you would like assistance configuring Xandros to boot Ubuntu.

---

### Post by sitedesign on 2006-12-05
If you download and use the alternative install version I think that option is in there. If not then that option will in there using the expert mode.

---

### Post by ajgreeny on 2006-12-05
If it were my choice I would let ubuntu put grub on the MBR, as it will find and include xandros in the grub menu.  Ubuntu always seems to do that better than many other distros.  However, to answer your question, I'm pretty sure you can do what you would like to but only with the alternate install CD, not the live/install CD.  Download a copy of that from the ubuntu website and you should be OK.  Alternatively, assuming you can get into ubuntu somehow with the xandros grub by manually editing your grub/menu.lst, boot into ubuntu, then in a terminal type:-
sudo grub-install /dev/hXX
where hXX is the partition where ubuntu is installed.  That will put grub on that partition but I'm not sure whether it makes it automatically bootable, and if it is not the boot partition of the disk I don't know how the bios will find it at boot time.  No doubt someone else will be able to tell you more.

PS it would be useful to see the menu.lst from xandros to try to figure out why ubuntu will not boot easily from that at the moment.

---

### Post by steve.horsley on 2006-12-05
The alternate installer has the option to install grub onto any partition. Of course, you normally specify the root partition of the Ubuntu system. This partition can then be chainloaded from another bootloader.

This option has always failed for me, leaving grub not installed, and no /boot/grub/menu.lst file either. I always (twice, when installing Dapper and Edgy) have to use the CD rescue mode, switch to the Ubuntu partition and then run **grub-install /dev/wherever**, then copy and hand edit a menu.lst from somewhere. 

I wonder if this failure is because I (so far) have always specified /dev/whatever. The installer asks for either /dev/whatever or the grub format (hd0,X). Next time, I will try the grub syntax.

---

### Post by rjmichaelson on 2006-12-06
Thank you all for some great help. I was not aware of the alternative install disk option. 

I may just take the plunge and reinstall Ubuntu and let it configure the boot loader. Before I got a workable copy of Xandros for my home-built machine, I installed Ubuntu (actually "Edubuntu", since my wife is a teacher), and its boot loader correctly allowed booting not only of XP Pro and XP 64 Bit, but also the RC1 versions of Vista 32 & 64 bit. I thought that was rather impressive for a freely-distributed OS, since not even my commercial product, Acronis Operating System Selector, cannot yet pull that off correctly.

---

