---
title: "64bit tickless for macbook pro"
date: 2007-11-18
forum: Apple Intel Users
---

### Post by lv1001 on 2007-11-18
Since kernel 2.6.24 finally supports tickless kernel for 64bit, did anyone try (or even better manage) to compile it for macbook pro rev. 3?

What patches are included in the ubunut kernels that one would have to include manually to get all features of ubunut working?

Thanks
  LV

---

### Post by cyberdork33 on 2007-11-18
> **lv1001 said:**
> Since kernel 2.6.24 finally supports tickless kernel for 64bit, did anyone try (or even better manage) to compile it for macbook pro rev. 3?

What patches are included in the ubunut kernels that one would have to include manually to get all features of ubunut working?

Thanks
  LV

Haven't tried the new, but am interested now... 

I usually only patch mactel patches to a vanilla kernel, and that seems to work pretty good.

---

### Post by volanin on 2007-11-18
Kernel 2.6.24 is still very unstable.
The vanilla version released is still RC3, but remember that RC for the kernel does not mean
the same thing as RC for userland programs. RC kernels have lots of bugs and regressions
that will be fixed before the final release.

If you want to try 64-bit tickless, I really recommend you give a try at Fedora's 2.6.23 kernel.
They have backported it, and tested it extensively.
You also get CFS as bonus!

I am doing it right now (although I use a Macbook) and have absolutely NO complains!
:)

---

### Post by Rog-Mahal on 2007-11-19
Do you have a link for the kernel source? Or did you have to download the install ISO?

---

### Post by volanin on 2007-11-19
Here you are:
[http://download.fedora.redhat.com/pub/fedora/linux/releases/8/Everything/source/SRPMS/kernel-2.6.23.1-42.fc8.src.rpm](http://download.fedora.redhat.com/pub/fedora/linux/releases/8/Everything/source/SRPMS/kernel-2.6.23.1-42.fc8.src.rpm)

You will have to extract the RPM and then apply the patches in the correct order.
Follow these instructions in the directory where you downloaded the RPM to
get a ready-to-compile source tree in TAR.BZ2 format real quick:
*(You will need to have the package **rpm** installed.)*

```
$ mkdir KERNEL
$ cd KERNEL
$ rpm2cpio ../kernel-2.6.23.1-42.fc8.src.rpm | cpio -i
$ tar -xjf linux-2.6.23.tar.bz2
$ cd linux-2.6.23
$ bzcat ../patch-2.6.23.1.bz2 | patch -p1
$ for PATCH in `grep '^ApplyPatch.*patch$' ../kernel.spec | cut -d' ' -f2`; do patch -p1 -i ../$PATCH; done
$ find -name '*.orig' -exec rm {} \;
$ cd ..
$ tar -cjf ../kernel-2.6.23.1-42.fc8.tar.bz2 linux-2.6.23
$ cd ..
$ rm -r KERNEL
```

Or in just a single line for some copy-and-paste goodness:

```
mkdir KERNEL; cd KERNEL; rpm2cpio ../kernel-2.6.23.1-42.fc8.src.rpm | cpio -i; tar -xjf linux-2.6.23.tar.bz2; cd linux-2.6.23; bzcat ../patch-2.6.23.1.bz2 | patch -p1; for PATCH in `grep '^ApplyPatch.*patch$' ../kernel.spec | cut -d' ' -f2`; do patch -p1 -i ../$PATCH; done; find -name '*.orig' -exec rm {} \;; cd ..; tar -cjf ../kernel-2.6.23.1-42.fc8.tar.bz2 linux-2.6.23; cd ..; rm -r KERNEL
```

---

### Post by Rog-Mahal on 2007-11-19
Sweet! Thanks a lot. Where should I get the patches, or are they included in your copy-and-paste goodness? Should I use the Ubuntu patches or are there some better ones?

 So have you noticed a big difference? Powertop recommends that I turn on the CONFIG_NO_HZ option, have you done that? Any recommendations for configuration would be greatly appreciated.

---

### Post by cyberdork33 on 2007-11-19
> **Rog-Mahal said:**
> Powertop recommends that I turn on the CONFIG_NO_HZ option, have you done that?

That option IS the tickless kernel option...

---

### Post by Rog-Mahal on 2007-11-19
Heh...I knew that....where would I find the right patches to apply?

---

### Post by cyberdork33 on 2007-11-19
> **Rog-Mahal said:**
> Heh...I knew that....where would I find the right patches to apply?

It looks to me like the commands he posted above already applied patches.

---

### Post by volanin on 2007-11-19
Yes, indeed!
The patches are all included already.
Just copy-and-paste that line and you are ready to go!
You will just have to configure the whole thing (and I can't help you with that since we have different laptops)


And, to answer if I noticed any big difference...
Yes, a lot.

Linux is a LOT more responsive, but not because of tickless at all, although it really saves some battery!
It's also not because of the new CFS scheduler. In my opinion, the best thing in this 2.6.23 kernel
compared to the 2.6.22 Ubuntu uses is the modification to I/O operations performance.

In Ubuntu, if you are doing anything that is disk-intensive, your whole system slows considerably.
With this new kernel everything just degrades gracefully, and you barely feel any slowdows or
huge delays. It's really great!
:)

---

### Post by Rog-Mahal on 2007-11-20
Joy! I'm very excited! I'll post how things turn out.

---

### Post by cyberdork33 on 2007-11-20
> **volanin said:**
> Yes, indeed!
The patches are all included already.
Just copy-and-paste that line and you are ready to go!
You will just have to configure the whole thing (and I can't help you with that since we have different laptops)


And, to answer if I noticed any big difference...
Yes, a lot.

Linux is a LOT more responsive, but not because of tickless at all, although it really saves some battery!
It's also not because of the new CFS scheduler. In my opinion, the best thing in this 2.6.23 kernel
compared to the 2.6.22 Ubuntu uses is the modification to I/O operations performance.

In Ubuntu, if you are doing anything that is disk-intensive, your whole system slows considerably.
With this new kernel everything just degrades gracefully, and you barely feel any slowdows or
huge delays. It's really great!
:)
Do you know if this still needs mactel patches?

---

### Post by volanin on 2007-11-20
Honestly, I never used the mactel patches.
I used to run a 2.6.23 vanilla kernel with no patches at all, and I never had any problems.
Then I changed to the fedora kernel, because it's better tested and has many power-saving patches.
And as you can see, with this kernel I am using only the fedora patches. Nothing more.

I am using a Macbook 3rd generation and absolutely EVERYTHING works.
Of course, I had to manually compile ndiswrapper and uvcvideo to this new kernel.
With it, even suspend/hibernate works fine, and I have found no single problem at all.
*(Except if I compile Intel HDA sound as a module: it breaks suspend. Just compile statically.)*
:)

