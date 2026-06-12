---
title: "ATI Help!"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by stuart_75 on 2007-07-10
Ive just swapped my nvidia to an ATI card, had trouble getting the resolution right, tried running xserver lots of times, no success. Then I mucked about with "gksudo gedit /boot/grub/menu.lst"

Now I can only get a black screen when booting up. Running xserver doesnt work whatever settings I choose.

Tried the recovery console, but cant seem to be able to edit the file.

Getting desperate now. Please can anyone help!

Thanks!!!!!!!!!

---

### Post by twiceasworn on 2007-07-10
before doing all of this did you backup your xorg.conf file?

---

### Post by stuart_75 on 2007-07-10
Dont think so. I think the problem is in the framebuffer resolution code. But I could be wrong.

I want to edit the file at the recovery console, but gedit seems to be the only way I know how to edit files.

---

### Post by stuart_75 on 2007-07-11
Bump!

---

### Post by xerox on 2007-07-11
If you still have the Ubuntu LiveCD, you could use to to restore any bad changes to your GRUB,  armed with a GRUB guide off the internet, of course.

Now about the ATI card, what kind do you have? I have an ATI card too, and normally (unless if I am playing a wined windows game that mucks around with my screen resolution) everything works fine. Do you actually have an ATI graphics card, or do you use something else? From what I understand, you used to have an nvidia and, by yourself switched it to an ATI?

---

### Post by stuart_75 on 2007-07-12
Its a ATI Radeon 9200SE. I have a copy of the Live CD if that helps.

---

### Post by smellysocks on 2007-07-12
It's probably not much help but I use the same card in my machine and have had no problems. I installed the lot with the card already in though.

I'm still newbie and pants with ubuntu so probably best to ignore me but is it something to do with your machine still expecting/being set up for the nvidia card?

---

### Post by stuart_75 on 2007-07-12
Ive had the card working before, but have swapped between nvidia & ATI several times.

Its just when I edited that damm file is when things went wrong. Can I restore default settings with the live CD if so how?

---

### Post by stuart_75 on 2007-07-14
Its a Radeon 9200SE, but I dont think its the hardware thats causing the problems. 

I really need a fresh install of grub or need to edit the menu.lst from the recovery console.

Can anyone tell me how to do either??

---

### Post by stuart_75 on 2007-07-15
Bumping this again, as Im desperate for a solution. Im stuck with XP now and that sucks!

---

### Post by w4ett on 2007-07-15
Try this thread:

[http://ubuntuforums.org/showthread.php?t=210820](http://ubuntuforums.org/showthread.php?t=210820)

Then when you get Grub working again, from the terminal reconfigure your xserver and select ati as your driver and select your desired resolution/refresh rates.

sudo dpkg-reconfigure -phigh xerver-xorg

---

### Post by stuart_75 on 2007-07-17
OK, ive reinstalled GRUB, but still getting nowhere. 

Black screen as soon as I select ubuntu from the boot screen.

I can boot with the recovery console fine. I just want to edit the menu.lst file and try a few different values on the screen resolution code. Cant run gedit, wont run. Booted the live cd ok, dont know what to do with it.

I just want to edit the damm file, is that so difficult to do?

Thanks!

---

### Post by CautionaryX on 2007-07-17
boot into recovery console and type this after login to manually change your resolution settings:

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Irony on 2007-07-17
See here for restoring grub, though I don't know why you would mess with grub to adjust a graphics card;

[http://ubuntuforums.org/showthread.php?p=2957094#post2957094](http://ubuntuforums.org/showthread.php?p=2957094#post2957094)

---

### Post by stuart_75 on 2007-07-17
I think I maybe getting grub and gnome mixed up (noob).

Still no luck, im gonna give the nvidea a try again, and maybe try and post a printout of my xorg and menu.lst files for you guys to chew over.

Thanks for the help so far.

Stuart.

---

### Post by stuart_75 on 2007-07-18
OK, Ive put the Nvidea card in, ran xserver a few times, ran Envy, now everthing is ok. Thank god for that.

The Ati card is now in the bin. Thanks for all the advice.

Stuart.

---

