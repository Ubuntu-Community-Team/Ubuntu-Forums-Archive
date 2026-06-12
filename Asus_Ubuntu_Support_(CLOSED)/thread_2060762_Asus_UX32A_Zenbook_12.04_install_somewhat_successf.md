---
title: "Asus UX32A Zenbook 12.04 install somewhat successful gfx issues"
date: 2012-09-20
forum: Asus Ubuntu Support (CLOSED)
---

### Post by infernozx on 2012-09-20
I'm not new to Ubuntu, but my last HP laptop just kind of worked out of the box when I put Ubuntu on it. 

I recently bought the Zenbook, and while I love the size, look, feel, everything, I've just spent about 12 hours actually getting ubuntu loaded.

If anyone wants a breakdown of how to get ubuntu on the machine as a sole boot, using the SSD as the "/" folder, and the HDD as the "/home" I can write that up tomorrow.

For now, I was wondering if someone can help me with trouble shooting my graphics problem.
To get past a black screen on boot, I was forced to add "nomodeset" into one of grubs line as suggested elsewhere in this forum. Unfortunately I think what that has done is force me to use some fairly basic drivers, and I can therefore not get Ubuntu to run in 3d mode, it's forced into 2D.

I'm not sure what information everyone needs, so please just ask and I'll post it up as soon as I can.

Thanks

---

### Post by infernozx on 2012-09-21
I installed the PPA and updated.

First reboot hung at boot.

[IMG]http://imgur.com/rA5UO.jpg[/IMG]



On reboot it wanted to go into recovery mode, recovery mode worked, but was in 2d, and the screen brightness functions still didn't work.

Rebooting through recovery mode, but once it's recovered doing the switch to full mode throws the warning that "Graphics drivers may need to be reloaded." it loaded into full mode, but was in 2d. I did have access to a list of drivers that are new though in the "Additional Drivers" icon.



Upon logging out, I went back to a black screen but had the sound that you get when you see the login screen. So it's not hanging, it's just not displaying.


Any other ideas?

---

### Post by infernozx on 2012-09-21
More information:

Rebooting and getting into the older versions of the kernel in grub. (nomodeset has been removed)

3.5.0-15 generic : Hangs in a black screen with the text like the picture above. Not always the same text though.. it seems to get to different places every time. 

There is a line: 
Kernel panic - not syncing: Attempting to kill the idle task!
panic occurred, switching back to text console

3.2.0-31 generic: boots to login screen, (I can hear the login "blooop" but the screen is black.)

3.2.0-30 generic:  boots to login screen, (I can hear the login "blooop" but the screen is black)

3.2.0-29 generic: boots to login screen, (I can hear the login "blooop" but the screen is black)


Getting into the grub editor with the "e" key at the grub menu, and changing the end of the appropriate line to nomodeset allows ubuntu to boot properly.



Drivers listed in additional drivers now:

mac_hid
LPC interface for Intel ICH
Intel Wireless WiFi Link AGN driver for Linux
Realtek RTS5139/29 USB card reader driver
Intel Core temperature monitor
I801 SMBus driver (This driver is not activated)
Intel Management Engine Interface
Intel HDA driver
Asus Notebooks WMI Hotkey Driver
PC Speaker beeper driver (This driver is not activated)
kvm_intel
Intel Graphics
USB Video Class driver



Any more ideas/troubleshooting?

Edit: Should report that since the first install that I manged to get booted in completely all function keys work as advertised except monitor brightness.

Sleep (f1) - works (but is unrecoverable after it shows a logout screen then the screen goes blank)
wifi (f2) - works
keyboard brightness up/down (f3/F4) - works
brightness (f5/f6) - no function at all
screen off (f7) - works, and turns the screen back on with the second push
monitor switch (f8) - untested
touchpad disable (f9) - works
sound up/down/mute (f10,f11,f12) - work

Function (A) - Autobrightness - no work
Function (C) - Unknown, no function
Function (V) - Unknown, no function.
Function Del - insert (works)
Function Up, Down, Left, Right - Pg-up, home, pg-down, end (work)

---

### Post by infernozx on 2012-09-21
1

---

### Post by infernozx on 2012-09-21
Update:

