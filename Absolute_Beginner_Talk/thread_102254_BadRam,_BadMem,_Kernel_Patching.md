---
title: "BadRam, BadMem, Kernel Patching"
date: 2005-12-11
forum: Absolute Beginner Talk
---

### Post by Pneuma on 2005-12-11
Hello everyone!

I've been lurking on these boards for a few months now.  Most of the problems I've run into with Ubuntu, such as installing rar support, video & sound codecs, etc, have been easily solved just by searching to see if someone else has dealt with the same obstacle.  However, now I've run into quite a big problem that I'm not sure how to fix.  It is way outside my scope.

First off, let me say that I'm a Windows user since 95, and have just recently made the switch to Linux.  I came to Ubuntu with the attitude that it was Windows without the chilling corporate shadow, security issues, spyware, viruses, and all the other things that make Windows a pain in the ass.  I found quite quickly that switching to Ubuntu was just trading one set of problems for another -- I had traded the problems of the Windows corporate hell for the problems that stem from my complete ignorance in managing a Linux system.    But that's okay -- with effort I can dispel that ignorance and become proficient with this great new OS.  No amount of effort on my part will make Windows any different than what it is.

I've shed the insulation Windows offered me with it's constant pampering, and truly I'm out in the cold.  I feel like I felt the day I moved out of my parents' house.  But the effort and willingness to learn how to survive in this new world is there.  Giving up on Linux and moving back to the increasingly insulting Windows environment would take an enormous toll on my self-esteem.

My PC is quite old.  Not long after first installing Ubuntu, I discovered that my PC's RAM contains bad addresses.  These bad addresses affect Ubuntu's stability very much.  If I attempt to do anything memory-intensive, such as watching a video, my machine is doomed to lock up within 45 seconds.  Imagine my surprise when I was searching Google for a copy of my manufacturer's warrenty policy (which has expired) only to discover that in fact you can tweak the kernel to avoid bad addresses!  My jaw fell agape at that innovation, and I was quite happy that I, a poor college student, might be able to stabilize his machine without losing money.

</blathering>

This leads me to my question.  I downloaded the BadMem source code and it's utils, read through the howto document included, and am attempting to follow the directions.  I've been halted at the compiling process, which is completely new to me.  This is the error I receive:

root@morgan:/usr/src/badmem/badmem-utils-v1.6# ./configure
checking for gcc... no
checking for cc... no
checking for cc... no
checking for cl... no
configure: error: no acceptable C compiler found in $PATH
See `config.log' for more details.

At first I figured I had dropped all the BadMem source code into the wrong directory, because I wasn't sure where else to put it.  /usr/src seemed appropriate because I am a user, and this is some source code.  Should it be located somewhere different?

And so I'm stuck.  It seems that I need first to learn about C compilers and how to properly use them.  After that, to patch my kernel with the badmem util I need to learn about kernel compiling.   I've hunted around for tutorials on these subjects, but I've not found anything specifically relevant to my situation.  If someone could point me to some information that would equip me, a total linux newbie, to compile this kernel patch, recompile his kernel successfully, so that I can isolate the memory addresses that are causing problems (i've already done an intensive memtest86 run and have all the addresses written down), that would be extremely helpful!  Thanks so much.

---

### Post by jdong on 2005-12-11
IIRC BadMem needs a kernel patch, in which case you'll need to recompile the kernel. There are a few kernel compilation articles around here, but they are not for the faint of heart -- you need to know what kernel modules your hardware requires.


But to get your started, mark build-essential and gcc-3.4 for install using the Synaptic Package Manager or similar APT tool.

---

### Post by hod139 on 2005-12-11
Welcome to the linux community.  Reading through your post, the first thing you need to install is the meta-package build-essential
```

sudo apt-get install build-essential

```
that will install everything necessary to compile code.  You might run into other dependencies though trying to compile this, so just keep posting with future questions.

---

### Post by az on 2005-12-11
I have a working linux-image-686 with badram patch working sitting on my desktop right now....

Are you running a 686? (Pii or better?)


I didn't do 386 (Damn!) and I flushed the source.  But it is easy to do if you are having trouble.

---

### Post by Pneuma on 2005-12-11
I'm using a 1.1 ghz AMD Athlon processor.  I have a single faulty 256 MB DDR DIMM.  The BadMem 'Howto' says that recompiling a kernel with bad ram is a bad idea.  However, all my bad addresses are in higher areas of ram (>160MB), so I'm going to attempt this with the one bad module.

After installing the "build-essential" package, I've sucessfully compiled and installed the badmem utilities package.  There appeared to be no problems.

These are the commands I used:

./configure (no problems)
make (no problems)
make clean (no problems)

I picked this up from a compiling tutorial.  As near as I can tell everything compiled and installed correctly and I did not miss any steps.

The 'howto' now says to "download, unpack, and configure your kernel as you are used to doing".  I am not used to doing this.  I got my Ubuntu CD from a friend!  It downloaded, configured, and compiled itself!

I appreciate all support very much.

---

### Post by hod139 on 2005-12-11
[QUOTE=Pneuma]
These are the commands I used:

./configure (no problems)
make (no problems)
make clean (no problems)
[/QUOTE]

I think what you really want to do is:
```

