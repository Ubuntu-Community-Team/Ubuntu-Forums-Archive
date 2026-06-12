---
title: "GA-M61P-S3 chipset driver help AM2 64 - Edgy Eft"
date: 2007-03-24
forum: Absolute Beginner Talk
---

### Post by megavolt1 on 2007-03-24
I cannot find the correct drivers (or procedure to install them)

Mother Board - GA-M61P-S3
Processor - AM2 64
OS - Edgy Eft
Kernel - Edgy Eft
Chipsets - GeForce 6100
                nForce 430

Things I have tried:

[INDENT][/INDENT]Swearing - this didn't help the situation, but I felt better

Recompiling forcedeth.c - this helped some. I could recognize the network card but as [INDENT][/INDENT]soon as I enabled it the system crashed, I'm sure I did something [INDENT][/INDENT]wrong??

See link: [https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346](https://launchpad.net/ubuntu/+source/linux-source-2.6.15/+bug/76346)

1)Download latest nvidia nforce package (I think)

2)For Dapper, I suggest you using forcedeth.c file contained under Fedora5 folder of the downloaded package (I used this one also)

3)Install build-essential plus linux-headers-2.6.15-27-amd64-k8 (I think I used the same version as my kernel but its all so fuzzy now)

4)Copy forcedeth.c into some folder, e.g. /.../desktop/forcedeth

5)Into this folder, make a file called "Makefile" containing the following line:
[INDENT][/INDENT]obj-m := forcedeth.o

6)Into this folder, execute the following command:
[INDENT][/INDENT]make -C /usr/src/linux-headers-2.6.15-27-amd64-k8/ [INDENT][/INDENT]SUBDIRS=$PWD modules

7)Copy the just created forcedeth.ko module into

/lib/modules/2.6.15-27-amd64-k8/kernel/drivers/net/
overwriting the old one

8)Execute this command: sudo depmod -a

9)Make a new initrd image: go into /boot/ folder, locate your initrd image, save it [INDENT][/INDENT]name, delete the file, and execute the following command:
[INDENT][/INDENT]mkinitramfs -o initrd.img-2.6.15-27-amd64-k8
[INDENT][/INDENT]10)Cross fingers and reboot ;)


Recompiling a new kernel (Which compiled fine didn't boot - I'm sure I did something wrong)

This kernel is supposed to support the new drivers

See link: [http://www.ubuntuforums.org/showthread.php?t=311158](http://www.ubuntuforums.org/showthread.php?t=311158)

1. Install the utilities needed to configure the kernel and move to /usr/src

Code: sudo apt-get install build-essential bin86 kernel-package libqt3-headers [INDENT][/INDENT]libqt3-mt-dev wget libncurses5 libncurses5-dev && cd /usr/src

2. Now we are going to download the kernel and unpack it.

Code: sudo wget [http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.20.tar.bz2) [INDENT][/INDENT]&& sudo tar -xvjf linux-2.6.20.tar.bz2

3. Now we are going to remove the link to the linux directory, make a new link to the new kernel, and move to the Linux directory:

Code: sudo rm -rf linux && sudo ln -s /usr/src/linux-2.6.20 linux && cd /usr/src/linux

NOTE: IF YOU WILL BE PATCHING THE KERNEL FOR A PROGRAM [INDENT][/INDENT](ex. fbsplash, bootsplash) APPLY THE PATCH AND SKIP TO STEP 6. [INDENT][/INDENT]IF NOT, GO AHEAD TO THE NEXT STEP.

4. Now download the latest kernel patch and become root: (Do NOT do this or the step [INDENT][/INDENT]below if you are using a different patch like beyond, emission, etc.)

Code: sudo wget [http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.20.3.bz2](http://www.kernel.org/pub/linux/kernel/v2.6/patch-2.6.20.3.bz2) && [INDENT][/INDENT]sudo -s -H

5. Apply the new patch: (Do NOT do this if you are using a different patch like beyond, [INDENT][/INDENT]emission, etc.)

Code: bzcat patch-2.6.20.3.bz2| patch -p1

6. Now import your current kernel configuration and configure the kernel:

Code: sudo cp /boot/config-`uname -r` .config && sudo make oldconfig && sudo make [INDENT][/INDENT]xconfig

[INDENT][/INDENT]IMPORTANT: READ THIS POST OR THE KERNEL MAY NOT COMPILE!
[INDENT][/INDENT]Hint: When make oldconfig is asking you questions, it is easiest to [INDENT][/INDENT]just hold down enter until it is finished.

7. Make yourself root if you are not already:

Code: sudo -s -H

8. Now time to build the kernel: Make sure that you are in /usr/src/linux with full root [INDENT][/INDENT]access. This will build a debian file that you can install.

Now in the terminal do this:

Code: make-kpkg clean
Code: make-kpkg -initrd --revision=386 kernel_image kernel_headers modules_image

Note: You can replace "386" with anything you want. Like "k7" or "686."
[INDENT][/INDENT]The kernel will now compile for 1-3 hours, depending on the speed [INDENT][/INDENT]of your processor. If you have an extremely slow processor, you [INDENT][/INDENT]may have to wait 3-4 hours for the kernel to compile. In the [INDENT][/INDENT]meantime, I would go out to a movie or do something else while [INDENT][/INDENT]the kernel is compiling.

9. Install the .deb files in /usr/src. There should be 2. One should be an image .deb file [INDENT][/INDENT]and the other a header .deb file. In terminal do:

Code: cd .. && dpkg -i *.deb

DO THIS FOR BOTH FILES.

IMPORTANT: IF YOU HAVE AN NVIDIA GRAPHICS CARD, YOU WILL HAVE TO REINSTALL THE DRIVERS FOR IT. REFER TO TROUBLESHOOTING BELOW.
  
10. Now reboot and you will have a faster system!


I reinstall edgy from scratch after this attempt!!

Can anyone help

Resigned,
megavolt1

---

### Post by megavolt1 on 2007-03-31
Still no good, please somebody help

---

### Post by megavolt1 on 2007-03-31
I got tired of waiting for a reply, so I downloaded and installed Ubuntu 7.04, Feisty Fawn Beta, and ALL!! of the problems were resolved right out of the box!

---