Give it a try, keeping your current kernel as backup if something fails.
It's the best advice I can give you.

---

### Post by cyberdork33 on 2007-11-20
> **volanin said:**
> Honestly, I never used the mactel patches.
I used to run a 2.6.23 vanilla kernel with no patches at all, and I never had any problems.
Then I changed to the fedora kernel, because it's better tested and has many power-saving patches.
And as you can see, with this kernel I am using only the fedora patches. Nothing more.

I am using a Macbook 3rd generation and absolutely EVERYTHING works.
Of course, I had to manually compile ndiswrapper and uvcvideo to this new kernel.
With it, even suspend/hibernate works fine, and I have found no single problem at all.
*(Except if I compile Intel HDA sound as a module: it breaks suspend. Just compile statically.)*
:)

Give it a try, keeping your current kernel as backup if something fails.
It's the best advice I can give you.
well i patched mactel anyway... no errors. This is a quick compile, so I just pulled the default ubuntu config and did an oldconfig on it, then deselected some hardware. We'll see how it goes.

---

### Post by Rog-Mahal on 2007-11-20
This is my first time compiling my own kernel, so please pardon my ignorance. 

Are the instructions [here]("http://ubuntuforums.org/showthread.php?t=442941") sufficient? 

The directories are different, and I'm assuming I don't need to do anything until step 11 or so. Thanks for your help guys :)

---

### Post by cyberdork33 on 2007-11-20
> **Rog-Mahal said:**
> This is my first time compiling my own kernel, so please pardon my ignorance. 

Are the instructions [here]("http://ubuntuforums.org/showthread.php?t=442941") sufficient? 