I managed to get ubuntu to boot, on all the kernels present by changing the "nomodeset" command to "acpi_osi=windows"

This made the suspend function work flawlessly, it also allowed me to use 3D mode, and have the extra driver support. There's a couple of odds and ends to fix up.

The big problem that's pretty unacceptable though is that it won't boot on the first try.

You have to let it boot and fail, then when it reboots it will send you to the Grub menu, once in the menu, you HAVE to press "e" then f10 to boot. You don't need to change any parameters, you just have to A) enter the menu, and B) Enter the editor, then go ahead and boot.

Anyone have any idea how this can be?

---

### Post by infernozx on 2012-09-22
New update:

The best install I've managed to get so far is with the 32bit version of 12.04

Install, then run the updates as depicted above.

Everything works, except for the brightness keys, suspend does work perfectly.

The only problem is that after removing "nomodeset" from GRUB, it boots about once in ever 3 tries. the other two tries will hang in one of two places, right before the login screen displays, and right after, when it's only 1/2 loaded. There's login boxes, and the title bar, but the background is just purple with polkadots.

The computer is frozen. No movement or response from the mouse/trackpad, keyboard or anything. It must be hard rebooted.

Any ideas?

---

### Post by BandedHawk on 2012-09-25
Currently trying some fixes against launchpad bug 1041883. Moderate success - still kernel panics until system warms up it appears. You can try the suggested kernel patches in the bug report and see if things improve. That would help with testing so that things are fixed for 12.10. One guy with a UX32VD is having no problems, the rest of us seem to continue to have the one boot in 3 works (on mine until things warm up).

[Bug 1041883]("https://bugs.launchpad.net/bugs/1041883")

---

### Post by BandedHawk on 2012-10-06
Outcome seems to be that a patched version of the kernel produced in the launchpad bug 1041883 properly sets video. But the kernel panics seem to arise from the btusb module having some sort of timing clash with the graphics mode switch. In any case, blacklisting btusb and then installing the module later in rc.local avoids the kernel panics that otherwise occur frequently booting 12.04. Hope that helps. Refer to the bug tracker for more information on what to do, and to get a 3.5.0-15 kernel build.

---

### Post by infernozx on 2012-10-08
Thanks, been following the link and it looks like it should be fixed for 12.10?

---

### Post by xicosm on 2012-10-19
I just got my UX32A and downloaded 12.10

I cannot get past the blank screen ... really frustrating

---

### Post by PartitionTable on 2012-10-20
> **xicosm said:**
> I just got my UX32A and downloaded 12.10

I cannot get past the blank screen ... really frustrating

Have you tried putting the computer to sleep and then waking it up?

Your post is making me apprehensive about updating to 12.10 
I'm having the black screen problem in 12.04, but to make it come back, I just put the computer to sleep and then wake it up (sometimes this takes as many as 4-5 tries though). But if it's not letting you get past the black screen at all, then I'm not going to risk it, and am just going to stick with 12.04 instead... 

Was kind of hoping the problem was going to be fixed in 12.10, because it does get frustrating when it takes multiple cycles to get the screen back.

---

### Post by xicosm on 2012-10-21
Apologies for the previous post ... I was really annoyed with the whole thing and at that point I didn't know about putting the laptop to sleep.

So yes, after I found that out, it works "fine". I still need to put it to sleep and wake up to get the screen working, but it does work every time.

---

### Post by PartitionTable on 2012-10-27
So I managed to get the screen to stop booting into black by adding nomodeset to grub.

The problem then is, the mouse disappears while being dragged around - it flickers visible to invisible while in use, and remains invisible while not used - and you're also stuck with the abhorrently large Unity 2D icons with no option to resize.

... I ended up removing nomodeset and going back to the black screen problem. Funnily enough, the mouse icon flickering didn't bother me nearly as much as the huge, clunky, Unity 2D.

Hopefully someone figures out a fix to this problem soon though, but I guess the Zenbooks are still fairly new computers.

---

### Post by markjohnson on 2012-10-29
Just to add my info, also using a UX32A, Ubuntu 12.10, I get the same problem with a black screen on boot. What I've been doing so far is to plug in an external HDMI monitor, than turn the internal monitor off and on again in the display settings.  This works until the next reboot.

