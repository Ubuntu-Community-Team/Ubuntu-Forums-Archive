---
title: "xubuntu install cd, grub &amp; kernel errors"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by armchaircritic on 2008-03-10
Hi all,

I was attempting to install xubuntu on an old laptop (met the specs for the 'alternate CD which I was using) and pretty much failed installing. I got some error messages such as grub missing and kernel unavailable etc. Sorry for the brevity but I'm new to this.

Since the laptop won't boot, can anyone give me advice about what I need to look at to get this working again? I don't want any hand holding just some advice about how I can install linux on this machine now. I read somewhere on this board in a similar thread from the search that compiling the kernel manually is the way to go?

Thanks very much for any replies.

---

### Post by ansicplusplus on 2008-03-10
Hy,
from your description I guess you tried a manual install and got only half of it through. 
You might be better of with a text-based installer if you are low on resources.

Try a fresh install using one of the mini.iso images. This is for gutsy-x86: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/)
They have a text gui and load all packages from the internet. Naturally this put's some load on your internet connection. You can also use a local server. Just mount a ubuntu dvd and make it available via http.

Yours, ansicplusplus

---

### Post by jesusfreak107 on 2008-03-10
Get [Puppy Linux]("http://www.puppylinux.org/user/viewpage.php?page_id=1"), it is a very light, ultra-fast, ultra-usable OS!  

(note: not an ad. I just like it a lot.)

---

### Post by Duck2006 on 2008-03-10
puppy linux or dsl linux both are small and will load on older systems.

---

### Post by armchaircritic on 2008-03-10
> **ansicplusplus said:**
> Hy,
from your description I guess you tried a manual install and got only half of it through. 
You might be better of with a text-based installer if you are low on resources.

Try a fresh install using one of the mini.iso images. This is for gutsy-x86: [http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/](http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/)
They have a text gui and load all packages from the internet. Naturally this put's some load on your internet connection. You can also use a local server. Just mount a ubuntu dvd and make it available via http.

Yours, ansicplusplus

Hi Ansicplusplus,

I was using the text based installer actually. Could it be the CD I burned the image to?


Thanks to the other posters, I will look into puppy linux and dsl linux.

---

### Post by jesusfreak107 on 2008-03-10
yes, it could be the CD.  I have never had a problem with mine, but I have heard that iso files are easily corrupted while burning them onto a cd.  so, unless you bought the CD, you might just try burning it again.  Or, you could just use Puppy.

---

### Post by ansicplusplus on 2008-03-11
Hi,
it 's not unusual that a fresh burned cd can't be read using an older cdrom. Some drives have increased difficulties when they or the media is getting warm after some install time. In those cases I burn the image using single speed. This does the trick mostly. An alternative is using the mini.iso. That image is so small that the cdrom hasn't much to read and will usually get it right.
Yours,ansicplusplus

---

### Post by armchaircritic on 2008-03-11
Hi All,

Well, after I botched that initial install, I'm having problems now with the PC refusing to boot from any CD. I did another CD and the lowest write speed. Anyone know where I go from here? 

The error I get on booting is something like

boot from CDROM.. Not found
...
error loading operating system


The PC is set up to boot from CD as the first source so I'm wildly confused as to what I need to do next.

Anyone who can give me some advice about this is a king among men :D

---

### Post by ansicplusplus on 2008-03-12
Hy,
well it seems to me that your cd drive is broken. For verification you can let him read an original (pressed) cd. Maybe a Knoppix cd from a magazine. As you have an old laptop the chances are pretty low to get a replacement drive. I recommend cleaning it carefully using a pressed air spray. Hopefully there is just some dust in the wrong places. 

However depending on what your bios offers you can still try to boot from an usb cd drive. Maybe someone can help you out with one of those usb dvdrw drives.
Another option could be to put the mini.iso on an usb stick. I never tried that for myself but since I can put a floppy image on an usbstick an boot it might be possible with a cd image, too.

Yours, ansicplusplus

---