The directories are different, and I'm assuming I don't need to do anything until step 11 or so. Thanks for your help guys :)
You really should still put your kernel sources in /usr/src as that is the standard location for them. You can copy your patched source archive into /usr/src and follow the instructions (skipping the part where you wget the kernel source [step4], and if you don't want the mactel patches, you can skip those steps as well [steps8-11]).

I don't know where you downloaded your kernel source to, but the command to move it to /usr/src is something along these lines:
```
sudo cp /path/to/archive/kernel-2.6.23.1-42.fc8.tar.bz2 /usr/src/
```

---

### Post by cyberdork33 on 2007-11-20
Ah crap, I forgot that fglrx won't compile against 2.6.23 yet. :(

I did something wrong though (Missed an option) as powertop is not working for some reason. I will have to mess with it later.

---

### Post by volanin on 2007-11-20
Well, this is my config file.
It's for a Macbook 3rd generation, but I believe most of the options should be the same.
You can use it as reference to configure your own kernel.

It's VERY slimmed down, with support for the Macbook hardware only.
It also only supports EXT2 and EXT3, so also add the filesystems that you use!
:)

---

### Post by cyberdork33 on 2007-11-20
> **volanin said:**
> Well, this is my config file.
It's for a Macbook 3rd generation, but I believe most of the options should be the same.
You can use it as reference to configure your own kernel.

It's VERY slimmed down, with support for the Macbook hardware only.
It also only supports EXT2 and EXT3, so also add the filesystems that you use!
:)
Thanks, I am familiar with configuring kernels, I just did this a little hastily.

---

### Post by lv1001 on 2007-11-21
I am not, so thank you very much for that config-file.
The last configuration i tried resulted in the processors not leaving C0.
I'll give it a try this afternoon.
If anyone gets a good configuration for a mac book pro santa rosa, that one would be nice too... ;-)

---

### Post by cyberdork33 on 2007-11-21
> **lv1001 said:**
> If anyone gets a good configuration for a mac book pro santa rosa, that one would be nice too... ;-)

Shouldn't be too big a jump from the posted config as they have much the same hardware, and the biggest difference is the graphics card. You probably want to use the proprietary driver for that anyway.

Gentoo has some very good information and config files for Macbook (Pro)s.
This page has information for all models:
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook](http://gentoo-wiki.com/HARDWARE_Apple_MacBook)
There are quite a few kernel configs for various machines here (None for Santa Rosa yet that I can tell):
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel)

---

### Post by Rog-Mahal on 2007-11-21
Blast! I've hit an error. Everything was going fine until I tried make menuconfig. I got a really long list of errors with the final output being 

```
make[1]: *** [scripts/kconfig/lxdialog/checklist.o] Error 1
make: *** [menuconfig] Error 2

```

I attached the full output of the error.

---

### Post by volanin on 2007-11-21
Easy one!
```
$ sudo aptitude install libncurses5-dev
```

---

### Post by Rog-Mahal on 2007-11-21
Well, I compiled and installed everything according to the howto I previously posted, and now the kernel hangs on boot. When I run the recovery mode, the last two lines I see are:

```
Begin: waiting for root filesystem... ...
Clocksource tsc unstable (delta = -90442356 ns)
```

Did I misconfigure something?

[EDIT] It hangs for about 2 minutes because it can't mount the root filesystem, then starts some kind of emergency shell. Is there any way I can look at a log of the boot so I can show you guys what I'm talking about?

---

### Post by lv1001 on 2007-11-22
I am not very successfull either.
The new kernel boots ok but of course does not start kde. I install the nvidia-driver with "sh NVIDIA-Linux-x86_64-100.14.19-pkg2.run" and it claims to install but "/etc/init.d/kdm restart" fails.
In addition, even though the Wake-Ups per second powertop reports go down from about 450 to about 50, the power consumption increses from about 18 Watt to about 22 Watt with the same display settings. What did I do wrong?

Again, any working macbook pro santa rosa config-file would be very much appreciated!!

Thanks
  Lewin

---

### Post by volanin on 2007-11-22
> Is there any way I can look at a log of the boot so I can show you guys what I'm talking about?
Yes. Just type ***dmesg***


Now now...
Personally, I have always created kernels MANUALLY, instead of using the tools provided by Ubuntu.
So, I cannot help you with the howto you previously posted, but I can show you my method.
It's not hard, and it won't break your system, but if you decide to follow it, be sure to
extra-check every step.


**1- Edit the kernel Makefile to define a custom kernel version string:**

Edit the ***Makefile*** located in your kernel source directory.
You should modify the lines in the very beginning to:
```
VERSION = 2
PATCHLEVEL = 6
SUBLEVEL = 23
EXTRAVERSION = -fedora
```

The kernel version string with this Makefile will be defined to ***2.6.23-fedora***
You can check the defined kernel version string with ***make kernelversion***


**2- Configure the kernel:**

