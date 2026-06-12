---
title: "How will Arch effect my partitioning?"
date: 2008-02-21
forum: Arch and derivatives
---

### Post by ErusGuleilmus on 2008-02-21
Hello,

  I have heard many positive things about Arch, and am considering giving it a shot. As it stands now, I have three partitions on my hard drive. One for Vista, one for Ubuntu, the last for openSUSE. I am planning on installing Arch over openSUSE. How will this effect my ability to boot into Ubuntu and Windows? 

Thanks!

---

### Post by bwtranch on 2008-02-21
> **ErusGuleilmus said:**
> Hello,

  I have heard many positive things about Arch, and am considering giving it a shot. As it stands now, I have three partitions on my hard drive. One for Vista, one for Ubuntu, the last for openSUSE. I am planning on installing Arch over openSUSE. How will this effect my ability to boot into Ubuntu and Windows? 

Thanks!
Well. it shouldn't effect Ubuntu or Windows, since the GRUB bootloader is already there to take care of that. What I worry about, is getting this all to work together? And why? If you've got Arch, you don't need Ubuntu. And really, if you've got Linux, why would you need windows?
But, no, it's easy if you want. Setup your fstab file. So it reads right. There are a lot of things on the web about this. But, I'm in the one queenie per camp group. You'll be way better off. So what you'll have is three kernels on a machine that needs only one good one (and all those device files and junk) . Does this make sense? Kinda goes against the priniple of Arch as being simple, lightweight, and easy-to-use. K.I.S.S.

---

### Post by santaslittlehelper on 2008-02-21
Hi

If you just what a look at arch VMware is a great way to do it.
If you install over openSUSE all you should have to worry about is you’re menu.lst 
Install arch, no need to install any bootloader, boot into Ubuntu, edit the menu.lst adding arch.
Should be all there’s to it.

---

### Post by fwojciec on 2008-02-21
Don't expect Arch to autodetect what is installed on each partition like the "just works" distros do -- but in either case you can skip the "install bootloader" step during the installation of Arch and simply add the appropriate entry for Arch to the menu.lst file that you're currently using to boot.

The default entries for Arch should look something like this:

> # (0) Arch Linux
title  Arch Linux
root   (hd**0,2**)
kernel /boot/vmlinuz26 root=/dev/**sda3** ro
initrd /boot/kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd**0,2**)
kernel /boot/vmlinuz26 root=/dev/**sda3** ro
initrd /boot/kernel26-fallback.img

The stuff in bold is what you'd have to customize for your system.  The root parameter is (hd[number of the hard driver],[number of partition]) -- watch out because the first drive/partition is always "0", the second one is "1" and so on.  The parameter in the kernel line should be pretty self explanatory -- one caveat though, Arch uses /dev/sd* notation (rather than /dev/hd*) for all drivers -- even ATA drives, so it might be a little different than Ubuntu or Suse in that regard.

---

### Post by ErusGuleilmus on 2008-02-21
Thank you all very much for your replies, they are very helpful. 
I have one more question to ask before I give installing Arch a go. How difficult is it to install the Nvidia drivers once I get X installed, so that I may have full 3d support? 

Thank You!

---

### Post by fwojciec on 2008-02-21
Installing nvidia driver is as simple as typing "pacman -Sy nvidia".  After that it's the matter of configuring it -- read this: [http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards]("http://wiki.archlinux.org/index.php/Beginners_Guide#NVIDIA_Graphic_Cards")

In general -- the Beginners Guide (where that link is from) should be your very very best friend during your first days with Arch.  Have fun.

---

### Post by floke on 2008-02-21
For everything you need to know:

[http://wiki.archlinux.org/index.php/Main_Page](http://wiki.archlinux.org/index.php/Main_Page)

---

### Post by bwtranch on 2008-02-21
> **ErusGuleilmus said:**
> Thank you all very much for your replies, they are very helpful. 
I have one more question to ask before I give installing Arch a go. How difficult is it to install the Nvidia drivers once I get X installed, so that I may have full 3d support? 

Thank You!
Hi! Thanks for the thanks! I was hoping you would take that the way I meant. I wasn't trying to be mean or anything:)
I had no problem with my nvidia FX5500 running AMD 64. I just followed the directions in the wiki and allowed the utility to create the xorg.conf file. Which it calls /etc/X11/FX86Config. I could probably do some further refinements to the file, but it works good enough for me right now. I think you're going to be really surprised at how well this works (Arch, that is). Then you can start learning about ABS and the AUR and all that cool stuff. Good Luck!

---

### Post by ErusGuleilmus on 2008-02-21
**fwojciec** , thank you for the link and command. I have no doubt that it will come in handy when I begin the install and setup tonight. 

**floke**, thank you for the link to the Wiki. This has already been an incredibly valuable resource already, thanks. 

**bwtranch**, no problem! Clicking the thanks icon is the least that I could do! I am VERY excited about trying Arch. Thank you for the support.

---

