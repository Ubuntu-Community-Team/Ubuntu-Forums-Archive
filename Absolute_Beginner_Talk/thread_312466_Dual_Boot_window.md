---
title: "Dual Boot window"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by urk_nono on 2006-12-04
So, does anyone know of a nicer looking log-in window when choosing between your OS? I loathe that hippy black&white login-window I get when starting up. I remember when my friend installed gentoo at my computer, there was a nice looking purple-ish window. If anyone knows of a way, could you redirect me? :)

---

### Post by Chinkostu on 2006-12-04
theres a commented out section in menu.lst if you're using GRUB

```

## Pretty colours
#color cyan/blue white/blue
```

just uncomment the color :)

---

### Post by urk_nono on 2006-12-04
> **Chinkostu said:**
> theres a commented out section in menu.lst

```

## Pretty colours
#color cyan/blue white/blue
```

just uncomment the color :)

Woah, thanks for fast reply! I'll get down and dirty :mrgreen:

---

### Post by Chinkostu on 2006-12-04
notice my quick edit for if you're using GRUB (which i assume is so)

do you know how to get in there and edit it?

---

### Post by urk_nono on 2006-12-04
> **Chinkostu said:**
> notice my quick edit for if you're using GRUB (which i assume is so)

do you know how to get in there and edit it?

Yesh, messh Money Penny. Mosht quick editing indeed.

Nope, no clue. I'm not even sure what Grub is ](*,)

---

### Post by Chinkostu on 2006-12-04
haha

```
gksudo gedit boot/grub/menu.lst
```

:)

i suppose i should have said, GRUB is the default boot manager thingy for Ubuntu, its installed when you install Ubuntu. so unless you installed a different one, it should be grub.

---

### Post by compmodder26 on 2006-12-04
You can also add a splash image to use in the background.  There are a few you can use at [gnome-look.org]("http://www.gnome-look.org/content/search.php?&search=1&type=0&name=grub&user=&text=&sort=0&scorefilter=0&licence=99&page=0").

To use them, just download and copy the file to your /boot/grub directory.

Then do:
```
sudo gedit /boot/grub/menu.lst
```

And add this (commented parts aren't necessary) (I usually put it after the hiddenmenu entry):
```
splashimage=(hd0,0)/boot/grub/*file_you_copied*
# Change (hd0,0) to match the location /boot
# Example: if /boot is on hda1 then you use (hd0,0)
#          hda2: (hd0,1)
#          hdb1: (hd1,0)
#          hdb2: (hd1,1)
#          etc......
```

---

### Post by Chinkostu on 2006-12-04
> **compmodder26 said:**
> You can also add a splash image to use in the background.  There are a few you can use at [gnome-look.org]("http://www.gnome-look.org/content/search.php?&search=1&type=0&name=grub&user=&text=&sort=0&scorefilter=0&licence=99&page=0").

To use them, just download and copy the file to your /boot/grub directory.

Then do:
```
sudo gedit /boot/grub/menu.lst
```

And add this (commented parts aren't necessary) (I usually put it after the hiddenmenu entry):
```
splashimage=(hd0,0)/boot/grub/*file_you_copied*
# Change (hd0,0) to match the location /boot
# Example: if /boot is on hda1 then you use (hd0,0)
#          hda2: (hd0,1)
#          hdb1: (hd1,0)
#          hdb2: (hd1,1)
#          etc......
```

wow cool! thanks!

---

### Post by urk_nono on 2006-12-04
Thank you both. Most appreciated! :mrgreen:

---

### Post by urk_nono on 2006-12-04
> **compmodder26 said:**
> 
And add this (commented parts aren't necessary) (I usually put it after the hiddenmenu entry):
```
splashimage=(hd0,0)/boot/grub/*file_you_copied*
# Change (hd0,0) to match the location /boot
# Example: if /boot is on hda1 then you use (hd0,0)
#          hda2: (hd0,1)
#          hdb1: (hd1,0)
#          hdb2: (hd1,1)
#          etc......
```

I can't seem to load the picture when booting. When I installed Ubuntu, I had two Partions: C: and D: For Ubuntu I made another partion from D:
Now, I'm not sure wheter to jot in (hd0,1) or something else.. Got any clue?

---

### Post by ron999 on 2006-12-04
Wow compmodder26
That gnome-look site's ok.
I've now got a GRUB menu with Che - just like my avatar!
:p :) :cool: 
[http://www.gnome-look.org/content/show.php?content=35754]("http://www.gnome-look.org/content/show.php?content=35754")

---

### Post by ImmigrantUS on 2006-12-04
Hey everybody! 

 I'm not originator of the thread, but would like to edit GRUB Login window as well.

     To Chinkostu:

  [COLOR="Red"]?[/COLOR] - Where to do I need to put this code -> [gksudo gedit boot/grub/menu.lst] to uncomment the color?

  [COLOR="Red"]?[/COLOR] - And where to do I need to put this code -> [## Pretty colours
#color cyan/blue white/blue] to actually uncomment it? Or is there a check box to be unchecked? Or whatever? 

  [COLOR="Red"]?[/COLOR] -  Are there other colors available, beside White/blue (read - Windows-like)?

      To: Compmodder26:
 
  [COLOR="Red"]?[/COLOR] - By splash image, do you mean it'll be a background of that Login screen? Or it'll be before or after that Login screen?

  [COLOR="Red"]?[/COLOR] - Can I download on other PC, then put file on Ubuntu PC(not yet connected to Internet) by USB stick or floppy?

  [COLOR="Red"]?[/COLOR] - And where to do I need to put this code -> [sudo gedit /boot/grub/menu.lst] to add those downloaded splash images?

   Thank you all! Good luck!

-----------------
P.s. Stupidity never ends! But... Hell, we are in it together ;-)

---

### Post by Chinkostu on 2006-12-04
go to applications, then terminal. sorry, should have explained!

for the splash screen, you need to put whatever hard drive has ubuntu on it. mine is (1,2)

---