Type ***make menuconfig*** and configure the kernel appropriately.
Or use one of the many config files that you can find around the net.
My personal config file for a Macbook 2.16GHz 3rd generation is attached.
You can use it with the command ***zcat config.gz > .config***


**3- Build the kernel:**

Type ***make***
This will take some time.


**4- Manually install the kernel modules:**

Type ***make modules_install***
This will install the kernel modules to /lib/modules/2.6.23-fedora

Also, you should create the firmware directory, as it is not created by the above command.
Do this by running the following command:
***mkdir /lib/firmware/2.6.23-fedora***


**5- Create an initrd image:**

The initrd image is fundamental in most linux distributions, and Ubuntu is no exception.
It's just a compressed file with some essential boot scripts and the kernel modules for your hardware.
You can easily create it by running the following command:
***update-initramfs -ck 2.6.23-fedora***

This command will create the file /boot/initrd.img-2.6.23-fedora


**6- Manually install the kernel image:**

Now you must install the kernel itself.
If you compiled a 32-bit kernel, the kernel image will be ***arch/i386/boot/bzImage***
Else, if you compiled a 64-bit kernel, the kernel image will be ***arch/x86_64/boot/bzImage***

Just copy it to your /boot directory, with this command:
***cp [KERNEL_IMAGE_FILE] /boot/vmlinuz-2.6.23-fedora***


**7- Update your GRUB menu:**

To update your GRUB menu, so that it displays the new kernel, run the following command:
***update-grub***


**8- Reboot!**

Reboot.
And choose your new kernel in the GRUB menu!


**9- Uninstalling:**

If you want to undo everything, leaving your system clean, just delete the files/directories below:

[b][i]/boot/vmlinuz-2.6.23-fedora
/boot/initrd.img-2.6.23-fedora
/lib/firmware/2.6.23-fedora
/lib/modules/2.6.23-fedora[/i][/b]

And update your GRUB menu again with:
***update-grub***


That's it!
Hope it helps.
By following these instructions, you can test many different kernel configurations without fear.
Just keep a backup working kernel in your GRUB menu in case you can't boot!
:)

---

### Post by Rog-Mahal on 2007-11-22
Cheers volanin! Thanks for all your help, I'll get started on the new kernel straight away.

[EDIT] Success! I'm running my new kernel now. There is a marked improvement, I'm very satisfied! Thanks a lot!

---

### Post by Rog-Mahal on 2007-11-25
My Apple remote worked out of the box with the old Ubuntu kernel, but it doesn't seem to be working now. Do I need to install lirc? I didn't need it previously. Thanks

---

### Post by volanin on 2007-11-25
> **Rog-Mahal said:**
> My Apple remote worked out of the box with the old Ubuntu kernel, but it doesn't seem to be working now. Do I need to install lirc? I didn't need it previously. Thanks

I always had lirc installed... so I don't know.
Technically, this kernel (with the config I attached) supports the remote.
Lirc is just a translator interface that reads the remote device and generates signals through its daemon.
Maybe the application you were using before could read the remote device directly... instead of connecting to the lirc daemon.
But nothing should have changed.

The remote device in my macbook is **/dev/usb/hiddev0**
Check if you have it there.
:)

---

### Post by orenouard on 2007-11-25
Thanks for the nice head-ups. Configured a very close kernel from your advice and flirting with the (theorical) 4 hours autonomy on powertop is nice now.

I'm having some different mileage though, so I thought I'd share it there to compare with what others have noticed:

it doesn't seems that it's the sound being compiled as a module that hinders suspend here. Actually when compiled statically it complained it could not load codecs but I might have overlooked something.

Actually suspend through the desktop's method (calling SuspendCommand=/usr/sbin/pmi action suspend) works perfectly once I have done at least one sudo pm-suspend so I guess there is one service refusing to yield without root prerogatives, must find out which.

Touchpad works but there might be an issue in compiling it and usbhid statically as it seems the order it loads up as compared to usbhid is important (seems appletouch must come first or it can't attach)

Applied the matel patches but applesmc is still annoyingly spamming (check with dmesg) :  [522.076508] applesmc: wait status failed: c != 8
[  522.082394] Read: Waited 10 ms for the value
Thought patches were supposed to correct that, anyone noticed this ?

---

### Post by Rog-Mahal on 2007-11-25
> **volanin said:**
> I always had lirc installed... so I don't know.
Technically, this kernel (with the config I attached) supports the remote.
Lirc is just a translator interface that reads the remote device and generates signals through its daemon.
Maybe the application you were using before could read the remote device directly... instead of connecting to the lirc daemon.
But nothing should have changed.

The remote device in my macbook is **/dev/usb/hiddev0**
Check if you have it there.
:)

