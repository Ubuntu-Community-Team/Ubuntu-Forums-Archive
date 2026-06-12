---
title: "Make command Errors."
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by wydra on 2007-11-17
I've looked at all of the similar threads to this one, I seem to be haing a problem with my kernel when I try to run the make command, but I have no Idea how to set up the kernel correctly to get it to work. Can someone please help me?

I'm running on a HP Pavillion dv5000

Ubuntu 6.06 Dapper Drake

HMD Turion x64 Mobile Technology Processor.

BTW: I find it wierd that the x64 version of Ubuntu doesn't work with that Chipset.

---

### Post by p_quarles on 2007-11-17
What are you trying to compile? Can you post the error message here?

---

### Post by qpieus on 2007-11-17
Have you installed the build-essential package?```
sudo apt-get install build-essential
```

---

### Post by shearn89 on 2007-11-17
If it gives error messages like "libxxxx >= #### required, #### installed", you may need to install the -dev package of the library it says. 
Eg. it says something about libgtk2.x.x, you have it installed, so try installing libgtk2.x.x-dev. Normally works.

---

### Post by wydra on 2007-11-18
Here's the error:

```

wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ make
make -C driver
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-29-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make: *** [all] Error 2
```

Thank you for responding so quickly, I haven't had a chance to look till now, I was at the movies. Your help is greatly appreciated.

---

### Post by FuturePilot on 2007-11-18
Have you run 
```
./configure
```
first?

---

### Post by wydra on 2007-11-18
No, there was nothing in the install guide about that. lemme give it a shot

EDIT: Nope, it doesn't work, it gives me a bash complaint. Say there is no file or dir.

---

### Post by dwhitney67 on 2007-11-18
> **wydra said:**
> Here's the error:

```

wydra@wydra-laptop:~/Desktop/ndiswrapper-1.49$ make
make -C driver
make[1]: Entering directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
Makefile:35: *** Cannot find kernel version in /lib/modules/2.6.15-29-386/build, is it configured?.  Stop.
make[1]: Leaving directory `/home/wydra/Desktop/ndiswrapper-1.49/driver'
make: *** [all] Error 2
```

Thank you for responding so quickly, I haven't had a chance to look till now, I was at the movies. Your help is greatly appreciated.

Run this command:

```
$ uname -r
```

Hopefully the result is *2.6.15-29-386*.  If not, that's a problem.  If it is, then verify that you have the kernel source installed at */lib/modules/2.6.15-29-386/build*.  The contents of that directory should look something like:

```
arch   crypto   fs       init  kernel  Makefile  Module.symvers  scripts   sound       usr
block  drivers  include  ipc   lib     mm        net             security  System.map
```

---

### Post by wydra on 2007-11-18
There is a directory all the way up to the version number, the command you told me to do checks out with what you said, but there is no build folder.

---

### Post by dwhitney67 on 2007-11-18
You need to get the kernel source code.  In theory, this command should do that:

[FONT="Courier New"]$ sudo apt-get install kernel-package[/FONT]

Also, if you do not already have it, you need to get the development stuff as well:

[FONT="Courier New"]$ sudo apt-get install build-essential[/FONT]

---

### Post by wydra on 2007-11-18
Nope, still no build folder...

Gah.

Should I restart?

---

### Post by dwhitney67 on 2007-11-18
You need to get the kernel source (code).  I am not at all familiar with Dapper, and for that matter, not too much with Ubuntu either.  I'm more familiar with Fedora.

Nevertheless, you need to find a way to get the kernel source.  Did the apt-get I indicated earlier not work (were there any errors?)?

---

### Post by wydra on 2007-11-18
Yes, it worked fine, there were no errors, but the build folder I read about doesnt exist under the version # directory... That must be the problem, the make command still isnt working.

---

### Post by dwhitney67 on 2007-11-18
Verify once again:

[FONT="Courier New"]$ uname -r[/FONT]

Feel free to peruse */lib/modules*.  There should be at least one kernel version number there; maybe more.  If you find one that is a later version than what the "uname" command is reporting, then by all means, reboot the system.

---

### Post by wydra on 2007-11-18
The version number is correct, the folder is there, the folder that isnt is this one...

lib/modules/2.6.15-29-386/build

---

### Post by dwhitney67 on 2007-11-18
Well, then it appears that you do not have the kernel source code.  You've got to find a way to download the source using apt-get.  Perhaps a Google search would help.  That's what I did earlier, and that where my apt-get advice came from.  However, it would appear that the "kernel-package" did not give you the source code.

Under Fedora, the package name is kernel-devel.  Maybe the same for Ubuntu?

Anyhow, it is late I need to get some Zs.  Good luck.

---

### Post by wydra on 2007-11-18
Oi, Would Kernel-Image be the same ting as Kernel Source?

Please guys, bear with me, I'm very new to Ubuntu. (I am loving it) I just am having a little trouble finding what I'm looking for, I don't want to screw up my comp, again...

---

### Post by tibellus on 2007-11-18
Hey there!

I don't know if it will make things work, but try  the following:
```
sudo aptitude install kernel-headers kernel-source kernel-image-2.6
```

Please post the results.

---

### Post by wydra on 2007-11-18
I will, I'm running KernelCheck right now, it's updating the kernel, lets see if that fixes it first.

---

### Post by wydra on 2007-11-18
I did that command, It updated some, but there are no visual changes to the lib/modules/2.6.15-29-386 folder, here are the sub folders of that one.

initrd kernel madwifi madwifi-ng volatile

and then there are some files. but no build folder still.

Can anyone who has the build file for that kernel version send it to me via filefront or something?

---

### Post by shearn89 on 2007-11-19
You need to do:
```
sudo apt-get install linux-headers-2.6.15-29-386
```
should fix it.

---

### Post by MachaB on 2007-11-22
Hi there,

I have more or less the same problem with Feisty; build directory does not exist and if I run 
```
sudo apt-get install linux-headers-$(uname -r) 
```
it says
```
E: couldn't find package linux-headers-2.6.20-15-generic
```

if I try to 
```
sudo apt-get install kernel-package
```
it says
```
E: couldn't find package kernel-package
```

Sounds very basic, but where can I get those packages from? 

Thanks in advance!

---

### Post by dwhitney67 on 2007-11-22
> **MachaB said:**
> Hi there,

I have more or less the same problem with Feisty; build directory does not exist and if I run 
```
sudo apt-get install linux-headers-$(uname -r) 
```


Use this form for the command:

```
sudo apt-get install linux-headers-`uname -r`
```

Please ensure that you use the correct quotes (in other words, _not_ the one paired with the double-quote key).  On my keyboard, the back quote is paired with the ~ key.

---

### Post by MachaB on 2007-11-23
Yeah, tried that too, with the correct quotes: same result. The command finds the right "version number" (?) i.e. "2.6.20-15-generic" but can't find the package.

---

### Post by dwhitney67 on 2007-11-23
Why don't you try to update your kernel?  My system has been "begging" me for several weeks now to upgrade to 2.6.20-16-generic.  It even provides me the option to install the headers.

P.S.  I am running Feisty 7.04.

---

### Post by xeth_delta on 2007-11-23
You can searching for the packages

```
sudo aptitude search linux-headers
```

Xeth

---

### Post by shearn89 on 2007-11-23
Again, you need to do:
```

sudo apt-get install linux-headers-2.6.15-29-386

```

What you could do is type "linux-headers-2.6.15-29" and hit tab twice at the end to list available options. Then choose something like -386 to match your architecture (type of cpu).

---

