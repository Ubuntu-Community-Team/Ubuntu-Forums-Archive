---
title: "Xserver keeps failing"
date: 2006-06-17
forum: Absolute Beginner Talk
---

### Post by SamMessing on 2006-06-17
Hello,

I am still fairly knew to Ubuntu, so I am not sure how easy/hard this problem is to fix... I am having trouble figuring out how to go about solving it.

I attempted to install XGL from this thread: [http://www.ubuntuforums.org/showthread.php?t=131267]("http://www.ubuntuforums.org/showthread.php?t=131267")

One of the steps in the install calls for a system reboot, upon rebooting, Xserver fails and I get the following error message:
```

(EE) NVIDIA (0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA (0): *** Aborting ***
(II) UnloadModule: "nvidia"
(II) UnloadModule: "ramdac"
(II) UnloadModule: "fb"
(EE) Screen(s) found, but none have a usable configuration.


Fatal server error:

no screens found
```

Here is a copy of the MODULES section of my /etc/x11/xorg.conf file:
```

Section "Module"
     Load "bitmap"
     Load "ddc"
#   Load "dri"
     Load "extmod"
     Load "freetype"
     Load "glx"
     Load "int10"
     Load "type1"
     Load "nvidia"
     Load "vbe"
```

I'm still pretty new, so let me know if more information is required. What should I do to fix this? Originally it was failing w/o

```
Load "nvidia"
```

in the xorg.conf file, so I added it, but it doesn't seem to make much difference. I have also made sure that I have the latest nvidia drivers, which I do, but I am not sure if that would have made any sort of difference.

Thanks!

Sam

P.S. I originally posted this question on that thread, but haven't recieved a reply from anyone, so I thought I'd try posting it here, as I think this probably is a pretty simple problem (although I could easily be wrong)

---

### Post by mlind on 2006-06-17
Do you have linux-restricted-modules and nvidia-glx packages installed ?

You must install linux-restricted-modules package that is corresponding
to your kernel. If you've got i386 arch kernel, install *linux-restricted-modules-386*

To find this out type *uname -r*

---

### Post by SamMessing on 2006-06-17
When I type uname -r, the response I get is:

```
2.6.16-ck3
```

when I try to do 

```
sudo apt-get install linux-restricted-modules-2.6.16-ck3 
```

I get the following message:

```
E: Couldn't find package linux-restricted-modules-2.6.16-ck3
```


Should I be typing something else at the end of linux-restricted-modules- ?


I also tried linux-restricted-modules-ck3, but that didn't work either.

I already have nvidia-glx installed

---

### Post by mlind on 2006-06-17
[QUOTE=SamMessing]When I type uname -r, the response I get is:

```
2.6.16-ck3
```

when I try to do 

```
sudo apt-get install linux-restricted-modules-2.6.16-ck3 
```

I get the following message:

```
E: Couldn't find package linux-restricted-modules-2.6.16-ck3
```


Should I be typing something else at the end of linux-restricted-modules- ?


I already have nvidia-glx installed[/QUOTE]

Are you using a custom kernel? Looks you've applied Con Kolivas patches..
You probably need to compile nvidia kernel modules manually too.

restricted-modules packages are provided for Ubuntu stock kernels only.

---

### Post by SamMessing on 2006-06-17
Yes I re-compiled the kernel following a HOWTO I had found. How do I go about manually compiling the nvidia module?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]Yes I re-compiled the kernel following a HOWTO I had found. How do I go about manually compiling the nvidia module?[/QUOTE]

tseliot has written a nice guide which should help [http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_2)

btw. Why did you make a custom kernel ?

---

### Post by SamMessing on 2006-06-18
I am running into the same problem with the HOWTO, the first step is to run the following command:

```
sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
```

but when I try to do that I get the error message: 
```

E: Couldn't find package linux-headers-2.6.16-ck3

```
(2.6.16-ck3 is what I get when I type uname -r)


I tried just going ahead and following the next steps, but the problem is that later it calls for the command:

```
./nvidia-installer -n -s --x-prefix=/usr/lib/xorg --kernel-source-path=/usr/src/kernel-headers-`uname -r`

```
which I get the following error for:

```
ERROR: You appear to be running an X server; please exit X before installing.
```

What is that command for stopping the Xserver? And does this make sense? Because currently Xserver fails when booting up... so it shouldn't be running...

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]I am running into the same problem with the HOWTO, the first step is to run the following command:

```
sudo apt-get --purge remove linux-restricted-modules-`uname -r` linux-restricted-modules-common nvidia-glx nvidia-settings nvidia-kernel-common
```