That file exists, but the remote (which used to function natively with rhythmbox) doesn't work. Think lirc will help?

---

### Post by thonuz on 2007-11-28
I got 2.6.23 working here using the .config file ready made and everything is working wonderfully almost. Boot time is 6 seconds faster on 2nd gen core duo and I can type without touchpad errors. One big problem I have though is with Flash:

/usr/lib/nspluginwrapper/i386/linux/npviewer.bin: 1: Syntax error: word unexpected (expecting ")")
nspluginwrapper: no appropriate viewer found for /usr/lib/flashplugin-nonfree/libflashplayer.so
dpkg: error processing flashplugin-nonfree (--configure):
 subprocess post-installation script returned error exit status 1

Do I need to recompile the kernel for nspluginwrapper or something?

---

### Post by volanin on 2007-11-29
> That file exists, but the remote (which used to function natively with rhythmbox) doesn't work.
Think lirc will help?

I always used lirc!
Works really fine for me in any program.


> Do I need to recompile the kernel for nspluginwrapper or something?

Sorry, never used nspluginwrapper.
You can ask Rog-Mahal, as he also uses the 2.6.23 Fedora 64-bit kernel!
:)

---

### Post by Rog-Mahal on 2007-11-29
Thanks volanin, I will install it straight away. PS how do you configure it, I didn't see an option for an Apple remote

I have nspluginwrapper installed and flashplugin-nonfree. Flash works, but Shockwave flash does not. Open a Firefox window and type about:plugins into your address bar, see if you have anything related to flash. There aren't any kernel options that need to be enabled (as far as I know). I used my old config file. Flash just works. If you still are having problems, you might want to try installing gnash, it's a free flash plugin for 64 bit systems and should be in synaptic. Let me know if this helps.

---

### Post by thonuz on 2007-11-30
Thanks. I'll look into this.
on the regular ubuntu 64 kernel I get flash working but not on the newer one so I must have messed up somewhere.

---

### Post by thonuz on 2007-12-01
I have one question. When we are using two kernels should we have two sets of kernel modules? I'm getting some random strangeness with this fedora 64 version like I can't drag and drop firefox links anymore, I can't add the isite module, I get no bash history when I use the arrow keys anymore, and also I have now an error--FATAL: Module cpufreq_stats not found.
PowerTOP 1.8  when running powertop, but it does start.

I'm going to try again from scratch.

---

### Post by cyberdork33 on 2007-12-01
> **thonuz said:**
> I have one question. When we are using two kernels should we have two sets of kernel modules? I'm getting some random strangeness with this fedora 64 version like I can't drag and drop firefox links anymore, I can't add the isite module, I get no bash history when I use the arrow keys anymore, and also I have now an error--FATAL: Module cpufreq_stats not found.
PowerTOP 1.8  when running powertop, but it does start.

I'm going to try again from scratch.that means you did not enable the cpufreq_stats part of the kernel.

In menuconfig, you can type "/" to search for items.

```
  &#9474; Symbol: CPU_FREQ_STAT [=m]                                                                            &#9474;  
  &#9474; Prompt: CPU frequency translation statistics                                                          &#9474;  
  &#9474;   Defined at drivers/cpufreq/Kconfig:37                                                               &#9474;  
  &#9474;   Depends on: CPU_FREQ                                                                                &#9474;  
  &#9474;   Location:                                                                                           &#9474;  
  &#9474;     -> Power management options                                                                       &#9474;  
  &#9474;       -> CPU Frequency scaling                                                                        &#9474;  
  &#9474;         -> CPU Frequency scaling (CPU_FREQ [=y])                                                      &#9474;  
  &#9474;   Selects: CPU_FREQ_TABLE  
```

---

### Post by Rog-Mahal on 2007-12-01
When you compiled your kernel, I believe you created a new set of kernel modules. Check your /lib/modules/ directory to make sure.  I chose to keep mine as streamlined as possible. I get the same error when using powertop, but it seems to function fine. iSight hasn't been one of my priorities, so I can't speak to that. Bash history is functioning fine for me. As for firefox links, I haven't had a problem yet. The instructions that volanin posted earlier in this thread worked well for me. Good luck!

---

### Post by cyberdork33 on 2007-12-01
> **Rog-Mahal said:**
> I get the same error when using powertop, but it seems to function fine.

I seemed to get that too when I compiled it into the kernel directly instead of as a module.

