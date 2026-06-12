---
title: "Please run this command to improve out-of-the-box Linux support for all Mac models"
date: 2010-08-20
forum: Apple Hardware Users
---

### Post by metatechbe on 2010-08-20
[COLOR=Red]WARNING : Deprecated approach, see [http://ubuntuforums.org/showpost.php?p=10828576&postcount=99](http://ubuntuforums.org/showpost.php?p=10828576&postcount=99)
[/COLOR]

Hello,

Can I kindly ask you to run the following command from a Terminal under MacOS X 10.5 or 10.6.  This will allow the "pure EFI boot" on Linux to work "out of the box" (ie without recompiling the Linux kernel) on all Mac models, by populating the "efifb_dmi_info" missing entries in the Linux kernel framebuffer driver (drivers/video/efifb.c).  Sorry, it cannot be launched from a Linux terminal, it is a chicken-and-egg problem) :

[FONT=Courier New]sudo ioreg -lw0 |grep manufacturer|cut -b25-80;sudo ioreg -lw0|grep "product-name"|cut -b 25-80;sudo dtrace -qn 'BEGIN{boot_args=((struct boot_args*)(`PE_state).bootArgs);printf("FrameBufferBase: 0x%08x\nPixelsPerScanLine: %d\nHorizontalResolution: %d\nVerticalResolution: %d", boot_args->Video.v_baseAddr, boot_args->Video.v_rowBytes/4, boot_args->Video.v_width, boot_args->Video.v_height);exit(0)} '
[/FONT]

[B]This command does not change anything to your system, it only reads the low-level EFI video values with the "ioreg" and the "dtrace" command and displays their values.
So basically the risk is 0.
[/B]
I am sure that with all the Mac passionates on this forum, in a few days we can cover all Apple models&#8230;

