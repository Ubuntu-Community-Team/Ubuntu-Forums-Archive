---
title: "Where can I find the Kernel Source"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by lebski88 on 2006-09-30
Hello Everyone,

I'm trying to get my wireless card setup on a new Ubuntu install. I'm currently trying to get ndiswrapper installed. I've managed installed the make libraries and have run:

sudo make install

in the ndiswrapper directory. However I get an error as it cannor find the kernel build files. So I'm reasoning that the kernel source files aren't installed.

My question: where do I find the kernel source package for ubuntu?

uname -r gives me: 2.6.15-26-386

I can't use apt-get as I have no internet access on my linux box and the files don't seem to be on the standard cd download.

I've spent 2 hours trying to find the source files so any help would be truelly appreciated.

Thanks!

---

### Post by chuckyp on 2006-09-30
Well you could download the .deb for the headers.  Then burn it to cd and install it with dpkg that should be all you need to build ndiswrapper but I thought ndiswrapper was already installed in dapper.

Anyhoot the naming conventions would be like 
linux-headers-2.6.15-26-386

[http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.47_i386.deb]("http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.15/linux-headers-2.6.15-26-386_2.6.15-26.47_i386.deb")

Keep in mind you will also need build-essentials if its not already installed to build ndiswrapper from source.

---

### Post by lebski88 on 2006-09-30
Great thanks; I'm downloading that now.

I'm not sure if ndiswrapper is installed or not. If it was installed how would I find out? I'm a newbie...

---

### Post by llamakc on 2006-09-30
type:

dpkg -l | grep ndis

Hey, it is not installed by default on my edgy box.

---

### Post by chuckyp on 2006-09-30
What type of wifi card are you using because their may be a better way to do it other than ndiswrapper?

---

### Post by lebski88 on 2006-09-30
Thanks!

Yeh that doesn't return anything :-( I've got the kernel headers now but I'm still missing some of the build essential packages. Currently I'm passing files back and forwards with a USB drive. Every dependancy has a dependancy and on and on and on...

:-S

Bloody drivers!

---

### Post by chuckyp on 2006-09-30
Well build-essentials would be needed to make something from source.   What type of card is this again?

---

### Post by lebski88 on 2006-09-30
It's a US Robotics 802.11g Wireless Turbo PCI Adapter. It worked under SuSE 10.0 with ndiswrapper.

This is killing me; I'm missing GCC 4.0 (the C compiler) which I need to build the ndis.

When I install the package it seems to crash out and not install it. I have all the dependancies (as far as I know).

Is there a command to install .deb packages from the command line? The Package Installer is crashing out without giving me any messages and I thought the command line might offer more information as to why things weren't working.

Setting up a wireless card is certainly a crash course in linux!

Thanks for all your help on this btw!

Ben

---

### Post by chuckyp on 2006-09-30
dpkg is the command to install debs.  Haven't used it in a while though but should be sudo dpkg -i nameoffile.deb

You can always man dpkg to find out its usage options or info dpkg.

Also if you need to find a command try apropos as in,   apropos irc  will show a list of installed programs relating to irc.

---

### Post by lebski88 on 2006-09-30
OK so I found the command I wanted;

dpgk --install ***.deb

I found out that it was crashing out due to my version of binutils being too old. Reinstalling the correct version now and hopefully I will be able to continue.

---

### Post by chuckyp on 2006-09-30
The other option would have been to just install most of these packages from the cdrom?  there should also be an ndiswrapper.deb if that version will work with your wifi card.

---

### Post by lebski88 on 2006-09-30
Dammit! It is on the CD... along with build essentials... feeling very very stupid now. Managed to get GCC working after uninstalling the previous binutils package.

Still I've learnt a lot about managing packages so I suppose it's not really lost time.

Thanks for telling me about the apropos command; that's really useful.

Right now I have to try and get it working. Thanks again for your help!

---

