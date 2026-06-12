---
title: "I cannot install anything after an &quot;partial upgrade&quot;"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by PeterP24 on 2008-01-11
Hi ! A few days ago after a long vacation I finally connected my laptop to the internet. The first thing I did was to run the Update Manager because it apeared to have some interesting upgrades. It apeared an message telling me that I can make only an partial upgrade (probably some of the upgrades couldn't be installed). I proceeded but then, at the end of the operation the Update Manager failed with an error. Since then I cannot install anything (neither by Synaptic nor by apt-get). Every installation fails, after downloading the packages, with the folowing error :
> [I][I]Reading package lists... Done
Building dependency tree       
Reading state information... Done

%bla bla bla - depending on the size of the program, his state, etc. ...%

Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic
E: Sub-process /usr/bin/dpkg returned an error code (1)[/I]


I'm using Ubuntu Gutsy 7.10 . Everything else works, except the installation of programs.I've searched this forums for posts related to my problem but I failed to find some answers. I have an Dell Inspiron 1501 (amd64) (if this information might help). 

Thanks in advance for your answers

---

### Post by oldos2er on 2008-01-11
Go to System, Administration, Software Sources, and make sure all the boxes are checked.

 If that doesn't fix your problem, please post back.

---

### Post by PeterP24 on 2008-01-12
Thank you for your response!

The only box unchecked was the Source Code box which is checked now. After pressing the reload button it apeared an window with the title :
* Could not download all repository indexes* 
with the  address in cause 
:* [http://archive.ubuntu.com/kubuntu/dists/gutsy/main/binary-amd64](http://archive.ubuntu.com/kubuntu/dists/gutsy/main/binary-amd64)....*

I've tried to install some programs (amule and electric cad).  It apears through that the programs were installed but the errors still persist at the end of the installations. Any advice on what to do next will by highly appreciated.

Best regards

Peter

---

### Post by fatality_uk on 2008-01-12
Have you previously manually changed your sources.lst? If so, reset the changes and try again.

---

### Post by PeterP24 on 2008-01-12
Thank you for your response!

The only box unchecked was the Source Code box which is checked now. After pressing the reload button it apeared an window with the title :
* Could not download all repository indexes* 
with the  address in cause 
:* [http://archive.ubuntu.com/kubuntu/dists/gutsy/main/binary-amd64](http://archive.ubuntu.com/kubuntu/dists/gutsy/main/binary-amd64)....*

I've tried to install some programs (amule and electric cad).  It apears through that the programs were installed but the errors still persist at the end of the installations. Any advice on what to do next will by highly appreciated.

Best regards

Peter

---

### Post by HermanAB on 2008-01-12
Simple fix:
Re-install Ubuntu.  It only takes about 30 minutes and provided that you have a separate /home partition, you don't even need to back-up anything.  If not, now you know why you should have a separate /home partition...

Then in future remember: "Don't fix it if it ain't broke!"  

More Linux problems are caused by updates, than are fixed by updates.  I re-install my systems once per year to get the latest version and I don't do updates, unless there is a very, very good reason.
Cheers,

Herman

---

### Post by PeterP24 on 2008-01-13
My appologies for posting twice my previous answer.

Yes, I you're right. I've tried for a whole week to fix this problem, and I think that I should have spent 30 minute to reinstall Ubuntu instead of searching for a solution.  I don't have the separate /home partition but I will create it in the next installation of Ubuntu. Now I see for my self  the use of the separate /home partition. I also agree with you, regarding the upgrades ( I've remember when I've made the passage from Feisty to Gutsy via upgrade from the server - after many problems I made an clean install from the cd)i, but I've upgraded Gutsy  a few times (mostly for having the latest versions of the programs I generally use : open office, gimp, amarok, etc.) and now is the first time when I experience problems. Still, I would like to use the option of the reinstallation as a last resort since the reinstallation of Ubuntu would bring a lot of new problems (related to drivers and other stuff which for the current installation are solved) which needs to be solved again. Another reason would be and here I quote an advice a friend gave to me : "for a problem in linux try to find an answer; don't reinstall unless you don't have another option. To reinstall the OS to solve the problem is specific to Windows ". 

To answer to a previous post : I did not modify manually the source.list thorough I've added some kubuntu repositories though Synaptic.

Thank you all for your help

Best regards

Peter

---

### Post by Xavieran on 2008-01-13
before you reinstall try > sudo dpkg --configure -a

---

### Post by PeterP24 on 2008-01-13
I did. Here is the output :
 [QUOTE]sudo dpkg --configure -a
[sudo] password for pierre:
Setting up linux-image-2.6.22-14-generic (2.6.22-14.47) ...
Running depmod.
update-initramfs: Generating /boot/initrd.img-2.6.22-14-generic
/usr/sbin/mkinitramfs: 13: getopt: not found
Terminating...
update-initramfs: failed for /boot/initrd.img-2.6.22-14-generic
Failed to create initrd image.
dpkg: error processing linux-image-2.6.22-14-generic (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 linux-image-2.6.22-14-generic

---

### Post by Xavieran on 2008-01-13
Sadly it looks like you will have to reinstall...:(

Errors installing a kernel must be bad...:(

---

### Post by PeterP24 on 2008-01-14
Oh, ok. Thank you all for your advices 

Peter

---