---

### Post by Rog-Mahal on 2007-12-01
Is there a problem with the way it's currently working? Think I should rebuild?

---

### Post by cyberdork33 on 2007-12-01
> **Rog-Mahal said:**
> Is there a problem with the way it's currently working? Think I should rebuild?
no it is probably working fine, it is just expecting it to be compiled as a module rather than part of the kernel.

---

### Post by volanin on 2007-12-01
Indeed:

```
$ strings /usr/sbin/powertop | grep 'modprobe cpufreq_stats'
/sbin/modprobe cpufreq_stats &> /dev/null
```

It hardcodes the module loading.
If you compiled cpufreq_stats statically, as I also did, it will complain but it will work perfectly!
:)

---

### Post by Rog-Mahal on 2007-12-01
Yup, I get the same output.

---

### Post by cyberdork33 on 2007-12-02
I finally got a pretty good kernel working on my iMac.

This is for a 3rd Generation 20" iMac w/ Core2 Cuo  (White):
[config-linux-2.6.23.1-42.f8-cd33_20071201.tar.gz]("http://www.rickycampbell.com/Ubuntu/config-linux-2.6.23.1-42.f8-cd33_20071201.tar.gz")

---

### Post by volanin on 2007-12-02
Post the config here!
:)

EDIT: Forget it!
How come I didn't see the attachment!

---

### Post by lv1001 on 2007-12-02
I still have trouble establishing a working config-file for macbook pro santa rosa. havn't tried that much however because of a lack of time.
So I had great hope in the kernel of the new hardy alpha...
But unfortunatelly it is still 2.6.22.
Are kernels updated within an release of ubuntu or would i have to wait for a newer kernel (2.6.24 or a 2.6.23 with backported tickless like fedoras) in some prerelease of hardy to get this feature?

Thanks,
  LV

---

### Post by cyberdork33 on 2007-12-02
> **lv1001 said:**
> I still have trouble establishing a working config-file for macbook pro santa rosa. havn't tried that much however because of a lack of time.
So I had great hope in the kernel of the new hardy alpha...
But unfortunatelly it is still 2.6.22.
Are kernels updated within an release of ubuntu or would i have to wait for a newer kernel (2.6.24 or a 2.6.23 with backported tickless like fedoras) in some prerelease of hardy to get this feature?

Thanks,
  LV

tickless kernel is not very close in official 64-bit linux. 

What kernel will be included in Hardy is a different question.
The roadmap is here:
[https://blueprints.launchpad.net/sprints/uds-boston-2007/+roadmap](https://blueprints.launchpad.net/sprints/uds-boston-2007/+roadmap)
and the kernel section says that the current plan is to use 2.6.24.

---

### Post by lv1001 on 2007-12-02
What do you mean by "tickless kernel is not very close in official 64-bit linux."?
Tickless is included in 2.6.24-rc3...

---

### Post by cyberdork33 on 2007-12-03
> **lv1001 said:**
> What do you mean by "tickless kernel is not very close in official 64-bit linux."?
Tickless is included in 2.6.24-rc3...

Great!

From all that I had read, the kernel developers were going to take their time for this because it was an issue in the 32-bit code. .24 was the first release they thought they could make it by and apparently that is the intent.

---

### Post by Rog-Mahal on 2007-12-04
I'm getting some weird output from powertop. It seems like for the past few days my wakeups from idle have skyrocketed. Here's the report:

```
Cn                Avg residency       P-states (frequencies)
C0 (cpu running)        (48.8%)         2.17 Ghz     0.8%
C1                0.0ms ( 0.0%)         2.00 Ghz     0.0%
C2                0.1ms (16.1%)         1333 Mhz     0.2%
C3                0.2ms (35.2%)         1000 Mhz    99.0%


Wakeups-from-idle per second : 3099.7   interval: 10.0s
Power usage (ACPI estimate): 21.8W (1.1 hours)

Top causes for wakeups:
  93.2% (4058.2)       <interrupt> : acpi 
   3.2% (139.0)       <interrupt> : uhci_hcd:usb5, i915@pci:0000:00:02.0 
   3.1% (136.8)       <interrupt> : ehci_hcd:usb1, uhci_hcd:usb2 
   0.5% ( 20.8)       <interrupt> : wifi0 
   0.0% (  0.4)       <interrupt> : libata, ohci1394, uhci_hcd:usb3

```

What is acpi doing? Certainly not saving power! Last night, before I shut my computer down I was playing a few games, could that have something to do with this?

---