[FONT=Courier New]
**Model           FBB         PPSL  HR    VR    Manufacturer**
[COLOR=Red]Macmini1,1         ???[/COLOR]
[COLOR=Red]Macmini2,1         ???[/COLOR]
Macmini3,1      0x40010000  1024  1024  768   Apple Inc. # 1 GB RAM 
[/FONT][FONT=Courier New]Macmini3,1      0x80010000  2048  1360 768   Apple Inc. # 2 GB RAM
[/FONT][FONT=Courier New]Macmini3,1      0xc0010000  2048  1280  800   Apple Inc. # 4 GB RAM
Macmini3,1      0xc0010000  1024  1024  768   Apple Inc. # 4 GB RAM 
[/FONT][FONT=Courier New]Macmini4,1      0xc0010000  2048  1920  1200   Apple Inc.
MacPro1,1       0xe0010000  2048  1680  1050  Apple Computer, Inc.
MacPro1,1       0xe0060000  2048  1920  1200  Apple Computer, Inc.
MacPro2,1       0xe0010000  2560  2560  1600  Apple Computer, Inc.
MacPro3,1       0x80060000  2048  1680  1050  Apple Inc.
[COLOR=Red]MacPro4,1         ???[/COLOR]
MacPro5,1       0x80010000  1280  1280  1024  Apple Inc.
[COLOR=Red]iMac4,1         ???[/COLOR]
[COLOR=Red]iMac4,2         ???[/COLOR]
iMac5,1         0x80010000  1472  1440  900   Apple Computer, Inc.  # 2 GB RAM
iMac5,1         0xc0010000  1472  1440  900   Apple Computer, Inc.  # 4 GB RAM
[COLOR=Red]iMac5,2         ???[/COLOR]
[COLOR=Red]iMac6,1         ???[/COLOR]
iMac7,1         0x80010000  1728  1680  1050  Apple Inc. # 2 GB RAM
iMac8,1         0x80010000  1728 1680  1050  Apple Inc. # 2 GB RAM
iMac8,1         0xc0010000  1728 1680  1050  Apple Inc. # 4 GB RAM
iMac8,1         0xc0060000  2048  1920  1200  Apple Inc.
iMac9,1        0xc0010000  2048  1680  1050  Apple Inc.
[/FONT][FONT=Courier New]iMac9,1        0xc0030000  2048  1920  1200  Apple Inc.
[/FONT][FONT=Courier New]iMac9,1        0xc0060000  2048  1920  1200  Apple Inc.[/FONT]
[FONT=Courier New] iMac10,1        0xc0010000  1920  1920  1080  Apple Inc.
iMac10,1        0xc0010000  2048  1920  1080  Apple Inc.
iMac11,1        0xc0010000  2560  2560  1440  Apple Inc.
iMac11,2        0xc0010000  1920  1920  1080  Apple Inc.
iMac11,3        0xc0010000  2560  2560  1440  Apple Inc.
Xserve1,1      0x40010000  1280  1280  800   Apple Inc.
Xserve1,1      0x80010000  1280  1280  800   Apple Inc.
Xserve2,1      0x80010000  1024  1024  768   Apple Inc.
Xserve3,1      0x80030000  2048  1600  1200   Apple Inc.
MacBook1,1      0x80000000  2048  1280  800   Apple Computer, Inc.
MacBook2,1      0x80000000  2048  1280  800   Apple Inc.
MacBook3,1      0x40000000  2048  1280  800   Apple Inc. # 1 GB RAM
MacBook3,1      0x80000000  2048  1280  800   Apple Inc. # 2 GB RAM
MacBook3,1      0xc0000000  2048  1280  800   Apple Inc. # 4 GB RAM
MacBook4,1      0xc0000000  2048  1280  800   Apple Inc.
MacBook5,1      0x80010000  2048  1280  800   Apple Inc. # 2 GB RAM
MacBook5,1      0xc0010000  2048  1280  800   Apple Inc. # 4 GB RAM
MacBook5,2      0xc0010000  2048  1280  800   Apple Inc. # 4 GB RAM
MacBook6,1      0x80010000  2048  1280  800   Apple Inc. # 2 GB RAM
MacBook6,1      0xc0010000  2048  1280  800   Apple Inc. # 4 GB RAM
MacBook7,1      0x80010000  2048  1280  800   Apple Inc. # 2 GB RAM
[COLOR=Red]MacBookAir1,1         ???[/COLOR]
MacBookAir2,1      0x80010000  2048  1280  800   Apple Inc.
MacBookAir3,1      0x80010000  2048  1366  768   Apple Inc. # 2 GB RAM
MacBookAir3,1      0xc0010000  2048  1366  768   Apple Inc. # 4 GB RAM
MacBookAir3,2      0x80010000  2048  1440  900   Apple Inc. # 2 GB RAM
MacBookAir3,2      0xc0010000  2048  1440  900   Apple Inc. # 4 GB RAM
MacBookPro1,1   0x80010000  1472  1440  900   Apple Computer, Inc.
[COLOR=Red]MacBookPro1,2         ???[/COLOR]
[COLOR=Red]MacBookPro2,1         ???[/COLOR]
MacBookPro2,2   0x80010000  1472  1440  900   Apple Computer, Inc.
MacBookPro3,1   0xc0030000  2048  1440  900   Apple Inc.
MacBookPro4,1   0x80060000  2048  1440  900   Apple Inc. # 2 GB RAM
MacBookPro4,1   0xc0030000  2048  1440  900   Apple Inc. # 4 GB RAM
MacBookPro4,1   0xc0060000  2048  1440  900   Apple Inc. # 4 GB RAM
MacBookPro5,1   0x90010000  2048  1440  900   Apple Inc. # ?
MacBookPro5,1   0xc0010000  2048  1440  900   Apple Inc. # Discrete graphics
MacBookPro5,1  0xb0030000  2048  1440  900   Apple Inc. # Integrated graphics
MacBookPro5,2   0xc0010000  2048  1920  1200  Apple Inc. # Discrete graphics
MacBookPro5,2  0xb0030000  2048  1920  1200  Apple Inc. # Integrated graphics
MacBookPro5,3   0xd0010000  2048  1440  900   Apple Inc. # Discrete graphics
MacBookPro5,3  0xc0030000  2048  1440  900   Apple Inc. # Integrated graphics
MacBookPro5,4   0xc0010000  2048  1440  900   Apple Inc. 
MacBookPro5,5   0xc0010000  2048  1280  800   Apple Inc.
MacBookPro6,1   0x90030000  2048  1920  1200  Apple Inc. # Discrete graphics
MacBookPro6,2   0x90030000  2048  1680  1050  Apple Inc. # Discrete graphics
MacBookPro7,1   0xc0010000  2048  1280  800   Apple Inc.
[/FONT]
Submissions from all remaining Intel-based Mac models are welcome.
Different values are possible on the same model, depending on the amount of RAM.

On my machine, when the 9400M is active at boot time the output is the following :
```
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xd0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```On my machine, when the 9600M is active at boot time the output is the following :
```
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```If your machine has 2 graphics cards and the graphic card is switched after boot time (in "Energy Saving" preference pane or with gfxCardStatus), the FrameBufferBase value does not change anymore, it keeps its previous value, so it is really needed to do a full reboot.

Please copy the terminal output on your machine and paste it in a reply to this post !
As soon as the output is collected for all models, I will consolidate them and submit it as a patch to the Linux kernel.

Many thanks in advance for your help in this collaborative work !

metatech

---

### Post by kennethsime on 2010-08-20
I would be happy to test on MBP 5,5 if I better understood what exactly this did, and if it could harm my mac partition or not.

---

### Post by metatechbe on 2010-08-21
> **kennethsime said:**
> I would be happy to test on MBP 5,5 if I better understood what exactly this did, and if it could harm my mac partition or not.

kennethsime,

This command does not change anything to your system, it only reads the low-level EFI video values with the "ioreg" and the "dtrace" command.
So basically the risk is 0.

Thanks in advance for your submission,

metatech

---

### Post by kennethsime on 2010-08-21
This is with the 9400m. I'm not sure if I have two cards, or how to check the 9600 if I do.

```
 <"Apple Inc.">
 <"MacBookPro5,5">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

```

---

### Post by Nikos.Alexandris on 2010-08-21
> **kennethsime said:**
> This is with the 9400m. I'm not sure if I have two cards, or how to check the 9600 if I do.

