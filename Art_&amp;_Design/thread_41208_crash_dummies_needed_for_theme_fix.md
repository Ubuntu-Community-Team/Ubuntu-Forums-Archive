---
title: "crash dummies needed for theme fix"
date: 2005-06-12
forum: Art &amp; Design
---

### Post by bvc on 2005-06-12
[http://kwh.kernow-gb.com/~bvc/theme/gtk/Marcintesh_OS-L-GTK-Color_Pack.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/gtk/Marcintesh_OS-L-GTK-Color_Pack.tar.gz)
[http://kwh.kernow-gb.com/~bvc/theme/icons/Marcintesh_OS-L-Icon-Color_Pack.tar.gz](http://kwh.kernow-gb.com/~bvc/theme/icons/Marcintesh_OS-L-Icon-Color_Pack.tar.gz)
It's the old (from over  a year ago) Marcintesh_OS-L-GTK-Color_Pack
screenie
[http://kwh.kernow-gb.com/~bvc/theme/screenshots/Marcintesh.jpg](http://kwh.kernow-gb.com/~bvc/theme/screenshots/Marcintesh.jpg)

I honestly do not know if the theme is the prob. I have never seen a pixmap theme crash anything or things so much and not give output as to what the problem is.

I have mandriva 2005 le and ubuntu hoary. Both have been giving me trouble before I even started to repolish this theme and both are old installs but they were not locking up. Ubuntu hoary from warty beta (updated via apt) and mandriva 2005 le from ML-9.1 (updated via urpmi, mostly cooker). My old box has ubuntu hoary and no problem with these themes **but I'd like confirmation** that they are fine.

If you'd like to help I'd appreciated it, as would others that want these themes.
[COLOR=red]**I'm not talking about crashing just an app, or even just gnome, I mean hard sys locks where you have to presss the reset button.**[/COLOR] I sit here now on mandriva 2005 le in firefox with an updated for combobox [BBX-Mercury-L](http://kwh.kernow-gb.com/~bvc/theme/gtk/BBX-Mercury-L.tar.gz) from which marcintesh was made from without a problem. The updated combo boxes and code on both are the same. Also updated the spin buttons in marcintesh blue and green.

**Once** running gimp from a terminal said that there was an unexpected identifier 'UR' on line 544 of the gtkrc in marcintesh blue. This is the line
```
stretch			= TRUE
```
go figure
so I removed it and added it again and haven't got the error again, but still have sys locks.

_Apps that are run before the crashes and locks_
gnome-theme-manager
firefox (with tabs open)
nautilus
sometimes epiphany

once firefox locks and is killed, no other browser will start. The most output I've gotten from this is Segmentation fault from epiphany and firefox. It's usually then that the sys locks but if you Ctrl+Alt+Delete when firefox freezes you can 'usually' reboot fine.

Also, before I started with this I updated clearlooks to 0.6. This was the first time I had the crashed and locks with the browsers. But even after reverting to clearlooks0.5 and then messing with marcintesh weird things continue, now on 2 distros, and the new clearlooks was never on mandriva. I'm sure they are not directly related but I find it interesting that clearlooks 0.6.1 was thene release with fixes for the combobox. hmmmm....

Doubt I'll get any takers, but I just thought I'd ask. What started as a simple update to proper comboboxes and spinbuttons has turned into a 2 day frustration.

So now, I'll try and just plain remove combobox and optionmenu and maybe reinstall a linux. Yuk.

thx all!

---

### Post by bvc on 2005-06-12
I removed the combobox from the theme, started the gnome-theme-manager and got this```
*** glibc detected *** free(): invalid next size (fast): 0x08406390 ***
```
tried to start it again
```
end from FAM server connection
```
and agian
```
gnome-theme-manager
end from FAM server connection
Segmentation fault
```

then it locked

that's actually the gam_server
I'm beginning to wonder if something or the filesys is corupted on /dev/hdb8 which is my shared data (icons, themes, art, some music)

yesterday while these crashes took place, hdb8-share failed and I had to run fsck manually. Yeah, we know what that usually means....fsck wants to fry your data, so I continued the boot...then got that error again after the next freeze, so in frustration manually told fsck to fix everything it threw at me. Freezes continue.


I'll move my themes off of it, umount it, and comment it out of fstab and see  :-x 13GB of data

---

### Post by bvc on 2005-06-12
[update]
-someone confirmed the theme worked on their box and 2 distros

[update]
-I can't even tar_up data without kernel panics, so I've been removing crap I haven't touched in a year and slowly moving crap over to another partition.

[update]
-it seems the data was corrupted which eliminated half the data.
When I would untar a tarball I would get tons of bad timestamps, so I basically cleaned house and I'm starting fresh without that partition mounted til I make sure I didn't lose anything too important and and all is well. I've been using the marcintesh blue theme and haven't had any probs, yet, and the old box is still using it to.

....now that the weekend is wasted on this crap, I guess I can get to work now that I'm sick of the computer

---

### Post by Confuse on 2005-06-18
Somewhat off topic but, does anyone have a .deb of the new clearlooks 0.6.1? I'm afraid to compile it as it needs all sorts of -dev packages I don't have and I'm also afraid of overwriting the old theme. If anyone could make one, it'd be highly appreciated. Thanks.

Damian

---

### Post by Spark* on 2005-06-19
[QUOTE=Confuse]Somewhat off topic but, does anyone have a .deb of the new clearlooks 0.6.1?[/QUOTE]
It's in breezy.

---

### Post by Confuse on 2005-06-19
[QUOTE=Spark*]It's in breezy.[/QUOTE]

Is there a package compiled for hoary? I tried installing the breezy one but it stayed as a broken package, although the theme worked. But now I can't upgrade my package because of that broken package.

---

