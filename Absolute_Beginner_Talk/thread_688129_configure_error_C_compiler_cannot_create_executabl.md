---
title: "configure: error: C compiler cannot create executable"
date: 2008-02-05
forum: Absolute Beginner Talk
---

### Post by Jmejme on 2008-02-05
kk heres thee deal im trying to compile and install an alsa driver because i like many others am having sound issues but when i do the ./configure command this is the what i get

```
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.
```

does anyone know whats going on here do i need to update something or download something?? i can post the config.log file too if needed

Please and thankyou

---

### Post by Jmejme on 2008-02-05
...nothing..? please ????

---

### Post by jw5801 on 2008-02-05
Hmm... that doesn't look particularly nice! Have you installed the build-essential package? ```
sudo apt-get install build-essential
```
Have you managed to compile anything else before this? We might be able to trace the problem a little better if you post the "config.log" too.

What leads you to believe you need to compile and install your own driver to fix an audio problem? I wouldn't have thought that was necessary... But I'm no expert on audio issues!

---

### Post by Jmejme on 2008-02-05
i have before yes and i dunno thats what i was told to do here

[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

i was pointed here from another post

---

### Post by Jmejme on 2008-02-05
```
configure:2084: checking for gcc
configure:2100: found /usr/bin/gcc
configure:2111: result: gcc
configure:2349: checking for C compiler version
configure:2356: gcc --version >&5
gcc (GCC) 4.1.3 20070929 (prerelease) (Ubuntu 4.1.2-16ubuntu2)
Copyright (C) 2006 Free Software Foundation, Inc.
```

Does this have something to do with it....do i not have an updated version and how do i update it... if i need to

---

### Post by Jmejme on 2008-02-05
once again ...left lol ....im assuming i have to be a bit persistent lol

---

### Post by jw5801 on 2008-02-05
Be patient! If you want instant help, try the irc channel. I wandered off to watch TV for a little bit. I take it that the second post was your config.log?

Hmm... actually a fairly simple problem! You're compiling in /usr/src/ which is a directory you don't have permission to write to as a regular user. Did you run ./configure, or sudo ./configure? If sudo ./configure doesn't work (I seem to recall that that format returns as error) you can either sudo into root "sudo -s" and then run "./configure" (exit or ctrl+d will get you out of root) or you could try "sudo bash configure" and see how that works for ya.

---

### Post by Jmejme on 2008-02-05
well yes i have learned that patience is a virtue :) i understand that not everyone is waiting around just to help me. i had hw to so lol. but i tried everything you told me even tried moving the files to my documents dir. same error every time...any clue? im stumped im gonna google it a little more

---

### Post by jw5801 on 2008-02-05
Which part of the howto are you struggling with? Are you trying to compile alsa-driver, alsa-lib or alsa-utils? Since everything you're running you need to run as root my approach would be to switch users into root (for just the terminal you're in) using ```
sudo -s
```then you can drop the "sudo" in front of all the other comands which might give you a little more success!

---

### Post by [Jamie] on 2008-02-06
I get this error when i try to compile anyhting.

Everything ive tried comes up the same. Could it be somethinbg to do with the install?

---

### Post by jw5801 on 2008-02-06
Could you try running it again and post the entire terminal output, including everything that you've done here? It will hopefully be something simple, like permissions on a directory being strange, rather than an issue with the toolchain itself (binutils and gcc).

---

### Post by [Jamie] on 2008-02-07
right,

This is an attempt to install the IDE Anjuta.

Console Output:
```
jrichardson@JRichardson:~$ cd /media/disk/anjuta
jrichardson@JRichardson:/media/disk/anjuta$ sudo ./configure
[sudo] password for jrichardson:
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for a thread-safe mkdir -p... /bin/mkdir -p
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... 
configure: error: C compiler cannot create executables
See `config.log' for more details.
jrichardson@JRichardson:/media/disk/anjuta$
```

---

### Post by jw5801 on 2008-02-07
This would be installing off a CD yes?

