---
title: "FluxBox"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by PPAAUULL on 2006-09-01
I am running Fluxbox on my old computer and I was wondering is there any good info on fluxbox and how to do stuff like change the desktop background and such?
Thanks so much for all the help.

---

### Post by croak77 on 2006-09-01
I use feh to set my background.

---

### Post by PPAAUULL on 2006-09-01
Where do I find that? Menu or what?

---

### Post by kerry_s on 2006-09-01
I would start with the flubox site itself( [http://fluxbox.sourceforge.net/docs/en/faq.php](http://fluxbox.sourceforge.net/docs/en/faq.php) ) I also did alot of googling for fluxbox tips. Fluxbox is a great desktop, i use the dapper server install + fluxbox setup. I use Eterm to set my backgroud and as my terminal( sudo apt-get install eterm ). For backdrop with eterm ( fbsetbg ~/.fluxbox/backgrounds/(name of pic) ).

---

### Post by bodhi.zazen on 2006-09-01
> **PPAAUULL said:**
> I am running Fluxbox on my old computer and I was wondering is there any good info on fluxbox and how to do stuff like change the desktop background and such?
Thanks so much for all the help.

Like kerry_s I use fbsetbg /path/to/image to set/change my background.

If you like the gui feel, check out rox. I use rox as a filer, but you can use rox to manage your background as well.

AKA rox-session

With rox session it is all point and click

---

### Post by croak77 on 2006-09-01
> **PPAAUULL said:**
> Where do I find that? Menu or what?

feh is in the repo's. It's a good image viewer that also sets background. To set a background; feh --bg-(scale,tile,seemless,center) /path/to/background.jpg. I don't care for fbsetbg. You might also want to install fluxconf. It includes a couple of program, fluxmenu, fluxkeys, and fluxconf.

---

### Post by gThree on 2006-09-01
Another vote for feh.  Very useful in other ways too.

---

### Post by An3Azz on 2006-09-21
If you use feh, the background is still gone after reboot and I have to set it manually, why?

---

### Post by Brunellus on 2006-09-21
see my sig for the ubuntu fluxbox howto

---

### Post by IYY on 2006-09-21
If you also want desktop icons, you could just install Rox-Filer. It comes with a desktop, which includes icons and the ability to change wallpaper.

---

