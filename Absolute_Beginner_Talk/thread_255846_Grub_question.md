---
title: "Grub question"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by demonoid on 2006-09-12
How can i make my GRUB look like [that]("http://www.vivalinux.com.ar/var/img/dist/viva_grub_grafico_ubuntu.jpeg") !
Thank you in advance !

---

### Post by kidders on 2006-09-12
Nice, isn't it! :-)

The thing to google is "grub splash". Basically, you can create a nice-looking splash screen, tell grub about it and off you go! You'll need a fairly smart graphics utility to do it though, because grub is fussy about the file format you use.

Install ImageMagick (it's very *very* nice) and something to draw pictures with. Many people mention Gimp, but I **hate** it lol. Then take a peek at [http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB](http://gentoo-wiki.com/HOWTO_Splash_image_in_GRUB) or any other grub/splash HOWTO of your choice. (Can anyone replace this link with one from Ubuntu's forums maybe?)

Hope that helps.

**Edit: Added a translation to Ubuntu speak for the above URL:**

To install on Ubuntu:

```

# gzip ImageName.xpm
# mv ImageName.xpm.gz /boot/grub/
# nano -w /boot/grub/menu.lst

```

Add this to the top:

```
splashimage=(hd0,0)/grub/ImageName.xpm.gz
```

**PLEASE NOTE:** If you've never tried this before, be fully prepared to break your bootloader! If you don't know how to deal with such irritations, don't try!

---

### Post by Herman on 2006-09-12
I don't know of a Ubuntu-specific splashimage help, but I have included a link to an excellent Red Hat grub-splash how-to in my Grub Page and then given a few tips about how to modify it to suit Ubuntu, [Click Here]("http://users.bigpond.net.au/hermanzone/p15.htm#splash").

Having a [Super Grub Disk]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html") handy would be a good precaution, yes, messing with splashimages can make your system unbootable, at least unbootable the way we're used to booting. There are lots of other ways to boot though. [Command Line Grub]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")  Have Fun!

Regards, Herman :D

---

### Post by demonoid on 2006-09-12
kidders  i make how you said but when i reboot and start grub it gives me a error "Failed to read splash image ((hd0,0))/grub/buba.xpm.gz"
Why it gives me that error the pic is 640X480 ziped xpm ?

---

### Post by moore.bryan on 2006-09-12
*from what i've read, a quick way to do this is to take any image you have and in a term ```
convert -resize 640x480 -colors 14 image_name.png image_name.xpm && gzip image_name.xpm
``` and then do all the stuff in the menu.lst file.*

---

### Post by Average Joe on 2006-09-12
The splash image will only give you a background at the boot stage. If you really want to have a bootscreen like you mentioned in your first port, you will need to do that with gfxboot.

Check: [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

---

### Post by elchinovi on 2006-09-12
> **demonoid said:**
> kidders  i make how you said but when i reboot and start grub it gives me a error "Failed to read splash image ((hd0,0))/grub/buba.xpm.gz"
Why it gives me that error the pic is 640X480 ziped xpm ?

What about where it says "(hd0,0)"... you have to modify that accordingly to your system partitions in case if you have a dual boot...
I might be wrong, but I was playing with the splash image last night, and it took me a little while to get the image in the right format, and the right path to the image on tne menu.lst
Buena Suerte!
;) 
El Chino.

---

### Post by Average Joe on 2006-09-12
I think when you name your image splash.xpm.gz and put it in the /boot/grub/ directory, then all you have to do is:

sudo update-grub

and it works. If it does, grub will mention that it found your splash image.

---

### Post by moore.bryan on 2006-09-12
> **Average Joe said:**
> The splash image will only give you a background at the boot stage. If you really want to have a bootscreen like you mentioned in your first port, you will need to do that with gfxboot.

Check: [http://www.ubuntuforums.org/showthread.php?t=208855](http://www.ubuntuforums.org/showthread.php?t=208855)

*is that really the only way?  seems like there should be others... i am tempted to try gfxboot, though...*

---

### Post by Average Joe on 2006-09-12
> **moore.bryan said:**
> *is that really the only way?  seems like there should be others... i am tempted to try gfxboot, though...*

I guess there are others too. I tried the gfxboot by following the steps mentioned in the thread I linked to in my previous post. It is not that difficult and it worked well.

But I still haven't figured out how one can *fully* customize that screen (see my last post on that thread). So I went back to my old grub again and now I only have a simple boot splash image. I guess I am actually not so interested in what my screen looks like before I start using my computer :).

---

### Post by moore.bryan on 2006-09-12
*i hear you... but with everyone looking for "eyecandy..."  :-)*

---

### Post by Average Joe on 2006-09-12
> **moore.bryan said:**
> *i hear you... but with everyone looking for "eyecandy..."  :-)*

Eyecandy is nice, I agree :). But if I have to take the effort to get it to work, I should look exactly the way I want it, otherwise I don't want it at all. And the boot-stuff eye candy you don't see at all after your computer has booted up. But that is just my $0.02.

---

### Post by kidders on 2006-09-13
> **demonoid said:**
> kidders  i make how you said but when i reboot and start grub it gives me a error "Failed to read splash image ((hd0,0))/grub/buba.xpm.gz"
Why it gives me that error the pic is 640X480 ziped xpm ?

The answers to this already seem to be posted :-) Most important is to make sure the (hd0,.... part really does point to the right place.

---

