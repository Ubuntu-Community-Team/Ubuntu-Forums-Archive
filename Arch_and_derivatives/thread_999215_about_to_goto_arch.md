---
title: "about to goto arch"
date: 2008-12-01
forum: Arch and derivatives
---

### Post by EnGorDiaz on 2008-12-01
this is my checklist

will my ati radeon hd3450 driver work with driver installation and not fiddling around with my xorg server for hours on end e.g is there ati drivers i can download before installing arch... or can i just add the device to the xorg server easily



can i use the fluxbox wm is there an option in the cd 

xwinrap? with conky?

thats all i want to know :)

are there also resources for such questions i am asking?

---

### Post by kerry_s on 2008-12-01
do you even understand what arch is?

you'll be at command line at the end of your install, from there you must install EVERYTHING you want. forget "no fiddling" you have to do it the manual way, there is no gui to setup your vid.

start here:
[http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide](http://wiki.archlinux.org/index.php/Official_Arch_Linux_Install_Guide)

---

### Post by hrod beraht on 2008-12-01
> **EnGorDiaz said:**
> will my ati radeon hd3450 driver work
There are both two open-source drivers you can use, as well as the proprietary driver. See the [[COLOR="Blue"]ATI wiki article[/COLOR]]("http://wiki.archlinux.org/index.php/ATI") for more detail.

> **EnGorDiaz said:**
> ...not fiddling around with my xorg server
The newest version of xorg has hotplugging enabled by default. This is a fairly big change from the older versions, so make sure you read the [[COLOR="Blue"]xorg input hotplugging wiki article[/COLOR]]("http://wiki.archlinux.org/index.php/Xorg_input_hotplugging") to understand the new xorg. (or just read the *I don't want this crap, how do I turn it off?* section if you don't care about hotplugging)

> **EnGorDiaz said:**
> can i use the fluxbox wm is there an option in the cd
Yep, Fluxbox is available. However, I believe the CD only contains the base install and not any GUI's/desktop environments/window managers. After you have installed the base system from the CD and have your mirrors set up, you can just download/install Fluxbox using the pacman package manager by doing:
[LIST]
[*]pacman -Syu (update the base install first)
[*]pacman -S fluxbox
[*]pacman -S fluxconf
[/LIST]
See the [[COLOR="Blue"]Fluxbox section of the beginner's guide[/COLOR]]("http://wiki.archlinux.org/index.php/Beginners_Guide#Fluxbox"), as well as the [[COLOR="Blue"]main Fluxbox page[/COLOR]]("http://wiki.archlinux.org/index.php/Fluxbox").

> **EnGorDiaz said:**
> are there also resources for such questions i am asking?
Arch has a fabulous wiki.
Installing Arch isn't difficult, but I'll also reiterate what Kerry_S said above in that you should know that **you** make the decisions about what is included in your Arch installation. There is no default anything in Arch - GUI or otherwise. Definitely read the [[COLOR="Blue"]beginner's guide[/COLOR]]("http://wiki.archlinux.org/index.php/Beginners_Guide") as step 1.

Bob

---

### Post by handy on 2008-12-01
Follow the beginners guide to the letter & it is really enjoyable & quite easy.

Deviate & you could waste a lot of time or even decide that Arch is not for you, though this depends on your background knowledge slightly, as Arch is different than other Linux distro's in its structure.

---

### Post by OutOfReach on 2008-12-01
I cannot stress reading the installation guide + beginners guide enough.
Installing and configuring Arch can be a breeze or it can be your worst nightmare, as long as you follow the guides it will be smooth sailing.

---

### Post by EnGorDiaz on 2008-12-01
so do i install lynx a cli browser to acess the wiki? is that ok i know what arch is i know it comes with no desktop enviroment :P

---

### Post by EnGorDiaz on 2008-12-01
and then from so forth switching from tty1 to tty2(lynx brower open on that one)

thank you guys for these guides :)

---

### Post by OutOfReach on 2008-12-01
Actually I think that the guide comes with the CD. I just don't know what directory. Maybe if someone can fill in the blank here.

---

### Post by cardinals_fan on 2008-12-01
> **OutOfReach said:**
> Actually I think that the guide comes with the CD. I just don't know what directory. Maybe if someone can fill in the blank here.
Perhaps in /arch ?

---

### Post by MisfitI38 on 2008-12-01
> **cardinals_fan said:**
> Perhaps in /arch ?

Correct.

---

### Post by EnGorDiaz on 2008-12-02
guys i want to say thank you for all the help i also want to say when i read the wiki and it had a section on ati a heavenly choir played in my head and also the tutorials omg i think i had a nerdgasm this is really a great distribution

---

### Post by tcoffeep on 2008-12-02
> **EnGorDiaz said:**
> this is really a great distribution

this is true. :)

---

### Post by wesley_of_course on 2008-12-02
> **OutOfReach said:**
> Actually I think that the guide comes with the CD. I just don't know what directory. Maybe if someone can fill in the blank here.
   less /arch/beginnersguide.txt 
 change to vc/2 with <ALT>+F2  .  Page 7 of 64 ; under documentation . Enjoy

---

