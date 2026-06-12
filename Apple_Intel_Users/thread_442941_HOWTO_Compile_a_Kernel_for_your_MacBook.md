---
title: "HOWTO: Compile a Kernel for your MacBook"
date: 2007-05-14
forum: Apple Intel Users
---

### Post by Gen2ly on 2007-05-14
Compiling a kernel is an advanced Linux topic and warrants a bit of a warning.  I think cyberdork33 put it best:

[quote=cyberdork33]... [it is not necessary] to make your own kernel as the Ubuntu kernel is fine. This is for the serious Linux user who would like to make a lean kernel, or maybe tryout the very latest Linux kernel, and not for a typical user.

In fact, compiling a custom kernel is more likely to break things that you do have working (and you would have to repeat the process of fixes them with your new kernel).[/quote]

I've been a bum lately so I thought I'd better to get off my lazy and contribute something useful to the forum.  When I last built a kernel, I took notes on my first generation MacBook and I thought it might be helpful to post what I learned here.  This process if research and followed carefully will install a tailored kernel to the Ubuntu installtion.  The kernel is the heart of Linux handling most the hardware processes.  This howto has been tested through second generation MacBooks and MacBook Pro's.  This howto should also be able to be adapted to other Intel-Macs.

For any reader that has ever compiled a kernel before we can say that "Compiling a Kernel" isn't as daunting as the terminology sounds.  Benefits of a correctly compiled kernel can result in a leaner kernel that can provide performance increases over the generic, pre-configured Ubuntu kernel.  Though this howto is basically a part of different readings in various Linux forums it is mostly derived from xXx 0wn3d xXx's  excellent [[COLOR="Sienna"]**kernel compile howto**[/COLOR]]("http://www.ubuntuforums.org/showthread.php?t=157560&highlight=compile+kernel").  I'd like to thank all for their part.


**[COLOR="DarkRed"][SIZE="4"]Compile a Kernel for your Intel-Mac[/SIZE][/COLOR]**

**1.** It makes everything very much easier if we act as root:
```
sudo bash
```

**2.**  Install the needed utilities and libraries to configure the kernel:
```
apt-get install build-essential bin86 kernel-package libqt3-headers libqt3-mt-dev libncurses5 libncurses5-dev
```

**3.** Now change to the directory where we will work with the kernel:
```
cd /usr/src
```

**4.** Download the kernel.  Visit [[COLOR="Sienna"]**kernel.org**[/COLOR]]("http://kernel.org/") to see what kernels are available.  If you want to use a stable kernel build don't choose a release canidate(rc) version as these are meant for testing.  To grab a kernel [FONT="Fixedsys"][COLOR="DarkGreen"]wget[/COLOR][/FONT] works nice to retrieve it.  For Example:
```
wget http://kernel.org/pub/linux/kernel/v2.6/linux-<version>.tar.bz2
```

**5.** Next unpack it:
```
tar -xvf linux-<version>.tar.bz2
```

**6.** Remove the symbolic link to the kernel if and previous kernels have been compiled:
```
rm -rf linux
```

**7.** Create a new link to the new kernel source.
```
ln -s /usr/src/linux-<version> linux
```

**8.** Subversion is required to download the mactel kernel patches.  

```
apt-get install subversion
```

**9.** Download the Kernel Patches by filling in the appropriate kernel version:

*[COLOR="DarkOrange"]Most patches eventually make the kernel tree and patching may not always be necessary.[/COLOR]*

```
svn co https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-<version>
```

**10.** Enter the patches Directory:
```
cd mactel-patches-<version>
```

**11.** and patch the kernel:
```
./apply /usr/src/linux
```

**12.** Now change to the unpacked kernel source directory:
```
cd ../linux
```

**13.** The kernel configuration file is a key to how well the kernel will run (if at all).  Research your computer and discover what hardware it has and apply the appropriate drivers to the kernel.  Also some people post their custom configurations.  Use these with care.  An updated [FONT="Fixedsys"][COLOR="DarkGreen"].config[/COLOR][/FONT] file can be found in various places.  The Gentoo Linux Wiki keeps pretty up to date ones:
[LIST]
[*][**[COLOR="Sienna"]MacBook[/COLOR]**]("http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel")
[*][**[COLOR="Sienna"]MacPro[/COLOR]**]("http://gentoo-wiki.com/MacProConfig")
[/LIST]
  
Use your favorite editor and save the configuration.  

Now, move and rename the kernel configuration to the Linux kernel source directory ([FONT="Fixedsys"][COLOR="DarkGreen"]/usr/src/linux[/COLOR][/FONT]):
```
mv config-<version> /usr/src/linux/.config
```

**15.** If kernel [FONT="Fixedsys"][COLOR="DarkGreen"].config[/COLOR][/FONT] is older than the current version of the kernel it needs to be updated:
```
make oldconfig
```

[FONT="Fixedsys"][COLOR="DarkGreen"]**make oldconfig**[/COLOR][/FONT] will ask a series of questions if the kernel version differs from the config version this is safe to do and should be done if even we are pretty sure the version matches.  A series of questions will be prompted for differing configuration options.  In most cases it is safe to hit enter for the default though it is best to look into what they do, type in a question mark for additional information.

**16.** Now configure the kernel for the Intel-Mac:
```
make menuconfig
```

I like [FONT="Fixedsys"][COLOR="DarkGreen"]make menuconfig[/COLOR][/FONT] but a graphical interface is also available:
```
make xconfig
```

Choose the option "Save to Disk" when ready.

**17.** Be sure to begin with a clean enviroment before beginning compiling (this is only necessary if the kernel has been compiled before):
```
make-kpkg clean
```

**18.** Now it's time to compile the kernel, it's headers, and modules all into a Debian Packages all in one easy step:
```
make-kpkg -initrd kernel_image kernel_headers modules_image
```

**19.** Compiling the kernel will take awhile so go enjoy a jolt.  

When compiling is done, go back to [FONT="Fixedsys"][COLOR="DarkGreen"]/usr/src[/COLOR][/FONT] directory, where the Debian Packages are saved.
```
cd ..
```

The kernel Debian Packages will be seen here and now we can install them.  If their are multiple versions here make sure to fill in the right version.
```
dpkg -i linux-image-*.Custom_i386.deb
dpkg -i linux-headers-*.Custom_i386.deb
```


**[COLOR="DarkRed"][SIZE="4"]Grub[/SIZE][/COLOR]**

Installing the debs will automatically update the bootloader's (Grub usually) configuration file.  I've found that Grub has better success booting Ubuntu if it defines partitions with Linux device definitions (e.g. /dev/sda) rather than the device-ID (UUID).  It's a good idea to take a look at it before rebooting your system to make sure Grub wrote it correctly.  Incorrect Grub setups will cause an error on boot that may look something like this:
[FONT="Fixedsys"]Kernel panic - not syncing : VFS . Unable to mount root fs on unknown-block(0,0)[/FONT]

If this happens Grub will need to be fixed, but first a little bit of an explanation.  When starting the computer and selecting the Linux icon the bios emulation starts, it in turn locates the boot loader (usually Grub).  Grub is has already been installed on the Master Boot Record (MBR) and has given information where the root(/) filesystem is and where it's configuration file is ([FONT="Fixedsys"]grub.conf[/FONT]).  Many people often refer to [FONT="Fixedsys"]menu.lst[/FONT] which is a link to [FONT="Fixedsys"]/boot/grub/grub.conf[/FONT].  This file will tell Grub the default kernel, grub color, and any number of options.

To check and edit Grub's options:
```
sudo gedit /boot/grub/menu.lst
```

and replace [FONT="Fixedsys"]root=UUID=some-long-string[/FONT] in your kernel line to [FONT="Fixedsys"]root=/dev/sda3[/FONT] or whatever your Linux partition is.  

This should do it.  If the kernel is configured correctly as well as Grub now we should load into the custom kernel.  Congratualtions.

**[COLOR="DarkRed"][SIZE="4"]Tips:[/SIZE][/COLOR]**

[LIST]
[*]If the grub loader isn't installed correctly look at this tutorial: [**[COLOR="Sienna"]How to restore Grub from a live Ubuntu CD.[/COLOR]**]("http://ubuntuforums.org/showthread.php?t=224351&highlight=grub").
[*]This [[COLOR="Sienna"]**other tutorial**[/COLOR]]("http://ubuntuforums.org/showpost.php?p=1174954&postcount=507") by xXx 0wn3d xXx to help optimize the kernel a bit.
[/LIST]

---

### Post by benanzo on 2007-05-14
Excellent

also make sure libncurses5 and libncurses5-dev are installed, otherwise menuconfig will give errors.

```
sudo apt-get install libncurses5 libncurses5-dev
```

---

### Post by Tribe on 2007-05-14
Very nice tutorial, thank a lot!

One question, though: since Feisty's kernel integrates some Mactel patches, have you noticed any significant improvements with a custom kernel over the canonical's ?

Bye

---

### Post by Gen2ly on 2007-05-14
> **Tribe said:**
> Very nice tutorial, thank a lot!

One question, though: since Feisty's kernel integrates some Mactel patches, have you noticed any significant improvements with a custom kernel over the canonical's ?

Bye

Boots a little bit quicker, and feel more responsive, as using the Ubuntu kernel has alot of features that one will never use.

> **benanzo said:**
> Excellent

also make sure libncurses5 and libncurses5-dev are installed, otherwise menuconfig will give errors.

```
sudo apt-get install libncurses5 libncurses5-dev
```

Thanks benanzo, I've compiled a kernel before this last time and couldn't think of all the dependences.

---

### Post by el dentist on 2007-05-15
Thanks. I'm looking forward to optimizing the kernel.

As far as which mactels this is compatible with, will this work on my 15.4 c2d macbook pro?

thanks in advance for help

:guitar:

---

### Post by ronocdh on 2007-05-15
I keep getting this error:
```
root@DragonBoat:/usr/src# svn co https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21.1 mactel-patches-2.6.21.1
svn: URL 'https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21.1' doesn't exist
root@DragonBoat:/usr/src# 

```
Did I misinterpret what Dirk meant by "version"? Is it a version of the Mactel patches rather than of the Linux kernel?

---

### Post by benanzo on 2007-05-15
the kernel only has mactel patches through 2.6.21 proper  I think [https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/)

---

### Post by ronocdh on 2007-05-16
> **benanzo said:**
> the kernel only has mactel patches through 2.6.21 proper  I think [https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/)
This worked perfectly, thanks. Ran into a bit of trouble at the end, though, trying to grab the debs. Was surprised about the i386 version, but they were nonexistent anyway. I'll take a fresh look at it tomorrow night and see what I did wrong.

---

### Post by Gen2ly on 2007-05-16
> **ronocdh said:**
> I keep getting this error:
> root@DragonBoat:/usr/src# svn co [https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21.1](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21.1) mactel-patches-2.6.21.1
svn: URL 'https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21.1' doesn't exist
root@DragonBoat:/usr/src# 

Did I misinterpret what Dirk meant by "version"? Is it a version of the Mactel patches rather than of the Linux kernel?

Yes use the basic version (i.e. 2.6.21).  Patches aren't tested on subversion of kernel builds.  (i.e. 2.6.21.1) and may not be safe.

---

### Post by benanzo on 2007-05-17
I just compiled 2.6.21.1 with mactel-patches-2.6.21 and everything seems to be A-OK so far.  However, the latest svn madwifi (0.9.3) is really playing hell on my ability to suspend (Nooo!!) and shutdown/reboot without "NETDEV WATCHDOG: wifi0: transmit timed out" locking up my system right before halt.

(I am finally having the same problems as everyone else)

I'm going to compile a 2.6.20 and use madwifi 0.9.2...I think that works.

ALSO:

