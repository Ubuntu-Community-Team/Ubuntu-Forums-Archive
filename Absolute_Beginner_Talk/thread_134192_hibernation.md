---
title: "hibernation"
date: 2006-02-21
forum: Absolute Beginner Talk
---

### Post by inovermyheadd on 2006-02-21
Whenever I try to hibernate my notebook it looks like it is going to recover the image...but after the progress hits 100% my screen goes blank and it locks up.  Anyone else having this problem?

I appreciate it!

Donald

[My computer specs]("http://www.powernotebooks.com/specs/PowerPro/g3-11.php")

---

### Post by JELaVallee on 2006-02-21
[QUOTE=inovermyheadd]Whenever I try to hibernate my notebook it looks like it is going to recover the image...but after the progress hits 100% my screen goes blank and it locks up.  Anyone else having this problem?
[/QUOTE]

Couple of things to check... I just had similar issues with my install of Breezy on a Thinkpad T43p...

For clarification, I'm assuming that 'hibernate'='suspend-to-disk' and that 'sleep'='suspend-to-memory' and it sounds like you're trying to get actual hibernate to work and it's freezes on the recovery from disk suspend.

First, are you running ACPI (the more advanced/stable power management system modules/interfaces)?  

This can be confirmed by typing the following in a terminal window:
```
lsmod | grep acpi
```

[The first command (lsmod) is for listing (ls) your currently running system modules (-mod).  The second command after the pipe-| (grep acpi) is for taking lsmod's output and only capturing the lines that have 'acpi' in them.] 

If this returns with a list of various '_acpi' module names, then you're system is loading acpi modules, but there's something wrong with the handling of the recovery phase.

Also, check your grub boot menu configuration like so:
```
username@machine-name:~$ cat /boot/grub/menu.lst | grep kernel
# kernel        /vmlinuz root=/dev/hda2 ro
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## primary kernel menu item.
## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
title           Ubuntu, kernel 2.6.12-10-686
kernel          /vmlinuz-2.6.12-10-686 root=/dev/sda9 ro quiet
title           Ubuntu, kernel 2.6.12-10-686 (recovery mode)
kernel          /vmlinuz-2.6.12-10-686 root=/dev/sda9 ro single
title           Ubuntu, kernel 2.6.12-9-386
kernel          /vmlinuz-2.6.12-9-386 root=/dev/sda9 ro quiet
title           Ubuntu, kernel 2.6.12-9-386 (recovery mode)
kernel          /vmlinuz-2.6.12-9-386 root=/dev/sda9 ro single
kernel          /memtest86+.bin

```

Yours may look different, but the important thing to look for are the lines with the pattern 'kernel /vmlinuz-2.6.XXX..."  In particular, if you see the flag 'splash' and/or 'acpi=off' at the end of those lines, you should try editing that file (use gedit via Application->Accessories->Text Editor) to remove both such entries for all your kernel entries.  BEFORE modifying the menu.lst file, be sure to make a backup of it, so that you can recover should you make a mistake/type-o.

'splash' will remove the "pretty Ubuntu" logo and boot list and just show the boot console on login, but it's known to affect hibernation recovery and was a problem for me.

Now you just need to reboot and test the hibernation again.

Let us know if you have any issues.

cheers,
Etienne

---

### Post by inovermyheadd on 2006-02-21
Hey Etienne thanks for the help.

The Good news is that removing the splash screen allowed the hibernation to work!

The Bad news is that when I recover from hibernation something wrong happens to my video.  The screen is full of scanlines and it is difficult to read stuff on my computer.

If I restart my computer everything goes back to normal minus the splash screen.

Is this weird?

I only removed the "splash" like you recommended

[PHP]title		Ubuntu, kernel 2.6.12-10-686 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro quiet
initrd		/boot/initrd.img-2.6.12-10-686
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-686 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-686 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-686
boot

title		Ubuntu, kernel 2.6.12-10-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro quiet
initrd		/boot/initrd.img-2.6.12-10-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-10-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-10-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-10-386
boot

title		Ubuntu, kernel 2.6.12-9-386 
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro quiet
initrd		/boot/initrd.img-2.6.12-9-386
savedefault
boot

title		Ubuntu, kernel 2.6.12-9-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.12-9-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.12-9-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin  [/PHP]

Does something look odd?

---

### Post by inovermyheadd on 2006-02-22
bump :-)

---

### Post by JELaVallee on 2006-02-22
[QUOTE=inovermyheadd]bump :-)[/QUOTE]
Sorry,

{Dealing with a sick child and a deadline on a project... sigh...}

Your menu.lst looks fine now... that display crapping out issue sounds like something fishy with your x-session or display drivers not recovering properly.

What's the hardware you're notebook has for video/display?

cheers,
Etienne

---

### Post by JELaVallee on 2006-02-22
[QUOTE=JELaVallee]
What's the hardware you're notebook has for video/display?
[/QUOTE]

Nevermind, I followed your spec link (nV 6600 mobile... NICE CARD)...

So, do you have nvidia drivers installed for your card or are you running with the default that ubuntu installed?

You could also try doing a restart of your x-session/server by doing a ctrl-alt-backspace.  This isn't a solution, but if your x-server comes back up clean, then we can narrow it down from there.

silly ions,
Etienne

---

### Post by inovermyheadd on 2006-02-22
ok, well...the x session/server restart removed the scanlines on the 2nd attempt.

As for the video drivers I have version:  1.0-7667

---

### Post by JELaVallee on 2006-02-24
[QUOTE=inovermyheadd]ok, well...the x session/server restart removed the scanlines on the 2nd attempt.

As for the video drivers I have version:  1.0-7667[/QUOTE]

I think this will do the trick for you:
[https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend](https://wiki.ubuntu.com/NvidiaLaptopBinaryDriverSuspend)

Lacking an nVidia card/install of breezy, I'm unable to test this, but the symptoms sound very similar to yours.

For confirming whether you're using the binary nVidia drivers for X or the open source ones, you can check your X config like this on the command line:
```
$ cat /etc/X11/xorg.conf|grep Device

```

This should dump all of your device entries (including input devices), one of them will be the video device and will either be "nvidia" (official nVidia binary driver) or "nv" (open source driver).

Let us know if this helps.

cheers,
Etienne

---

### Post by inovermyheadd on 2006-02-25
Thanks Etienne,

that did do the trick!:)

---

### Post by JELaVallee on 2006-02-27
[QUOTE=inovermyheadd]Thanks Etienne,

that did do the trick!:)[/QUOTE]

Cool!  Glad to be of help.

And this benefits me because I just got an nVidia 6600GT for my desktop Breezy /Dapper system and gave me a good reason to read up on nVidia support/config.

cheers,
Etienne

---

### Post by cward002 on 2006-04-18
[QUOTE=JELaVallee]Cool!  Glad to be of help.

And this benefits me because I just got an nVidia 6600GT for my desktop Breezy /Dapper system and gave me a good reason to read up on nVidia support/config.

cheers,
Etienne[/QUOTE]
I am having similar problems when my satellite P25 comes out fo hibernation. It boots back up fine but the screen remains dark although I can see enough to know that it has loaded the login screen but I cant see the screen well to do anything else. I have tried re-booting, re-starting the X session etc. I dont think the backlight is gone as the laptop is only two years old. I am running Breezy. Thank you for any assistance

---

