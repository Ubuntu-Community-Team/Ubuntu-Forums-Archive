---
title: "Graphical Grub Menu"
date: 2007-10-05
forum: Absolute Beginner Talk
---

### Post by ferronica on 2007-10-05
Is there nice GRUB menu available for ubuntu 7.04 for dual booting XP and ubuntu other then simple Black and white :(

---

### Post by BrendanM on 2007-10-05
Check this out: [http://ubuntuforums.org/showthread.php?t=208855](http://ubuntuforums.org/showthread.php?t=208855)

---

### Post by molly_001 on 2007-10-05
I did not look at the thread above referenced by Brandon, but my guess is that it leads towards tutorials on changing the GRUB splash image.  That's a nice touch, that.  I use the following GRUB splash on a relative's triple boot:

[[IMG]http://img502.imageshack.us/img502/4273/grubcamut8.th.jpg[/IMG]]("http://img502.imageshack.us/my.php?image=grubcamut8.jpg")

---

### Post by nowshining on 2007-10-05
lolz u picked the photo lineup of Bill Gates when he was younger :P ROFLMAO

---

### Post by TeaSwigger on 2007-10-05
Hello ferronica,

There absolutely is. I don't mean to "talk down" in how I'm going to address your post, I'm only trying to make things as clear as possible without knowing your level of knowledge yet.

If you mean you'd like a background or something to spiff up the black and white screen where you choose which operating system to boot up in a dual boot computer, then you would need to make changes in what is called GRUB. That's what handles that part of your computer's start-up. There's a nifty little tool kindly made by Tomosaur called GRUBed, see this post:

[http://ubuntuforums.org/showthread.php?t=228104](http://ubuntuforums.org/showthread.php?t=228104)

Because there isn't much computing power at that point in start-up to work with, we're limited in what can be done visually. But I added a background picture for that screen on my sister's PC and she really likes it.

What is entailed is simply" adding one line as the very first line in a file "/boot/grub/menu.lst" This file is the GRUB configuration. Goofing this file up can leave your computer unable to boot, a tricky situation to fix if you don't know your way around all that stuff yet, so be *very careful* if making any changes at all in that file. You can edit it by opening it in a text editor like gedit with admin privilidges, so the command would be "gksu gedit /boot/grub/menu.lst." The line which adds the background my sis likes is this:

```
splashimage (hd0,4)/boot/grub/images/CRW_7206_14.xpm.gz
```

Note the (hd0,4). That tells it where the image is. Hard Drive (hd), the first one (0), the fourth partition. If this value is not right, it won't stop the show or anything; you'll get a warning that the image wasn't found, press any key to continue. So you'd just go ahead in and fix it. GRUBed I referred to above can guide you through this and make the change for you. The image is oh-so-memorably titled CRW_7206_14.xpm.gz. I think I got it in this package:

[http://packages.ubuntu.com/feisty/admin/grub-splashimages](http://packages.ubuntu.com/feisty/admin/grub-splashimages)

The colors of the text and the background can also be changed although the defaults work fine with that image so I left them alone. Anyways, that's a cool thing about linux, you can customize just about anything. :)

---

