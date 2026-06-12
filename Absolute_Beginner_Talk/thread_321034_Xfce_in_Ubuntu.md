---
title: "Xfce in Ubuntu"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by Big_Croc7 on 2006-12-18
Hi!

I've now installed Linux on two different systems; one is running Ubuntu, the other is running Xubuntu.  I've decided I like Xfce better than gnome, mostly because it's faster, and I'd like to install it on my Ubuntu system.  However, is there an easy way to do this other than installing the xubuntu-desktop package?  I'd like to run Xfce, but with the Ubuntu applications (e.g. Open Office, Nautilus) so I don't want to install all the other programs (such as abiword, gnumeric etc.) that will install by default with Xubuntu-desktop.

Also, more importantly, will all the gnome programs run under Xfce, and will it still run faster, or is Xubuntu faster just because the actual applications are 'lighter' than the Ubuntu equivalents?

thanks! :-)

---

### Post by taurus on 2006-12-18
Well, you can go for the XFce4 instead of xubuntu-desktop...

```
sudo aptitude update
sudo aptitude install xfce4
```

---

### Post by Big_Croc7 on 2006-12-18
Linux: If in doubt, type in obvious names of things!  Thanks, that looks like exactly what I was asking for...
:-)

---

### Post by BLTicklemonster on 2006-12-18
Shoot, run fluxbox, and make gnome-panel load in startup.

---

### Post by Big_Croc7 on 2006-12-19
Thanks - have now installed Xfce - might get round to trying Fluxbox soon as well.  Is it possible to make them share the same settings (eg. for the panel, etc?)  Specifically it would be nice if the panel menus and items were the same in both.
:-)

---

### Post by Kimm on 2006-12-19
> **Big_Croc7 said:**
> Thanks - have now installed Xfce - might get round to trying Fluxbox soon as well.  Is it possible to make them share the same settings (eg. for the panel, etc?)  Specifically it would be nice if the panel menus and items were the same in both.
:-)

If you use gnome-panel, it will use the same settings no mather which desktop you use :)

---

### Post by BLTicklemonster on 2006-12-19
You can make them both load the gnome-panel, or xfce4-panel if you want, and have them familiar enough for you so that you don't have some sort of culture shock thing going on.

---

### Post by Big_Croc7 on 2006-12-20
Yeah, that sounds good... umm so how do I do that? sorry, have looked round but can't find how to do it anywhere. Is it a question of loading a gnome-panel application at start-up? if so, how do I load it?

---

### Post by BLTicklemonster on 2006-12-20
Look and see if there's a hidden folder in your /home/yourname/ directory (press ctrl+H to view hiddens) called .fluxbox. If not, then go to /usr/share/ and see if there's a fluxbox directory there, if so copy it to /home/yourname/ and rename it to .fluxbox (though I don't know why it needs to be hidden, but whatever)

In that folder there should be a file named startup.

Add to the end where it shows startup stuff

xfce4-panel &

(or gnome-panel &  though I think if you use that, you need gnome-sessions & also)

save and close.

Restarting fluxbox won't bring this up, you'll need to log off and log back on.

---

### Post by Big_Croc7 on 2007-01-12
sorry about the delay in replying, I was hoping to try this before I went on holiday but didn't get chance... works like a charm. Thankyou! :)

---

