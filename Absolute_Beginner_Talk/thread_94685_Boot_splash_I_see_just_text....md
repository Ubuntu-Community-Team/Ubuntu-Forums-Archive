---
title: "Boot splash? I see just text..."
date: 2005-11-24
forum: Absolute Beginner Talk
---

### Post by doyenne on 2005-11-24
I installed Ubuntu Breezy from CD. At the end of the installation, it configured GRUB. Now I see a boring black-and-white text screen where I can choose which OS to boot. 

I used to run Mandrake 10.0 which installed a nice graphical boot menu (using lilo). Is it possible to have such a nice graphical boot selection with Ubuntu?

---

### Post by thomas.mcmahon on 2005-11-24
Haha it's not boring man its &#252;ber1337!

Sorry though I don't know how to fix your problem.

---

### Post by endy on 2005-11-24
Perhaps this thread could be what you are looking for:

[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

Bear in mind it's written for the older version of Ubuntu and may not work as expected and as this is editing grub you could end up with a machine that doesn't boot.

---

### Post by Brunellus on 2005-11-24
I have never known anything other than text GRUB screens, so I don't know what to tell  you.

if you want mandrake, you know where to find it.

---

### Post by Sionide on 2005-11-24
[http://ubuntuforums.org/showthread.php?t=30341](http://ubuntuforums.org/showthread.php?t=30341)

This is definately what you need. I did this and now I have the coolest Ubuntu background with a Tux I added myself - it rocks. I have attached it to this post.

---

### Post by doyenne on 2005-11-25
Well, of course I do not want to go back to Mandrake :) 

I followed the given links but again I am warned that perhaps my system won't boot anymore... :confused: 

I thought Ubuntu was even better for beginners than Mandrake so I had expected a nice boot screen automatically. Well, at the end of the installation I saw sth about GRUB and lilo -- I don't know why GRUB was installed instead of lilo. In fact I have never used GRUB before (only lilo); is there a reason why GRUB is chosen? Is it perhaps less difficult to have a graphical boot screen when using lilo?

---

### Post by endy on 2005-11-25
Grub has a number of advantages, the two I always think of are that once you edit the config you don't have to run anything to make the changes active like you do with lilo. The second, and my favourite, is that you can edit the boot config from the grub menu before the OS boots, that's saved my ass a few times :)

---

### Post by Darrin on 2005-11-25
As for me, I can really care less if its a text or graphical boot manager. But I guess graphical would make it prettier.  I suppose if its easy and safe enough to do, then why not go for it. I know OS such as Linspire has a nice blue background with the linspire logo on it.

---

### Post by Schmots on 2005-11-25
Ok, here is my grub config

# Nice, fat splash-image to spice things up :)
# Comment out if you don't have a graphics card installed
splashimage=(hd0,0)/boot/grub/splash.xpm.gz

and here is what it says

splashimage(this lets grub know to use this splace image)=(hd0,0)((first harddrive first partition, /boot in my case)/boot/grub/splash.xpm.gz(full path to the grub splash screen)

now I have never made a splash screen just downloaded others, so I can't help you with a custom one, but I hope at least the proper config line helps.

---

