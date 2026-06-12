---
title: "Hidden Second Operating System / Wireless from LiveCD"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by mdavison20 on 2008-02-12
I have a Dell Inspiron 6000

Ok, I  have two quick questions.

Can I dual boot my computer but make it so that no one would be aware that Ubuntu is installed? Like I have to hit some key combination to make it come up, otherwise it will boot like normal and if anyone starts my computer they wouldn't be aware of it?

Also, for the liveCD, is it fairly simple to get it to work with a wireless card already built into your computer? I will be using the computer wirelessly from a LiveCD so having internet access when booted is essential.

---

### Post by seventhc on 2008-02-12
If it's like your parents computer, I'd be carefu,l if you make a mistake during install, Windows will be gone. It is easy to install but for some reason it seems most people just click next without reading anything.
You would first have to create a partition for ubuntu. Wouldn't they notice there drive got smaller somehow? lol

The live cd should pick up your wireless, just boot from it, it doesn't install unless you tell it to. It is completely safe to run the live cd to see what hardware will work.
If it works on the live cd then it should also work when installed.

---

### Post by Ek0nomik on 2008-02-12
> **mdavison20 said:**
> I have a Dell Inspiron 6000

Ok, I  have two quick questions.

Can I dual boot my computer but make it so that no one would be aware that Ubuntu is installed? Like I have to hit some key combination to make it come up, otherwise it will boot like normal and if anyone starts my computer they wouldn't be aware of it?

Also, for the liveCD, is it fairly simple to get it to work with a wireless card already built into your computer? I will be using the computer wirelessly from a LiveCD so having internet access when booted is essential.

You can have it so that your computer will boot into Windows by default.  When the grub menu shows up you can just move your arrow down to select Ubuntu, but you can have Windows be the default.  I suppose you could give Ubuntu a secret name like '.', so nobody would know what that was.  But, you can't have a secret key combination from what I am aware of.

Regarding the wireless, what kind of wireless card is it?  You don't need wireless when using the Live CD, all the packages it installs are on the disc itself.  If you are unaware of what wireless card you have, loading Ubuntu and going to Accessories/Terminal and typing in the following should reveal it:

```
lspci
```

You can just post the entire output onto the forums if you are unaware of how to read the output you got.

---

### Post by dca on 2008-02-12
Hmmm, Windows is designed (LOL!) to be the only OS on your computer.  That's pretty much where GRUB comes in giving you the ability on multi-booting or selecting kernel-specific start-ups...  There's no special key-combo or hack you can use where a shift can be made where the PC or laptop starts up normally w/ the Windows splash screen and then switch...

---

### Post by mdavison20 on 2008-02-12
what about having the computer boot in command startup? when you hit like f2 or something, it gives you various options to boot your system, is there a way that I can start ubuntu through a command line? And from the option of which OS to boot, just reduce the time that is shown to like 0 seconds, so it shows up but quickly moves on?

---

### Post by dstew on 2008-02-12
Add the command **hiddenmenu** to the file /boot/grub/menu.lst in the top area (above the timeout line would be good) and the menu won't show up, it will just go to the default OS, which you can make to be Windows. If you press the escape key during the timeout interval, the menu will pop up.

---

### Post by PeterJS on 2008-02-12
This really isn't as compex as every one is making it. You can install grub, just like a normal dual boot, after it's installed you can go in to it's configuration and set the default OS to windows, set the gub menu to automatically hide itself, and then set the time out window to activate the grub menu with the ESC key to something nice and short like 1 or 2 seconds.

---

### Post by dca on 2008-02-12
> **PeterJS said:**
> This really isn't as compex as every one is making it. You can install grub, just like a normal dual boot, after it's installed you can go in to it's configuration and set the default OS to windows, set the gub menu to automatically hide itself, and then set the time out window to activate the grub menu with the ESC key to something nice and short like 1 or 2 seconds.

Ah ha, but if it's not his system and he's trying to hide the install...???

---

### Post by PeterJS on 2008-02-12
Is you average person really going to notice the gub loading messages and a one or two second delay in the boot process?

---

### Post by Moop on 2008-02-12
Can't you just not install grub and put it on a cd that you would boot from?

---

### Post by dstew on 2008-02-13
Or, you could just make a grub floppy and boot from there.

---