Try copying the whole lot to your hard drive (somewhere in your home directory) and then running the command there. I believe that ./configure is attempting to write a makefile to your current directory, which it can't do since it's on a read only disc!

---

### Post by erginemr on 2008-02-07
You should make sure that you have the build-essential meta package installed:
```
sudo aptitude install build-essential
```
Can you please also try:
```
sudo aptitude install libc6-dev g++ gcc
```

---

### Post by Cypher on 2008-02-07
Let's try something even more basic to see if you have the necessary headers in place. Type the following in your favorite text editor and save it as hello.c
```

#include <stdio.h>

int main(void)
{
    printf("Hello World\n");

    return 0;
}

```
Once saved, from the command line compile the program with
```

gcc -o hello hello.c

```
Execute the program with "./hello" and you should get the "Hello World" print out. If that all works, then the basic compiler is working and the headers are there. If the program doesn't compile, then we will debug further..

---

### Post by [Jamie] on 2008-02-07
i tried what you said and get the error:
```

jrichardson@JRichardson:/media/disk$ gcc -o hello hello.c
hello.c:1:19: error: stdio.h: No such file or directory
hello.c: In function ‘main’:
hello.c:5: warning: incompatible implicit declaration of built-in function ‘printf’
```

so im guessing the headers arent right!

---

### Post by jw5801 on 2008-02-07
Please install build-essential as I suggested in my first post.

---

### Post by [Jamie] on 2008-02-07
ive used

```
 sudo apt-get install build-essentials
```

but it comes up with package not found... ill try the other code.

---

### Post by erginemr on 2008-02-07
It should be "build-essential" with no "s" in the end. When you start typing a few letters, press Tab and Linux CLI will auto complete the package name for you.

You should also try: "sudo aptitude install libc6-dev g++ gcc"

---

### Post by stevescripts on 2008-02-07
You are really gonna need build-essential - try it without the s at the end ;)

Steve
(who sees somebody beat me to the punch ;)  I must be typing too slow ...)

---

### Post by [Jamie] on 2008-02-07
righty... that has a better effect!  (my bad there)

it then asks for the ubunto 7.10 release cd, the disk i have is: 

"ubuntu-7.10-desktop-i386.iso" 


and i get an error: 

"Cannot mount the selected drive" (i have searched the forums and will try a few things for this problem!)

---

### Post by jw5801 on 2008-02-07
> **'[Jamie] said:**
> righty... that has a better effect!  (my bad there)

it then asks for the ubunto 7.10 release cd, the disk i have is: 

"ubuntu-7.10-desktop-i386.iso" 


and i get an error: 

"Cannot mount the selected drive" (i have searched the forums and will try a few things for this problem!)

So you don't have an active internet connection on your Linux box? Because that means that apt is attempting to access the packages that are on your CD rather than those in the online repositories. If it's not mounting properly make sure your CD drive is listed in /etc/fstab with a mountpoint of /media/cdrom (or post your /etc/fstab) and that the Ubuntu CD is in the drive!

---

### Post by [Jamie] on 2008-02-07
yeah, i dont have a connection just yet... i will as soon as i get some rj45 cable ends!

will this mean that gusty wont look on the cd for the packages?

will just go get my fstab and post that up cos getting the drive to mount would be useful too!!

---

### Post by jw5801 on 2008-02-07
Gutsy should look on your CD, in fact it appears to be set up to do so, we'll just have to work out why it can't mount the disc!

---