but when I try to do that I get the error message: 
```

E: Couldn't find package linux-headers-2.6.16-ck3

```
(2.6.16-ck3 is what I get when I type uname -r)


I tried just going ahead and following the next steps, but the problem is that later it calls for the command:

```
./nvidia-installer -n -s --x-prefix=/usr/lib/xorg --kernel-source-path=/usr/src/kernel-headers-`uname -r`

```
which I get the following error for:

```
ERROR: You appear to be running an X server; please exit X before installing.
```

What is that command for stopping the Xserver? And does this make sense? Because currently Xserver fails when booting up... so it shouldn't be running...[/QUOTE]

First command is for removing any traces from Ubuntu's nvidia bundle.
You don't have any rescricted-modules package installed, so try just

```

sudo apt-get --purge remove nvidia-glx nvidia-kernel-common

```

Installer probably wants the display daemon dead
```

sudo /etc/init.d/gdm stop

```

If installer is not satisfied yet, drop to runlevel 1 by doing *sudo init 1*.

/edit typo

---

### Post by mlind on 2006-06-18
btw. you should not install linux-headers package because those are provided along
upstream tarball and there's no matching headers for kernel that new..

---

### Post by SamMessing on 2006-06-18
Well that seemed to work, but now I am running into another problem, it tells me to do the command:

```
sudo apt-get install nvidia-xconfig
```

but when I do I get the following error
```

Package nvidia-xconfig is not avaible, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package nvidia-xconfig has no installation candidate
```

What should I do?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]Well that seemed to work, but now I am running into another problem, it tells me to do the command:

```
sudo apt-get install nvidia-xconfig
```

but when I do I get the following error
```

Package nvidia-xconfig is not avaible, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
E: Package nvidia-xconfig has no installation candidate
```

What should I do?[/QUOTE]

nvidia-xconfig is just a script for changing "nv" Driver to "nvidia"
on /etc/X11/xorg.conf, just edit it manually. Also, **disable** dri module too.

then restart X using
```

sudo /etc/init.d/gdm restart

```

---

### Post by SamMessing on 2006-06-18
You said I don't need to install kernel-headers since there aren't any for my kernel, but then I run into problems when the HOWTO asks me to place things into the folder /usr/src/kernel-headers-`uname -r` because it doesn't exist.

So when I run the command
```

sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/kernel-headers-`uname -r`

```
nothing happens.


What should I do? Should I use a different directory than kernel-headers-`uname -r`?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]You said I don't need to install kernel-headers since there aren't any for my kernel, but then I run into problems when the HOWTO asks me to place things into the folder /usr/src/kernel-headers-`uname -r` because it doesn't exist.

So when I run the command
```

sudo ./nvidia-installer -n -s --x-prefix=/usr/lib/xorg/ --kernel-source-path=/usr/src/kernel-headers-`uname -r`

```
nothing happens.


What should I do? Should I use a different directory than kernel-headers-`uname -r`?[/QUOTE]

