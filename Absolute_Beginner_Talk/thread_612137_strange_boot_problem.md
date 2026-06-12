---
title: "strange boot problem"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by Jeffie on 2007-11-13
When i turn off my computer with Ubuntu 7.10 and i start the computer on another time, my laptop acts very weird:

First he runs for 2 sec, i even don't get into grub, its only blank screen!! 
After this my computer turns off automatic, and after a couple of seconds he starts again automatic and starts up normally...

I have in another partition windows vista and when i turn off my computer with windows vista i don't have this problem!!

Can anyone help?

---

### Post by Paul820 on 2007-11-13
DON'T DO THAT COMMAND it will wipe your system.

---

### Post by Jeffie on 2007-11-14
Aargh, i did the command before the warning was posted!!!! Now i even cannot go into grub, is there any way i can go into windows? I have a live CD 7.10 but its not a boot cd, it only creats a boot if i start the cd in windows!! what a mess!

---

### Post by Paul820 on 2007-11-14
Oh no, that idiot has wrecked a few systems, i'm very sorry to hear he got you. Anyway, lets see if we can help you get it back to normal. What do you mean it only boots from within windows? Do you have your bios to boot from cd first and not the hard-drive? You can get to your bios by press one of the f-buttons, usually f11 or f2. What happens when your system boots, is grub still there? Or does it boot straight to windows?

---

### Post by Jeffie on 2007-11-14
problem is i can't go into linux neither windows because i can't go into "grub"
it says:
loading grub
error 15

my cd from ubuntu 7.10 i burned myself and it seems not to have boot quality's...

my cd from 7.04 can boot but the problem with this cd is that i cannot go into the ubuntu 7.04 desktop because of complication problem with graphic card.

---

### Post by Inxsible on 2007-11-14
Always make backups of the home drive. It helps a lot !

Unfortunately its pretty late for you now, but maybe in the future.

---

### Post by Paul820 on 2007-11-14
Is is possible for you to download and burn a disc? If you can there is the super grub disk that you can use to help fix your grub boot loader [http://supergrub.forjamari.linex.org/]("http://supergrub.forjamari.linex.org/")

---

### Post by Inxsible on 2007-11-14
+ 1 on the supergrub disk. That's the only way to correct a grub issue, if you cannot login to any of your OS'es :(

---

### Post by Jeffie on 2007-11-14
it is possible with other pc to burn a disc, i will try to download this super grub.

---

### Post by Inxsible on 2007-11-14
you could also try this link to restore your grub. Try this first and see if it works before downloading the supergrub disk

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RestoreGrub#head-bf3232f10ddf1b078de064622ccbb25225cdb3c0)

---

### Post by Jeffie on 2007-11-14
if i use fixmbr or fixboot with vista recovery, it might help?

---

### Post by Inxsible on 2007-11-14
Did you try the link I gave you earlier ?

FixMBR will probably remove your Ubuntu entries and boot you directly to Windows. Try the link I gave you, i think it will work

---

### Post by Paul820 on 2007-11-14
That will wipe out your grub boot loader so you will have to find some software for vista that will let you read linux partitions. I don't know if anything is available for vista that allows you to do that, you will have to look on the net.

---

### Post by tech9 on 2007-11-14
SuperGrub should get you working again... I had Grub Error 15 in the past, and fixed it will SuperGrub Disk

---

### Post by Jeffie on 2007-11-14
Anyway, i will just install windows vista again, it seems i will not lose my files if i do it like this, after installing windows i can go into linux with the 7.10 cd :-)...

But for further problems... Is it possible to just make a dual boot in the vista bootloader instead of using grub?

Like choosing
a) windows vista
b) grub (with ubuntu offcourse)

i tried a program (forgot the name) but it seems that when i selected ubuntu in the boot list he could not find the location...

---

### Post by Inxsible on 2007-11-14
> **Jeffie said:**
> Anyway, i will just install windows vista again, it seems i will not lose my files if i do it like this, after installing windows i can go into linux with the 7.10 cd :-)...

But for further problems... Is it possible to just make a dual boot in the vista bootloader instead of using grub?

Like choosing
a) windows vista
b) grub (with ubuntu offcourse)

i tried a program (forgot the name) but it seems that when i selected ubuntu in the boot list he could not find the location...
EasyBCD is what you are looking for. I havent used it since I am always in Ubuntu rather than Vista.But search for it and you will find a good how to.

---

### Post by tech9 on 2007-11-15
> **Jeffie said:**
> Anyway, i will just install windows vista again, it seems i will not lose my files if i do it like this, after installing windows i can go into linux with the 7.10 cd :-)...

But for further problems... Is it possible to just make a dual boot in the vista bootloader instead of using grub?

Like choosing
a) windows vista
b) grub (with ubuntu offcourse)

i tried a program (forgot the name) but it seems that when i selected ubuntu in the boot list he could not find the location...

yes

---

### Post by Inxsible on 2007-11-15
Here's the link which will help you set up Vista after you have installed Ubuntu.

[EasyBCD]("http://apcmag.com/5045/how_to_dual_boot_vista_with_linux")

---