### Post by [Jamie] on 2008-02-07
fstab is as follows:

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda2
UUID=7cce629c-4314-4cc7-9120-b872c98e5fff /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda5
UUID=172af942-db38-4da5-8d15-187933e953ec none            swap    sw              0       0
/dev/scd0       /media/cdrom0   auto	user,noauto,exec	0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0	0
```

---

### Post by jw5801 on 2008-02-07
Hmm... /dev/scd0 doesn't sit right with me... If you put the CD in the drive does gnome mount it nicely for you? If so can you let it do that (you should see an icon for it on your desktop) then open up a terminal and run the command "mount" then post the output here for me?

---

### Post by zvacet on 2008-02-07
> /dev/scd0       /media/cdrom0  	udf,iso9660 user,noauto,exec	0       0

Before you do this change you can back up fstab file just in case.

---

### Post by [Jamie] on 2008-02-07
no, gnome doesnt mount it either...

i get nice icons for my hard disks, but nothing for the CD...

i know the drive at least was working because the windows 98 system i installed from ran the install cd fine but anything subsequently doesnt seem to work, i can mount USB devices fine as well.

---

### Post by [Jamie] on 2008-02-07
> /dev/scd0 /media/cdrom0 udf,iso9660 user,noauto,exec 0 0
Before you do this change you can back up fstab file just in case.

thats what was there before... i changed it to current from a suggestion in another thread, with no effect.

---

### Post by jw5801 on 2008-02-07
Hmm...
Well lets just see if we can mount it at all, try running:
```
sudo mount /dev/scd0 /media/cdrom
```
If it tells you something about not being a block device and trying with the loop option (I know it's required to mount .iso, can't remember for cdrom) then use:```
sudo mount -o loop /dev/scd0 /media/cdrom
```

---

### Post by jw5801 on 2008-02-07
I posted and then realised you'd posted back, which made my post redundant so I edited it with another option! Thought I'd better post again in case the edit got missed.

---

### Post by stevescripts on 2008-02-07
I wonder if the OP installed from the livecd?

*IF* I recall correctly - build-essential was not on my livecd (it is at work, will check
in the morning).

I *do* distinctly recall that synaptic went to the net to fetch build-essential and friends,
which, is painstakingly slow on dial-up.

Steve

---

### Post by jw5801 on 2008-02-07
There are quite a few packages on the LiveCD that aren't part of the default install (I'm not honestly sure why build-essential isn't part of the normal install), but can be installed later. The way apt works is to install the newest versions of software it has available from it's sources, so if you have a working internet connection, it will ignore the LiveCD entry in /etc/apt/sources.list as the packages in the online repositories are more up-to-date.

build-essential is definitely on the LiveCD, it's the first thing I install every time I install the OS, as I need it to compile ndiswrapper to get my wireless network card working.

---

### Post by stevescripts on 2008-02-07
> **jw5801 said:**
> 
...
build-essential is definitely on the LiveCD, it's the first thing I install every time I install the OS, as I need it to compile ndiswrapper to get my wireless network card working.

jw5801 - Thank you for clearing that up!

Steve
(BTW - was just visiting with (and getting help from ) one of your contrymen) :)

---

### Post by raffytaffy on 2008-02-07
Had similar problem to you.. I had to export cflags like so
> export CFLAGS="-O2 -mtune=k8 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"

Please note I am on a amd box

---

### Post by [Jamie] on 2008-02-09
back again, sorry for the delay.

i got my linux box online last night and have managed to install build-essential and everything is now good...

except i still cant mount the cd, would be nice to get this fixed!

RaffyTaffy
> 
export CFLAGS="-O2 -mtune=k8 -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions"

what does this do?

---

### Post by jw5801 on 2008-02-09
> **jw5801 said:**
> Hmm...
Well lets just see if we can mount it at all, try running:
```
sudo mount /dev/scd0 /media/cdrom
```
If it tells you something about not being a block device and trying with the loop option (I know it's required to mount .iso, can't remember for cdrom) then use:```
sudo mount -o loop /dev/scd0 /media/cdrom
```

I think my post got lost on the previous page :) give it a shot from the command line and see what happens!

---

### Post by jw5801 on 2008-02-09
> **'[Jamie] said:**
> 
RaffyTaffy


what does this do?

Those are options to pass to the C compiler (the thing that was spitting out errors), they should be defined in a default file somewhere to be accessed by the program "make," which reads the Makefile and compiles the program for you. If they're not properly defined, or you need specific options to compile something then the CFLAGS variable is the place these are set to. The command given alters the CFLAGS variable, thus altering the options passed to the C compiler.

---

### Post by [Jamie] on 2008-02-09
oh righty... shan't need that then cos the compiler is working now. all it needed was build-essential off the net.

---