Have you tried running nvidia-installer without any parameters, it should work.
Just make sure you make symlink called */usr/src/**linux*** point to your current kernel.

---

### Post by SamMessing on 2006-06-18
I will try that, how do I do the sym link? What is the command?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]I will try that, how do I do the sym link? What is the command?[/QUOTE]

Sorry, I had a typo... /usrc/src/**linux** must point on your current kernel

```

sudo ln -sf *target symlink*

```


This could work
```

sudo ln -sf /usr/src/linux-2.6.16 /usr/src/linux

```


/edit typo

---

### Post by SamMessing on 2006-06-18
Alright, running ./nvidia-installer works, but when I try it it says I have Xserver running, when I type the command
```

init 1
```

and get down to runlevel 1 and try to run ./nvidia-installer, I get the following message:

You appear to be running in runlevel 1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficulty for nvidia-installer to correctly setup the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 (`telinit 3`) before installing.

Quit installation now? (select 'no' to continue)


Should I continue? Or should I do something else?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]Alright, running ./nvidia-installer works, but when I try it it says I have Xserver running, when I type the command
```

init 1
```

and get down to runlevel 1 and try to run ./nvidia-installer, I get the following message:

You appear to be running in runlevel 1; this may cause problems. For example: some distributions that use devfs do not run the devfs daemon in runlevel 1, making it difficulty for nvidia-installer to correctly setup the kernel module configuration files. It is recommended that you quit installation now and switch to runlevel 3 (`telinit 3`) before installing.

Quit installation now? (select 'no' to continue)


Should I continue? Or should I do something else?[/QUOTE]

hehe, looks like this is no easy task after all. I hope it's worth it ;)

On debian system, runlevels 2-5 are the same, and runlevel 1 is for single user.
If **stopping gdm/kdm** doesn't resolve issue for the nvidia-installer, then you must do it
on runlevel 1. Ubuntu doesn't use devfs, and I guess it should work just ok.

---

### Post by SamMessing on 2006-06-18
Hmm....

So attempting to say "no" when it asks if I want to quit the installer just brings me to the following message page:
```

ERROR: You appear to be running an X server; please exit X before installing.
```


This is at runlevel 1... what should I do?

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]Hmm....

So attempting to say "no" when it asks if I want to quit the installer just brings me to the following message page:
```

ERROR: You appear to be running an X server; please exit X before installing.
```


This is at runlevel 1... what should I do?[/QUOTE]

Read the tutorial on post #6 again, it should contain everything you need.
If problems like these are too hard to overcome, I'm sorry but I suggest you go
back to using stock kernel.

I also think that using unstable kernel patches will bring more problems than they
solve. Ubuntu kernel is very good and stable.

---

### Post by SamMessing on 2006-06-18
I think your suggestion to move back to a standard kernel is the best idea, especially since I am still new to Linux. I have searched the wiki and haven't been able to find information about how to restore linux....

In my attempt to get the nvidia drivers working I have made enough mistakes that now when trying to boot any kernel I have (my custom compiled or the standard one) I get the error message about the Xserver failing.

Since I just installed Ubuntu for the first time, there are no documents that I am afraid of losing. Am I right in thinking that the easiest thing for me to do to get back to a working standard kernel is to do some sort of system restore? Or to re-install ubuntu?

Where should I look for information on how to do this (if this is the best way)... I am having trouble finding it on the wiki,

Thanks,
Sam

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]I think your suggestion to move back to a standard kernel is the best idea, especially since I am still new to Linux. I have searched the wiki and haven't been able to find information about how to restore linux....

In my attempt to get the nvidia drivers working I have made enough mistakes that now when trying to boot any kernel I have (my custom compiled or the standard one) I get the error message about the Xserver failing.

Since I just installed Ubuntu for the first time, there are no documents that I am afraid of losing. Am I right in thinking that the easiest thing for me to do to get back to a working standard kernel is to do some sort of system restore? Or to re-install ubuntu?

Where should I look for information on how to do this (if this is the best way)... I am having trouble finding it on the wiki,

Thanks,
Sam[/QUOTE]

For easiest path, install linux-686 package, which will install newes i686 kernel,
and corresponding restricted-modules tool. You must have restricted repository
enabled on /etc/apt/sources.list. Or you can just install linux-image-686 package
which will not provide restricted-modules and doesn't need extra repository enabled.

```

sudo aptitude install linux-686

```

or

```

sudo aptitude install linux-image-686

```

then you should try booting using your new kernel and if it works, remove
the custom kernel you built.

---

### Post by SamMessing on 2006-06-18
So I did what you suggested, and then tried booting the new kernel. Now when it boots I see the splash screen (where it shows booting progress), which I didn't see before, but after that I get the same message of the Xserver failing. 

It also gives me the same reason, about the Nvidia Module.


Do I need to do a complete re-install of ubuntu? If so, what is necessary to do that?


Thanks,

Sam

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]So I did what you suggested, and then tried booting the new kernel. Now when it boots I see the splash screen (where it shows booting progress), which I didn't see before, but after that I get the same message of the Xserver failing. 

It also gives me the same reason, about the Nvidia Module.


Do I need to do a complete re-install of ubuntu? If so, what is necessary to do that?


Thanks,

Sam[/QUOTE]

No you don't need to reinstall Ubuntu. If you installed restricted-modules, you
still must install nvidia-glx too. And make sure you're booted into new kernel.

If you get Xserver failing again, reconfigure it and choose old "nv"
driver instead.
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by SamMessing on 2006-06-18
It worked! Thank you so much for your help!

One last question, how do I go about deleting the previous kernels?

Thanks again!!

Sam

---

### Post by mlind on 2006-06-18
[QUOTE=SamMessing]It worked! Thank you so much for your help!

One last question, how do I go about deleting the previous kernels?

Thanks again!!

Sam[/QUOTE]

I think easies way to do this is to use **synaptic**. You can find it from
System Menu > Administration > Synaptic Package Manager.

Ubuntu kernels are listed on "Base System" category and you custom packages
which are not on any repository can be found "Installed (local or obsolete)" when
you switch to Status view.



You can also use dpkg -l *linux-* to get list of installed packages that contain word
linux- and then find kernel package you want to remove and use apt-get remove to
remove it.

---

### Post by SamMessing on 2006-06-19
That worked great! Thank you so much for helping me with this, it's nice to have Ubuntu up and running again!

---

