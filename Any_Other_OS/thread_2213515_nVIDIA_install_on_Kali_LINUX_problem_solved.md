---
title: "nVIDIA install on Kali LINUX problem solved"
date: 2014-03-27
forum: Any Other OS
---

### Post by mehran1983 on 2014-03-27
Hi guys, do you still have problem with installing nVIDIA driver on you latest kali linux?
here is the solution for you, what I experienced was desperately following all others forums instructions, non of them worked for me
here is my laptop Specs:
nVIDIA 750M
Core i7 qm
Lenovo Y500
Kali Linux 1.0.6 amd64

what I finally understood was that all the linux kernels in kali repository are not complete
so I went to kernel.org  and downloaded the latest LTS kernel source
I compiled the source and get my own kernel-image.deb and kerne-headers.deb
the next thing I've done was removing the existing nvidia drivers module from DKMS by this command: dkms remove nvidia/331.49 --all
***note that in my case I had installed dkms of nvidia driver with 331.49 version you might not have it or it might be different version
the second thing I've done was that I removed all the nvidia installed packages from the os
apt-get remove nvidia-* --purge
apt-get remove nvidia* --purge

then I went to tty1 by simply hitting Ctrl+Alt+F1
logged in by root account
and then I disabled the current desktop manager, in my case I have KDE as my desktop X, so I disabled it by this command: service kdm stop
after it stopped the X desktop, I installed the nVIDIA driver as follow: 
./Nvidia-331.49.run -a --no-unified-memory
------------------------------------------------------------------
after this it will came up the screen, you must skip the dkms registration by simply choosing no for this dialog box
then follow the installation window and its up to you if you wanna have 32bit libs installed or not
then voila you have installed it

after it gives you the success message, choose the nvidia as you X desktop manager
then it will send you back to bash command environment
now you can back to graphical mode by this command: service start kdm
thats all, enjoy your nvidia full performance.

*** please keep in mind, while you are in a compiling stage of the kernel choose the **make xconfig **as your compiller command it will bring up the very nice gui interface, click on the menu and search for nouveau and disable it for nvidia and radeon ATI
then save it as your .config file

if you have no idea how to compile the new kernel I post the tutorial [here]("http://www.tecmint.com/kernel-compilation-in-debian-linux/")

goodluck

---

### Post by coffeecat on 2014-03-28
*Thread moved to **Other OS/Distro Support**.*

---

