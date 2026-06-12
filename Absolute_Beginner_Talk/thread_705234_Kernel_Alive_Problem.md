---
title: "Kernel Alive Problem"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by constantinos1987 on 2008-02-23
Good day to all

I am a complete beginner in the world of Linux and I need your advice

THE PROBLEM:

I have an installation problem when trying to install ubuntu 7.10 - server edition AMD64 on my new laptop. When pressing return on the "Install to the hard disk " option, the kernel loads and then I get a  screen with the note:

kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000

the installation won't go any further.

THE SYSTEM:

Proccessor: Intel Core 2 Duo Processor T7250 (4 MB Cache, 2.0 GHz, 800 MHz FSB)

RAM:            2048MB (2x 1024MB) DDR2 667 MHz

Hard Disk:    250GB (SATA 5400RPM)

Video Card: NVIDIA Geforce 8600M GT

No other Operating System. Just an empty machine with BIOS

WHAT I HAVE TRIED:

I tried the server edition for i386 architectures, but instead of an error message, it gets a completely blank screen, with the monitor still working.

I tried suggestions from other posts, but they wouldn't work either.


Anything I can do to fix this?

Thanks.

---

### Post by mrsteveman1 on 2008-02-23
My x64 server does the same thing (the kernel is supposed to do that on x64 systems), and keeps booting, so it sounds like a driver problem or perhaps something hanging the kernel.

So have you tried this kernel line?

```
vga=normal ide=nodma apm=off acpi=off noresume nosmp noapic maxcpus=0 edd=off single
```

This should disable a lot of things that cause problems and boot into single user mode. My guess is that this is a graphics problem, i seem to remember the nvidia 8600 series isn't as well supported but i may be wrong.

---

### Post by SOULRiDER on 2008-02-23
Arent core 2 duo processors 32bit? I dont think youc an isntall anything 64bit on a 32bit processor.


EDIT: I just read you tried the 32bit version and that you get some problems too. I know those video cards sometimes have problems but i dont see why they should affect you on a server edition install. As mrsteven pointed out, you probably have to disable some options.

---

### Post by mrsteveman1 on 2008-02-23
All core 2 duo chips support EM64T, its the core 1 duo chips that don't.

---

### Post by constantinos1987 on 2008-02-23
With the options you gave me, the installation continued and finished

The cd is ejected and a reboot initiates

But when this happens, the same error message is shown on the screen

kernel alive
kernel direct mapping tables up to 100000000 @ 8000-d000

I try to use the safe-mode, but it still crashes after some line of code.

Am I doing something wrong?

Thanks for all the help people!

---

### Post by mrsteveman1 on 2008-02-23
Ok, as far as the kernel is concerned, booting from the livecd and an installed system are identical, the same kernel gets loaded and the same modules should load as well.

I think you did hit on something though if the installation worked with the line i gave you. Now what you need to do is boot the livecd with each one of those options separately, and see which one it was that made the system work.

It shouldn't be hard to do the same thing on an installed system, the option can be added permanently to /boot/grub/menu.lst. You should be able to temporarily edit the boot line of the installed system as well, press escape when grub is loading, then press E to edit the boot selection, and add whichever option worked to the end of the kernel line.

Definitely test with the livecd though, just add each option separate till you see which one works.

for what its worth, the lines you are seeing aren't errors, they happen on all 64bit systems it seems. I'll digg through the kernel source and see what it means if i can't find it online.

EDIT: The mapping tables thing is printed to the screen when the kernel is first initializing, it has to do with the way the kernel accesses memory before everything else works. It's not an error, but im not sure why its printed to the screen.

---

### Post by constantinos1987 on 2008-02-23
I tried all of these options on their own.
None of these options solves the problem on its own.
I did get the following message though under acpi=0
_______________________________________________________________________

[	44.282480] ..MP_BIOS bug: 8254 timer not connected to IO-APIC
[	44.545038] PCI: Failed to allocate mem resource #6:20000@90000000 for 0000:0
1:00.0




kernel alive
kernel...
_________________________________________________________________________

And something that might seem trivial:
You have to keep the power-off button pressed for some seconds before you can close the machine, but that wasn't needed in the above message. It closed immediately

I guess I could check all possible combinations of the above options, but my knowledge of discrete mathematics -although limited- tells me that such an endeavor might not be very feasible...

I just hate it when I am THAT unlucky! But I am patient... And I want to try something different from Windows...

Thanks for the attention!

---

### Post by mrsteveman1 on 2008-02-23
Ok, work backwards and remove one thing from the line at a time until it STOPS working.

So making an intelligent guess, try doing nosmp maxcpus=0 and noapic together since they are related.

BTW, i believe the difference in the power off thing is that in real mode (when the bios still has a lot of control) the power button on some machines is a simple power off, while once the kernel boots the system uses ACPI to turn the machine off, which imposes the 4 second rule where you have to press it for a while.

---

### Post by constantinos1987 on 2008-02-24
The options that make it work are acpi=off and nosmp

When I was installing it, I had a BIOS like interface(I thought it was supposed to be more graphical)
Now that I run it, my only interface is a console. Shouldn't I have a GUI like Gnome?

Maybe I should reinstall with ONLY the above options?

Also, I was not connected to the Internet during installation.

---

### Post by mrsteveman1 on 2008-02-24
Since this is quite obviously a multi core machine it would be preferable to run with SMP on, and definitely don't want to leave ACPI off either but for the moment, if it works, good. I'm not sure why its not working but perhaps some debug information can be gotten so ubuntu devs can fix it later on.

If you installed with the desktop livecd you should now have a GUI desktop, if you don't you can check if gnome is even installed by doing this:

```
sudo dpkg --list | grep gnome
```

should return a bunch of stuff. 

to start gnome if its not running do:

```
sudo /etc/init.d/gdm start
```

I have noticed that the desktop installer will actually comment out the apt sources on the new machine if it cant find those sources during the installation, which is not good behavior for sure.

---

### Post by constantinos1987 on 2008-02-26
So I managed to Install Kubuntu 7.10 on my system. 
I still have to have no smp and acpi off.

In the beginning, I couldn't have a graphical environment because there were no drivers for my card
After a very hard time(for someone new like me) with the console, I managed to install the drivers.

Process of installing the drivers (in root):

Insert the Kubuntu install dvd
```
mount /dev/cdrom /cdrom
apt-get install build-essential
```
(installation begins for some essential header files for the system(for all I know))
unmount /cdrom

I insert the cd where I burnt  the drivers
```
mount /dev/cdrom /cdrom
cd /media/cdrom
sh NVIDIA....(whatever the name of the Driver)
```

installation begins and I followed each step.

After all this trouble I managed to have KDE

Now, I certainly don't want to have no smp(from what you told me and what I've read)

Is there any way I can provide any more information to you people to fix the problem?

Where can I get this debug information?

Maybe I should try a different distribution?

---

### Post by mrsteveman1 on 2008-02-26
I'll list some files that you perhaps should zip up and post or send to the ubuntu kernel developers. Some of these may not exist because the system renames log files when they get too big.


/var/log/kern.log
/var/log/kern.log.0
/var/log/debug
/var/log/debug.0
/var/log/boot
/var/log/faillog

There are other ways to debug the kernel but they are more complicated than just grabbing a few files from the system

---

