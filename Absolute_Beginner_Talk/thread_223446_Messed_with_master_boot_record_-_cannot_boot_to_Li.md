---
title: "Messed with master boot record - cannot boot to Linux - oinly WinXP?"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by tjp.thomas on 2006-07-26
Hi there. I am new (obviously)... I just installed Ubuntu 6.06 and it went like a charm. Now my system is a dual-OS kinda one, which means that I for a while at least will be using both WinXP and Ubuntu. After installing Ubuntu I actually did have a dual-boot system running, however, I was not satisfied with the options listed so I decided to try a few alternatives... now only WinXP works; and I don't know how to get the Ubuntu boot manager back. For starters - that I was I am after... to get the Ubuntu boot loader back. Can you help me?

/tom

---

### Post by Kilz on 2006-07-26
[Take a look here ]("https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-5dbdd6b5302831ed4335bd0b7387ffcad2543857")for instructions.

---

### Post by tjp.thomas on 2006-07-26
Thanks a lot... Is there anyway that I can make WinXP my default selection?

---

### Post by greeneemer on 2006-07-26
> **tjp.thomas said:**
> Thanks a lot... Is there anyway that I can make WinXP my default selection?```
sudo gedit /boot/grub/menu.lst
```
Look for the *default* option and change it to the entry in the menu that you want to be selected by default. It the first uncommented option in the file, pretty high up. Just remember that it starts with 0, and that > title		Other operating systems:
root also counts as one.
So, if your list consist of two Ubuntu kernels, and two recovery modes to those, the memtest86, "Other operating systems" and then last Windows XP, then you should write ```
default 6
```

---

### Post by tjp.thomas on 2006-07-26
that I will test when I get home... you have described my boot-setup precisly.... so i guess "Default 6" it is.... THANKS

---

### Post by tjp.thomas on 2006-07-26
Sorry!!... but do you know if I can edit the mail.lst file so that I only have Ubuntu/Ubuntu safe-mode and WinXP?

---

### Post by greeneemer on 2006-07-27
Well, you can just delete/outcomment the entries you dont want.
```

#title		Ubuntu, kernel 2.6.15-26-386
#root		(hd0,1)
#kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
#initrd		/boot/initrd.img-2.6.15-26-386
#savedefault
#boot

``` (well, that was the newest kernel, but you get the idea)

A tip is also to uninstall those old kernels that you dont use (2.6.15-23 if I may guess)
Just open Synaptic and uninstall linux-image-2.6.15-23-386 (just make sure that you didn't boot from that kernel ;)) or whatever old kernels you have installed. Then you wont have anything else but the newest kernel, memtest86 and Windows XP in your list. Just remember to change your *default* value after you have uninstalled a kernel as that value isn't updated automagically.

---

### Post by tjp.thomas on 2006-07-27
Thanks for the feedback... I will try and see if this is do-able... will provide some feedback here later...

---

### Post by tjp.thomas on 2006-07-27
It Works... Thanks A Lot!

---

