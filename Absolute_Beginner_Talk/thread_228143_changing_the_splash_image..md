---
title: "changing the splash image."
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by drosophyllum on 2006-08-02
I used to have two installed programs that would change my boot splash and my normal splash. But since I reinstalled I lost it. So im wondering if anyone has this or knows what it was. 

thank you

](*,)

---

### Post by shanepardue on 2006-08-02
i don't remember the name, but i'm sure if you type splash from synaptic or aptitude you'll be set!

---

### Post by drosophyllum on 2006-08-02
Im looking for the name, because im on my gentoo box right now.... :) 
.... btw splashy was the bootsplash on but i now need a normal splash changer.

.... Also does anyone kno whow to change the boot splash for lilo or grub as I see its one of its commands.

---

### Post by Indras on 2006-08-02
> **drosophyllum said:**
> Im looking for the name, because im on my gentoo box right now.... :) 
.... btw splashy was the bootsplash on but i now need a normal splash changer.

.... Also does anyone kno whow to change the boot splash for lilo or grub as I see its one of its commands.

To make Grub have a graphical look to it, use GfxBoot, here's the wiki on how to do it:
[http://doc.gwos.org/index.php/GfxBoot](http://doc.gwos.org/index.php/GfxBoot)
There's a bunch of themes at the bottom you can download, just replace message.suse with the one you download, and everything should work okay.  If you still have questions, nearly all of them are answered in this thread [here](http://www.ubuntuforums.org/showthread.php?t=208855).

To simply add a background to your grub menu, but keep the same layout and text type, use this page:
[http://ubuntuguide.org/wiki/Dapper#displaysplashimagegrub](http://ubuntuguide.org/wiki/Dapper#displaysplashimagegrub)

Similarly, your bootup screen, with the orange Ubuntu logo and scrolling text at the bottom teling you what is currently starting, can be changed with info here:
[http://ubuntuforums.org/showthread.php?t=82835](http://ubuntuforums.org/showthread.php?t=82835)

Note that for many of them, you're going to have to increase your screen size in order to make them show up correctly, otherwise you'll just get a black screen on bootup and shutdown.  I wrote a nice little tutorial on how to change your text-mode screen resolution here: [http://www.ubuntuforums.org/showthread.php?t=227513](http://www.ubuntuforums.org/showthread.php?t=227513)
If you set your screen to boot at 800x600 with at least 16 bit colors, you should have no trouble using any of the usplash images in the thread (search through the thread, there's like 12 pages of posts, and lots of nice usplash images you can use).

---