According to [http://www.everymac.com/systems/apple/macbook_pro/stats/macbook-pro-core-2-duo-2.26-aluminum-13-mid-2009-sd-firewire-800-unibody-specs.html]("http://www.everymac.com/systems/apple/macbook_pro/stats/macbook-pro-core-2-duo-2.26-aluminum-13-mid-2009-sd-firewire-800-unibody-specs.html") and/or [http://www.everymac.com/systems/apple/macbook_pro/stats/macbook-pro-core-2-duo-2.53-aluminum-13-mid-2009-sd-firewire-800-unibody-specs.html]("http://www.everymac.com/systems/apple/macbook_pro/stats/macbook-pro-core-2-duo-2.53-aluminum-13-mid-2009-sd-firewire-800-unibody-specs.html")

the mbp 5,5 has only an integrated 9400M card.

---

### Post by Nikos.Alexandris on 2010-08-21
> **metatechbe said:**
> 
...

Please copy the terminal output on your machine and paste it in a reply to this post !
As soon as the output is collected for all models, I will consolidate them and submit it as a patch to the Linux kernel.

...

P.S. : Dear forum moderators, could this post be "sticky" for 2 weeks, so that all people have their chance to see it and contribute their value ? Thanks !

Maybe add in this thread (first post) a link to the "previous" thread [COLOR="Blue"][http://ubuntuforums.org/showthread.php?t=1076879]("http://ubuntuforums.org/showthread.php?t=1076879")[/COLOR] and a link in the "previous" thread pointing to the current thread?

(I randomly came in to the current thread)

---

### Post by Nikos.Alexandris on 2010-08-21
Something interesting (which you already might know):

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8a3bdfe6cd841880a5d849c40f90093b3817f6e0]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8a3bdfe6cd841880a5d849c40f90093b3817f6e0")

Regards, Nikos

---

### Post by metatechbe on 2010-08-21
> **Nikos.Alexandris said:**
> Something interesting (which you already might know):

[http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8a3bdfe6cd841880a5d849c40f90093b3817f6e0]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8a3bdfe6cd841880a5d849c40f90093b3817f6e0")

Regards, Nikos

Nikos,

Yes, for my investigation I used the following pieces of information : 
- [alexmurray's findings in the rEFIt shell in the Ubuntu forum ]("http://ubuntuforums.org/showthread.php?t=1076879")
- [Thomas Gerlach's contribution to the Linux framebuffer driver]("http://git.kernel.org/?p=linux/kernel/git/torvalds/linux-2.6.git;a=commit;h=8a3bdfe6cd841880a5d849c40f90093b3817f6e0")
- [dtrace examples from on the blog of Amit Singh]("http://www.osxbook.com/blog/2009/02/25/displaying-the-physical-memory-map/"), author or "Mac OS X Internals: A Systems Approach"
- [Apple BootX open source code]("http://www.opensource.apple.com/source/BootX/BootX-46/bootx.tproj/include.subproj/boot_args.h")

After my method was tested successfully by several other people in the initial thread, I also contributed it to : 
- [Grub2 Wiki]("http://grub.enbug.org/TestingOnMacbook")
- [Red Hat bug 528232]("https://bugzilla.redhat.com/show_bug.cgi?id=528232")

I hope to collect information on as many Mac hardware models as possible…

Regards,

metatech

---

### Post by Nikos.Alexandris on 2010-08-21
metatech,

you know very well what you are doing. I am just trying to help by making sure important information (I read) is on your list since I am not able to truly help (with coding, etc.).

Thank you for your efforts, Nikos

---

### Post by furok23 on 2010-08-22
hey man id love to help, but im when i run the command i get the same output for both of my graphics cards.. or at least what i think is both cards...

 <"Apple Inc.">
 <"MacBookPro6,2">
FrameBuff erBase: 0x90030000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

im prolly doing it wrong ya?

---

### Post by ZeroLinux on 2010-08-22
<"Apple Inc.">
 <"iMac10,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1920
HorizontalResolution: 1920
VerticalResolution: 1080

---

### Post by metatechbe on 2010-08-22
> **furok23 said:**
> hey man id love to help, but im when i run the command i get the same output for both of my graphics cards.. or at least what i think is both cards&#8230;

im prolly doing it wrong ya?

Furok23,

Thanks for trying hard to help...

In order to get the other FrameBufferBase value, you should go the the "Energy saving" preference pane and change the radio button there ("("better battery life" or "higher performance"), then do a full reboot. 
If you cannot find the radio button or it does not work, it probably means MacBook 2010 models have automatic switching based on graphic workload, and, at boot time, the selected graphic card is always the integrated one (Intel in this model).  
Do you see the radio button or not ?

Thanks,

metatech

---

### Post by siepo on 2010-08-22
<"Apple Computer, Inc.">
 <"MacBook1,1">
FrameBuff erBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by furok23 on 2010-08-22
> **metatechbe said:**
> Furok23,

Thanks for trying hard to help...

In order to get the other FrameBufferBase value, you should go the the "Energy saving" preference pane and change the radio button there ("("better battery life" or "higher performance"), then do a full reboot. 
If you cannot find the radio button or it does not work, it probably means MacBook 2010 models have automatic switching based on graphic workload, and, at boot time, the selected graphic card is always the integrated one (Intel in this model).  
Do you see the radio button or not ?

Thanks,

metatech

yea i was in there. interestingly enough, i still get the same buffer value for both settings...
my process was:
evergy save mode on (integrated graphics switching), run code

energy save mode off (high performance graphics always on), restart, confirm high performance graphics, run code. 

same values. shenanigans i say
any other mpb 6,2 users confirm this?

---

### Post by v41 on 2010-08-23
<"Apple Inc.">
<"MacBook4,1">
FrameBuff erBase: 0xc0000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by Sidolin on 2010-08-23
> **furok23 said:**
> yea i was in there. interestingly enough, i still get the same buffer value for both settings...
my process was:
evergy save mode on (integrated graphics switching), run code

energy save mode off (high performance graphics always on), restart, confirm high performance graphics, run code. 

same values. shenanigans i say
any other mpb 6,2 users confirm this?

Same on my mbp 6,2. I'll post the output from tinkering with the efi shell later, maybe that helps.

Edit: See the attachment for efi information, especially dff7 and dfh9.

---

### Post by metatechbe on 2010-08-24
> **Sidolin said:**
> Same on my mbp 6,2. I'll post the output from tinkering with the efi shell later, maybe that helps.

Edit: See the attachment for efi information, especially dff7 and dfh9.

Sidolin,

Thanks for the rEFIt shell outputs.
It looks like the MBP 2010 have the following behaviour : the discrete NVIDIA graphic card is activated during the boot, and it switches dynamically to the integrated Intel afterwards.

On my MBP 2009, depending on the "Energy saving" radio button, the activated card at boot time shows its properties (FrameBufferBase, PixelsPerScanLine, ...) in rEFIt shell and the deactivated card does not show them.

In order to get the FrameBufferBase of the integrated graphics on a MBP 2010, it seems that another method is needed... 

Can you confirm that your "Energy saving" radio button was in the "on" position during your test ?

Regards,

metatech

---

### Post by metatechbe on 2010-08-24
Sidolin,

With the NVIDIA address do you manage to specify the "BusID" of the Intel one in xorg.conf ? Does it actually use the Intel graphics or not ?

Regards,

metatetch

---

### Post by alphaamanitin on 2010-08-24
metatechabe, not that I do not trust you, but I for one would feel much better if a mod came in here and confirmed what appears to me, to be a harmless command, is harmless.  Still, it requires sudo so that in itself is enough to give me pause.  I won't be of any help either way though as I do not use a Mac.  Well that is not true.  I do use a mac desktop at work runing OSX 10.5 or something.  Would that help?  I don't know the model or anything about it really as I am a PC guy.

AlphaA

---

### Post by DBO on 2010-08-24
alphaamanitin,

I am not a mod but I do work for Canonical. The command metatechbe is having people run is primarily a diagnostics command, it should not harm your computer. That said, I would always advise caution. If you are uncomfortable it is always the best practice to not run a foreign command.

metatechbe,
I have a macbook pro 6,2. If you want to hop on IRC I would be happy to do some live debugging work with you on the macbook 6,2.

Jason "DBO" Smith

---

### Post by lael on 2010-08-25
<"Apple Inc.">
 <"MacBookPro5,2">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1200

Identical for both the 9400M and the 9600M GT cards.

---

### Post by lael on 2010-08-25
<"Apple Inc.">
 <"MacBookPro6,1">
FrameBuff erBase: 0x90030000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1200

I get the same result when using the Intel HD Graphics or the Nvidia GeForce GT 330M card (can see which one in the system profiler)

---

### Post by lael on 2010-08-25
> **furok23 said:**
> hey man id love to help, but im when i run the command i get the same output for both of my graphics cards.. or at least what i think is both cards...

 <"Apple Inc.">
 <"MacBookPro6,2">
FrameBuff erBase: 0x90030000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

im prolly doing it wrong ya?

I saw the same exact result with my MacBookPro6,1, I tried a bunch of stuff, and even ran some HD 1080p content that would scale up the larger graphics card.

I don't know much about this, but from what I read about how the seamless graphics switching, it makes sense that they both use the same memory location isn't that how they seamlessly switch between cards, by utilizing the same buffer space?

[http://www.anandtech.com/show/2934/nvidia-optimus-truly-seamless-switchable-graphics-and-asus-ul50vf/3](http://www.anandtech.com/show/2934/nvidia-optimus-truly-seamless-switchable-graphics-and-asus-ul50vf/3)

---

### Post by metatechbe on 2010-08-25
lael,

Thanks for your (double) contribution !
For the MacBookPro 5,2, are you sure you did a full reboot after switching the graphic card ? On my 5,3, it is really needed (gfxCardStatus or logout/login is not enough)...

Thanks,

metatech

---

### Post by metatechbe on 2010-08-25
Hello,

From the kernel source it seems that it is not needed to recompile the kernel, adding this kernel parameter should be enough (the values are specific to your model, coming from the ioreg/dtrace output) :

```
video=efifb:base:0xc0030000,stride:2048,width:1440,height:900

```I still need to test it.  I plan to add it /etc/default/grub in the GRUB_CMDLINE_LINUX_DEFAULT option.

Regards,

metatech

---

### Post by lael on 2010-08-25
> **metatechbe said:**
> lael,

Thanks for your (double) contribution !
For the MacBookPro 5,2, are you sure you did a full reboot after switching the graphic card ? On my 5,3, it is really needed (gfxCardStatus or logout/login is not enough)...

Thanks,

metatech

You are right. Rebooting did make a difference.
9400M:
<"Apple Inc.">
<"MacBookPro5,2">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1200

9600M GT:
<"Apple Inc.">
<"MacBookPro5,2">
FrameBuff erBase: 0xb0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1200

---

### Post by lael on 2010-08-25
> **metatechbe said:**
> Hello,

From the kernel source it seems that it is not needed to recompile the kernel, adding this kernel parameter should be enough (the values are specific to your model, coming from the ioreg/dtrace output) :

```
video=efifb:base:0xd001000,stride:2048,width:1440,height:900

```I still need to test it.  I plan to add it /etc/default/grub in the GRUB_CMDLINE_LINUX_DEFAULT option.

Regards,

metatech

Does this mean that it will be possible to boot directly into GRUB2 skipping rEFIt?

I like that rEFIt exists, but I don't like seeing 2 boot screens on every boot.

---

### Post by doctorjames on 2010-08-25
<"Apple Inc.">
 <"Macmini3,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

 <"Apple Inc.">
 <"MacBookPro4,1">
FrameBuff erBase: 0xc0060000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by Hiram on 2010-08-25
<"Apple Inc.">
 <"MacBook5,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by Nikos.Alexandris on 2010-08-26
> **lael said:**
> Does this mean that it will be possible to boot directly into GRUB2 skipping rEFIt?

I like that rEFIt exists, but I don't like seeing 2 boot screens on every boot.

If this works there will be a 20+ seconds cut-off from waiting rEFIt, etc. Then again, e.g. when in need to check for firmware updates (=boot in OSX), booting OSX won't be possible, right?

---

### Post by linuxopjemac on 2010-08-26
<"Apple Inc.">
 <"MacBook2,1">
sudo: dtrace: command not found

I am still on Tiger by the way...

---

### Post by linuxopjemac on 2010-08-26
<"Apple Inc.">
 <"MacBook2,1">
sudo: dtrace: command not found

I am still on Tiger, maybe that's the reason I get this error?

---

### Post by davidryderuk on 2010-08-26
<"Apple Inc.">
 <"MacBook7,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by metatechbe on 2010-08-27
<"Apple Inc.">
 <"iMac11,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 2560
HorizontalResolution:2560
VerticalResolution: 1440

---

### Post by mohaas05 on 2010-09-01
<"Apple Inc.">
<"MacBookPro7,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by foal3x on 2010-09-01
<"Apple Inc.">
 <"iMac10,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1600
HorizontalResolution: 1600
VerticalResolution: 900

 ATI Radeon HD 4670

---

### Post by entangled on 2010-09-02
<"Apple Inc.">
 <"iMac11,2">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1920
HorizontalResolution: 1920
VerticalResolution: 1080

---

### Post by unixninja92 on 2010-09-02
<"Apple Inc.">
 <"MacBookPro5,4">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by bLax169 on 2010-09-03
9400 after statup

 <"MacBookPro5,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

9600GT after startup

<"Apple Inc.">
 <"MacBookPro5,1">
FrameBuff erBase: 0xb0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by jooooooon on 2010-09-05
<"Apple Inc.">
 <"iMac7,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

(yes, that space in "FrameBuff er" is output by the command)

---

### Post by nick100 on 2010-09-07
> **metatechbe said:**
> Hello,

Can I kindly ask you to run the following command from a Terminal under MacOS X.  This will allow the "pure EFI boot" on Linux to work "out of the box" (ie without recompiling the Linux kernel) on all Mac models, by populating the "efifb_dmi_info" missing entries in the Linux kernel framebuffer driver (drivers/video/efifb.c).  Sorry, it cannot be launched from a Linux terminal, it is a chicken-and-egg problem) :

[FONT="Courier New"]sudo ioreg -lw0 |grep manufacturer|cut -b25-80;sudo ioreg -lw0|grep "product-name"|cut -b 25-80;sudo dtrace -qn 'BEGIN{boot_args=((struct boot_args*)(`PE_state).bootArgs);printf("FrameBufferBase: 0x%08x\nPixelsPerScanLine: %d\nHorizontalResolution: %d\nVerticalResolution: %d", boot_args->Video.v_baseAddr, boot_args->Video.v_rowBytes/4, boot_args->Video.v_width, boot_args->Video.v_height);exit(0)} '
[/FONT]

[B]This command does not change anything to your system, it only reads the low-level EFI video values with the "ioreg" and the "dtrace" command and displays their values.
So basically the risk is 0.
[/B]
I am sure that with all the Mac passionates on this forum, in a few days we can cover all Apple models...
Submissions from all Intel-based Mac models are welcome (iMac, MacBook, MacBook Pro, ...).

On my machine, when the 9400M is active at boot time the output is the following :
```
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xd0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```
On my machine, when the 9600M is active at boot time the output is the following :
```
<"Apple Inc.">
<"MacBookPro5,3">
FrameBufferBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```
I already have the output for MacBookPro5,1 and MacBookPro5,3, but for all others models, one or several values are missing&#8230;

If your machine has 2 graphics cards and the graphic card is switched after boot time (in "Energy Saving" preference pane or with gfxCardStatus), the FrameBufferBase value does not change anymore, it keeps its previous value, so it is really needed to do a full reboot.

Please copy the terminal output on your machine and paste it in a reply to this post !
As soon as the output is collected for all models, I will consolidate them and submit it as a patch to the Linux kernel.

Many thanks in advance for your help in this collaborative work !

metatech

P.S. : Dear forum moderators, could this post be "sticky" for 2 weeks, so that all people have their chance to see it and contribute their value ? Thanks !
PixelsPerScanLine: 512
HorizontalResolution: 1680
VerticalResolution: 1050
ubuntu:~ nick$

---

### Post by nick100 on 2010-09-07
PixelsPerScanLine: 512
HorizontalResolution: 1680
VerticalResolution: 1050
ubuntu:~ nick$

---

### Post by cybercookie72 on 2010-09-07
<"Apple Computer, Inc.">
 <"MacBookPro1,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1472
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by loukingjr on 2010-09-08
late 2007 imac

 <"Apple Computer, Inc.">
 <"iMac5,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 1472
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by funkwurm on 2010-09-09
Every little helps


 <"Apple Computer, Inc.">
 <"MacBookPro1,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1472
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by fseoer2010 on 2010-09-10
That's a very good post! I have learnt so much from this post! And I will tell my friends this website. Thanx for your sharing.

---

### Post by Robert Biloute on 2010-09-11
<"Apple Inc.">
 <"MacBookPro6,2">
FrameBuff erBase: 0x90030000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by itismike on 2010-09-12
<"Apple Inc.">
 <"MacBookPro6,2">
FrameBuff erBase: 0x90030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

The above was identical immediately after booting up and also a few minutes after playing an OpenGL-intensive flight simulator.

---

### Post by jaysmc on 2010-09-12
<"Apple Inc.">
 <"MacPro3,1">
FrameBuff erBase: 0x80060000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by linuxway on 2010-09-12
I got the following message:
"sudo: dtrace: command not found"

---

### Post by logandzwon on 2010-09-13
NVIDIA GeForce 9600M GT;

 <"Apple Inc.">
 <"MacBookPro5,3">
FrameBuff erBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900



I think my model was already posted. I'll try to post up a macmini4,1 server before next week though.-

In case anyone is wondering what the command does, it's just running "ioreg -lw0" as root, all the other stuff just cuts out and then formats the output into the desired format.

---

### Post by ipc on 2010-09-13
<"Apple Inc.">
 <"MacPro5,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1280
HorizontalResolution: 1280
VerticalResolution: 1024

---

### Post by heluani on 2010-09-13
```
 <"Apple Inc.">
 <"MacBookAir2,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800
```

Macbook Air 2,1 booting fine into grub2 without refit for about a year now.

PS. If you know how to deal with the EFI shell, I'd love if you could pm me (or in another thread) to commands dealing with audio to activate the mic.

---

### Post by jamesey on 2010-09-14
I purcahsed an imac9,1 within a week of it's release in march 2009. Here are my results

```

 <"Apple Inc.">
 <"iMac9,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050
```

---

### Post by SeineDudeheit on 2010-09-16
Macbook Pro 5,3 with 9400m activated.
```

 <"Apple Inc.">
 <"MacBookPro5,3">
FrameBuff erBase: 0xd0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```

looking forward to activate the 9400m in linux to safe up some battery time... ;-)

---

### Post by logandzwon on 2010-09-17
<"Apple Inc.">
 <"Macmini4,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1080

---

### Post by peterx14 on 2010-09-19
<"Apple Inc.">
 <"MacBook3,1">
FrameBuff erBase: 0x40000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

Best wishes! :)

Update: This machine only has it's factory default 1GB of RAM.... dunno if it makes any difference!

---

### Post by metatechbe on 2010-10-23
Originally submitted by RickvanderZwet on grub wiki
<"Apple Inc.">
 <"MacBookPro4,1">
FrameBufferBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

Remark : the value is different than the one reported by doctorjames for the same model (0xc0030000). A difference is in the first hex digit is generally due to the amount of physical RAM in the machine, but a difference in the fourth hex digit is not explained yet.  Anyone has ideas ? Maybe it is due to which PCI devices are active ?

Thanks.

---

### Post by SuperDodge on 2010-10-24
<"Apple Inc.">
 <"MacBookAir3,2">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by ebsi on 2010-10-24
Macbook Air 11"

<"Apple Inc.">
<"MacBookAir3,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1366
VerticalResolution: 768

---

### Post by wiml on 2010-10-25
A few more entries:

```
 <"Apple Computer, Inc.">
 <"MacPro2,1">
FrameBuff erBase: 0xe0010000
PixelsPerScanLine: 2560
HorizontalResolution: 2560
VerticalResolution: 1600

```

```
 <"Apple Inc.">
 <"Xserve2,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1024
HorizontalResolution: 1024
VerticalResolution: 768

```

```
 <"Macmini3,1">
 <"Apple Inc.">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1024
HorizontalResolution: 1024
VerticalResolution: 768

```

---

### Post by WanderingOak on 2010-10-25
<"Apple Inc.">
 <"iMac7,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by t0dbld on 2010-10-25
<"Apple Inc.">
 <"Macmini4,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

Im currently on snow leopard server and the command did not work, it still goes blank after selecting any of the option menus in live disk or after selecting install from the efi boot menu

---

### Post by BOYerchen on 2010-10-27
From my Mac Mini at work:

```

 <"Apple Inc.">
 <"Macmini3,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1080

```

---

### Post by fearphage on 2010-10-27
From new iMac at work:

```
<"Apple Inc.">
 <"iMac11,3">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2560
HorizontalResolution: 2560
VerticalResolution: 1440
```

---

### Post by JammyZ on 2010-10-27
```

 <"Apple Inc.">
 <"MacBook2,1">
FrameBuff erBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

```

---

### Post by Gordonta on 2010-10-28
Code:                                                                                                                                                    <"Apple Inc."> 
<" iMac 9,1 ">
FrameBuff erBase:  0xc0030000
PixelsPerScanLine:  2048
HorizontalResolution:  1920
VerticalResolution:  1200

iMac 24", 2.93 GHz Intel Core2Duo, 4 GB Ram, NVidia GeForce GT 120

---

### Post by apoth on 2010-10-28
```
 <"Apple Inc.">
 <"MacBookAir3,2">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

```

New MacBook Air, 13" with 4GB RAM.

---

### Post by teh603 on 2010-10-28
<"Apple Inc.">
 <"Macmini3,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1360
VerticalResolution: 768


Didn't see this one listed, and figured you might want to add it.

---

### Post by forbes on 2010-10-29
Will this be part of 11.04?

MacBook Air 11" with 4GB of RAM:

```
 <"Apple Inc.">
 <"MacBookAir3,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1366
VerticalResolution: 768

```

---

### Post by nikdzl on 2010-11-09
<"MacBookPro5,1">
FrameBuff erBase: 0x90010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by larsribe on 2010-11-12
<"Apple Inc.">
 <"Xserve3,1">
FrameBufferBase: 0x80030000
PixelsPerScanLine: 2048
HorizontalResolution: 1600
VerticalResolution: 1200

---

### Post by metatechbe on 2010-11-12
> **nikdzl said:**
> <"MacBookPro5,1">
FrameBuff erBase: 0x90010000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

Thanks nikdzl. 
This value has never been reported before for this model.
How much RAM do have ?
Which graphic card was active when you ran the command ?
Do you have unusual devices connected (USB or other) ?

Thanks.

metatech

---

### Post by tctc on 2010-12-04
<"iMac8,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050
iMac:~ user$ 

4GB memory

 <"Apple Inc.">
 <"MacBook5,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800
MacBook:~ user$ 

4GB memory

---

### Post by Drudus on 2010-12-04
<"Apple Computer, Inc.">
 <"MacPro1,1">
FrameBuff erBase: 0xe0060000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1200


Mac Pro 1,1 with replaced NVIDIA 8800GT

---

### Post by tctc on 2010-12-07
<"Apple Inc.">
 <"iMac8,1">
FrameBufferBase: 0x80010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050
iMac:~ user$ 2GB memory

---

### Post by anunn2001 on 2010-12-07
<"Apple Computer, Inc.">
 <"MacPro1,1">
FrameBuff erBase: 0xe0020000
PixelsPerScanLine: 2560
HorizontalResolution: 2560
VerticalResolution: 1600

---

### Post by mackaframa85 on 2010-12-08
<"Apple Inc.">
 <"iMac7,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1280
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by dpny on 2010-12-08
<"Apple Inc.">
 <"MacPro5,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1920
HorizontalResolution: 1920
VerticalResolution: 1080

8 GB RAM
1 GB 5870

---

### Post by mark.i.r.muir on 2011-02-02
<"Apple Inc.">
 <"Macmini2,1">
FrameBuff erBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 1024

---

### Post by srs5694 on 2011-02-02
Here's mine, from a Mac Mini with 1 GiB of RAM:

<"Apple Computer, Inc.">
 <"Macmini1,1">
FrameBuff erBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 800
VerticalResolution: 600

Note that I was booted via EFI already; I don't know if that makes any difference. I mention it mainly because my actual video resolution is 1280x1024, not the reported 800x600 -- but maybe that's just a default or something....

---

### Post by derflooh on 2011-02-06
<"Apple Inc.">
 <"MacBookPro3,1">
FrameBufferBase: 0x80030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

2GB Ram

---

### Post by uced on 2011-02-09
MacMini 2GHz Intel Core 2 Duo
Memory: 4 GB 1067 MHz DDR3

<"Apple Inc.">
 <"Macmini3,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 1024

---

### Post by racan on 2011-02-25
For iMac with 4 GB ram the output is


 <"Apple Inc.">
 <"iMac7,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by ruiferreira on 2011-02-26
<"Apple Inc.">
 <"MacBookPro8,1">
FrameBuff erBase: 0x90000000
PixelsPerScanLine: 1280
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by aka TRAP on 2011-02-26
<"Apple Inc.">
 <"MacBook7,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by jeremybar on 2011-03-02
```
 <"Apple Inc.">
 <"MacBookPro7,1">
FrameBufferBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

```

---

### Post by gforster on 2011-03-02
Macbook Pro 8,2 (15" model with hi-res anti-glare screen, AMD Radeon HD 6750M; 4GB RAM)

```
 <"Apple Inc.">
 <"MacBookPro8,2">
FrameBuff erBase: 0x90010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

```

---

### Post by TheShanthan on 2011-03-02
<"Apple Inc.">
 <"MacBookPro5,5">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800


I took your word for it. Please dont do anything to my comp.

---

### Post by zencoder on 2011-03-10
Thread is l-o-o-o-o-ng, not sure if this model has been posted yet...

Mac mini Server (Mid 2010) 8GB ram

I was running the server 'headless' and got the first result via an ssh shell.

 <"Apple Inc.">
 <"Macmini4,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 1024
HorizontalResolution: 1024
VerticalResolution: 768


I rebooted with an HDMI connection to an ASUS VH242H. It came up in a native, low res mode, so I changed the display refresh rate to 60 Hertz NTSC (was set to 50/PAL) and the resolution to 1080p. This is the result after changing those settings but NOT rebooting:

 <"Apple Inc.">
 <"Macmini4,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 720


I then performed a reboot, logged in locally to the desktop, opened an ssh shell, and ran the command via the ssh shell and got this result:

 <"Apple Inc.">
 <"Macmini4,1">
FrameBuff erBase: 0xc0010000
PixelsPerScanLine: 2048
HorizontalResolution: 1920
VerticalResolution: 1080
hqosx01:~ admin$

Does *any* of this help? Any further actions required, please let me know and I'll do what I can.

---

### Post by macsforever2000 on 2011-03-14
I didn't see this result for my 2008 Mac Pro (8 GB RAM, ATI Radeon HD 2600):
 
<"Apple Inc.">
 <"MacPro3,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1920
HorizontalResolution: 1920
VerticalResolution: 1200

---

### Post by DarkCloud2015 on 2011-03-14
<"Apple Inc.">
 <"MacBook7,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by hanfi on 2011-04-04
```

<"Apple Inc.">
<"MacBookPro4,1">
FrameBufferBase: 0x80060000 
PixelsPerScanLine: 2048 
HorizontalResolution: 1920 
VerticalResolution: 1200

```

---

### Post by hostile on 2011-05-05
<"Apple Computer, Inc.">
 <"iMac5,1">
FrameBuff erBase: 0x80010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by Nitram-TM on 2011-05-06
Here's mine, hope it helps.

<"Apple Inc.">
<"MacBookPro8,1">
FrameBufferBase: 0x90000000
PixelsPerScanLine: 1280
HorizontalResolution: 1280
VerticalResolution: 800

---

### Post by Slowpokemon on 2011-05-06
```
<"Apple Computer, Inc.">
<"Macmini1,1">
FrameBufferBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 1024
```1 GB 667 MHz DDR2 SDRAM

---

### Post by Slowpokemon on 2011-05-06
```
<"Apple Inc.">
<"Macmini2,1">
FrameBuff erBase: 0x80000000
PixelsPerScanLine: 2048
HorizontalResolution: 1280
VerticalResolution: 1024
```

---

### Post by polarbear10 on 2011-05-17
MacbookPro 2Ghz i7 (purchased April 2011)

 <"Apple Inc.">
 <"MacBookPro8,2">
FrameBuff erBase: 0x90010000
PixelsPerScanLine: 1728
HorizontalResolution: 1680
VerticalResolution: 1050

---

### Post by metatechbe on 2011-05-17
All,
For the record, I came to the conclusion that the "efifb.c patching" is the
wrong approach. 
Normally the bootloader is responsible for querying the graphics hardware
properties (FrameBufferBase, PixelsPerScanLine, HorizontalResolution,
VerticalResolution), and then it passes them to the kernel through the
"linux_kernel_params" structure.
Grub2 can do that, for both UGA (PCI scanning trick) or GOP (returned by the
official EFI API).
The kernel should not have this list of hard-coded values.  Furthermore, these
values are not unique for a Mac model, but can very depending on the amount of
RAM and possibly also on the connected devices at boot time.
See user submissions in this thread.
On top of that, these values in efifb.c are really misleading : someone looking
for a reason why the EFI boot does not work on a brand new model might think
that his model is missing in the list and that causes the problem, which is a
wrong track.
I think we should remove these hard-coded values from the kernel and only rely
on values passed by the booloader (which should be dynamically queried), so
that it will work on all models.
Regards,
metatech

---

### Post by nicholas on 2013-03-03
This is the output from my 17" MacBook Pro (early 2008), 4GB RAM, 512MB NVidia 8600M GT.

```
 <"Apple Inc.">
 <"MacBookPro4,1">
FrameBuff erBase: 0xc0060000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050
```

---

### Post by izzo on 2013-03-04
<"Apple Inc.">
 <"MacBookPro6,2">
FrameBuff erBase: 0xc0030000
PixelsPerScanLine: 2048
HorizontalResolution: 1440
VerticalResolution: 900

---

### Post by heat33330 on 2013-03-06
This is only for intel Macs, you should change the end to "all intel Mac models".

---

### Post by StampU on 2013-03-19
<"Apple Inc.">
 <"MacBookPro9,1">
FrameBuff erBase: 0x90020000
PixelsPerScanLine: 2048
HorizontalResolution: 1680
VerticalResolution: 1050

---

