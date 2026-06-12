---
title: "Stuck using make, gives error no rule to make target"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by Online Gamer on 2006-03-22
Hi All
Just to let you know I am a Linux Noob and was mediocre at Windows, but I've followed a couple of how to's on compiling from source an rt2570 driver for my Belkin wireless usb stick. Problem is I think I've done and installed everything that I should but I still get this error on using make.

> steven@ubuntu:/usr/src/rt2570-1.1.0-b1/Module$ sudo make
make[1]: Entering directory `/lib/modules/2.6.12-10-686-smp/build'
make[1]: *** No rule to make target `modules'.  Stop.
make[1]: Leaving directory `/lib/modules/2.6.12-10-686-smp/build'
rt2570.ko failed to build!
make: *** [module] Error 1


Any help at all would be very much appreciated bearing in mind how unbelievably bad my understanding of linux is.

Thanks in advance
Online Gamer

---

### Post by dragonfyre13 on 2006-03-22
Sounds like it can't find the Make file. I think, when I compiled that, the make file was in a subdirectory. It took a second to hunt and peck, but open the folder in nautilus, and look through the folders below it for a file called "make"

There is no extension on the file name, so if you find one like that, ignore it.

If you can't find a file named "make", but do find a file named "make.unx" or "make.lnx' or something similar, rename it so it doesn't have an extension. Then run make in the folder where the file "make" is located.

---

### Post by engla on 2006-03-22
Often, one has to use ./configure first, like this:

./configure
make
sudo make install

Note that the only place where you need to be root/use sudo is the installation step. Skip sudo for the other commands, that will only give you permissions trouble.

---

### Post by Online Gamer on 2006-03-23
Thanks for the replies guys but still no Joy, dragonfyre13 there is a file calledMakefile in the Module subdirectory and make was run in this subdirectory to give the error quoted in the first post.

Engla there is no configure file to run ./configure before make it just seems to be a straight compile, except for me lol. Thx for the sudo tip.

If anyone needs some info from my system then I can use the CLI to get it and quote it in a reply. I'm one level above dense in the skill ratings lol.

If anyone else can help as I'm convinced it will be something simple I've done or not installed prior to this.

Thanks so far guys

Online Gamer

---

### Post by engla on 2006-03-23
Hm. I only have guesses, but:
Are you sure you run 'make' in the right directory? There seems to be a makefile in that directory, and it works.

That first makefile passes on to "/lib/modules/2.6.12-10-686-smp/build", where it expects a new makefile [this directory should be a symlink to /usr/src/linux or such, verify that]. This is your kernel source.. it could well be that this source tree is not setup as the module expects it; it might be that you have to "configure" in this directory too. However, being the kernel, it's not really easy. This is how it could be done, from memory:

1. Enter the kernel source top directory.
cd /lib/modules/2.6.12-10-686-smp/build
2. Copy your existing configuration to this directory
cp /boot/config-`uname -r` .config
3. Configure with that copied-in config
make oldconfig
Answer any questions if there are any with just enter (default choice)
4. Make until it's configured
make
You shouldn't have to wait for this to finish, you don't need a whole new kernel. 
Here it comes: I *think * you quit after all the HOSTCC lines seem to be done. Type ctrl-C to just break out of it there.

Now you can try again.

If you have issues, feel free to icq/irc/msn me if you want to chat about it -- it's much easier to resolve things like this "live"

[B]
Addendum:[/B] I noticed you are working in /usr/src [totally okay]. Doing that, you either have to add your user to the **src** group, or consistently use sudo for all commands. You can choose yourself, but being in the src group is safer and easier but you probably will have some problems with that since you already modified some files with sudo there. So just be consistent and stay with that..

**Addendum II:** You're not really doing standard easy stuff here, this is not what ubuntu is supposed to be. Most users trying to do this would get the same errors you do and follow basically the same path, the only thing that differs is the experience and thereby independence of problem solving in linux.

---

### Post by Online Gamer on 2006-03-24
Hi Engla, once again thanks for replying its so very much appreciated. I'm just checking on a friends p.c for replies to the post. Dont worry I'm not going to give up on ubuntu but I'm in the process of flattening my hard drives and re-installing ubuntu from cd. I think you are probably right seeing as I installed that kernel for hyperthreading support from synaptic and everything seemed OK. But I think it didn't install properly or synaptic just does a basic install and doesn't complete everything that ubuntu programs need to run. Hence you saying I may need to configure my kernel.

To cut a long story short I'm going to install afresh and use the default installation kernel and see if I can get this to compile.

This serves 2 things, it proves it's something I did or didn't do correctly or left synaptic to do and it doesn't secondly if this works with the default kernel I'll have learned something and be wireless with no wifey complaining about 20 meters of cat 5 trailing round the kitchen and over the cooker all the time.

Anyway thanks for your help    wish me good luck and I'll let everyone know the outcome via this thread as to what happens. If nothing else it may help everyone with this problem learn that you have to configure your kernel if you get this type of error.

Still an avid ubuntu linux fan and eager to play and learn (with a little help from my friends :-) ))

Thanks 
Online Gamer

---

### Post by antgbd on 2006-11-07
Hi,

I recently had the same problem, when trying to compile the helloworld module in the introduction to kernel hacking.

I was using the flowing line to run the make
make -C /usr/src/linux M=`pwd` modules

I since found out the reason that the Makefile was not being found is that pwd does not add escape characters to spaces. This caused the directory to be incorrect.

The solution to this is was either type in the address of the module manually or remove all spaces from folder names.

Hope this might help you find your problem,

just have a quick look around for the use of pwd and any spaces in folder names you may have.

   Anthony

---

### Post by Dymaxium on 2008-02-23
Wasn't expecting spaces in a folder name to be a problem, but that worked for me.  Thanks!!!

---