For those of you who have a running 2.6.21 kernel, have a look and powertop.
[http://www.linuxpowertop.org/](http://www.linuxpowertop.org/)

It's a little utility (resembling top) developed by Intel that detects in fine detail exactly how much wattage your machine is consuming (and what is consuming it) and offers wonderful suggestions on how to conserve power and maximize your battery life.  I applied all the suggestions (including turning off beagled) and now I'm getting a solid 3 hrs on my 1st-gen MacBook with the LCD backlight at 60%.  FYI, it's a little dumb in that it will only give you one suggestion at a time until you apply whatever it suggests.  This requires multiple kernel recompiles to enable/disable various features before it will give you a new suggestion.  It's only going to work on a 2.6.21+ kernel because it needs the advanced TIMER_STATS option to be enabled.

The mactel-linux people have been tossing around some of the suggestions it gives (some of their patchs are causing power-drain.)  But they're working on it.

---

### Post by oskarloko on 2007-05-20
Well, it has been a long time from my last post...

I'll try a new kernel build from 2.6.21 release... let's see how free wireless works

I'm in doubt about two methods for building a .conofig file
[LIST=1]
[*]Use gentoo wiki .config
[*]Use original ubuntu kernel .config
[/LIST]

But It will be needed a revision of config...

For now, I'll use the first one.

Is there any restricted kernel module / firmware needed ? 
Is included on fresh kernel source or how can be it included ?



Yes, other own kernel builds improve apps and xorg... I expect same with new kernel !!



Thanks !!

---

### Post by oskarloko on 2007-05-20
Link for kernel
[http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.21.tar.bz2](http://kernel.org/pub/linux/kernel/v2.6/linux-2.6.21.tar.bz2)

Link for patches
[https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21/](https://svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.21/)

Command to create kernel
make-kpkg -initrd kernel_image kernel_headers modules_image -revision oba20070520mactel

( Whats the difference between* -append-to-version* and *-revision* ? )

---

### Post by oskarloko on 2007-05-20
Not luck :(

I repeat same [errors]("http://ubuntuforums.org/showpost.php?p=2553087&postcount=17")...
```

intelfb: Video mode must be programmed at boot time
ata-piix 0000:00:1F invalid map value 0
i8042.c not controller found

```

And, even more rare, no [FONT="Courier New"]/var/log/boot[/FONT] line is written.
And booting messages  are shown twice

:confused::confused::confused::confused:

Brigthness control don't work either....


But that's nothing, now [FONT="Courier New"]dpkg[/FONT] and other package apps doesn't work. It was my fault. I launched by error the kernel .deb install on console twice; and cancelled it by pressing [FONT="Courier New"][ctr]+[c][/FONT] . Now it seems that anything related to packages doesn't work ( I tried to recover )

Sorry for crying on your shoulders, ok, I'll keep trying ( tomorrow maybe... now it's late)

Well, something good: I sawn [_**here**_]("http://ubuntuforums.org/showthread.php?t=441013&highlight=kernel+restricted")  how to use restricted modules on own-build kernels.

Other resources I'm looking at:
- [https://wiki.ubuntu.com/KernelTeam](https://wiki.ubuntu.com/KernelTeam)
- Splash: [http://ubuntuforums.org/showpost.php?p=906326&postcount=9](http://ubuntuforums.org/showpost.php?p=906326&postcount=9)

---

### Post by Gen2ly on 2007-05-20
I did a little bit of research and Gentoo also has a custom kernel build where it looks like add a VESA TNG driver.  Ubuntu and Gentoo apparently handle frame buffers differently.  I'm don't have access to my Ubuntu box at the moment.  Try compiling the kernel without frame buffer support.  You wont' have a splash but it should boot.

```
< > Support for frame buffer devices
```

---

### Post by oskarloko on 2007-05-21
...ok, I'll try. 

But there's no ubuntu booting problem, in fact, it boots making weird things but boots ok ( even more quikcly than with old kernel )

---

### Post by Gen2ly on 2007-05-22
Ok, then you have a functional kernel, nice job.  I'm beginning to think that the resolution at boot is unknown.  Are you seeing large lettering?  You can specify to the vga driver of your screen size.  In [FONT="Fixedsys"]/boot/grub/menu.lst[/FONT] add to the end of your kernel line:

```
vga=792
```

Here's more info on [setting screen resolution at boot]("http://ubuntuforums.org/showthread.php?t=258484&highlight=kernel+booting+parameters"), also it (I believe) will help with the bootsplash if you want ti back.

---

### Post by wyley.r on 2007-06-05
I have some pretty strange behavior here.  I followed these steps as near to the letter as I could and compiled the 2.6.21 kernel.  At first, the new kernel didn't boot at all, and gave the message:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

A quick search in the forums allowed me to fix this by changing the grub menu.lst entry for the new kernel:  in the "kernel" command, I changed the "root=UUID=[long string of numbers...]" argument to "root=/dev/sda3".  The kernel apparently now boots fine.

I say "apparently" because of what happens *after* booting.  GDM starts fine, and I can log in using any session...but as soon as I do, I get a brief splash screen (not sure what it's called...where icons for nautilus, metacity, etc. appear as they are loaded), then the desktop flashes black, and then it goes completely white.

I can still see and move the mouse without any trouble, but there are apparently no toolbars or menus; it's just a white, empty desktop.  This behavior is consistent across all GDM sessions (including Failsafe GNOME) except for Failsafe Terminal, which works normally.

I've poked around in the system logs a little to see if I could find any clues as to what's going on, but nothing has jumped out at me.  To be honest, I'm not really sure where I would look -- or if the "white desktop" would even show up in any log as an error.  I've also tried removing and re-installing 915resolution, to no avail.  And GNOME still loads completely normally if I boot a generic kernel.

So, I'm wondering what the next step is.  Is it likely that I forgot to turn something on in the kernel?  Is there any (however slim) chance that my tinkering with grub has caused this problem?  Or am I looking for a more subtle problem, in the rest of my software?

Thanks for your help!

Richard

---

### Post by Gen2ly on 2007-06-05
> **wyley.r said:**
> I have some pretty strange behavior here.  I followed these steps as near to the letter as I could and compiled the 2.6.21 kernel.  At first, the new kernel didn't boot at all, and gave the message:

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)
```

A quick search in the forums allowed me to fix this by changing the grub menu.lst entry for the new kernel:  in the "kernel" command, I changed the "root=UUID=[long string of numbers...]" argument to "root=/dev/sda3".  The kernel apparently now boots fine.

Appreciate the information wyley.  I've tinkering with the that maybe I should add a section that describes how to lookup a UUID and edit grub.

> GDM starts fine, and I can log in using any session...but as soon as I do, I get a brief splash screen (not sure what it's called...where icons for nautilus, metacity, etc. appear as they are loaded), then the desktop flashes black, and then it goes completely white... 

I've poked around in the system logs a little to see if I could find any clues as to what's going on, but nothing has jumped out at me.  To be honest, I'm not really sure where I would look -- or if the "white desktop" would even show up in any log as an error... 

Is there any (however slim) chance that my tinkering with grub has caused this problem?  

Please try deleting .Xauthority in the home directory first. I've seen a few strange things at times when this becomes corrupt.  Don't worry about deleting it as it will be regenertated.  As for you grub quandry - not very likely.  Grub is 2 boot with, it will  specify the vga driver for video until the xorg driver is loaded.  If it's not fixed, can I ask what .config you used?

---

### Post by wyley.r on 2007-06-05
> If it's not fixed, can I ask what .config you used?

Unfortunately, it's not fixed.  I deleted ~/.Xauthority from within the failsafe Xterm session and thereafter restarted X (several times, actually) with no improvement.  I did notice, however, that my usual desktop background appears for a second when X restarts, or when I switch from GNOME to a virtual terminal (e.g., tty2, via Ctrl+Alt+F2).

The .config file I used was the one from the Gentoo wiki.  Looking back at it now, there's no comments in it to verify that I grabbed the right one...but I'm pretty sure I did, and I didn't modify at all.

Any other ideas?

---

### Post by Gen2ly on 2007-06-06
> **wyley.r said:**
> Unfortunately, it's not fixed.  I deleted ~/.Xauthority from within the failsafe Xterm session and thereafter restarted X (several times, actually) with no improvement.  I did notice, however, that my usual desktop background appears for a second when X restarts, or when I switch from GNOME to a virtual terminal (e.g., tty2, via Ctrl+Alt+F2).

The .config file I used was the one from the Gentoo wiki.  Looking back at it now, there's no comments in it to verify that I grabbed the right one...but I'm pretty sure I did, and I didn't modify at all.

Any other ideas?

This probably has to do the the kernel space driver.  This is the .config I use:

[http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files#Kernel_.config](http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files#Kernel_.config)

The setup needs to look as such:

```
Device Drivers  ---> 
  Character devices  ---> 
    <*> Direct Rendering Manager (XFree86 4.1.0 and higher DRI support)  
    < >   3dfx Banshee/Voodoo3+                                          
    < >   ATI Rage 128                                                   
    < >   ATI Radeon                                                     
    < >   Intel I810                                                     
    <*>   Intel 830M, 845G, 852GM, 855GM, 865G (i915 driver)  --->  

  Graphics support  --->
 <*> Intel 830M/845G/852GM/855GM/865G/915G/945G support (EXPERIMENTAL)
    [ ]   Intel driver Debug Messages
    
    [*]   DDC/I2C for Intel framebuffer support

```

Make sure there are not other video drivers selected as this can lead to problems.

---

### Post by wyley.r on 2007-06-06
Well, I decided to start afresh.  I re-downloaded the Gentoo .config, make'd oldconfig and menuconfig, and -- lo and behold -- I'm up and running.

I couldn't tell you what I did differently, really.  I did notice that a couple of the options you gave in your last post were off, but simply turning them on and re-compiling didn't work; I still had the white screen.  But reconfiguring worked.  I must have had something turned off (or on) that I shouldn't have.

Thanks for your help, though!

Richard

---

### Post by oskarloko on 2007-06-06
... just to know 

¿ using Metacity, Beryl, Compiz... ?

¿using xorg i810 or intel driver ?

If you haven't touched anything of above, the basic ubuntu install is with metacity and i810 xorg driver...

( I can be wrong, graphic drivers - kernel and xorg - it's a little mess to me )


Excuse my poor English...

---

### Post by ivesjd on 2007-06-06
I ended up with a kernel panic, said it couldnt mount the root file system. I'm gonna try again tomorrow I think.

---

### Post by Gen2ly on 2007-06-07
Perhaps you're adding or taking items from the .config that need/needn't be there.  The details in my last post were not off.  Thats what you need.  I wouldn't tinker with that config on the first try.  The only difference being that you can compile them in as modules.  Is it Feisty you have installed?

---

### Post by ivesjd on 2007-06-07
Yes it is. And yes I messed with the config quite abit. But really, I wasnt expecting it to work on the first try.

---

### Post by Gen2ly on 2007-06-07
ivesjd, try turning off Desktop Effects.  I just read this thread:

[http://ubuntuforums.org/showthread.php?t=414561](http://ubuntuforums.org/showthread.php?t=414561)

and this one:

[http://ubuntuforums.org/showthread.php?t=465980](http://ubuntuforums.org/showthread.php?t=465980)

It's very possible Compiz is having troubles.

---

### Post by luisbg on 2007-06-25
Anybody could share the resulting debs (image and headers). If someone sends them to my mail bethencourt AT gmail DOT com. I can upload them to a webspace I have and share the link with all.

Thanks!

luisbg

---

### Post by luisbg on 2007-06-25
I meant...

Can anybody please share the resulting debs?

Luis

---

### Post by benanzo on 2007-06-26
I put up my [kernel and header debs along with the config]("http://www.starlitworld.com/macbook_kernel/") for a first-gen MacBook with Core Duo.

```

wget http://www.starlitworld.com/macbook_kernel/linux-headers-2.6.21.1-mactel_i386.deb
wget http://www.starlitworld.com/macbook_kernel/linux-image-2.6.21.1-mactel_i386.deb
wget http://www.starlitworld.com/macbook_kernel/CONFIG.txt

```


There are several power-saving features enabled like dynamic ticks and usb sleep (as suggested by PowerTOP.)

It's a 2.6.21.1 kernel with mactel patches 2.6.21

Good Luck!

---

### Post by ivesjd on 2007-06-26
> **benanzo said:**
> I put up my [kernel and header debs along with the config]("http://www.starlitworld.com/macbook_kernel/") for a first-gen MacBook with Core Duo.

There are several power-saving features enabled like dynamic ticks and usb sleep (as suggested by PowerTOP.)

It's a 2.6.21.1 kernel with mactel patches 2.6.21

Good Luck!

Downloading the headers fails. But thanks alot, Ive wanted a kernel for macbook but just havent been able to compile one yet :)

---

### Post by kzm. on 2007-06-26
this is a very interesting thread. i wont have time to go with benanzos config till at least the weekend. if anybody with a c2d does, i would be pleased to know how it go and what he need to change.

about the compiz/beryl suggestion.. does it mean it will not work with the new kernel?

---

### Post by luisbg on 2007-06-26
Thanks benanzo!

Once we get some Core 2 Duo debs up I will share both of them in my webspace (ubuntustudio server). And we will have the macbooks covered.

Maybe we can try and do the same for MacBook Pro?

I tried a few times to compile a working for my C2D, had no luck, something is going wrong with the initramfs.

Please those of you with C2D debs share.

Luis

---

### Post by ivesjd on 2007-06-26
JUst wondering, why are you using ubuntu studio for a server?

---

### Post by luisbg on 2007-06-26
Oh no I meant the ubuntu studio server, the one with the soon to be dead repo (all going to universe), website, mailing list for devs, and all that jazz.

Luis

pd: sorry for the confusion

---

### Post by benanzo on 2007-06-26
For those having trouble downloading my debs, you should use wget or "Save Link As..." in Firefox.

Also, I have a problem when I install a custom kernel and reboot it is unable to mount root filesystem.  After some investigation I discovered that when it updated my GRUB menu.lst file it uses the UUID for the / (root) partition...which should work, but doesn't.

Just edit that line right after installing the kernel deb to map to /dev/sda1 (or whatever your / (root) partition is) instead of the UUID.

The way it will be:
```
root=UUID=some-long-string
```
change it to:
```
root=/dev/sda1 (or whatever your / is)
```

---

### Post by cyberdork33 on 2007-06-27
Gentoo moved their kernel configs here
[http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel](http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel)

---

### Post by luisbg on 2007-06-28
still no macbook core 2 duo kernel debs?

---

### Post by cyberdork33 on 2007-06-28
> **luisbg said:**
> still no macbook core 2 duo kernel debs?
There is a config file on the gentoo page... why don't you build one?

I have some for one that I modified for a 20" C2D iMac that I will get on here after I make some tweaks.

---

### Post by luisbg on 2007-06-28
I did build my own, tried a few times but always had problems with the initrmfs.

Now, after a total clean reinstall I'm trying again, compiling right now. Let's see if it works.

Luis

---

### Post by luisbg on 2007-06-28
Kernel panic - not syncing : VFS . Unable to mount root fs on unknown-block(0,0)

still the same kernel panic

---

### Post by cyberdork33 on 2007-06-28
This should be the issue that was mentioned earlier:
[quote=benanzo]
Also, I have a problem when I install a custom kernel and reboot it is unable to mount root filesystem. After some investigation I discovered that when it updated my GRUB menu.lst file it uses the UUID for the / (root) partition...which should work, but doesn't.

Just edit that line right after installing the kernel deb to map to /dev/sda1 (or whatever your / (root) partition is) instead of the UUID.

The way it will be:
```
root=UUID=some-long-string
```

change it to:
```
root=/dev/sda1 (or whatever your / is)
```[/quote]

---

### Post by luisbg on 2007-06-28
cyberdork33 thanks!

awesome! have my own kernel working now. I don't have suspend though :(

and btw, all except the feisty kernel are missing the /sys/devices/platform/applesmc/ (I'm including gutsy's kernels 2.6.22 too). anybody knows how to handle the fan speed on this kernels?

luis

---

### Post by luisbg on 2007-06-28
I'm going to go ahead and reply myself for the future forum readers with the same doubt in their heads...

there is a module called applesmc
if you don't have that useful folder in /sys/devices/platform/

sudo modprobe applesmc

and add a line with applesmc in the /ect/modules file so it is loaded on boot.

cheers,
luis

---

### Post by cyberdork33 on 2007-06-28
> **luisbg said:**
> cyberdork33 thanks!
awesome! have my own kernel working now. I don't have suspend though :(


suspend support is another patch I think... suspend2 patches i believe. It has been a long time since I have made my own kernels... most of these things are included in the distro kernels.

On that note, I have a working 2.6.21 kernel config, but I could not get fglrx working correctly with it, and Idk if it is specifically my kernel's fault, or just because I am trying to use a newer kernel / fglrx combo. I think I need to work a bit on it before I give it out.

---

### Post by luisbg on 2007-06-28
yeah ati doesn't help much so getting it perfect is tricky.

luis

---

### Post by Gen2ly on 2007-06-28
I brought up to date the post.  Didnt' think to mention that about the grub line. Thanks.  

Also, I wasn't able to find a MacBook Pro kernel config but I think the only difference is the ATI, and now, nvidia card.  If someone knows of one I'll be happy to list it.

---

### Post by cyberdork33 on 2007-06-29
Has anyone looked at the name of some of these patches?

2.6.22:

appletouch-fix-run-amok-problem.patch
appletouch-shut-up-when-it-has-nothing-to-say.patch

hehe

---

### Post by cyberdork33 on 2007-06-30
Alright, finally got a suitable kernel.

**20" iMac Core2 Duo**
This kernel is *C2D specific* without generic x86 instructions and the appletouch driver is disabled (not needed on iMac).
If booting directly from EFI (elilo) then you can append 'video=imacfb:i20' to use the native iMac framebuffer device.
This seems to mess up your iSight if you had it working (at least for me). Please give feedback on this. You *should* just have to recompile/install the uvcvideo module to get it working again.

**Kernel:**
[http://cyberdork33.com/ubuntu/linux-image-2.6.21.5-mactel-c2dimac20-cd33.deb](http://cyberdork33.com/ubuntu/linux-image-2.6.21.5-mactel-c2dimac20-cd33.deb)
**Headers:**
[http://cyberdork33.com/ubuntu/linux-headers-2.6.21.5-mactel-c2dimac20-cd33.deb](http://cyberdork33.com/ubuntu/linux-headers-2.6.21.5-mactel-c2dimac20-cd33.deb)

***config file posted below. There were still some things I wasn't sure about, so please post tweaks.***

You can use this guide to get the latest fglrx driver and compile it for this kernel:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.38.6_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide#Method_2:_Install_the_8.38.6_Driver_Manually)

Or you can use the module and driver I compiled below:

**fglrx kernel module:**
[http://cyberdork33.com/ubuntu/fglrx-kernel-2.6.21.5-mactel-c2dimac20-cd33_8.38.6-1.deb](http://cyberdork33.com/ubuntu/fglrx-kernel-2.6.21.5-mactel-c2dimac20-cd33_8.38.6-1.deb)
**Updated fglrx driver:**
[http://cyberdork33.com/ubuntu/xorg-driver-fglrx_8.38.6-1_i386.deb](http://cyberdork33.com/ubuntu/xorg-driver-fglrx_8.38.6-1_i386.deb)
**ATI Control Panel (not needed, but nice to have):**
[http://cyberdork33.com/ubuntu/fglrx-amdcccle_8.38.6-1_i386.deb](http://cyberdork33.com/ubuntu/fglrx-amdcccle_8.38.6-1_i386.deb)

Extras for anyone that might want them:
xorg-driver-fglrx-dev:
[http://cyberdork33.com/ubuntu/xorg-driver-fglrx-dev_8.38.6-1_i386.deb](http://cyberdork33.com/ubuntu/xorg-driver-fglrx-dev_8.38.6-1_i386.deb)
fglrx kernel module source:
[http://cyberdork33.com/ubuntu/fglrx-kernel-source_8.38.6-1_i386.deb](http://cyberdork33.com/ubuntu/fglrx-kernel-source_8.38.6-1_i386.deb)
kernel config:
[http://cyberdork33.com/ubuntu/config-2.6.21.5-mactel-c2dimac20-cd33](http://cyberdork33.com/ubuntu/config-2.6.21.5-mactel-c2dimac20-cd33)

Bonus!:
Replace the os_linux.icns file for refit with this:
[http://cyberdork33.com/ubuntu/Ubuntu.icns](http://cyberdork33.com/ubuntu/Ubuntu.icns)

---

### Post by benanzo on 2007-06-30
> If booting directly from EFI (elilo) then you can append 'video=imacfb:i20' to use the native iMac framebuffer device.

Are you able to boot this kernel via EFI?  I noticed that CONFIG_EFI_VARS is not set so ELILO shouldn't be able to boot it.  You can change it to CONFIG_EFI_VARS=m to utilize the EFI variables for ELILO and then you can set boot options with **efibootmgr**.

I'm not sure with the ATI chips, but I know that with the Intels we're having trouble getting framebuffer info directly out of EFI, so if you're on a Mini or a MacBook you'd be stuck using **vesa** with 800x600 res...not usable.  Therefore it's advised to continue using the emulated BIOS for now.

---

### Post by cyberdork33 on 2007-06-30
CONFIG_EFI is set which is the option to make the kernel bootable from EFI.

I didn't think that the access to the EFI Variables was needed for the normal user. I don't boot directly from EFI, so I do not quite understand it all. If the other option needs to be enabled then I can make that change.

```
CONFIG_EFI_VARS:
If you say Y here, you are able to get EFI (Extensible Firmware
Interface) variable information via sysfs.  You may read,
write, create, and destroy EFI variables through this interface.
```

---

### Post by grim1234 on 2007-07-02
Hmm.. after compiling and booting I have no wireless device.

I have a mabook v1, the wireless on the default kernel is ath0.

I used the 2.6.21 source, with the latest mactel patches applied.

Have I missed something from the config? Do I just need to reinitialise ath0 or something similar?

Thanks!

---

### Post by Gen2ly on 2007-07-03
> **grim1234 said:**
> Hmm.. after compiling and booting I have no wireless device.

I have a mabook v1, the wireless on the default kernel is ath0.

I used the 2.6.21 source, with the latest mactel patches applied.

Have I missed something from the config? Do I just need to reinitialise ath0 or something similar?

Thanks!

Wireless is compiled against the kernel, i.e. it uses some of the kernel to compile the driver.  You will need to reinstall the madwifi driver.

[http://ubuntuforums.org/showthread.php?t=485579](http://ubuntuforums.org/showthread.php?t=485579)
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

---

### Post by cyberdork33 on 2007-07-03
yep. There is probably more too. The module that gets your iSight working (uvcvideo), fglrx (if you have ATI), etc.

---

### Post by grim1234 on 2007-07-03
> **Dirk.R.Gently said:**
> Wireless is compiled against the kernel, i.e. it uses some of the kernel to compile the driver.  You will need to reinstall the madwifi driver.

[http://ubuntuforums.org/showthread.php?t=485579](http://ubuntuforums.org/showthread.php?t=485579)
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

Thanks for the answer!

So the previous driver that was installed by default was specific to the 2.6.20-15generic kernel?

Do I need to remove the previous driver?

---

### Post by grim1234 on 2007-07-03
> **cyberdork33 said:**
> yep. There is probably more too. The module that gets your iSight working (uvcvideo), fglrx (if you have ATI), etc.

Is that because all modules are kernel specific? Do I need to be careful there are no leftover modules from the other kernel? 

Anything else to watch out for?

---

### Post by benanzo on 2007-07-03
no, you don't need to uninstall the previous driver.  Kernel modules (like madwifi) install in a directory specific to the current kernel so you can have multiple kernels with multiple madwifi modules installed simultaneously.

---

### Post by grim1234 on 2007-07-03
> **benanzo said:**
> no, you don't need to uninstall the previous driver.  Kernel modules (like madwifi) install in a directory specific to the current kernel so you can have multiple kernels with multiple madwifi modules installed simultaneously.

Great, very logical. 

Where are the modules stored? Are they part of a .deb package? 

I've just been reading a bit about modprobe, does that need to be configured for the modules built for the new kernel?

---

### Post by cyberdork33 on 2007-07-03
you just need to follow the instructions to get it working again after booting your new kernel. usually...

---

### Post by grim1234 on 2007-07-03
Yes, I'm sure it'll work, I just want to understand how, so I can better understand the system and ask less questions.

:)

---

### Post by cyberdork33 on 2007-07-03
/lib/modules

---

### Post by cyberdork33 on 2007-07-08
Just some information. Linux Kernel 2.6.22 Final has been released. This kernel contains many new improvements for Mac Linux support (applesmc - light sensor, sudden motion sensor, keyboard backlight control, fan control)

---

### Post by kzm. on 2007-07-09
will gutsy use that kernel?

---

### Post by benanzo on 2007-07-09
yes, but the Ubuntu kernel team will take newer patches right up until the kernel freeze sometime in august-september

---

### Post by grim1234 on 2007-07-09
are there any outstanding mactel patches or have they all been integrated into 2.6.22?

i.e. : do we still need to patch the 2.6.22 prior to compiling?

---

### Post by cyberdork33 on 2007-07-09
there are some newer patches still. Fixes for the erratic touchpad behavior and some other things are still yet to be added.

[http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/](http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/)

I would attempt to patch as they mactel source will always be more up to date than the vanilla kernel.

---

### Post by grim1234 on 2007-07-10
I get the following error after compiling 2.6.22, with mactel patches applied, and config from gentoo for macbook core duo. 

```
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(8,3)
```

I don't know why it's 8,3, it should be 0,3.

Here is the grub entry :

```

title		Ubuntu, kernel 2.6.22-mactel-macbook-coreduo
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-mactel-macbook-coreduo root=/dev/sda3 ro quiet splash lpj=7330000
initrd		/boot/initrd.img-2.6.22-mactel-macbook-coreduo
quiet
savedefault

```

I have run grub at a terminal and entered

```

root (hd0,3)
setup (hd0,3)

```

I'm using refit as a loader, after this there are 2 linux icons instead of one.

Does anyone know how to fix this? The generic kernel still loads without problems. 

Is it a kernel option perhaps?

---

### Post by cyberdork33 on 2007-07-10
Guessing here:
You have to make sure that support for your root filesystem is compiled into the kernel (not a module) otherwise you cannot start your system, because the kernel cannot open the filesystem to load the module to open the filesystem... (yea you can see the problem here)

EDIT:
Another issue: You are using (hd0,3)  but then specify root=/dev/sda3. This is not the same. (hd0,2) = sda3 (grub counts from 0)

---

### Post by benanzo on 2007-07-10
If you used the gentoo config then support for your root filesystem should already be compiled in (unless you changed it.)

The problem here is that you've got the wrong partition mapped to your **/** (root) drive in GRUB's menu.lst or when  you setup GRUB, you told it to boot from the wrong partition.

If your **/** (root) partition is /dev/sda3 (which is where it most-likely is if you're triple booting) then GRUB will find your system on **(hd0,2)** not **(hd0,3)**.  GRUB starts counting at zero.

To fix:
```
sudo grub
```
```
root (hd0,2)
```
```
setup (hd0,2)
```
```
quit
```

Good Luck!

---

### Post by detjoe on 2007-07-12
Thanks for this awesome HowTo. Did anybody find a .config for the new Santa Rosa MBP? 

Thanks again!

---

### Post by anujseth on 2007-07-13
has anyone managed to check out the mactel patches for the 2.6.22 kernel, trying since yesterday theres something wrong with the svn ... even the web based one won't let me check them out ... if anyone has them upload them here if possible

---

### Post by anujseth on 2007-07-13
sorry , don't bother ... working 

```
svn co http://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.22/ ./mactel-patches-2.6.22

```

---

### Post by Tu13erhead on 2007-07-26
I recompiled per this walkthrough and everything seems to be okay except my touchpad isn't working.  I've been playing around with xorg.conf trying to get it to work and I get nothing.  External mice work fine.

Any ideas?

---

### Post by jbob286 on 2007-07-29
I compiled the 2.6.22.1 kernel with the mactel patches following this howto. This is on a first gen macbook. Unfortunately, I can not compile the latest madwifi driver. I get this error:

```

root@joel-laptop:/home/joel/Desktop/madwifi-0.9.3.1# make
Checking requirements... ok.
Checking kernel configuration... ok.
make -C /lib/modules/2.6.22.1-mactel-macbook-coreduo/build SUBDIRS=/home/joel/Desktop/madwifi-0.9.3.1 modules
make[1]: Entering directory `/usr/src/linux-2.6.22.1'
  CC [M]  /home/joel/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o
cc1: warnings being treated as errors
/home/joel/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c: In function 'ath_pci_probe':
/home/joel/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.c:210: warning: 'deprecated_irq_flag' is deprecated (declared at include/linux/interrupt.h:66)
make[3]: *** [/home/joel/Desktop/madwifi-0.9.3.1/ath/if_ath_pci.o] Error 1
make[2]: *** [/home/joel/Desktop/madwifi-0.9.3.1/ath] Error 2
make[1]: *** [_module_/home/joel/Desktop/madwifi-0.9.3.1] Error 2
make[1]: Leaving directory `/usr/src/linux-2.6.22.1'
make: *** [modules] Error 2

```

What does this mean?

Also, the battery monitor crashes and will not start.

---

### Post by Gen2ly on 2007-07-29
Hi there jbob.  Definitely something about the new kernel i think.  I know the kernel has a introduced an improved networking stack, I read somewhere else someone too was having this issue.  I think we'll have to wait for the new madwifi drivers to be released though. :(  On the plus side you should be able fix fix the gnome-power-manager by killing the process and starting it once more.

---

### Post by Gen2ly on 2007-08-06
Without adieu I present to you the 2.6.22 kernel [COLOR="Navy"][FONT="Fixedsys"].config[/FONT][/COLOR]:
[URL="http://gentoo-wiki.com/HARDWARE_Apple_MacBook/Configuration_Files/Kernel#2.6.22"]
**[COLOR="Sienna"]Gentoo Linux Wiki**[/URL][/COLOR] 

Many of you have already probably done yours but I wanted to test this first.  It's pretty thorough and I'm pretty happy with it.  This configuration is for a First Generation MacBook but should be easy to config for a Second Generation:
[LIST]
[*]Add hyperthreading
[*]Processor type Core 2 Duo
[*]Add 64bit support if using the AMD-64 Ubuntu.
[/LIST]
I diff'd my kernel [COLOR="Navy"][FONT="Fixedsys"].config[/FONT][/COLOR] with [Jen-Fro's]("http://forums.gentoo.org/viewtopic-p-4159968.html#4159968") MacBook Pro kernel [COLOR="Navy"][FONT="Fixedsys"].config[/FONT][/COLOR] and it's probably as triim as it gonna be.  MacBook Pro users should use that link and change these:
[LIST]
[*]Build Appletouch into the kernel.
[*]Alsa as driver?
[/LIST]
**Some notable differences about this 2.6.22.**
[LIST]
[*]Centrino Speedstep left out, Pentium 4 cpu scaling appears to be much more efficient.
[*]Suspend2Source still doesn't work, have to build specifically for it which I don't get.
[*]The console framebuffer driver is disabled - can cause nasty xserver hangs in collaboration with the i810 driver, particularly dbe and programs such as Compiz.
[*]Alsa driver still works better than the kernel version.
[/LIST]
**What you'll need to do after compiling the kernel:**
[LIST]
[*]Reinstall the madwifi drivers.
[*]Reinstall the Alsa driver ( preferred method. )
[/LIST]

 Would like to see the Second Generation MacBook and MacBook Pro kernel [COLOR="Navy"][FONT="Fixedsys"].config[/FONT][/COLOR]'s put up if someone has the time.

This will also be my last kernel update as I have now all the features I need and don't care to trade features for stablility.  I have been looking forward to running stable a long time, and don't plan to change for quite some time.

Good Day.

---

### Post by thephotoman on 2007-08-12
After following the instructions provided here for 2.6.22.2, I found that my wireless card didn't work.  Furthermore, other people here have encountered problems with the stable MadWiFi drivers.  So, once I got the kernel booted, I went back over to my Mac OS side and downloaded the latest version of MadWiFi from Subversion.  It works.

I have taken the liberty of uploading the source of the working MadWiFi drivers to my own server.  You can find it here: [http://www.photosinensis.com/code/madwifi-svn-08112007.tar.gz](http://www.photosinensis.com/code/madwifi-svn-08112007.tar.gz)

I thank you for the guide to setting up the kernel.

---

### Post by Cheka on 2007-08-31
Hey all,

When compiling the kernel, is there special option i need to set for 32bit compatibility mode? (Obviously compiling as a  64bit kernel)

Thanks for your help

---

### Post by karl_kashofer on 2007-08-31
Hi !

I did follow this howto using the 2.6.22 kernel and mactel patches. Everything worked fine, used the config from the gentoo wiki for the 2.6.20 kernel, used defaults for the questions asked by oldconfig, got it to compile, installed it, rebootet.

It did actually boot, but the touchpad is dead. It does not seem to be detected during boot, kdm.log mentions no synaptics touchpad found.

Any hints what to do ?

Thanks,
Karl
Black Macbook 13.3 2.16Ghz

---

### Post by cyberdork33 on 2007-08-31
> **karl_kashofer said:**
> Hi !

I did follow this howto using the 2.6.22 kernel and mactel patches. Everything worked fine, used the config from the gentoo wiki for the 2.6.20 kernel, used defaults for the questions asked by oldconfig, got it to compile, installed it, rebootet.

It did actually boot, but the touchpad is dead. It does not seem to be detected during boot, kdm.log mentions no synaptics touchpad found.

Any hints what to do ?

Thanks,
Karl
Black Macbook 13.3 2.16Ghz
make sure that applesmc  and appletouch modules are loaded or compiled into the kernel.

---

### Post by karl_kashofer on 2007-08-31
Hi again !

> **cyberdork33 said:**
> make sure that applesmc  and appletouch modules are loaded or compiled into the kernel.

Thanks, that did it !!!!

I now run my self-compiled 2.6.22 kernel on my Macbook 13.3 2.16Ghz! 

To all: This resolves the issue with the erratic touchpad behaviour !!!

Now lets wait for apple to fix their firmware so we can get a keyboard in grub...

Thanks for your help !!
Cheers,
Karl

---

### Post by cyberdork33 on 2007-08-31
> **karl_kashofer said:**
> Hi again !



Thanks, that did it !!!!

I now run my self-compiled 2.6.22 kernel on my Macbook 13.3 2.16Ghz! 

To all: This resolves the issue with the erratic touchpad behaviour !!!

Now lets wait for apple to fix their firmware so we can get a keyboard in grub...

Thanks for your help !!
Cheers,
Karl
and boot legacy OS from external drives.

---

### Post by karl_kashofer on 2007-09-01
Hi again !

Happy with my new kernel, but just now aptitude wants to update the 2.6.20 kernel packages.

I am pretty sure this would interfere with my menu.lst, is there a simple way to prevent dist-upgrade from updating the kernel packages ?

Thanks,
Karl

---

### Post by cyberdork33 on 2007-09-01
> **karl_kashofer said:**
> Hi again !

Happy with my new kernel, but just now aptitude wants to update the 2.6.20 kernel packages.

I am pretty sure this would interfere with my menu.lst, is there a simple way to prevent dist-upgrade from updating the kernel packages ?

Thanks,
Karl

if you put your custom kernel entry in the menu.lst file outside the AUTOMAGIC KERNELS LIST section it will not be changed. If you want your custom kernel to be default always then put the config lines directly under ```
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST
``` and before the ```
### BEGIN AUTOMAGIC KERNELS LIST
```

Upgrading the kernel should not be an issue after that.

---

### Post by fizz on 2007-09-04
im a little confused as to which .config to use. I have a first gen macbook pro with the atheros wireless chipset. On the one page, for  first gen mbp it just says similar to. I did go ahead and use the second gen config, but it wouldnt boot, it would just hang on the splash screen. i had to use a live cd to mount the filesystem and remove that entry from grub so that I could boot.  Thanks in advance if you have anything that would help me get on the right course.

---

### Post by cyberdork33 on 2007-09-04
> **fizz said:**
> im a little confused as to which .config to use. I have a first gen macbook pro with the atheros wireless chipset. On the one page, for  first gen mbp it just says similar to. I did go ahead and use the second gen config, but it wouldnt boot, it would just hang on the splash screen. i had to use a live cd to mount the filesystem and remove that entry from grub so that I could boot.  Thanks in advance if you have anything that would help me get on the right course.Tailoring your kernel is kind of an art. You will have to dabble with the config to get it working for your machine. Note that the config posted for the MacbookPro is 64-bit. You you have installed the normal 32bit OS, then you need to make sure that it is compatible with 32bit, and not 64bit only.

---

### Post by fizz on 2007-09-05
Alright, I'll give it another shot this afternoon. Thanks...

---

### Post by AWerner32 on 2007-09-09
hey i have it booting just fine, used kernel 2.6.22.6 and the mactel patches 2.6.22 everything works but the sound and wifi, i was using the proprietary atheros wireless driver for wifi and i have no idea how to approach the sounds thing. I am probably going to go ahead and install madwif drivers.

---

### Post by cyberdork33 on 2007-09-09
> **AWerner32 said:**
> hey i have it booting just fine, used kernel 2.6.22.6 and the mactel patches 2.6.22 everything works but the sound and wifi, i was using the proprietary atheros wireless driver for wifi and i have no idea how to approach the sounds thing. I am probably going to go ahead and install madwif drivers.

There were a few changes in thee sound settings for me in 2.6.22.6 I would suggest running alsamixer and make sure that all the channels are unmuted, and determine which one actually controls sound output. The "Master" channel on my iMac does absolutely nothing now.

---

### Post by tehkain on 2007-09-09
Anyone here compiling kernels for gutsy with the mactel patches? I am really running hot and  am looking into this now. This is on a few day old Macbook c2d with a super drive.

---

### Post by AWerner32 on 2007-09-10
no the problem as it appears to me is that linux doesnt see the sound card at all

---

### Post by cyberdork33 on 2007-09-10
> **AWerner32 said:**
> no the problem as it appears to me is that linux doesnt see the sound card at all
Maybe a misconfigured kernel? Did you add support for ALSA and choose the correct hardware?

---

### Post by xeth_delta on 2007-10-10
Hi everyone!

I might be wrong about this, but has aybody else noticed that the 2.6.20 kernel configuration file in the gentoowiki for the second generation Macbooks is actually configured for the Pentium 4? It is not only the CPU scaling that is chosen for this kind of processor, but also the CPU type itsef!

I have a second generation Macbook and used the 2.6.22 kernel configuration file for the First generation Macbook and made the changes needed for it to work properly on my laptop. I am still testing it but if anyody is interested I can post it on the forum.

I am glad to say that suspend to ram and hibernate seem to be working properly. I had to recompile the wireless card and alsa drivers.

There seems to be a problem with the touchpad that persists from the Gutsy kernel. Several times I have to move the pointer for a click to be performed completely. I have noticed also focuse problems when selecting forms fields with the mouse, for example in web pages.

Anyone else has noticed these problems?

Xeth

---

### Post by xoai on 2007-10-10
Did anyone here compile the last stable 2.6.23 kernel with mactel patch? I just tried and got the error
applesmc-add-macbook-temperature-keys.patch would not apply cleanly

-_- It seems that Mactel Patch does not update so freequently!

---

### Post by rekstorm on 2007-10-11
> **xeth_delta said:**
> Hi everyone!

I might be wrong about this, but has aybody else noticed that the 2.6.20 kernel configuration file in the gentoowiki for the second generation Macbooks is actually configured for the Pentium 4? It is not only the CPU scaling that is chosen for this kind of processor, but also the CPU type itsef!

I have a second generation Macbook and used the 2.6.22 kernel configuration file for the First generation Macbook and made the changes needed for it to work properly on my laptop. I am still testing it but if anyody is interested I can post it on the forum.

I am glad to say that suspend to ram and hibernate seem to be working properly. I had to recompile the wireless card and alsa drivers.

There seems to be a problem with the touchpad that persists from the Gutsy kernel. Several times I have to move the pointer for a click to be performed completely. I have noticed also focuse problems when selecting forms fields with the mouse, for example in web pages.

Anyone else has noticed these problems?

Xeth

Hi, I'm interested in version 2.6.22 kernel config for C2D (second generation) macbook. did you compile it for x86 (32 bit) or for x86-64 (64 bit)?
Are you running it on Feisty or on Gutsy beta?

thank you!
Bye

---

### Post by cyberdork33 on 2007-10-11
> **xoai said:**
> Did anyone here compile the last stable 2.6.23 kernel with mactel patch? I just tried and got the error
applesmc-add-macbook-temperature-keys.patch would not apply cleanly

-_- It seems that Mactel Patch does not update so freequently!
There is no directory for 2.6.23 in the mactel subversion repository. and the last change to the 2.6.22 patches was 2 weeks ago.

---

### Post by xeth_delta on 2007-10-11
> **rekstorm said:**
> Hi, I'm interested in version 2.6.22 kernel config for C2D (second generation) macbook. did you compile it for x86 (32 bit) or for x86-64 (64 bit)?
Are you running it on Feisty or on Gutsy beta?

thank you!
Bye

I am running the 2.6.22 kernel on Feisty Fawn, 32 bit.
About the Gutsy kernel. You can install it from the Gutsy repositories and run it on Feisty too. There is a thread on this subject. You just have to be careful not to forget restoring /etc/apt/sources.list to its original state after installing that kernel.

Let me know if you still need the config file.

Xeth

---

### Post by rekstorm on 2007-10-12
yeah... I'm currently running 2.6.22-14 in gutsy beta, but I'm interested in compiling a 2.6.22 kernel by myself to have better optimization and to be able to use some stuffs like powertop, so, if you can, post the kernel config.
To compile it did you follow the same hits described in this thread? 
When you said "I had to recompile wireless card and alsa drivers" which step did you follow?
thak you in advance!

---

### Post by xeth_delta on 2007-10-12
> yeah... I'm currently running 2.6.22-14 in gutsy beta, but I'm interested in compiling a 2.6.22 kernel by myself to have better optimization and to be able to use some stuffs like powertop, so, if you can, post the kernel config.
To compile it did you follow the same hits described in this thread? 
When you said "I had to recompile wireless card and alsa drivers" which step did you follow?
thak you in advance!

I have indeed used the steps mentioned in this thread to compile the kernel:
-Instructions posted by Dirk.R.Gently
-applied the patches from [http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/]("http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/") 

You should be able to run powertop from the kernel you already have, shouldn't you?

As I said in a previous post I am still trying it and I have found several new problems you should be aware of:
-Some strange mouse click and focus behaviour
-Apple remote doesn't work as before. The infrared sensor is supposed to work directly from lirc right now, but I have not managed to do so yet [http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/appleir-undo-hid-blacklist.patch?revision=135&view=markup]("http://mactel-linux.svn.sourceforge.net/viewvc/mactel-linux/trunk/kernel/mactel-patches-2.6.22/appleir-undo-hid-blacklist.patch?revision=135&view=markup")
-Madwifi: There seems to be a problem with some versions of the driver source code and the new kernel. I myself get the following error messages after a certain time:
```
dmesg
wifi0: rx FIFO overrun; resetting
```
I understand form this thread they might have found a solution, installing the svn version: [http://ubuntuforums.org/showthread.php?t=442941&page=8]("http://ubuntuforums.org/showthread.php?t=442941&page=8")
I will try this a bit later and come back with any news.

On the positive side, there are a lot fewer modules loaded, hibernate and suspend to ram work, the cpu seems to be a bit cooler, powertop is usable, and there is better energy efficiency than in the stock kernel in Feisty.

The .config file I used is the following:

```
#
# Automatically generated make config: don't edit
# Linux kernel version: 2.6.22.9-mactel
# Sun Sep 30 12:38:43 2007
#
CONFIG_X86_32=y
CONFIG_GENERIC_TIME=y
CONFIG_CLOCKSOURCE_WATCHDOG=y
CONFIG_GENERIC_CLOCKEVENTS=y
CONFIG_GENERIC_CLOCKEVENTS_BROADCAST=y
CONFIG_LOCKDEP_SUPPORT=y
CONFIG_STACKTRACE_SUPPORT=y
CONFIG_SEMAPHORE_SLEEPERS=y
CONFIG_X86=y
CONFIG_MMU=y
CONFIG_ZONE_DMA=y
CONFIG_QUICKLIST=y
CONFIG_GENERIC_ISA_DMA=y
CONFIG_GENERIC_IOMAP=y
CONFIG_GENERIC_BUG=y
CONFIG_GENERIC_HWEIGHT=y
CONFIG_ARCH_MAY_HAVE_PC_FDC=y
CONFIG_DMI=y
CONFIG_DEFCONFIG_LIST="/lib/modules/$UNAME_RELEASE/.config"

#
# Code maturity level options
#
CONFIG_EXPERIMENTAL=y
CONFIG_LOCK_KERNEL=y
CONFIG_INIT_ENV_ARG_LIMIT=32

#
# General setup
#
CONFIG_LOCALVERSION=""
CONFIG_LOCALVERSION_AUTO=y
CONFIG_SWAP=y
CONFIG_SYSVIPC=y
# CONFIG_IPC_NS is not set
CONFIG_SYSVIPC_SYSCTL=y
CONFIG_POSIX_MQUEUE=y
CONFIG_BSD_PROCESS_ACCT=y
# CONFIG_BSD_PROCESS_ACCT_V3 is not set
# CONFIG_TASKSTATS is not set
# CONFIG_UTS_NS is not set
# CONFIG_AUDIT is not set
CONFIG_IKCONFIG=y
CONFIG_IKCONFIG_PROC=y
CONFIG_LOG_BUF_SHIFT=15
# CONFIG_CPUSETS is not set
# CONFIG_SYSFS_DEPRECATED is not set
# CONFIG_RELAY is not set
CONFIG_BLK_DEV_INITRD=y
CONFIG_INITRAMFS_SOURCE=""
# CONFIG_CC_OPTIMIZE_FOR_SIZE is not set
CONFIG_SYSCTL=y
# CONFIG_EMBEDDED is not set
CONFIG_UID16=y
CONFIG_SYSCTL_SYSCALL=y
CONFIG_KALLSYMS=y
# CONFIG_KALLSYMS_ALL is not set
# CONFIG_KALLSYMS_EXTRA_PASS is not set
CONFIG_HOTPLUG=y
CONFIG_PRINTK=y
CONFIG_BUG=y
CONFIG_ELF_CORE=y
CONFIG_BASE_FULL=y
CONFIG_FUTEX=y
CONFIG_ANON_INODES=y
CONFIG_EPOLL=y
CONFIG_SIGNALFD=y
CONFIG_EVENTFD=y
CONFIG_SHMEM=y
CONFIG_VM_EVENT_COUNTERS=y
CONFIG_SLUB_DEBUG=y
# CONFIG_SLAB is not set
CONFIG_SLUB=y
# CONFIG_SLOB is not set
CONFIG_RT_MUTEXES=y
# CONFIG_TINY_SHMEM is not set
CONFIG_BASE_SMALL=0

#
# Loadable module support
#
CONFIG_MODULES=y
CONFIG_MODULE_UNLOAD=y
# CONFIG_MODULE_FORCE_UNLOAD is not set
# CONFIG_MODVERSIONS is not set
# CONFIG_MODULE_SRCVERSION_ALL is not set
CONFIG_KMOD=y
CONFIG_STOP_MACHINE=y

#
# Block layer
#
CONFIG_BLOCK=y
# CONFIG_LBD is not set
# CONFIG_BLK_DEV_IO_TRACE is not set
# CONFIG_LSF is not set

#
# IO Schedulers
#
CONFIG_IOSCHED_NOOP=y
# CONFIG_IOSCHED_AS is not set
# CONFIG_IOSCHED_DEADLINE is not set
CONFIG_IOSCHED_CFQ=y
# CONFIG_DEFAULT_AS is not set
# CONFIG_DEFAULT_DEADLINE is not set
CONFIG_DEFAULT_CFQ=y
# CONFIG_DEFAULT_NOOP is not set
CONFIG_DEFAULT_IOSCHED="cfq"

#
# Processor type and features
#
CONFIG_TICK_ONESHOT=y
CONFIG_NO_HZ=y
CONFIG_HIGH_RES_TIMERS=y
CONFIG_SMP=y
CONFIG_X86_PC=y
# CONFIG_X86_ELAN is not set
# CONFIG_X86_VOYAGER is not set
# CONFIG_X86_NUMAQ is not set
# CONFIG_X86_SUMMIT is not set
# CONFIG_X86_BIGSMP is not set
# CONFIG_X86_VISWS is not set
# CONFIG_X86_GENERICARCH is not set
# CONFIG_X86_ES7000 is not set
# CONFIG_PARAVIRT is not set
# CONFIG_M386 is not set
# CONFIG_M486 is not set
# CONFIG_M586 is not set
# CONFIG_M586TSC is not set
# CONFIG_M586MMX is not set
# CONFIG_M686 is not set
# CONFIG_MPENTIUMII is not set
# CONFIG_MPENTIUMIII is not set
# CONFIG_MPENTIUMM is not set
CONFIG_MCORE2=y
# CONFIG_MPENTIUM4 is not set
# CONFIG_MK6 is not set
# CONFIG_MK7 is not set
# CONFIG_MK8 is not set
# CONFIG_MCRUSOE is not set
# CONFIG_MEFFICEON is not set
# CONFIG_MWINCHIPC6 is not set
# CONFIG_MWINCHIP2 is not set
# CONFIG_MWINCHIP3D is not set
# CONFIG_MGEODEGX1 is not set
# CONFIG_MGEODE_LX is not set
# CONFIG_MCYRIXIII is not set
# CONFIG_MVIAC3_2 is not set
# CONFIG_MVIAC7 is not set
# CONFIG_X86_GENERIC is not set
CONFIG_X86_CMPXCHG=y
CONFIG_X86_L1_CACHE_SHIFT=6
CONFIG_X86_XADD=y
CONFIG_RWSEM_XCHGADD_ALGORITHM=y
# CONFIG_ARCH_HAS_ILOG2_U32 is not set
# CONFIG_ARCH_HAS_ILOG2_U64 is not set
CONFIG_GENERIC_CALIBRATE_DELAY=y
CONFIG_X86_WP_WORKS_OK=y
CONFIG_X86_INVLPG=y
CONFIG_X86_BSWAP=y
CONFIG_X86_POPAD_OK=y
CONFIG_X86_GOOD_APIC=y
CONFIG_X86_INTEL_USERCOPY=y
CONFIG_X86_USE_PPRO_CHECKSUM=y
CONFIG_X86_TSC=y
CONFIG_X86_MINIMUM_CPU_MODEL=4
CONFIG_HPET_TIMER=y
CONFIG_HPET_EMULATE_RTC=y
CONFIG_NR_CPUS=2
CONFIG_SCHED_SMT=y
CONFIG_SCHED_MC=y
# CONFIG_PREEMPT_NONE is not set
CONFIG_PREEMPT_VOLUNTARY=y
# CONFIG_PREEMPT is not set
CONFIG_PREEMPT_BKL=y
CONFIG_X86_LOCAL_APIC=y
CONFIG_X86_IO_APIC=y
CONFIG_X86_MCE=y
# CONFIG_X86_MCE_NONFATAL is not set
CONFIG_X86_MCE_P4THERMAL=y
CONFIG_VM86=y
# CONFIG_TOSHIBA is not set
# CONFIG_I8K is not set
# CONFIG_X86_REBOOTFIXUPS is not set
# CONFIG_MICROCODE is not set
CONFIG_X86_MSR=y
CONFIG_X86_CPUID=y

#
# Firmware Drivers
#
# CONFIG_EDD is not set
# CONFIG_DELL_RBU is not set
# CONFIG_DCDBAS is not set
CONFIG_NOHIGHMEM=y
# CONFIG_HIGHMEM4G is not set
# CONFIG_HIGHMEM64G is not set
CONFIG_PAGE_OFFSET=0xC0000000
CONFIG_NEED_NODE_MEMMAP_SIZE=y
CONFIG_ARCH_FLATMEM_ENABLE=y
CONFIG_ARCH_SPARSEMEM_ENABLE=y
CONFIG_ARCH_SELECT_MEMORY_MODEL=y
CONFIG_ARCH_POPULATES_NODE_MAP=y
CONFIG_SELECT_MEMORY_MODEL=y
# CONFIG_FLATMEM_MANUAL is not set
# CONFIG_DISCONTIGMEM_MANUAL is not set
CONFIG_SPARSEMEM_MANUAL=y
CONFIG_SPARSEMEM=y
CONFIG_HAVE_MEMORY_PRESENT=y
CONFIG_SPARSEMEM_STATIC=y

#
# Memory hotplug is currently incompatible with Software Suspend
#
CONFIG_SPLIT_PTLOCK_CPUS=4
# CONFIG_RESOURCES_64BIT is not set
CONFIG_ZONE_DMA_FLAG=1
CONFIG_NR_QUICK=1
# CONFIG_MATH_EMULATION is not set
CONFIG_MTRR=y
# CONFIG_EFI is not set
# CONFIG_IRQBALANCE is not set
CONFIG_SECCOMP=y
# CONFIG_HZ_100 is not set
# CONFIG_HZ_250 is not set
# CONFIG_HZ_300 is not set
CONFIG_HZ_1000=y
CONFIG_HZ=1000
CONFIG_KEXEC=y
CONFIG_PHYSICAL_START=0x100000
# CONFIG_RELOCATABLE is not set
CONFIG_PHYSICAL_ALIGN=0x100000
CONFIG_HOTPLUG_CPU=y
CONFIG_COMPAT_VDSO=y

#
# Power management options (ACPI, APM)
#
CONFIG_PM=y
# CONFIG_PM_LEGACY is not set
# CONFIG_PM_DEBUG is not set
# CONFIG_PM_SYSFS_DEPRECATED is not set
CONFIG_SOFTWARE_SUSPEND=y
CONFIG_PM_STD_PARTITION=""
CONFIG_SUSPEND_SMP=y

#
# ACPI (Advanced Configuration and Power Interface) Support
#
CONFIG_ACPI=y
CONFIG_ACPI_SLEEP=y
CONFIG_ACPI_SLEEP_PROC_FS=y
# CONFIG_ACPI_SLEEP_PROC_SLEEP is not set
# CONFIG_ACPI_PROCFS is not set
CONFIG_ACPI_AC=y
CONFIG_ACPI_BATTERY=y
CONFIG_ACPI_BUTTON=y
CONFIG_ACPI_VIDEO=y
CONFIG_ACPI_FAN=y
# CONFIG_ACPI_DOCK is not set
CONFIG_ACPI_PROCESSOR=y
CONFIG_ACPI_HOTPLUG_CPU=y
CONFIG_ACPI_THERMAL=y
# CONFIG_ACPI_ASUS is not set
# CONFIG_ACPI_TOSHIBA is not set
CONFIG_ACPI_BLACKLIST_YEAR=0
# CONFIG_ACPI_DEBUG is not set
CONFIG_ACPI_EC=y
CONFIG_ACPI_POWER=y
CONFIG_ACPI_SYSTEM=y
CONFIG_X86_PM_TIMER=y
CONFIG_ACPI_CONTAINER=y
# CONFIG_ACPI_SBS is not set
# CONFIG_APM is not set

#
# CPU Frequency scaling
#
CONFIG_CPU_FREQ=y
CONFIG_CPU_FREQ_TABLE=y
# CONFIG_CPU_FREQ_DEBUG is not set
CONFIG_CPU_FREQ_STAT=y
# CONFIG_CPU_FREQ_STAT_DETAILS is not set
CONFIG_CPU_FREQ_DEFAULT_GOV_PERFORMANCE=y
# CONFIG_CPU_FREQ_DEFAULT_GOV_USERSPACE is not set
CONFIG_CPU_FREQ_GOV_PERFORMANCE=y
CONFIG_CPU_FREQ_GOV_POWERSAVE=y
CONFIG_CPU_FREQ_GOV_USERSPACE=y
CONFIG_CPU_FREQ_GOV_ONDEMAND=y
CONFIG_CPU_FREQ_GOV_CONSERVATIVE=y

#
# CPUFreq processor drivers
#
CONFIG_X86_ACPI_CPUFREQ=y
# CONFIG_X86_POWERNOW_K6 is not set
# CONFIG_X86_POWERNOW_K7 is not set
# CONFIG_X86_POWERNOW_K8 is not set
# CONFIG_X86_GX_SUSPMOD is not set
# CONFIG_X86_SPEEDSTEP_CENTRINO is not set
# CONFIG_X86_SPEEDSTEP_ICH is not set
# CONFIG_X86_SPEEDSTEP_SMI is not set
# CONFIG_X86_P4_CLOCKMOD is not set
# CONFIG_X86_CPUFREQ_NFORCE2 is not set
# CONFIG_X86_LONGRUN is not set
# CONFIG_X86_LONGHAUL is not set
# CONFIG_X86_E_POWERSAVER is not set

#
# shared options
#
# CONFIG_X86_ACPI_CPUFREQ_PROC_INTF is not set
# CONFIG_X86_SPEEDSTEP_LIB is not set

#
# Bus options (PCI, PCMCIA, EISA, MCA, ISA)
#
CONFIG_PCI=y
# CONFIG_PCI_GOBIOS is not set
# CONFIG_PCI_GOMMCONFIG is not set
# CONFIG_PCI_GODIRECT is not set
CONFIG_PCI_GOANY=y
CONFIG_PCI_BIOS=y
CONFIG_PCI_DIRECT=y
CONFIG_PCI_MMCONFIG=y
CONFIG_PCIEPORTBUS=y
CONFIG_PCIEAER=y
CONFIG_ARCH_SUPPORTS_MSI=y
CONFIG_PCI_MSI=y
# CONFIG_PCI_DEBUG is not set
CONFIG_HT_IRQ=y
CONFIG_ISA_DMA_API=y
# CONFIG_ISA is not set
# CONFIG_MCA is not set
# CONFIG_SCx200 is not set

#
# PCCARD (PCMCIA/CardBus) support
#
# CONFIG_PCCARD is not set
# CONFIG_HOTPLUG_PCI is not set

#
# Executable file formats
#
CONFIG_BINFMT_ELF=y
# CONFIG_BINFMT_AOUT is not set
# CONFIG_BINFMT_MISC is not set

#
# Networking
#
CONFIG_NET=y

#
# Networking options
#
CONFIG_PACKET=y
CONFIG_PACKET_MMAP=y
CONFIG_UNIX=y
CONFIG_XFRM=y
CONFIG_XFRM_USER=y
# CONFIG_XFRM_SUB_POLICY is not set
# CONFIG_XFRM_MIGRATE is not set
# CONFIG_NET_KEY is not set
CONFIG_INET=y
# CONFIG_IP_MULTICAST is not set
# CONFIG_IP_ADVANCED_ROUTER is not set
CONFIG_IP_FIB_HASH=y
# CONFIG_IP_PNP is not set
# CONFIG_NET_IPIP is not set
# CONFIG_NET_IPGRE is not set
# CONFIG_ARPD is not set
# CONFIG_SYN_COOKIES is not set
# CONFIG_INET_AH is not set
# CONFIG_INET_ESP is not set
# CONFIG_INET_IPCOMP is not set
# CONFIG_INET_XFRM_TUNNEL is not set
# CONFIG_INET_TUNNEL is not set
CONFIG_INET_XFRM_MODE_TRANSPORT=y
CONFIG_INET_XFRM_MODE_TUNNEL=y
CONFIG_INET_XFRM_MODE_BEET=y
# CONFIG_INET_DIAG is not set
# CONFIG_TCP_CONG_ADVANCED is not set
CONFIG_TCP_CONG_CUBIC=y
CONFIG_DEFAULT_TCP_CONG="cubic"
# CONFIG_TCP_MD5SIG is not set
# CONFIG_IP_VS is not set
# CONFIG_IPV6 is not set
# CONFIG_INET6_XFRM_TUNNEL is not set
# CONFIG_INET6_TUNNEL is not set
# CONFIG_NETLABEL is not set
# CONFIG_NETWORK_SECMARK is not set
CONFIG_NETFILTER=y
# CONFIG_NETFILTER_DEBUG is not set

#
# Core Netfilter Configuration
#
CONFIG_NETFILTER_NETLINK=m
CONFIG_NETFILTER_NETLINK_QUEUE=m
CONFIG_NETFILTER_NETLINK_LOG=m
CONFIG_NF_CONNTRACK_ENABLED=m
CONFIG_NF_CONNTRACK=m
CONFIG_NF_CT_ACCT=y
CONFIG_NF_CONNTRACK_MARK=y
# CONFIG_NF_CONNTRACK_EVENTS is not set
CONFIG_NF_CT_PROTO_GRE=m
CONFIG_NF_CT_PROTO_SCTP=m
# CONFIG_NF_CONNTRACK_AMANDA is not set
CONFIG_NF_CONNTRACK_FTP=m
CONFIG_NF_CONNTRACK_H323=m
# CONFIG_NF_CONNTRACK_IRC is not set
CONFIG_NF_CONNTRACK_NETBIOS_NS=m
CONFIG_NF_CONNTRACK_PPTP=m
CONFIG_NF_CONNTRACK_SANE=m
CONFIG_NF_CONNTRACK_SIP=m
CONFIG_NF_CONNTRACK_TFTP=m
CONFIG_NF_CT_NETLINK=m
CONFIG_NETFILTER_XTABLES=m
CONFIG_NETFILTER_XT_TARGET_CLASSIFY=m
# CONFIG_NETFILTER_XT_TARGET_CONNMARK is not set
# CONFIG_NETFILTER_XT_TARGET_DSCP is not set
CONFIG_NETFILTER_XT_TARGET_MARK=m
CONFIG_NETFILTER_XT_TARGET_NFQUEUE=m
CONFIG_NETFILTER_XT_TARGET_NFLOG=m
# CONFIG_NETFILTER_XT_TARGET_NOTRACK is not set
CONFIG_NETFILTER_XT_TARGET_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_COMMENT=m
CONFIG_NETFILTER_XT_MATCH_CONNBYTES=m
CONFIG_NETFILTER_XT_MATCH_CONNMARK=m
CONFIG_NETFILTER_XT_MATCH_CONNTRACK=m
CONFIG_NETFILTER_XT_MATCH_DCCP=m
CONFIG_NETFILTER_XT_MATCH_DSCP=m
CONFIG_NETFILTER_XT_MATCH_ESP=m
CONFIG_NETFILTER_XT_MATCH_HELPER=m
CONFIG_NETFILTER_XT_MATCH_LENGTH=m
CONFIG_NETFILTER_XT_MATCH_LIMIT=m
CONFIG_NETFILTER_XT_MATCH_MAC=m
CONFIG_NETFILTER_XT_MATCH_MARK=m
CONFIG_NETFILTER_XT_MATCH_POLICY=m
CONFIG_NETFILTER_XT_MATCH_MULTIPORT=m
CONFIG_NETFILTER_XT_MATCH_PKTTYPE=m
CONFIG_NETFILTER_XT_MATCH_QUOTA=m
CONFIG_NETFILTER_XT_MATCH_REALM=m
CONFIG_NETFILTER_XT_MATCH_SCTP=m
CONFIG_NETFILTER_XT_MATCH_STATE=m
CONFIG_NETFILTER_XT_MATCH_STATISTIC=m
CONFIG_NETFILTER_XT_MATCH_STRING=m
CONFIG_NETFILTER_XT_MATCH_TCPMSS=m
CONFIG_NETFILTER_XT_MATCH_HASHLIMIT=m

#
# IP: Netfilter Configuration
#
CONFIG_NF_CONNTRACK_IPV4=m
CONFIG_NF_CONNTRACK_PROC_COMPAT=y
CONFIG_IP_NF_QUEUE=m
CONFIG_IP_NF_IPTABLES=m
CONFIG_IP_NF_MATCH_IPRANGE=m
CONFIG_IP_NF_MATCH_TOS=m
CONFIG_IP_NF_MATCH_RECENT=m
CONFIG_IP_NF_MATCH_ECN=m
CONFIG_IP_NF_MATCH_AH=m
CONFIG_IP_NF_MATCH_TTL=m
CONFIG_IP_NF_MATCH_OWNER=m
CONFIG_IP_NF_MATCH_ADDRTYPE=m
CONFIG_IP_NF_FILTER=m
CONFIG_IP_NF_TARGET_REJECT=m
CONFIG_IP_NF_TARGET_LOG=m
CONFIG_IP_NF_TARGET_ULOG=m
CONFIG_NF_NAT=m
CONFIG_NF_NAT_NEEDED=y
CONFIG_IP_NF_TARGET_MASQUERADE=m
CONFIG_IP_NF_TARGET_REDIRECT=m
CONFIG_IP_NF_TARGET_NETMAP=m
CONFIG_IP_NF_TARGET_SAME=m
CONFIG_NF_NAT_SNMP_BASIC=m
CONFIG_NF_NAT_PROTO_GRE=m
CONFIG_NF_NAT_FTP=m
# CONFIG_NF_NAT_IRC is not set
CONFIG_NF_NAT_TFTP=m
# CONFIG_NF_NAT_AMANDA is not set
CONFIG_NF_NAT_PPTP=m
CONFIG_NF_NAT_H323=m
CONFIG_NF_NAT_SIP=m
CONFIG_IP_NF_MANGLE=m
CONFIG_IP_NF_TARGET_TOS=m
CONFIG_IP_NF_TARGET_ECN=m
CONFIG_IP_NF_TARGET_TTL=m
CONFIG_IP_NF_TARGET_CLUSTERIP=m
CONFIG_IP_NF_RAW=m
CONFIG_IP_NF_ARPTABLES=m
CONFIG_IP_NF_ARPFILTER=m
CONFIG_IP_NF_ARP_MANGLE=m
# CONFIG_IP_DCCP is not set
CONFIG_IP_SCTP=y
# CONFIG_SCTP_DBG_MSG is not set
# CONFIG_SCTP_DBG_OBJCNT is not set
# CONFIG_SCTP_HMAC_NONE is not set
# CONFIG_SCTP_HMAC_SHA1 is not set
CONFIG_SCTP_HMAC_MD5=y
# CONFIG_TIPC is not set
# CONFIG_ATM is not set
# CONFIG_BRIDGE is not set
# CONFIG_VLAN_8021Q is not set
# CONFIG_DECNET is not set
# CONFIG_LLC2 is not set
# CONFIG_IPX is not set
# CONFIG_ATALK is not set
# CONFIG_X25 is not set
# CONFIG_LAPB is not set
# CONFIG_ECONET is not set
# CONFIG_WAN_ROUTER is not set

#
# QoS and/or fair queueing
#
# CONFIG_NET_SCHED is not set
CONFIG_NET_CLS_ROUTE=y

#
# Network testing
#
# CONFIG_NET_PKTGEN is not set
# CONFIG_HAMRADIO is not set
# CONFIG_IRDA is not set
CONFIG_BT=m
CONFIG_BT_L2CAP=m
CONFIG_BT_SCO=m
CONFIG_BT_RFCOMM=m
CONFIG_BT_RFCOMM_TTY=y
CONFIG_BT_BNEP=m
CONFIG_BT_BNEP_MC_FILTER=y
CONFIG_BT_BNEP_PROTO_FILTER=y
CONFIG_BT_HIDP=m

#
# Bluetooth device drivers
#
CONFIG_BT_HCIUSB=m
CONFIG_BT_HCIUSB_SCO=y
CONFIG_BT_HCIUART=m
CONFIG_BT_HCIUART_H4=y
CONFIG_BT_HCIUART_BCSP=y
CONFIG_BT_HCIBCM203X=m
CONFIG_BT_HCIBPA10X=m
CONFIG_BT_HCIBFUSB=m
CONFIG_BT_HCIVHCI=m
# CONFIG_AF_RXRPC is not set

#
# Wireless
#
# CONFIG_CFG80211 is not set
CONFIG_WIRELESS_EXT=y
# CONFIG_MAC80211 is not set
CONFIG_IEEE80211=m
# CONFIG_IEEE80211_DEBUG is not set
CONFIG_IEEE80211_CRYPT_WEP=m
CONFIG_IEEE80211_CRYPT_CCMP=m
CONFIG_IEEE80211_CRYPT_TKIP=m
CONFIG_IEEE80211_SOFTMAC=m
# CONFIG_IEEE80211_SOFTMAC_DEBUG is not set
# CONFIG_RFKILL is not set

#
# Device Drivers
#

#
# Generic Driver Options
#
CONFIG_STANDALONE=y
CONFIG_PREVENT_FIRMWARE_BUILD=y
CONFIG_FW_LOADER=m
# CONFIG_DEBUG_DRIVER is not set
# CONFIG_DEBUG_DEVRES is not set
# CONFIG_SYS_HYPERVISOR is not set

#
# Connector - unified userspace <-> kernelspace linker
#
# CONFIG_CONNECTOR is not set
# CONFIG_MTD is not set

#
# Parallel port support
#
CONFIG_PARPORT=y
# CONFIG_PARPORT_PC is not set
# CONFIG_PARPORT_GSC is not set
# CONFIG_PARPORT_AX88796 is not set
# CONFIG_PARPORT_1284 is not set

#
# Plug and Play support
#
CONFIG_PNP=y
# CONFIG_PNP_DEBUG is not set

#
# Protocols
#
CONFIG_PNPACPI=y

#
# Block devices
#
# CONFIG_BLK_DEV_FD is not set
# CONFIG_BLK_CPQ_DA is not set
# CONFIG_BLK_CPQ_CISS_DA is not set
# CONFIG_BLK_DEV_DAC960 is not set
# CONFIG_BLK_DEV_UMEM is not set
# CONFIG_BLK_DEV_COW_COMMON is not set
CONFIG_BLK_DEV_LOOP=y
# CONFIG_BLK_DEV_CRYPTOLOOP is not set
CONFIG_BLK_DEV_NBD=m
# CONFIG_BLK_DEV_SX8 is not set
# CONFIG_BLK_DEV_UB is not set
CONFIG_BLK_DEV_RAM=y
CONFIG_BLK_DEV_RAM_COUNT=16
CONFIG_BLK_DEV_RAM_SIZE=4096
CONFIG_BLK_DEV_RAM_BLOCKSIZE=1024
CONFIG_CDROM_PKTCDVD=m
CONFIG_CDROM_PKTCDVD_BUFFERS=8
# CONFIG_CDROM_PKTCDVD_WCACHE is not set
# CONFIG_ATA_OVER_ETH is not set

#
# Misc devices
#
# CONFIG_IBM_ASM is not set
# CONFIG_PHANTOM is not set
# CONFIG_SGI_IOC4 is not set
# CONFIG_TIFM_CORE is not set
# CONFIG_ASUS_LAPTOP is not set
# CONFIG_MSI_LAPTOP is not set
# CONFIG_SONY_LAPTOP is not set
# CONFIG_THINKPAD_ACPI is not set
CONFIG_IDE=y
CONFIG_BLK_DEV_IDE=y

#
# Please see Documentation/ide.txt for help/info on IDE drives
#
# CONFIG_BLK_DEV_IDE_SATA is not set
# CONFIG_BLK_DEV_HD_IDE is not set
CONFIG_BLK_DEV_IDEDISK=y
# CONFIG_IDEDISK_MULTI_MODE is not set
CONFIG_BLK_DEV_IDECD=y
# CONFIG_BLK_DEV_IDETAPE is not set
# CONFIG_BLK_DEV_IDEFLOPPY is not set
# CONFIG_BLK_DEV_IDESCSI is not set
CONFIG_BLK_DEV_IDEACPI=y
# CONFIG_IDE_TASK_IOCTL is not set
CONFIG_IDE_PROC_FS=y

#
# IDE chipset support/bugfixes
#
# CONFIG_IDE_GENERIC is not set
# CONFIG_BLK_DEV_CMD640 is not set
# CONFIG_BLK_DEV_IDEPNP is not set
CONFIG_BLK_DEV_IDEPCI=y
CONFIG_IDEPCI_SHARE_IRQ=y
CONFIG_IDEPCI_PCIBUS_ORDER=y
# CONFIG_BLK_DEV_OFFBOARD is not set
# CONFIG_BLK_DEV_GENERIC is not set
# CONFIG_BLK_DEV_OPTI621 is not set
# CONFIG_BLK_DEV_RZ1000 is not set
CONFIG_BLK_DEV_IDEDMA_PCI=y
# CONFIG_BLK_DEV_IDEDMA_FORCED is not set
# CONFIG_IDEDMA_ONLYDISK is not set
# CONFIG_BLK_DEV_AEC62XX is not set
# CONFIG_BLK_DEV_ALI15X3 is not set
# CONFIG_BLK_DEV_AMD74XX is not set
# CONFIG_BLK_DEV_ATIIXP is not set
# CONFIG_BLK_DEV_CMD64X is not set
# CONFIG_BLK_DEV_TRIFLEX is not set
# CONFIG_BLK_DEV_CY82C693 is not set
# CONFIG_BLK_DEV_CS5520 is not set
# CONFIG_BLK_DEV_CS5530 is not set
# CONFIG_BLK_DEV_CS5535 is not set
# CONFIG_BLK_DEV_HPT34X is not set
# CONFIG_BLK_DEV_HPT366 is not set
# CONFIG_BLK_DEV_JMICRON is not set
# CONFIG_BLK_DEV_SC1200 is not set
CONFIG_BLK_DEV_PIIX=y
# CONFIG_BLK_DEV_IT8213 is not set
# CONFIG_BLK_DEV_IT821X is not set
# CONFIG_BLK_DEV_NS87415 is not set
# CONFIG_BLK_DEV_PDC202XX_OLD is not set
# CONFIG_BLK_DEV_PDC202XX_NEW is not set
# CONFIG_BLK_DEV_SVWKS is not set
# CONFIG_BLK_DEV_SIIMAGE is not set
# CONFIG_BLK_DEV_SIS5513 is not set
# CONFIG_BLK_DEV_SLC90E66 is not set
# CONFIG_BLK_DEV_TRM290 is not set
# CONFIG_BLK_DEV_VIA82CXXX is not set
# CONFIG_BLK_DEV_TC86C001 is not set
# CONFIG_IDE_ARM is not set
CONFIG_BLK_DEV_IDEDMA=y
# CONFIG_IDEDMA_IVB is not set
# CONFIG_BLK_DEV_HD is not set

#
# SCSI device support
#
# CONFIG_RAID_ATTRS is not set
CONFIG_SCSI=y
# CONFIG_SCSI_TGT is not set
# CONFIG_SCSI_NETLINK is not set
# CONFIG_SCSI_PROC_FS is not set

#
# SCSI support type (disk, tape, CD-ROM)
#
CONFIG_BLK_DEV_SD=y
# CONFIG_CHR_DEV_ST is not set
# CONFIG_CHR_DEV_OSST is not set
# CONFIG_BLK_DEV_SR is not set
CONFIG_CHR_DEV_SG=y
# CONFIG_CHR_DEV_SCH is not set

#
# Some SCSI devices (e.g. CD jukebox) support multiple LUNs
#
# CONFIG_SCSI_MULTI_LUN is not set
# CONFIG_SCSI_CONSTANTS is not set
# CONFIG_SCSI_LOGGING is not set
# CONFIG_SCSI_SCAN_ASYNC is not set
CONFIG_SCSI_WAIT_SCAN=m

#
# SCSI Transports
#
# CONFIG_SCSI_SPI_ATTRS is not set
# CONFIG_SCSI_FC_ATTRS is not set
# CONFIG_SCSI_ISCSI_ATTRS is not set
# CONFIG_SCSI_SAS_ATTRS is not set
# CONFIG_SCSI_SAS_LIBSAS is not set

#
# SCSI low-level drivers
#
# CONFIG_ISCSI_TCP is not set
# CONFIG_BLK_DEV_3W_XXXX_RAID is not set
# CONFIG_SCSI_3W_9XXX is not set
# CONFIG_SCSI_ACARD is not set
# CONFIG_SCSI_AACRAID is not set
# CONFIG_SCSI_AIC7XXX is not set
# CONFIG_SCSI_AIC7XXX_OLD is not set
# CONFIG_SCSI_AIC79XX is not set
# CONFIG_SCSI_AIC94XX is not set
# CONFIG_SCSI_DPT_I2O is not set
# CONFIG_SCSI_ADVANSYS is not set
# CONFIG_SCSI_ARCMSR is not set
# CONFIG_MEGARAID_NEWGEN is not set
# CONFIG_MEGARAID_LEGACY is not set
# CONFIG_MEGARAID_SAS is not set
# CONFIG_SCSI_HPTIOP is not set
# CONFIG_SCSI_BUSLOGIC is not set
# CONFIG_SCSI_DMX3191D is not set
# CONFIG_SCSI_EATA is not set
# CONFIG_SCSI_FUTURE_DOMAIN is not set
# CONFIG_SCSI_GDTH is not set
# CONFIG_SCSI_IPS is not set
# CONFIG_SCSI_INITIO is not set
# CONFIG_SCSI_INIA100 is not set
# CONFIG_SCSI_STEX is not set
# CONFIG_SCSI_SYM53C8XX_2 is not set
# CONFIG_SCSI_IPR is not set
# CONFIG_SCSI_QLOGIC_1280 is not set
# CONFIG_SCSI_QLA_FC is not set
# CONFIG_SCSI_QLA_ISCSI is not set
# CONFIG_SCSI_LPFC is not set
# CONFIG_SCSI_DC395x is not set
# CONFIG_SCSI_DC390T is not set
# CONFIG_SCSI_NSP32 is not set
# CONFIG_SCSI_DEBUG is not set
# CONFIG_SCSI_SRP is not set
CONFIG_ATA=y
# CONFIG_ATA_NONSTANDARD is not set
CONFIG_ATA_ACPI=y
CONFIG_SATA_AHCI=y
# CONFIG_SATA_SVW is not set
CONFIG_ATA_PIIX=y
# CONFIG_SATA_MV is not set
# CONFIG_SATA_NV is not set
# CONFIG_PDC_ADMA is not set
# CONFIG_SATA_QSTOR is not set
# CONFIG_SATA_PROMISE is not set
# CONFIG_SATA_SX4 is not set
# CONFIG_SATA_SIL is not set
# CONFIG_SATA_SIL24 is not set
# CONFIG_SATA_SIS is not set
# CONFIG_SATA_ULI is not set
# CONFIG_SATA_VIA is not set
# CONFIG_SATA_VITESSE is not set
# CONFIG_SATA_INIC162X is not set
# CONFIG_PATA_ALI is not set
# CONFIG_PATA_AMD is not set
# CONFIG_PATA_ARTOP is not set
# CONFIG_PATA_ATIIXP is not set
# CONFIG_PATA_CMD640_PCI is not set
# CONFIG_PATA_CMD64X is not set
# CONFIG_PATA_CS5520 is not set
# CONFIG_PATA_CS5530 is not set
# CONFIG_PATA_CS5535 is not set
# CONFIG_PATA_CYPRESS is not set
# CONFIG_PATA_EFAR is not set
CONFIG_ATA_GENERIC=y
# CONFIG_PATA_HPT366 is not set
# CONFIG_PATA_HPT37X is not set
# CONFIG_PATA_HPT3X2N is not set
# CONFIG_PATA_HPT3X3 is not set
# CONFIG_PATA_IT821X is not set
# CONFIG_PATA_IT8213 is not set
# CONFIG_PATA_JMICRON is not set
# CONFIG_PATA_TRIFLEX is not set
# CONFIG_PATA_MARVELL is not set
CONFIG_PATA_MPIIX=y
# CONFIG_PATA_OLDPIIX is not set
# CONFIG_PATA_NETCELL is not set
# CONFIG_PATA_NS87410 is not set
# CONFIG_PATA_OPTI is not set
# CONFIG_PATA_OPTIDMA is not set
# CONFIG_PATA_PDC_OLD is not set
# CONFIG_PATA_RADISYS is not set
# CONFIG_PATA_RZ1000 is not set
# CONFIG_PATA_SC1200 is not set
# CONFIG_PATA_SERVERWORKS is not set
# CONFIG_PATA_PDC2027X is not set
# CONFIG_PATA_SIL680 is not set
# CONFIG_PATA_SIS is not set
# CONFIG_PATA_VIA is not set
# CONFIG_PATA_WINBOND is not set

#
# Multi-device support (RAID and LVM)
#
# CONFIG_MD is not set

#
# Fusion MPT device support
#
# CONFIG_FUSION is not set
# CONFIG_FUSION_SPI is not set
# CONFIG_FUSION_FC is not set
# CONFIG_FUSION_SAS is not set

#
# IEEE 1394 (FireWire) support
#
# CONFIG_FIREWIRE is not set
CONFIG_IEEE1394=m

#
# Subsystem Options
#
# CONFIG_IEEE1394_VERBOSEDEBUG is not set

#
# Controllers
#
# CONFIG_IEEE1394_PCILYNX is not set
CONFIG_IEEE1394_OHCI1394=m

#
# Protocols
#
# CONFIG_IEEE1394_VIDEO1394 is not set
CONFIG_IEEE1394_SBP2=m
# CONFIG_IEEE1394_SBP2_PHYS_DMA is not set
CONFIG_IEEE1394_ETH1394_ROM_ENTRY=y
CONFIG_IEEE1394_ETH1394=m
# CONFIG_IEEE1394_DV1394 is not set
CONFIG_IEEE1394_RAWIO=m

#
# I2O device support
#
# CONFIG_I2O is not set
CONFIG_MACINTOSH_DRIVERS=y
CONFIG_MAC_EMUMOUSEBTN=y

#
# Network device support
#
CONFIG_NETDEVICES=y
# CONFIG_DUMMY is not set
# CONFIG_BONDING is not set
# CONFIG_EQUALIZER is not set
# CONFIG_TUN is not set
# CONFIG_NET_SB1000 is not set
# CONFIG_ARCNET is not set
# CONFIG_PHYLIB is not set

#
# Ethernet (10 or 100Mbit)
#
CONFIG_NET_ETHERNET=y
CONFIG_MII=y
# CONFIG_HAPPYMEAL is not set
# CONFIG_SUNGEM is not set
# CONFIG_CASSINI is not set
# CONFIG_NET_VENDOR_3COM is not set

#
# Tulip family network device support
#
# CONFIG_NET_TULIP is not set
# CONFIG_HP100 is not set
CONFIG_NET_PCI=y
# CONFIG_PCNET32 is not set
# CONFIG_AMD8111_ETH is not set
# CONFIG_ADAPTEC_STARFIRE is not set
# CONFIG_B44 is not set
# CONFIG_FORCEDETH is not set
# CONFIG_DGRS is not set
# CONFIG_EEPRO100 is not set
CONFIG_E100=y
# CONFIG_FEALNX is not set
# CONFIG_NATSEMI is not set
# CONFIG_NE2K_PCI is not set
# CONFIG_8139CP is not set
# CONFIG_8139TOO is not set
# CONFIG_SIS900 is not set
# CONFIG_EPIC100 is not set
# CONFIG_SUNDANCE is not set
# CONFIG_TLAN is not set
# CONFIG_VIA_RHINE is not set
# CONFIG_SC92031 is not set
# CONFIG_NET_POCKET is not set
CONFIG_NETDEV_1000=y
# CONFIG_ACENIC is not set
# CONFIG_DL2K is not set
# CONFIG_E1000 is not set
# CONFIG_NS83820 is not set
# CONFIG_HAMACHI is not set
# CONFIG_YELLOWFIN is not set
# CONFIG_R8169 is not set
# CONFIG_SIS190 is not set
# CONFIG_SKGE is not set
CONFIG_SKY2=y
# CONFIG_SK98LIN is not set
# CONFIG_VIA_VELOCITY is not set
# CONFIG_TIGON3 is not set
# CONFIG_BNX2 is not set
# CONFIG_QLA3XXX is not set
# CONFIG_ATL1 is not set
# CONFIG_NETDEV_10000 is not set
# CONFIG_TR is not set

#
# Wireless LAN
#
# CONFIG_WLAN_PRE80211 is not set
# CONFIG_WLAN_80211 is not set

#
# USB Network Adapters
#
# CONFIG_USB_CATC is not set
# CONFIG_USB_KAWETH is not set
# CONFIG_USB_PEGASUS is not set
# CONFIG_USB_RTL8150 is not set
# CONFIG_USB_USBNET_MII is not set
# CONFIG_USB_USBNET is not set
# CONFIG_WAN is not set
# CONFIG_FDDI is not set
# CONFIG_HIPPI is not set
# CONFIG_PLIP is not set
# CONFIG_PPP is not set
# CONFIG_SLIP is not set
# CONFIG_NET_FC is not set
# CONFIG_SHAPER is not set
# CONFIG_NETCONSOLE is not set
# CONFIG_NETPOLL is not set
# CONFIG_NET_POLL_CONTROLLER is not set

#
# ISDN subsystem
#
# CONFIG_ISDN is not set

#
# Telephony Support
#
# CONFIG_PHONE is not set

#
# Input device support
#
CONFIG_INPUT=y
# CONFIG_INPUT_FF_MEMLESS is not set
CONFIG_INPUT_POLLDEV=y

#
# Userland interfaces
#
CONFIG_INPUT_MOUSEDEV=y
CONFIG_INPUT_MOUSEDEV_PSAUX=y
CONFIG_INPUT_MOUSEDEV_SCREEN_X=1024
CONFIG_INPUT_MOUSEDEV_SCREEN_Y=768
# CONFIG_INPUT_JOYDEV is not set
# CONFIG_INPUT_TSDEV is not set
CONFIG_INPUT_EVDEV=y
# CONFIG_INPUT_EVBUG is not set

#
# Input Device Drivers
#
CONFIG_INPUT_KEYBOARD=y
CONFIG_KEYBOARD_ATKBD=y
# CONFIG_KEYBOARD_SUNKBD is not set
# CONFIG_KEYBOARD_LKKBD is not set
# CONFIG_KEYBOARD_XTKBD is not set
# CONFIG_KEYBOARD_NEWTON is not set
# CONFIG_KEYBOARD_STOWAWAY is not set
CONFIG_INPUT_MOUSE=y
CONFIG_MOUSE_PS2=y
CONFIG_MOUSE_PS2_ALPS=y
CONFIG_MOUSE_PS2_LOGIPS2PP=y
CONFIG_MOUSE_PS2_SYNAPTICS=y
CONFIG_MOUSE_PS2_LIFEBOOK=y
CONFIG_MOUSE_PS2_TRACKPOINT=y
# CONFIG_MOUSE_PS2_TOUCHKIT is not set
# CONFIG_MOUSE_SERIAL is not set
CONFIG_MOUSE_APPLETOUCH=y
# CONFIG_MOUSE_VSXXXAA is not set
# CONFIG_INPUT_JOYSTICK is not set
# CONFIG_INPUT_TABLET is not set
# CONFIG_INPUT_TOUCHSCREEN is not set
CONFIG_INPUT_MISC=y
# CONFIG_INPUT_PCSPKR is not set
# CONFIG_INPUT_WISTRON_BTNS is not set
# CONFIG_INPUT_ATLAS_BTNS is not set
# CONFIG_INPUT_ATI_REMOTE is not set
# CONFIG_INPUT_ATI_REMOTE2 is not set
# CONFIG_INPUT_KEYSPAN_REMOTE is not set
# CONFIG_INPUT_POWERMATE is not set
# CONFIG_INPUT_YEALINK is not set
# CONFIG_INPUT_UINPUT is not set

#
# Hardware I/O ports
#
CONFIG_SERIO=y
CONFIG_SERIO_I8042=y
# CONFIG_SERIO_SERPORT is not set
# CONFIG_SERIO_CT82C710 is not set
# CONFIG_SERIO_PARKBD is not set
# CONFIG_SERIO_PCIPS2 is not set
CONFIG_SERIO_LIBPS2=y
# CONFIG_SERIO_RAW is not set
# CONFIG_GAMEPORT is not set

#
# Character devices
#
CONFIG_VT=y
CONFIG_VT_CONSOLE=y
CONFIG_HW_CONSOLE=y
# CONFIG_VT_HW_CONSOLE_BINDING is not set
# CONFIG_SERIAL_NONSTANDARD is not set

#
# Serial drivers
#
CONFIG_SERIAL_8250=y
# CONFIG_SERIAL_8250_CONSOLE is not set
CONFIG_SERIAL_8250_PCI=y
CONFIG_SERIAL_8250_PNP=y
CONFIG_SERIAL_8250_NR_UARTS=4
CONFIG_SERIAL_8250_RUNTIME_UARTS=4
# CONFIG_SERIAL_8250_EXTENDED is not set

#
# Non-8250 serial port support
#
CONFIG_SERIAL_CORE=y
# CONFIG_SERIAL_JSM is not set
CONFIG_UNIX98_PTYS=y
CONFIG_LEGACY_PTYS=y
CONFIG_LEGACY_PTY_COUNT=256
# CONFIG_PRINTER is not set
# CONFIG_PPDEV is not set
# CONFIG_TIPAR is not set

#
# IPMI
#
# CONFIG_IPMI_HANDLER is not set
# CONFIG_WATCHDOG is not set
# CONFIG_HW_RANDOM is not set
CONFIG_NVRAM=y
CONFIG_RTC=y
# CONFIG_R3964 is not set
# CONFIG_APPLICOM is not set
# CONFIG_SONYPI is not set
CONFIG_AGP=y
# CONFIG_AGP_ALI is not set
# CONFIG_AGP_ATI is not set
# CONFIG_AGP_AMD is not set
# CONFIG_AGP_AMD64 is not set
CONFIG_AGP_INTEL=y
# CONFIG_AGP_NVIDIA is not set
# CONFIG_AGP_SIS is not set
# CONFIG_AGP_SWORKS is not set
# CONFIG_AGP_VIA is not set
# CONFIG_AGP_EFFICEON is not set
CONFIG_DRM=y
# CONFIG_DRM_TDFX is not set
# CONFIG_DRM_R128 is not set
# CONFIG_DRM_RADEON is not set
# CONFIG_DRM_I810 is not set
# CONFIG_DRM_I830 is not set
CONFIG_DRM_I915=y
# CONFIG_DRM_MGA is not set
# CONFIG_DRM_SIS is not set
# CONFIG_DRM_VIA is not set
# CONFIG_DRM_SAVAGE is not set
# CONFIG_MWAVE is not set
# CONFIG_PC8736x_GPIO is not set
# CONFIG_NSC_GPIO is not set
# CONFIG_CS5535_GPIO is not set
# CONFIG_RAW_DRIVER is not set
CONFIG_HPET=y
# CONFIG_HPET_RTC_IRQ is not set
CONFIG_HPET_MMAP=y
# CONFIG_HANGCHECK_TIMER is not set

#
# TPM devices
#
# CONFIG_TCG_TPM is not set
# CONFIG_TELCLOCK is not set
CONFIG_DEVPORT=y
CONFIG_I2C=y
CONFIG_I2C_BOARDINFO=y
CONFIG_I2C_CHARDEV=y

#
# I2C Algorithms
#
CONFIG_I2C_ALGOBIT=y
# CONFIG_I2C_ALGOPCF is not set
# CONFIG_I2C_ALGOPCA is not set

#
# I2C Hardware Bus support
#
# CONFIG_I2C_ALI1535 is not set
# CONFIG_I2C_ALI1563 is not set
# CONFIG_I2C_ALI15X3 is not set
# CONFIG_I2C_AMD756 is not set
# CONFIG_I2C_AMD8111 is not set
# CONFIG_I2C_I801 is not set
CONFIG_I2C_I810=y
# CONFIG_I2C_PIIX4 is not set
CONFIG_I2C_ISA=y
# CONFIG_I2C_NFORCE2 is not set
# CONFIG_I2C_OCORES is not set
# CONFIG_I2C_PARPORT is not set
# CONFIG_I2C_PARPORT_LIGHT is not set
# CONFIG_I2C_PROSAVAGE is not set
# CONFIG_I2C_SAVAGE4 is not set
# CONFIG_I2C_SIMTEC is not set
# CONFIG_SCx200_ACB is not set
# CONFIG_I2C_SIS5595 is not set
# CONFIG_I2C_SIS630 is not set
# CONFIG_I2C_SIS96X is not set
# CONFIG_I2C_STUB is not set
# CONFIG_I2C_TINY_USB is not set
# CONFIG_I2C_VIA is not set
# CONFIG_I2C_VIAPRO is not set
# CONFIG_I2C_VOODOO3 is not set

#
# Miscellaneous I2C Chip support
#
# CONFIG_SENSORS_DS1337 is not set
# CONFIG_SENSORS_DS1374 is not set
# CONFIG_SENSORS_EEPROM is not set
# CONFIG_SENSORS_PCF8574 is not set
# CONFIG_SENSORS_PCA9539 is not set
# CONFIG_SENSORS_PCF8591 is not set
# CONFIG_SENSORS_MAX6875 is not set
# CONFIG_I2C_DEBUG_CORE is not set
# CONFIG_I2C_DEBUG_ALGO is not set
# CONFIG_I2C_DEBUG_BUS is not set
# CONFIG_I2C_DEBUG_CHIP is not set

#
# SPI support
#
# CONFIG_SPI is not set
# CONFIG_SPI_MASTER is not set

#
# Dallas's 1-wire bus
#
# CONFIG_W1 is not set
CONFIG_HWMON=y
CONFIG_HWMON_VID=y
# CONFIG_SENSORS_ABITUGURU is not set
CONFIG_SENSORS_AD7418=m
# CONFIG_SENSORS_ADM1021 is not set
# CONFIG_SENSORS_ADM1025 is not set
# CONFIG_SENSORS_ADM1026 is not set
# CONFIG_SENSORS_ADM1029 is not set
# CONFIG_SENSORS_ADM1031 is not set
# CONFIG_SENSORS_ADM9240 is not set
# CONFIG_SENSORS_K8TEMP is not set
# CONFIG_SENSORS_ASB100 is not set
# CONFIG_SENSORS_ATXP1 is not set
# CONFIG_SENSORS_DS1621 is not set
# CONFIG_SENSORS_F71805F is not set
# CONFIG_SENSORS_FSCHER is not set
# CONFIG_SENSORS_FSCPOS is not set
# CONFIG_SENSORS_GL518SM is not set
# CONFIG_SENSORS_GL520SM is not set
CONFIG_SENSORS_CORETEMP=y
CONFIG_SENSORS_IT87=y
# CONFIG_SENSORS_LM63 is not set
# CONFIG_SENSORS_LM75 is not set
# CONFIG_SENSORS_LM77 is not set
# CONFIG_SENSORS_LM78 is not set
# CONFIG_SENSORS_LM80 is not set
# CONFIG_SENSORS_LM83 is not set
# CONFIG_SENSORS_LM85 is not set
# CONFIG_SENSORS_LM87 is not set
# CONFIG_SENSORS_LM90 is not set
# CONFIG_SENSORS_LM92 is not set
# CONFIG_SENSORS_MAX1619 is not set
CONFIG_SENSORS_MAX6650=m
# CONFIG_SENSORS_PC87360 is not set
# CONFIG_SENSORS_PC87427 is not set
# CONFIG_SENSORS_SIS5595 is not set
# CONFIG_SENSORS_SMSC47M1 is not set
# CONFIG_SENSORS_SMSC47M192 is not set
# CONFIG_SENSORS_SMSC47B397 is not set
# CONFIG_SENSORS_VIA686A is not set
# CONFIG_SENSORS_VT1211 is not set
# CONFIG_SENSORS_VT8231 is not set
# CONFIG_SENSORS_W83781D is not set
# CONFIG_SENSORS_W83791D is not set
# CONFIG_SENSORS_W83792D is not set
# CONFIG_SENSORS_W83793 is not set
# CONFIG_SENSORS_W83L785TS is not set
# CONFIG_SENSORS_W83627HF is not set
# CONFIG_SENSORS_W83627EHF is not set
# CONFIG_SENSORS_HDAPS is not set
CONFIG_SENSORS_APPLESMC=y
# CONFIG_HWMON_DEBUG_CHIP is not set

#
# Multifunction device drivers
#
# CONFIG_MFD_SM501 is not set

#
# Multimedia devices
#
# CONFIG_VIDEO_DEV is not set
# CONFIG_DVB_CORE is not set
# CONFIG_DAB is not set

#
# Graphics support
#
CONFIG_BACKLIGHT_LCD_SUPPORT=y
CONFIG_BACKLIGHT_CLASS_DEVICE=y
CONFIG_LCD_CLASS_DEVICE=y
# CONFIG_BACKLIGHT_PROGEAR is not set

#
# Display device support
#
# CONFIG_DISPLAY_SUPPORT is not set
# CONFIG_VGASTATE is not set
CONFIG_FB=y
CONFIG_FIRMWARE_EDID=y
CONFIG_FB_DDC=y
CONFIG_FB_CFB_FILLRECT=y
CONFIG_FB_CFB_COPYAREA=y
CONFIG_FB_CFB_IMAGEBLIT=y
# CONFIG_FB_SYS_FILLRECT is not set
# CONFIG_FB_SYS_COPYAREA is not set
# CONFIG_FB_SYS_IMAGEBLIT is not set
# CONFIG_FB_SYS_FOPS is not set
CONFIG_FB_DEFERRED_IO=y
# CONFIG_FB_SVGALIB is not set
# CONFIG_FB_MACMODES is not set
# CONFIG_FB_BACKLIGHT is not set
CONFIG_FB_MODE_HELPERS=y
# CONFIG_FB_TILEBLITTING is not set

#
# Frame buffer hardware drivers
#
# CONFIG_FB_CIRRUS is not set
# CONFIG_FB_PM2 is not set
# CONFIG_FB_CYBER2000 is not set
# CONFIG_FB_ARC is not set
# CONFIG_FB_ASILIANT is not set
# CONFIG_FB_IMSTT is not set
# CONFIG_FB_VGA16 is not set
CONFIG_FB_VESA=y
# CONFIG_FB_HECUBA is not set
# CONFIG_FB_HGA is not set
# CONFIG_FB_S1D13XXX is not set
# CONFIG_FB_NVIDIA is not set
# CONFIG_FB_RIVA is not set
# CONFIG_FB_I810 is not set
# CONFIG_FB_LE80578 is not set
CONFIG_FB_INTEL=y
# CONFIG_FB_INTEL_DEBUG is not set
CONFIG_FB_INTEL_I2C=y
# CONFIG_FB_MATROX is not set
# CONFIG_FB_RADEON is not set
# CONFIG_FB_ATY128 is not set
# CONFIG_FB_ATY is not set
# CONFIG_FB_S3 is not set
# CONFIG_FB_SAVAGE is not set
# CONFIG_FB_SIS is not set
# CONFIG_FB_NEOMAGIC is not set
# CONFIG_FB_KYRO is not set
# CONFIG_FB_3DFX is not set
# CONFIG_FB_VOODOO1 is not set
# CONFIG_FB_VT8623 is not set
# CONFIG_FB_CYBLA is not set
# CONFIG_FB_TRIDENT is not set
# CONFIG_FB_ARK is not set
# CONFIG_FB_PM3 is not set
# CONFIG_FB_GEODE is not set
# CONFIG_FB_VIRTUAL is not set

#
# Console display driver support
#
CONFIG_VGA_CONSOLE=y
CONFIG_VGACON_SOFT_SCROLLBACK=y
CONFIG_VGACON_SOFT_SCROLLBACK_SIZE=1000
CONFIG_VIDEO_SELECT=y
CONFIG_DUMMY_CONSOLE=y
CONFIG_FRAMEBUFFER_CONSOLE=y
# CONFIG_FRAMEBUFFER_CONSOLE_ROTATION is not set
CONFIG_FONTS=y
# CONFIG_FONT_8x8 is not set
CONFIG_FONT_8x16=y
CONFIG_FONT_6x11=y
# CONFIG_FONT_7x14 is not set
# CONFIG_FONT_PEARL_8x8 is not set
# CONFIG_FONT_ACORN_8x8 is not set
# CONFIG_FONT_MINI_4x6 is not set
CONFIG_FONT_SUN8x16=y
# CONFIG_FONT_SUN12x22 is not set
# CONFIG_FONT_10x18 is not set
CONFIG_LOGO=y
CONFIG_LOGO_LINUX_MONO=y
CONFIG_LOGO_LINUX_VGA16=y
CONFIG_LOGO_LINUX_CLUT224=y

#
# Sound
#
CONFIG_SOUND=m

#
# Advanced Linux Sound Architecture
#
# CONFIG_SND is not set

#
# Open Sound System
#
# CONFIG_SOUND_PRIME is not set

#
# HID Devices
#
CONFIG_HID=y
# CONFIG_HID_DEBUG is not set

#
# USB Input Devices
#
CONFIG_USB_HID=y
CONFIG_USB_HIDINPUT_POWERBOOK=y
# CONFIG_HID_FF is not set
# CONFIG_USB_HIDDEV is not set

#
# USB support
#
CONFIG_USB_ARCH_HAS_HCD=y
CONFIG_USB_ARCH_HAS_OHCI=y
CONFIG_USB_ARCH_HAS_EHCI=y
CONFIG_USB=y
# CONFIG_USB_DEBUG is not set

#
# Miscellaneous USB options
#
CONFIG_USB_DEVICEFS=y
CONFIG_USB_DEVICE_CLASS=y
# CONFIG_USB_DYNAMIC_MINORS is not set
CONFIG_USB_SUSPEND=y
# CONFIG_USB_OTG is not set

#
# USB Host Controller Drivers
#
CONFIG_USB_EHCI_HCD=y
# CONFIG_USB_EHCI_SPLIT_ISO is not set
# CONFIG_USB_EHCI_ROOT_HUB_TT is not set
# CONFIG_USB_EHCI_TT_NEWSCHED is not set
# CONFIG_USB_EHCI_BIG_ENDIAN_MMIO is not set
# CONFIG_USB_ISP116X_HCD is not set
# CONFIG_USB_OHCI_HCD is not set
CONFIG_USB_UHCI_HCD=y
# CONFIG_USB_SL811_HCD is not set

#
# USB Device Class drivers
#
# CONFIG_USB_ACM is not set
CONFIG_USB_PRINTER=m

#
# NOTE: USB_STORAGE enables SCSI, and 'SCSI disk support'
#

#
# may also be needed; see USB_STORAGE Help for more information
#
CONFIG_USB_STORAGE=m
# CONFIG_USB_STORAGE_DEBUG is not set
# CONFIG_USB_STORAGE_DATAFAB is not set
# CONFIG_USB_STORAGE_FREECOM is not set
# CONFIG_USB_STORAGE_ISD200 is not set
# CONFIG_USB_STORAGE_DPCM is not set
# CONFIG_USB_STORAGE_USBAT is not set
# CONFIG_USB_STORAGE_SDDR09 is not set
# CONFIG_USB_STORAGE_SDDR55 is not set
# CONFIG_USB_STORAGE_JUMPSHOT is not set
# CONFIG_USB_STORAGE_ALAUDA is not set
# CONFIG_USB_STORAGE_KARMA is not set
# CONFIG_USB_LIBUSUAL is not set

#
# USB Imaging devices
#
# CONFIG_USB_MDC800 is not set
# CONFIG_USB_MICROTEK is not set
CONFIG_USB_MON=y

#
# USB port drivers
#
# CONFIG_USB_USS720 is not set

#
# USB Serial Converter support
#
# CONFIG_USB_SERIAL is not set

#
# USB Miscellaneous drivers
#
# CONFIG_USB_EMI62 is not set
# CONFIG_USB_EMI26 is not set
# CONFIG_USB_ADUTUX is not set
# CONFIG_USB_AUERSWALD is not set
# CONFIG_USB_RIO500 is not set
# CONFIG_USB_LEGOTOWER is not set
# CONFIG_USB_LCD is not set
CONFIG_USB_BERRY_CHARGE=m
# CONFIG_USB_LED is not set
# CONFIG_USB_CYPRESS_CY7C63 is not set
# CONFIG_USB_CYTHERM is not set
# CONFIG_USB_PHIDGET is not set
# CONFIG_USB_IDMOUSE is not set
# CONFIG_USB_FTDI_ELAN is not set
# CONFIG_USB_APPLEDISPLAY is not set
# CONFIG_USB_SISUSBVGA is not set
# CONFIG_USB_LD is not set
# CONFIG_USB_TRANCEVIBRATOR is not set
# CONFIG_USB_IOWARRIOR is not set
# CONFIG_USB_TEST is not set

#
# USB DSL modem support
#

#
# USB Gadget Support
#
# CONFIG_USB_GADGET is not set
# CONFIG_MMC is not set

#
# LED devices
#
CONFIG_NEW_LEDS=y
CONFIG_LEDS_CLASS=y

#
# LED drivers
#

#
# LED Triggers
#
CONFIG_LEDS_TRIGGERS=y
CONFIG_LEDS_TRIGGER_TIMER=y
CONFIG_LEDS_TRIGGER_IDE_DISK=y
CONFIG_LEDS_TRIGGER_HEARTBEAT=y

#
# InfiniBand support
#
# CONFIG_INFINIBAND is not set

#
# EDAC - error detection and reporting (RAS) (EXPERIMENTAL)
#
# CONFIG_EDAC is not set

#
# Real Time Clock
#
# CONFIG_RTC_CLASS is not set

#
# DMA Engine support
#
# CONFIG_DMA_ENGINE is not set

#
# DMA Clients
#

#
# DMA Devices
#

#
# Auxiliary Display support
#

#
# Virtualization
#
# CONFIG_KVM is not set

#
# File systems
#
# CONFIG_EXT2_FS is not set
CONFIG_EXT3_FS=y
# CONFIG_EXT3_FS_XATTR is not set
# CONFIG_EXT4DEV_FS is not set
CONFIG_JBD=y
# CONFIG_JBD_DEBUG is not set
CONFIG_REISERFS_FS=m
# CONFIG_REISERFS_CHECK is not set
# CONFIG_REISERFS_PROC_INFO is not set
# CONFIG_REISERFS_FS_XATTR is not set
# CONFIG_JFS_FS is not set
CONFIG_FS_POSIX_ACL=y
# CONFIG_XFS_FS is not set
# CONFIG_GFS2_FS is not set
# CONFIG_OCFS2_FS is not set
# CONFIG_MINIX_FS is not set
# CONFIG_ROMFS_FS is not set
CONFIG_INOTIFY=y
CONFIG_INOTIFY_USER=y
# CONFIG_QUOTA is not set
CONFIG_DNOTIFY=y
# CONFIG_AUTOFS_FS is not set
CONFIG_AUTOFS4_FS=y
CONFIG_FUSE_FS=m

#
# CD-ROM/DVD Filesystems
#
CONFIG_ISO9660_FS=y
CONFIG_JOLIET=y
CONFIG_ZISOFS=y
CONFIG_UDF_FS=y
CONFIG_UDF_NLS=y

#
# DOS/FAT/NT Filesystems
#
CONFIG_FAT_FS=y
# CONFIG_MSDOS_FS is not set
CONFIG_VFAT_FS=y
CONFIG_FAT_DEFAULT_CODEPAGE=437
CONFIG_FAT_DEFAULT_IOCHARSET="iso8859-1"
CONFIG_NTFS_FS=m
# CONFIG_NTFS_DEBUG is not set
CONFIG_NTFS_RW=y

#
# Pseudo filesystems
#
CONFIG_PROC_FS=y
CONFIG_PROC_KCORE=y
CONFIG_PROC_SYSCTL=y
CONFIG_SYSFS=y
CONFIG_TMPFS=y
# CONFIG_TMPFS_POSIX_ACL is not set
# CONFIG_HUGETLBFS is not set
# CONFIG_HUGETLB_PAGE is not set
CONFIG_RAMFS=y
CONFIG_CONFIGFS_FS=y

#
# Miscellaneous filesystems
#
# CONFIG_ADFS_FS is not set
# CONFIG_AFFS_FS is not set
# CONFIG_HFS_FS is not set
CONFIG_HFSPLUS_FS=y
# CONFIG_BEFS_FS is not set
# CONFIG_BFS_FS is not set
# CONFIG_EFS_FS is not set
# CONFIG_CRAMFS is not set
# CONFIG_VXFS_FS is not set
# CONFIG_HPFS_FS is not set
# CONFIG_QNX4FS_FS is not set
# CONFIG_SYSV_FS is not set
# CONFIG_UFS_FS is not set

#
# Network File Systems
#
CONFIG_NFS_FS=m
CONFIG_NFS_V3=y
CONFIG_NFS_V3_ACL=y
# CONFIG_NFS_V4 is not set
# CONFIG_NFS_DIRECTIO is not set
CONFIG_NFSD=m
CONFIG_NFSD_V3=y
# CONFIG_NFSD_V3_ACL is not set
# CONFIG_NFSD_V4 is not set
CONFIG_NFSD_TCP=y
CONFIG_LOCKD=m
CONFIG_LOCKD_V4=y
CONFIG_EXPORTFS=m
CONFIG_NFS_ACL_SUPPORT=m
CONFIG_NFS_COMMON=y
CONFIG_SUNRPC=m
# CONFIG_SUNRPC_BIND34 is not set
# CONFIG_RPCSEC_GSS_KRB5 is not set
# CONFIG_RPCSEC_GSS_SPKM3 is not set
CONFIG_SMB_FS=m
# CONFIG_SMB_NLS_DEFAULT is not set
CONFIG_CIFS=m
# CONFIG_CIFS_STATS is not set
# CONFIG_CIFS_WEAK_PW_HASH is not set
CONFIG_CIFS_XATTR=y
CONFIG_CIFS_POSIX=y
# CONFIG_CIFS_DEBUG2 is not set
# CONFIG_CIFS_EXPERIMENTAL is not set
# CONFIG_NCP_FS is not set
# CONFIG_CODA_FS is not set
# CONFIG_AFS_FS is not set
# CONFIG_9P_FS is not set

#
# Partition Types
#
CONFIG_PARTITION_ADVANCED=y
# CONFIG_ACORN_PARTITION is not set
# CONFIG_OSF_PARTITION is not set
# CONFIG_AMIGA_PARTITION is not set
# CONFIG_ATARI_PARTITION is not set
CONFIG_MAC_PARTITION=y
CONFIG_MSDOS_PARTITION=y
# CONFIG_BSD_DISKLABEL is not set
# CONFIG_MINIX_SUBPARTITION is not set
# CONFIG_SOLARIS_X86_PARTITION is not set
# CONFIG_UNIXWARE_DISKLABEL is not set
CONFIG_LDM_PARTITION=y
# CONFIG_LDM_DEBUG is not set
# CONFIG_SGI_PARTITION is not set
# CONFIG_ULTRIX_PARTITION is not set
# CONFIG_SUN_PARTITION is not set
# CONFIG_KARMA_PARTITION is not set
CONFIG_EFI_PARTITION=y
# CONFIG_SYSV68_PARTITION is not set

#
# Native Language Support
#
CONFIG_NLS=y
CONFIG_NLS_DEFAULT="iso8859-15"
CONFIG_NLS_CODEPAGE_437=y
# CONFIG_NLS_CODEPAGE_737 is not set
# CONFIG_NLS_CODEPAGE_775 is not set
# CONFIG_NLS_CODEPAGE_850 is not set
# CONFIG_NLS_CODEPAGE_852 is not set
# CONFIG_NLS_CODEPAGE_855 is not set
# CONFIG_NLS_CODEPAGE_857 is not set
# CONFIG_NLS_CODEPAGE_860 is not set
# CONFIG_NLS_CODEPAGE_861 is not set
# CONFIG_NLS_CODEPAGE_862 is not set
# CONFIG_NLS_CODEPAGE_863 is not set
# CONFIG_NLS_CODEPAGE_864 is not set
# CONFIG_NLS_CODEPAGE_865 is not set
# CONFIG_NLS_CODEPAGE_866 is not set
# CONFIG_NLS_CODEPAGE_869 is not set
# CONFIG_NLS_CODEPAGE_936 is not set
# CONFIG_NLS_CODEPAGE_950 is not set
# CONFIG_NLS_CODEPAGE_932 is not set
# CONFIG_NLS_CODEPAGE_949 is not set
# CONFIG_NLS_CODEPAGE_874 is not set
# CONFIG_NLS_ISO8859_8 is not set
# CONFIG_NLS_CODEPAGE_1250 is not set
# CONFIG_NLS_CODEPAGE_1251 is not set
CONFIG_NLS_ASCII=y
CONFIG_NLS_ISO8859_1=y
# CONFIG_NLS_ISO8859_2 is not set
# CONFIG_NLS_ISO8859_3 is not set
# CONFIG_NLS_ISO8859_4 is not set
# CONFIG_NLS_ISO8859_5 is not set
# CONFIG_NLS_ISO8859_6 is not set
# CONFIG_NLS_ISO8859_7 is not set
# CONFIG_NLS_ISO8859_9 is not set
# CONFIG_NLS_ISO8859_13 is not set
# CONFIG_NLS_ISO8859_14 is not set
CONFIG_NLS_ISO8859_15=y
# CONFIG_NLS_KOI8_R is not set
# CONFIG_NLS_KOI8_U is not set
CONFIG_NLS_UTF8=y

#
# Distributed Lock Manager
#
CONFIG_DLM=y
# CONFIG_DLM_DEBUG is not set

#
# Instrumentation Support
#
# CONFIG_PROFILING is not set
# CONFIG_KPROBES is not set

#
# Kernel hacking
#
CONFIG_TRACE_IRQFLAGS_SUPPORT=y
CONFIG_PRINTK_TIME=y
# CONFIG_ENABLE_MUST_CHECK is not set
# CONFIG_MAGIC_SYSRQ is not set
# CONFIG_UNUSED_SYMBOLS is not set
# CONFIG_DEBUG_FS is not set
# CONFIG_HEADERS_CHECK is not set
CONFIG_DEBUG_KERNEL=y
# CONFIG_DEBUG_SHIRQ is not set
# CONFIG_DETECT_SOFTLOCKUP is not set
# CONFIG_SCHEDSTATS is not set
CONFIG_TIMER_STATS=y
# CONFIG_DEBUG_RT_MUTEXES is not set
# CONFIG_RT_MUTEX_TESTER is not set
# CONFIG_DEBUG_SPINLOCK is not set
# CONFIG_DEBUG_MUTEXES is not set
# CONFIG_DEBUG_LOCK_ALLOC is not set
# CONFIG_PROVE_LOCKING is not set
# CONFIG_DEBUG_SPINLOCK_SLEEP is not set
# CONFIG_DEBUG_LOCKING_API_SELFTESTS is not set
# CONFIG_DEBUG_KOBJECT is not set
CONFIG_DEBUG_BUGVERBOSE=y
# CONFIG_DEBUG_INFO is not set
# CONFIG_DEBUG_VM is not set
# CONFIG_DEBUG_LIST is not set
# CONFIG_FRAME_POINTER is not set
# CONFIG_FORCED_INLINING is not set
# CONFIG_RCU_TORTURE_TEST is not set
# CONFIG_FAULT_INJECTION is not set
CONFIG_EARLY_PRINTK=y
# CONFIG_DEBUG_STACKOVERFLOW is not set
# CONFIG_DEBUG_STACK_USAGE is not set

#
# Page alloc debug is incompatible with Software Suspend on i386
#
# CONFIG_DEBUG_RODATA is not set
# CONFIG_4KSTACKS is not set
CONFIG_X86_FIND_SMP_CONFIG=y
CONFIG_X86_MPPARSE=y
CONFIG_DOUBLEFAULT=y

#
# Security options
#
# CONFIG_KEYS is not set
CONFIG_SECURITY=y
# CONFIG_SECURITY_NETWORK is not set
CONFIG_SECURITY_CAPABILITIES=y
# CONFIG_SECURITY_ROOTPLUG is not set

#
# Cryptographic options
#
CONFIG_CRYPTO=y
CONFIG_CRYPTO_ALGAPI=y
CONFIG_CRYPTO_BLKCIPHER=m
CONFIG_CRYPTO_HASH=y
CONFIG_CRYPTO_MANAGER=y
CONFIG_CRYPTO_HMAC=y
# CONFIG_CRYPTO_XCBC is not set
# CONFIG_CRYPTO_NULL is not set
# CONFIG_CRYPTO_MD4 is not set
CONFIG_CRYPTO_MD5=y
CONFIG_CRYPTO_SHA1=m
CONFIG_CRYPTO_SHA256=m
CONFIG_CRYPTO_SHA512=m
# CONFIG_CRYPTO_WP512 is not set
# CONFIG_CRYPTO_TGR192 is not set
# CONFIG_CRYPTO_GF128MUL is not set
CONFIG_CRYPTO_ECB=m
CONFIG_CRYPTO_CBC=m
CONFIG_CRYPTO_PCBC=m
# CONFIG_CRYPTO_LRW is not set
# CONFIG_CRYPTO_CRYPTD is not set
CONFIG_CRYPTO_DES=m
# CONFIG_CRYPTO_FCRYPT is not set
CONFIG_CRYPTO_BLOWFISH=m
# CONFIG_CRYPTO_TWOFISH is not set
# CONFIG_CRYPTO_TWOFISH_586 is not set
# CONFIG_CRYPTO_SERPENT is not set
CONFIG_CRYPTO_AES=m
# CONFIG_CRYPTO_AES_586 is not set
# CONFIG_CRYPTO_CAST5 is not set
# CONFIG_CRYPTO_CAST6 is not set
# CONFIG_CRYPTO_TEA is not set
CONFIG_CRYPTO_ARC4=m
# CONFIG_CRYPTO_KHAZAD is not set
# CONFIG_CRYPTO_ANUBIS is not set
# CONFIG_CRYPTO_DEFLATE is not set
CONFIG_CRYPTO_MICHAEL_MIC=m
# CONFIG_CRYPTO_CRC32C is not set
# CONFIG_CRYPTO_CAMELLIA is not set
# CONFIG_CRYPTO_TEST is not set

#
# Hardware crypto devices
#
# CONFIG_CRYPTO_DEV_PADLOCK is not set
# CONFIG_CRYPTO_DEV_GEODE is not set

#
# Library routines
#
CONFIG_BITREVERSE=y
# CONFIG_CRC_CCITT is not set
# CONFIG_CRC16 is not set
# CONFIG_CRC_ITU_T is not set
CONFIG_CRC32=y
# CONFIG_LIBCRC32C is not set
CONFIG_ZLIB_INFLATE=y
CONFIG_TEXTSEARCH=y
CONFIG_TEXTSEARCH_KMP=m
CONFIG_TEXTSEARCH_BM=m
CONFIG_TEXTSEARCH_FSM=m
CONFIG_PLIST=y
CONFIG_HAS_IOMEM=y
CONFIG_HAS_IOPORT=y
CONFIG_HAS_DMA=y
CONFIG_GENERIC_HARDIRQS=y
CONFIG_GENERIC_IRQ_PROBE=y
CONFIG_GENERIC_PENDING_IRQ=y
CONFIG_X86_SMP=y
CONFIG_X86_HT=y
CONFIG_X86_BIOS_REBOOT=y
CONFIG_X86_TRAMPOLINE=y
CONFIG_KTIME_SCALAR=y

```

Alsa and wifi drivers compilation:
ALSA: After rebooting the sound system was not working, so I downloaded the alsa driver, libraries and utilities from [http://alsa-project.org/main/index.php/Download]("http://alsa-project.org/main/index.php/Download").
Attention: There might be a way to create deb packages after compiling so that the package management system can remove them later. I have nevertheless simply used the standard steps for compiling and installing from the source code:
```

./configure
make
sudo make install

```
and for the driver:
```

./configure --with-cards=hda-intel
make
sudo make install

```
you can restart the sound system with:
```
sudo /etc/init.d/alsasound restart
```

MADWIFI:
Unpack the archive where the driver is, enter the directory and
```
make && make install
```

I hope this post is useful to anyone. Any corrections and observations are appreciated.

Xeth

---

### Post by rekstorm on 2007-10-12
thank you very much,
some optimizations suggested by powertop, like USB autosuspend, cannot be applied due to default kernel config.
I'll try with this one on gutsy as soon as possible.

you can try to create a deb package with checkinstall

"-Some strange mouse click and focus behaviour" what do you mean? in which sofware ?

> **cyberdork33 said:**
> There is no directory for 2.6.23 in the mactel subversion repository. and the last change to the 2.6.22 patches was 2 weeks ago.
They are now available!

---

### Post by xeth_delta on 2007-10-12
> **rekstorm said:**
> thank you very much,
some optimizations suggested by powertop, like USB autosuspend, cannot be applied due to default kernel config.
I'll try with this one on gutsy as soon as possible.

you can try to create a deb package with checkinstall

"-Some strange mouse click and focus behaviour" what do you mean? in which sofware ?


For a click to be completed you have to move the pointer. For example, I click on a link and nothing happens. Move the pointer, the click is realized. This does not happen all the time.
Focus problems: for instance, I click on the search field of the forum. The cursor is blinking but the typing is not produced there. clicking one or two times again in the field will "make the trick" and allow you to type there. I think I saw at some point a thread covering this problem.

I do not think this is related to any particular choices in the config file, as I had the same behaviour with the Gutsy kernel on Feisty.

Xeth

---

### Post by rekstorm on 2007-10-12
ok, maybe something related to xorg.conf? (but discussing this here will be OT)
thanks

---

### Post by Ganonzote on 2007-11-01
I have compiled 2.6.23 kernel for a C2D with mactel patches. It work's fine but f**n key is not working**.

With precompiled kernels it was working fine.

Can someone help me?

---

### Post by cyberdork33 on 2007-11-05
For those compiling manually, the fan control in AppleSMC has changed:

Enable Manual Control:
```
echo 1 > /sys/devices/platform/applesmc.768/fan1_manual
echo 1 > /sys/devices/platform/applesmc.768/fan2_manual
```Set speed:
```
echo 4000 > /sys/devices/platform/applesmc.768/fan1_output
echo 4000 > /sys/devices/platform/applesmc.768/fan2_output
```

---

### Post by onyxrev on 2007-12-22
Hey!  This thread is awesome.  Thanks to building my own kernel, I now have working suspend and fully functional crypto on a 2nd gen Macbook with 2.6.22-12.

Since it was requested, I'm going to post my 2nd Gen Macbook Core2Duo .config file.  I merged the CPU section of the 2nd Gen Macbook Gentoo 2.6.20 config with the 1st Gen Macbook Gentoo 2.6.22 config.  I made a few changes with respect to crypto (I use encrypted root, swap and home) by adding more hash and ciphers and enabled EFI/GPT partition tables (they were disabled in the Gentoo config, limiting us to four partitions!).  Also, emulation of IA32 allows for Flash to work right in AMD64.

I'm certain it isn't perfect, but it works for me.

---

### Post by phonky on 2008-03-26
Compiled my 2nd gen macbook pro with 2.6.24.3

I can't get desktop effects to run though. fglrxinfo tells me
the mesa drivers is loaded....

do I need to recompile the linux-restricted-modules too?

thank you for any help

---

### Post by cyberdork33 on 2008-03-26
> **phonky said:**
> Compiled my 2nd gen macbook pro with 2.6.24.3

I can't get desktop effects to run though. fglrxinfo tells me
the mesa drivers is loaded....

do I need to recompile the linux-restricted-modules too?

thank you for any help
you have to compile any modules (including fglrx) against your new kernel.

---

### Post by liquidfunk on 2008-04-08
Now will this make everything on my Macbook work? Such as the Wireless/ graphics etc? Or do I have to do this separately?

---

### Post by cyberdork33 on 2008-04-08
> **liquidfunk said:**
> Now will this make everything on my Macbook work? No. This is an advanced topic. You do not need to make your own kernel as the Ubuntu kernel is fine. This is for the serious Linux user who would like to make a lean kernel, or maybe tryout the very latest Linux kernel, and not for a typical user. 

In fact, compiling a custom kernel is more likely to break things that you do have working (and you would have to repeat the process of fixes them with your new kernel).

---

### Post by liquidfunk on 2008-04-08
Thanks for clearing that up :)

---

### Post by bozzochet on 2008-04-09
> **phonky said:**
> Compiled my 2nd gen macbook pro with 2.6.24.3

I can't get desktop effects to run though. fglrxinfo tells me
the mesa drivers is loaded....

do I need to recompile the linux-restricted-modules too?

thank you for any help

> **cyberdork33 said:**
> you have to compile any modules (including fglrx) against your new kernel.

I had an idea, explained and discussed (the problem I have...) well into this post : [http://ubuntuforums.org/showthread.php?t=738094](http://ubuntuforums.org/showthread.php?t=738094)

The idea is to modify the precompiled kernel making the results "appear" as an upgrade of "official" one. In this way we have not to "build" up all the related packages (modules, backport modules, resctricted modules, ecc...). Seems strange but isn't also than the same thing manteiners do...
The mactel mantainers make their kernel, with additional patch, making it to be an upgrade, not a new kernel...
Anyone like this idea and/or knows why I'm not able to do this?

I think also that this could be a good way for every kernel customization. Every people could continue, in parallel, the work of mantainers (of official repository, or semi-official repo) with personal upgrades for the kernel, avoiding every time to restart from beginning, "losing" the work made before. I think it would be the very realization of **open source** concept...

Let me now (on PVT for avoiding OT) what do you think about this idea...

---

### Post by cyberdork33 on 2008-04-09
it is because the mactel kernel is really just the regular Ubuntu kernel source with a couple of changes made, so the modules are really compatible, but everything sees them as separate. What is done for the mactel kernel is a metapackage is made for all the modules that basically redirects things to the normal ubuntu modules. you can have a look in the PPA at the packages and see how they are made.

---

### Post by bozzochet on 2008-04-10
I didn't understand too much your reply (I have a poor english) but if I understood something:
I recompiled the mactel package (without changing with debuild and with my changes trough make-kpkg) and didn't seems a metapackage, it precisely as the ufficial package.
About the compatibility you have right, but infact mactel kernel only ADD compatibilty so is a SURE kernel for everyone, if I want to make a kernel with LESS compatibility it would be not for everyone (and I will not put it on repository, infact) but the idea is not loosing time for making thing that others made yet, and having a package that has, without effort, the "official" changelog, the official patches, the official configuration, the official list of manteiners, ecc..., OVER (and not BEFORE) those I will make my personal changes...

---

### Post by Gen2ly on 2008-04-10
Updated!  Now with more

waaaaaaaaaaaaaaaaa!

---

### Post by cyberdork33 on 2008-04-10
> **bozzochet said:**
> I didn't understand too much your reply (I have a poor english) but if I understood something:
I recompiled the mactel package (without changing with debuild and with my changes trough make-kpkg) and didn't seems a metapackage, it precisely as the ufficial package.
About the compatibility you have right, but infact mactel kernel only ADD compatibilty so is a SURE kernel for everyone, if I want to make a kernel with LESS compatibility it would be not for everyone (and I will not put it on repository, infact) but the idea is not loosing time for making thing that others made yet, and having a package that has, without effort, the "official" changelog, the official patches, the official configuration, the official list of manteiners, ecc..., OVER (and not BEFORE) those I will make my personal changes...Well, I didn't understand much of what you said either...

If you look at the packages in the mactel ppa, there are packages that go along with  the mactel kernel:
[https://edge.launchpad.net/~mactel-support/+archive]("https://edge.launchpad.net/%7Emactel-support/+archive")

you can click on the little triangles to read more info about them, but some of them say they include things like : > [LIST]
[*]             **linux-restricted-modules-2.6.24-11-mactel**             Wrapper to -generic restricted modules[/LIST][LIST]
[*]             **linux-ubuntu-modules-2.6.24-11-mactel**             Wrapper to -generic restricted modules[/LIST]These are "wrappers" for the generic packages.

---

### Post by bozzochet on 2008-04-11
Sorry... I forget to say that I was speaking about 2.6**.22** packge!!! The "gutsy" mactel kernel is an upgrade of the official one in the same way as the official mantainers do when make kernel upgrades...
I suppose the "wrapper" is needed fr 2.6.24 because, if I'm not in error, this mactel package is not more an upgrade, but is a sort of new kernel flavour (like generic or server)...
I'm talking to small-modify the generic (or server) official one starting from precompiled one avoid to build all from beginning: with "debuild" I can recompile the precompiled having a package identical to the one on repos, I would like to modify small things and the make a "debuild" also, without downloading and applying patches (yet in the precompiled), inserting the changlelog, the list of mantainer, the dependencies, etc... into my NEW package, all things that are yet in the precompiled but that I loose restarting from vanilla one (or also from *mkpropered* source tree)!!

---

### Post by Gen2ly on 2008-04-11
the mactel patches, which is what I think is being referred to are usually just a bunch of bug fixes, though sometimes they add hardware support too.  If not comfortable the kernel will stillcompile without them.

---

### Post by cyberdork33 on 2008-04-11
the kernel in the mactel ppa for gutsy is not compatible with the other packages because that work was not done for gutsy (there was an unresolved issue, plus focus was shifted to support hardy). 

If you are saying that you want to start from a vanilla kernel, I don't think it will work because of the numerous ubuntu patches applied to the generic kernel. The mactel kernels in the ppa are the source for the generic kernel with a couple of mods to add support for keyboards, etc. changes that have not yet made it into the generic ubuntu kernel. Since the mactel kernel is essentially the same as the generic kernel, the modules can still be used with it.

If you are just talking about adding the official mactel patches from mactel-linux.org, then I think we are talking about completely different things.

---

### Post by bozzochet on 2008-04-11
No...
The Gutsy kernel from Mactel IS compatible with other packages (modules) because I've installed (I installed only the linux-image package; there are not the other packages on repo!), with the other packages from official repo, and all is working perfectly!

I DON'T WANT TO START FROM VANILLA kerne!!!
I want to start from precompiled one (or from the official precompiled one or, in my situation, from the precompiled mactel one)!!! WIth all the patches and all the stuff YET inserted into it!

I want to be able to make same SMALL changes on it and then recompile it and then install it as an upgrade of the kernel currently installed!!

---

### Post by cyberdork33 on 2008-04-11
> **bozzochet said:**
> I want to start from precompiled one (or from the official precompiled one or, in my situation, from the precompiled mactel one)!!! WIth all the patches and all the stuff YET inserted into it!

I want to be able to make same SMALL changes on it and then recompile it and then install it as an upgrade of the kernel currently installed!!Ok, then here is what you have to do. Get the -mactel kernel source from the ppa. You can access this on the launchpad page. I *think* that if you modify this source a bit and compile without upping the version numbers, then the wrappers in the mactel-support ppa shoud work with your "fixed" mactel kernel like you just downloaded the kernel from the ppa.

If it does not work like this, then the "wrapper" packages will have to be downloaded and edited to match the infromation in your new kernel in a similar manner. I, myself, do not know how to create these packages properly as Chris (Seq) was the one that developed them.

Also, if you can help keep these mactel kernels up to date, then it would be appreciated. The one in the ppa now is a bit old. Needed patches should be applied to the latest -generic source and uploaded to the ppa.

---

### Post by bozzochet on 2008-04-11
Gutsy kernel (2.6.22) has no wrappers!

If you look my thread (and the errors I have), I CANNOT simply modify the source tree... When I made a simple "make xconfig" on source tree then the "debuild" command return me an error of "source tree not clean". I don't found anyone that is able to say to me WHAT to do at this moment!!

I repeat for clearness: I download the source of the precompiled linux-image-..... kernel, if I do "debuild" I obtain packages equal to the one on the repo, if i do changes and then "debuild" I obtain an error.

---

### Post by cyberdork33 on 2008-04-11
> **bozzochet said:**
> Gutsy kernel (2.6.22) has no wrappers!

If you look my thread (and the errors I have), I CANNOT simply modify the source tree... When I made a simple "make xconfig" on source tree then the "debuild" command return me an error of "source tree not clean". I don't found anyone that is able to say to me WHAT to do at this moment!!

I repeat for clearness: I download the source of the precompiled linux-image-..... kernel, if I do "debuild" I obtain packages equal to the one on the repo, if i do changes and then "debuild" I obtain an error.If you build once, then you have to make clean before trying to build again.

---

### Post by bozzochet on 2008-04-12
Is NOT sufficient do: make clean.
I tried also "debuild clean", before or after make clean but the error also appear...
The problem seems to be in the file into debian/config/ dir, but obviously if I remove them I have also errors (now the error is the not presence of these file!)...

---

### Post by bozzochet on 2008-04-12
dear cyberdork33, since I see you're interested with my problem can I ask to you to read, if you want and if you've time, the thread linked by me in the first post here: there's all the problem explained well...
Thanks for your interesting!

---

### Post by cyberdork33 on 2008-04-12
> **bozzochet said:**
> The idea is to modify the precompiled kernel making the results "appear" as an upgrade of "official" one. In this way we have not to "build" up all the related packages (modules, backport modules, resctricted modules, ecc...). Seems strange but isn't also than the same thing manteiners do...
The mactel mantainers make their kernel, with additional patch, making it to be an upgrade, not a new kernel...I have tried to tell you that you can look at how the "wrappers" are made to accomplish this. I know there are not wrappers for gutsy, but they would work the same in gutsy as hardy. Then it would not matter if the kernel looks like a "new kernel" or if it is an upgrade (which would _still_ need upgraded supporting packages).

as for your problem in the thread, did you try "make mrproper" since that is what the error said needed to be done? 

Unfortunately I am not a developer, so I am not that familiar with this stuff, but I have been trying to point you to some information. Sorry.

---

### Post by bozzochet on 2008-04-12
If I do "make mrproper" the source tree is clean, but also patches, debian dir, etc... are cleaned!!

I wat an upgrade, instead of a new kernel for not neeeding to upgrade the modules packages too...

When I've installed the mactel kernel only the linux-image-XXX package was downloaded and installed but for the other packages (ubuntu modules, backport modules, restricted modules, etc...) the official one were mantained...

Thanks for your help...

---

### Post by guzzos on 2008-07-12
Hello, I am trying to apply the mactel patches in this guide for when I try to execute the command './apply /usr/src/linux' it says the apply command not found.  Is there a work around this issue.

Thanks for any help.
:confused:

---

### Post by flaggh on 2008-07-12
What version of Ubuntu are you running?  What type of Mac are your runnning it on?  I believe most of these patches have already been included in Hardy and rolling your own kernel is not necessary anymore.  Add the Mactel repository to /etc/apt/sources.list and run the update manager to get yourself up to date.

```
# Mactel PPA
deb http://ppa.launchpad.net/mactel-support/ubuntu hardy main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu hardy main

```

This thread is in the archive section.  For help you should visit the new Apple Forum at [http://ubuntuforums.org/forumdisplay.php?f=328]("http://ubuntuforums.org/forumdisplay.php?f=328")

---

### Post by guzzos on 2008-07-12
This is the guide I am following
[URL="http://ubuntuforums.org/showthread.php?t=442941"]
I'm running Ubuntu hardy 8.04 on a Macbook 4,1 Kernel version 2.6.25.

Mactel patches for this version are at:
https://mactel-linux.svn.sourceforge.net/svnroot/mactel-linux/trunk/kernel/mactel-patches-2.6.25/

I'm trying this because no matter what I still without WiFi and Sound. I already had those sources.   Any idea?

---

### Post by flaggh on 2008-07-12
There are already many questions regarding how to fix wifi and sound in the new forum, so you should first search there.  Nobody really browses the archives anymore so you won't get much help here.  Please go to the new Apple forum for help:
[http://ubuntuforums.org/forumdisplay.php?f=328]("http://ubuntuforums.org/forumdisplay.php?f=328")
You'll need to know what wifi adapter your running:
```
 lspci | grep Network 
```
and audio device:
```
lspci | grep Audio 
```
and search the forum for information on fixing these before you post any questions.  I have a Macbook 2,1 and everything works great.  I did not have to apply any kernel patches, but I don't have information on your specific model so I don't know what fixing your problems entails.  There are plenty of people on the new forum that can help you.

---