./configure 
make 
sudo make install

```

make clean actually deletes the executable(s) and object files in the directory.  make install installs them, and you usually need root rights to install, which is why I said to put sudo in front.

---

### Post by az on 2005-12-11
I believe the badmem page is outdated.  It mentione the 2.2 kernel.  I know that the badram patch is available for much more recent kernels (think last month, not 2001)

You need to recompile the kernel becaue the badram patch it not something that can be modularised.  Also, compiling the kernel is very memory-intensive, so you would have to pull out your bad memory stick to do this.

From the top of my head, you install build-essential gcc-3.4 linux-source-2.6  and kernel-package

(I will assume you are running the k7 kernel for your AMD processor)

You get the patch from the badram page 
[http://rick.vanrein.org/linux/badram/download.html](http://rick.vanrein.org/linux/badram/download.html)

[http://rick.vanrein.org/linux/badram/software/BadRAM-2.6.12.1.patch](http://rick.vanrein.org/linux/badram/software/BadRAM-2.6.12.1.patch)

uncompress your kernel source

cd /usr/src
sudo tar xvjf linux-source*
cd linux-source*
sudo cp /boot/config/config-2.6.12-9-k7 .config
sudo patch -p1 < ~/BadRAM-2.6.12.1.patch   #(assuming you saved it in your home directory)

Then you build the kernel.

sudo make-kpkg --initrd --append-to-version=-badram --revision=1 --stem=linux kernel_image kernel_headers

It will ask you to configure badram support and you should say "y" for yes.
"Work around bad spots in RAM (BADRAM) [Y/n/?] (NEW)"

That should take a few hours.  The install the .deb files that creates.  When you boot, you should boot into your new cusom kernel.

sudo dpkg -i linux-image-2.6.12-1-badram.deb

Good luck.

*edit1: I have been meaning to make a 386 version.  I will see if the above works verbatim...
*edit2: compiling.   Should be done by 7am tomorrow on my old hardware :)

---

### Post by Pneuma on 2005-12-11
If it's as simple as recompiling with the patch and then informing the new kernel of the bad addresses with a conf file, then what is the purpose of installing the badmem utils on the page?  Are they outdated and irrelevant? If they are, should they be removed before continuing?

The kernel source that I am uncompressing, is this the kernel I am running locally right now?  Or am I downloading another kernel and then overwriting the one I already have patch-included compilation of that kernel?

I do not know whether or not I am running the K7 kernel.  I am running whatever kernel was compiled upon installation.

I only have the one faulty ram stick.  I have no access to others.  The bad addresses are all in the >160MB range.  The BadMem Howto says that bad addresses in upper range should be OK for recompiling the kernel.  Do you suppose the risk is too great of ending up with a corrupt kernel or no kernel at all?

---

### Post by az on 2005-12-11
[QUOTE=Pneuma]If it's as simple as recompiling with the patch and then informing the new kernel of the bad addresses with a conf file, then what is the purpose of installing the badmem utils on the page?  Are they outdated and irrelevant? If they are, should they be removed before continuing?[/QUOTE]

Badram uses boot prompts.  The parameters passed to the kernel by grub on the kernel line, for example.

Ubuntu installs memtest86.  You can boot into memtes86 and see where your errors are.  There is a setting in memtest to display the errors in a format that is useable by the badram patch.  Just add that to your grub menu.list in /boot/grub and boot into a badram-enabled kernel and you are done.

Example:  /boot/grub/menu.list excerpt:

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash badram=0x13495568,0xfffffff,0x13495568,0xfffffffc

 ...
Then you run sudo update-grub

...


title           Ubuntu, kernel 2.6.15-7-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-7-686 root=/dev/hda1 ro quiet splash badram=0x13495568,0xfffffff,0x13495568,0xfffffffc
initrd          /boot/initrd.img-2.6.15-7-686
savedefault
boot



You can also change the boot prompt by hitting "e" for edit in the grub menu when you boot and editing the kernel line to add the "badram=....." parameter

[QUOTE=Pneuma]The kernel source that I am uncompressing, is this the kernel I am running locally right now?  Or am I downloading another kernel and then overwriting the one I already have patch-included compilation of that kernel?[/QUOTE]

If you are running breezy, then yes, 2.6.12-9-386 is your runing kernel.  You are going to compile it and make it into a package with a different name and version number than your running kernel.  They will get installed side-by-side so that if the custom kernel does not work, just reboot and pick the original one in grub and you will boot it.

[QUOTE=Pneuma]I do not know whether or not I am running the K7 kernel.  I am running whatever kernel was compiled upon installation.[/QUOTE]

386 is the stock kernel because it runs on everything.  You may notice a performance bootst by running a k7 kernel on AMD since it can use AMD-specific optimisations.  A lot of people do not even bother.

[QUOTE=Pneuma]I only have the one faulty ram stick.  I have no access to others.  The bad addresses are all in the >160MB range.  The BadMem Howto says that bad addresses in upper range should be OK for recompiling the kernel.  Do you suppose the risk is too great of ending up with a corrupt kernel or no kernel at all?[/QUOTE]

I'll put the one I am making on the web and you can download it.  I will leave the url in the morning.

You can try compiling yourself.  Your computer may crash because it is CPU intensive and I think it will use all the memory it can.  Not sure.  I think the compilation will fail with errors before it builds you a corrupt kernel.

I compile a kernel to see if a used CPU fan is worth keeping or not.

---

### Post by az on 2005-12-11
Yes, I asked about incorporating the badram patch into the stock kernel.  No answer.

[http://lists.ubuntu.com/archives/kernel-team/2005-November/000607.html](http://lists.ubuntu.com/archives/kernel-team/2005-November/000607.html)

---

### Post by psusi on 2005-12-11
I would sugest that you run memtest86, choose that option from the grub boot menu.  You mention that all the bad ram is above 160 MB, so do you know that because you already ran memtest86?

If you know the bad ram is above 160 MB, then add "mem=160M" to the kernel command line to tell it not to use more than 160 MB.  If all the ram above 160 MB is bad, then you should just stick with this.  If only some is, then using this option should give you a stable system on which to recompile the kernel with the badmem patch so you can use the parts of ram above 160 MB that are still good.

---

### Post by az on 2005-12-12
[QUOTE=azz]I'll put the one I am making on the web and you can download it.  I will leave the url in the morning.[/QUOTE]

Snuffed it up.

Right.  The instructions seem to work fine, but the kernel I built using a sorta hybrid-Breezy-Dapper toolchain will not install on breezy because it needs a later version of intramfs.  Bummer.

I will build it on a breezy box later today.

---

### Post by az on 2005-12-13
It seems to work.  It boots and works fine.

[http://apqi.com/ubuntu/linux-image-2.6.12-badram_1_i386.deb](http://apqi.com/ubuntu/linux-image-2.6.12-badram_1_i386.deb)
[http://apqi.com/ubuntu/linux-headers-2.6.12-badram_1_i386.deb](http://apqi.com/ubuntu/linux-headers-2.6.12-badram_1_i386.deb)


This is a custom kernel and has no security updates.   You can compile linux-restricted-modules or any other extra kernel driver for it, if you need them, using the linux-headers package.

---

### Post by jdong on 2005-12-13
Azz -- to be in accordance with the GPL you must also host/post URL's for source packages. Not trying to be a PITA, honest, but I've been burned many times around here for doing the same.

---

### Post by az on 2005-12-13
[QUOTE=jdong]Azz -- to be in accordance with the GPL you must also host/post URL's for source packages. Not trying to be a PITA, honest, but 
I've been burned many times around here for doing the same.[/QUOTE]

You're right.  I am not a fan of custom-build debs and scripts being posted willy-nilly, myself.

I will compress the tree and post it.  The URL is
[http://apqi.com/ubuntu/linux-source-2.6.12-badram.tar.bz2](http://apqi.com/ubuntu/linux-source-2.6.12-badram.tar.bz2)

I do not reccommend anyone using this, though.  Please see the previous post with the description of how to install the linux-source from ubuntu and patch it with the badram patch.  You will have access to security updates, that way.

---

### Post by scunc_dvl on 2005-12-18
Another badram patch request:

I successfully compiled a new kernel with the badram patch for kernel 2.6.12, from VanRein's site (I don't know why debian.org maintains a really old patch...), and everything seemed okay except no appropriate log message came up with "dmesg|grep Memory"... a little investegation made me realize I was still thinking in the old and the patch had no 64-bit code in it.

My absent-mindedness was confirmed when I looked at the site and there was only an untested 64 bit version of the patch for the later kernel version, 2.6.13.

ACK!! And* it's just roughly 500 lines of code, which tempted me to work on it myself...But I would really like to have someone hammer something out, since it's probably close to it's debugging stage as it is already.* (Clearly I'm at a newbie stage because I'm posting here rather than asking the developers themselves... And this is my first post ever :P ).  

(For code that size, I think it would be a blessing to have it in the stock kernel too, count me in for that)

Though my case is hardly urgent, the address at MB 418 is so rarely touched by anything, what's more urgent is me NOT spending my money on the expensive ram that I should've put in my Athlon 64..which is another hindsight mistake, don't put cheap ram in an athlon UNLESS badram is there (and working) to protect you :P

((PS I'm also thinking of a tool similar to DOS's debug.exe, a non-virtual memory reader (or HEX dumper) or something to that effect, does such a thing exist for Linux or are "nearpointer hacks" non- existant since the death of Windows 95? )

---

### Post by yurtboy on 2006-09-20
thanks for posting the kernel deb package.
saved me a bit of work.
Al

---

### Post by dm1024 on 2007-06-01
Did anyone tried it with 2.6.20 / 2.6.22 kernel?
I haven't success.

---

