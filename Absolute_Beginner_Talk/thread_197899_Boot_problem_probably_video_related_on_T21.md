---
title: "Boot problem probably video related on T21"
date: 2006-06-16
forum: Absolute Beginner Talk
---

### Post by Lonestar on 2006-06-16
I am a first time Linux user and so far everything is going well with Ubuntu Dappper 6.06 install I did, except now I am having one problem.  During the Grub boot process at the time the Linux Kernel is starting the screen "hangs"...by searching the forum for my laptop I found this advice:

[INDENT]"Try to add "acpi=off apm=on" as a boot option in grub.  If the above does not work, try to add "noapic" as well."[/INDENT]

I discovered where I can edit the startup "boot option" in Grub by choosing one of the existing options and hitting E for edit, where I then added the above info.  It did work but I ran out of time before I had to take the train to the office to experiment further. 

 :?: My question is: does making the change, that I described above, make the additional statement (acpi=off apm=on noapic) permanent?  Or do I need to make the change to the file via terminal? If so, I would appreciate it if someone could explain which file and provide some quick instructions.

:?: Also, since this is video related, is there a driver that is optimized for my system that I could use?  If so, where do I find a video driver and how do I install it?

**My laptop info is**:

Thinkpad T21

[INDENT][LIST]
[*]CPU:  Intel Pentium III 800 MHz

[*]Video:  S3 Savage IX8  AGP 2X  8 MB SGRAM Video Memory 

[*]Display:  14.1" TFT  1024x768

[*]Memory:   512 MB Ram

[*]Hard Drive:  20 GB 2.5" HDD
[/LIST][/INDENT]

I have been reading this forum and I think it is a great resource.  Plus I was very pleasantly surprised how easy Ubuntu is to install and use, I may never go back to Windows.

Thanks!

---

### Post by rbalfour on 2006-06-16
edit the file /boot/grub/menu.lst

locate the kernel you boot and add the options.

ie (DON'T COPY and PASTE THIS! Your file may be different)
```

title           Ubuntu, kernel 2.6.15-25-686
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-686 root=/dev/hda1 ro quiet splash acpi=off apm=on noapic
initrd          /boot/initrd.img-2.6.15-25-686
savedefault
boot

```

---

### Post by Lonestar on 2006-06-16
Thanks rbalfour, I will give that a try when I get home tonight.  Follow-up though, you said "locate the kernel you boot..." being a "newb" is there only one choice? If not, how do I know which kernel?

Also do you, or anyone else reading this, have any advice on the video driver part of my orginal post?

Thanks again for your help.

---

### Post by rbalfour on 2006-06-16
when it boots hit "ESC" and you will see a boot menu.
Look at the selected kernel. that is the one you add it too.
Or if you miss the menu, look at that file, the one with savedefault is the kernel you boot with.

gl.

---

### Post by josephzacker on 2007-09-07
I am running a Thinkpad T21 2648 (Pentium III, S3, 384MB, 12GB), and I experienced the same video hangups until I did the following...

When GRUB begins to load, hit ESC
Select Recovery Mode
Type sudo nano /etc/X11/xorg.conf
Find the "Device" section
Add this line
Option        "BusType"         "PCI"
Save the file and exit
Reboot

That should fix your problem...

---

### Post by KenSpeedie on 2008-01-29
I saw josephzacker's reply.  I followed his direections and bingo - problem solved.

Thanks!

---