---

### Post by cutekazuya on 2012-11-02
> **markjohnson said:**
> Just to add my info, also using a UX32A, Ubuntu 12.10, I get the same problem with a black screen on boot. What I've been doing so far is to plug in an external HDMI monitor, than turn the internal monitor off and on again in the display settings.  This works until the next reboot.

Here is a fix:

When the screen is blank and ubuntu is loaded (login sound), Press Fn + f1. This will put the laptop in sleep, press power to turn it back on. 

Once you have logged into ubuntu -

1) Download latest kernel 3.7rc3, download 4  .deb files:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/)

2) Install Kernel

Open terminal > CD Downloads/
sudo dpkg -i linux-*.deb
sudo reboot

Blank screen problem should be gone and suspend also works great. 

All fn keys work except wifi and brightness control

Let me know if anyone has a workaround for the brightness control

---

### Post by markjohnson on 2012-11-04
The 3.7 kernel solved the blank screen problem. However, the brightness control wouldn't work (altering manually using gnome-settings-daemon, as it works with 3.5), and suspend hung before completion.

---

### Post by PartitionTable on 2012-11-10
> **cutekazuya said:**
> 
1) Download latest kernel 3.7rc3, download 4  .deb files:

[http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v3.7-rc3-raring/)

2) Install Kernel

Open terminal > CD Downloads/
sudo dpkg -i linux-*.deb
sudo reboot

When I follow that link, there's more than 4 .deb files, what exactly am I supposed to download? Do I just download all the files on that page?

Here's the directory I see;

[IMG]http://i.imgur.com/2ZEE7.png[/IMG]

---

### Post by cutekazuya on 2012-11-17
You have to download 4 files

if you are using 32bit ubuntu than download 3 files ending with i386 and if you are using 64bit then 3 files ending with amd64

the 4th one is the following, regardless of 32bit or 64bit:

[linux-headers-3.7.0-030700rc3_3.7.0-030700rc3.201210310756_all.deb]("http://kernel.ubuntu.com/%7Ekernel-ppa/mainline/v3.7-rc3-raring/linux-headers-3.7.0-030700rc3_3.7.0-030700rc3.201210310756_all.deb")

> **PartitionTable said:**
> When I follow that link, there's more than 4 .deb files, what exactly am I supposed to download? Do I just download all the files on that page?

Here's the directory I see;

[IMG]http://i.imgur.com/2ZEE7.png[/IMG]

---

### Post by cutekazuya on 2012-11-17
after some digging around, i found a kernel that works perfectly:

1) download kernel

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/)

2) install it

Open terminal > CD Downloads/
sudo dpkg -i linux-*.deb
sudo reboot

make sure you are not using acpi_backlight=[I]vendor in /etc/default/grub

All the fn keys work with this kernel, yes fn + f5 / f6 for screen brightness as well.

[/I]The only other problem I had was I kept getting "System program problem detected", I just switched off the apport reporting:[I]

sudo gedit /etc/default/apport

[/I]change enabled=1 to enabled=0

---

### Post by PartitionTable on 2013-01-24
> **cutekazuya said:**
> after some digging around, i found a kernel that works perfectly:

1) download kernel

[http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/](http://kernel.ubuntu.com/~kernel-ppa/mainline/drm-intel-experimental/2012-10-20-quantal/)

Anyone else had any luck with this kernel?

---

### Post by stonedmind on 2013-03-30
Hey guys. I have the same laptop. But get really annoying trouble with Ubuntu. Its all time get freezes. Maybe someone know what is it.

---

### Post by cl17g on 2013-04-05
Hi,

You seem fairly happy with the kernel 3.7 (there should be 3.8, now... even better?). I wouldn't mind to adjust brightness not using the Fn keys. What I am worried about is if everything else works or not. At the moment I am a bit confused. I am interested in a[SIZE=2]n Asus UX32VD-R4002P[/SIZE], but I still don't know if Ubuntu is working on it (and of course I do not intend to use Windows instead!).

What is the state of the art? Any suggestion? Should I wait for new kernels (newer than 3.8)?

Thank you

---

