---
title: "PowerMac G4 Install Problem"
date: 2005-02-16
forum: Apple PPC Users
---

### Post by bob_h on 2005-02-16
Hi - trying to install Warty on Powermac G4 Digital Audio running OWC cpu upgrade to 1.47ghz

Install process seems fine - however, on reboot (to complete second stage installation) the process freezes at line:

"openpic:exit"

Any ideas?

---

### Post by jr416de on 2005-03-05
I am having the same problem on a non upgraded MDD dual 1.25 G4

Any help for this?

---

### Post by procdan on 2005-03-06
OK, I'm a noob, but here it is...

On my DA (466 - no cpu upgrade), I see 'openpic' very briefly during the initrd stage of the boot. Perhaps your yaboot is not configured correctly to use initrd. I just read about some x86 users having problems with their initrd settings, too.

Previously, I only encountered problems with this when I *tried* (and mostly failed) to upgrade from Debian Woody to Sid (from kernel 2.4.18 to 2.6.1). When I installed Ubuntu from the disk they mailed me (from Switzerland! - Thanks!!), it installed and rebooted as smooth as silk, including hardware autodetect.

I don't know what to tell you to do, but you could try penguinppc.org/yaboot/ to see what's there. If you want, I'll post my yaboot config, though it may do you no good.

Best of luck.

---

### Post by noodles on 2005-03-17
Hi, I'm a total newbie. I'm running a dual g4 1.4ghz with 2gig of ram.

I was having the same problem, but I think it's a kernel problem not yaboot. It starts to load the kernel and after the openpict freezes. If you look at the top you will see the kernel number. Here is what worked for my dual processor, (I don't know what to do about the OWC one).

I first removed all my extra drives and ram and anyhting that might conflict. After many tries I got it to boot. I went to the synaptic manager under system- administration. I found the kernal, located under base, that ended with smp ( this is the kernel for dual processors) install it. Do not upgrade the default kernal as it will be written back into yaboot. If you do, type old at the boot promt. Now when you boot up you should see the kernel with the smp loading. I reinstalled all my ram and drives and it works great.

As I mentioned I am a total newbie but maybe this will help someone else find an easier way. good luck

---

### Post by MissIbuki on 2005-03-17
[QUOTE=noodles]Hi, I'm a total newbie. I'm running a dual g4 1.4ghz with 2gig of ram.

I was having the same problem, but I think it's a kernel problem not yaboot. It starts to load the kernel and after the openpict freezes. If you look at the top you will see the kernel number. Here is what worked for my dual processor, (I don't know what to do about the OWC one).

I first removed all my extra drives and ram and anyhting that might conflict. After many tries I got it to boot. I went to the synaptic manager under system- administration. I found the kernal, located under base, that ended with smp ( this is the kernel for dual processors) install it. Do not upgrade the default kernal as it will be written back into yaboot. If you do, type old at the boot promt. Now when you boot up you should see the kernel with the smp loading. I reinstalled all my ram and drives and it works great.

As I mentioned I am a total newbie but maybe this will help someone else find an easier way. good luck[/QUOTE]
 okay, I was having this problem. It's not the kernel-- it's yaboot. Yaboot, if you don't have kernel 2.4.x, still tries to boot that one on random points... when yaboot comes up, hit enter and force it to  "default linux". It should work from there. I'll find a workaround for it...

---

### Post by noodles on 2005-03-18
I don't understand. On my system it hangs with the 2.6.10-4 at the top after the openpict. With my new kernal it boots with the 2.6.10-5-smp and works. If I type old it starts to load the 2.6.10-4 and hangs. I thought it was the kernel, as the update fixed my system (but it also remapped yaboot). Is it a mapping issue to the kernel in yaboot instead? I think this is what you are saying. But if it is showing the kernal at the top dosen't that mean that it has started to load the right kernel? Or is that just saying that is the kernel it is going to try and load but can't actually find it?

---

### Post by bob_h on 2005-03-27
I have not had any luck with this but, according to the Gentoo forums, this is a kernel configuration problem relating to one or more of:

. framebuffer device configuration

. bootsplash configuration

See for example:

[http://forums.gentoo.org/viewtopic-t-172132-highlight-openpic+exitg.html](http://forums.gentoo.org/viewtopic-t-172132-highlight-openpic+exitg.html)
[http://forums.gentoo.org/viewtopic-t-298919-highlight-openpic+exitg.html](http://forums.gentoo.org/viewtopic-t-298919-highlight-openpic+exitg.html)

I am not able to test this under Ubuntu as I do not know how to recompile a kernel when I can't boot into the installation

Very sad

---

### Post by joxe on 2005-06-22
Hello!

I'm also an ab-so-lu-te-ly newbie in linux, and I'm experiencing the same problem. My G4 (AGP 350Mhz upgraded to 1,4Ghz, 1,3Gb RAM) will not boot Ubuntu (warty nor hoary) unless I remove some RAM to make it stay under 1Gb. I have tried the smp kernel but the result is the same: "openpic:exit". Oddly enough, the LiveCD boots flawlessly. Could anybody help? (Remember that I am absolutely new to linux. No idea on compiling kernels and such things! ;))

This is what I see when I try to boot linux with all my RAM installed:

[img]http://homepage.mac.com/joxe/.Pictures/ubuntuboot.jpg[/img]

Thanks for your help! XD

---

### Post by C.Mudj on 2005-07-04
um... that is exactly the problem I'm having with my AGP 350 Mhz, upgraded to 1.0 Ghz.  It's quite frustrating.  This latest post is nearly two weeks old... what happened?  Were you able to resolve it?  If so, how?

Thanks.

---

### Post by joxe on 2005-07-12
Hi there!

I finally got my machine to work by installing a new kernel. Found some help on compiling and installing the kernel in a spanish mac forum and, after trying quite hard, my G4 can boot Ubuntu now. The process is simple:


1.- Remove some RAM from your machine until it boots


2.- Get the *'kernel packge' *software from Synaptic


3.- Download the latest stable kernel sources from [www.ppckernel.org](www.ppckernel.org) (version 2.6.12.2, I think)


4.- Uncompress the kernel source files


5.- Open a terminal to the directory with the uncompressed files


6.- Type: 
      [PHP]make menuconfig[/PHP]
You'll see the kernel configuration menu. You can choose which hardware you want to support and which not. (Read the online help carefully!)


7.- Once finished configuring the kernel, you have to compile it. Type:
    [PHP]make clean[/PHP]
        This will remove some temporary files
    [PHP]make-kpkg kernel_image[/PHP]
        This will compile the kernel and create an installation file, it will take around 30-40 minutes to compile
    [PHP]make-kpkg modules modules_image[/PHP]
        I'm not quite sure wether this is neccesary, but do it just in case. It adds some software modules the new kernel migght need.

8.- Now, you'll have an install package in the parent folder of your source files, named *'kernel-image-2.6.12.2.powerpc.deb'*, or something similar. (If you have decompressed the source to /usr/source, the installation package will be at /usr/). From a terminal, go to that directory and type:


    [PHP]dpkg -i [name of the installation package without brackets]
[/PHP]
9.- Now you must edit the 'yaboot.conf' file to tell the bootloader where your new kernel is. Go to your /boot directory and look for the new kernel. It will be called something like *'vmlinux-2.6.12.2'*. Maybe it has an alias called just vmlinux that points to it.

10.-With gedit, for example, edit the /etc/yaboot.conf file, and add the following lines:

[PHP]image=/boot/vmlinux-2.6.12.2 (or whatever the name of your new kernel happens to be)
	label=mykernel
	read-only
	append="quiet splash"[/PHP]

11.-Close the file and, from a terminal, type [PHP]ybin -v[/PHP]

12.-Reinstall your RAM and reboot. After telling yaboot to boot linux, type mykernel when it asks for the boot options. If your kernel is well configured, it will boot with no problem.


If you want to skip steps 1 to 7, I might put the kernel installer I created somewhere so that you can download it and see if it works...

---

### Post by hot_pastrami on 2005-08-08
I'm having the same problem now that I finally got the first stage of the install to run.  Is the above posting *really* the solution to this problem?  If so, then the amount of effort needed to get Linux running on an unmodified PowerPC is pretty daunting, and I haven't got the ambition.  I'm hoping that there's a more straightforward solution, because I'd really like to start learning to use Linux.

Google searches for "openpic: exit" reveal lots of people with this problem, and not much useful in the way of solutions.  A common answer seems to be "remove some RAM and install again."  If Microsoft said that, users would be foaming.

---

