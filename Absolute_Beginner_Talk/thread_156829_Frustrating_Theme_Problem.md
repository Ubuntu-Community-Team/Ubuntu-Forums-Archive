---
title: "Frustrating Theme Problem"
date: 2006-04-07
forum: Absolute Beginner Talk
---

### Post by brandoncolorado on 2006-04-07
Hi,

I went to [http://art.gnome.org](http://art.gnome.org)

I download several login themes and installed them via:

sudo gdmsetup
I setup about 4 themes and said to go on random.
Now, when I restart it says it can't find theme "circles" (there is a path).

It reverts back to the default gnome theme, but I can't enter my username, the box won't accept text.  If I restart, same thing every time.

Any ideas?

---

### Post by erikpiper on 2006-04-07
By login themes, do you mean where you enter your username/password? If so,
[http://www.ubuntuforums.org/showthread.php?t=77694&highlight=gnome+splashscreen](http://www.ubuntuforums.org/showthread.php?t=77694&highlight=gnome+splashscreen)
^Will help you. First post, section 8. (GREAT howto for eyecandy! At least skim it!)

---

### Post by brandoncolorado on 2006-04-07
Sorry, but I'm kind of new to Ubuntu.  I can't get in to run any commands, otherwise I would just gdmsetup and remove the theme.  I can't login to Ubuntu.

---

### Post by erikpiper on 2006-04-07
Oooh.. I'm sorry.. I didnt read the whole post... 

I really dont know.. Someone else should..

---

### Post by aysiu on 2006-04-07
Press Control-Alt-F1
Log in
Type ```
cd /usr/share/gdm/themes
ls
``` What do you see? Is Circles there? If so, you should see at least this: ```
/usr/share/gdm/themes/circles
/usr/share/gdm/themes/circles/GdmGreeterTheme.desktop
/usr/share/gdm/themes/circles/circles.xml
/usr/share/gdm/themes/circles/background.svg
/usr/share/gdm/themes/circles/flower.png
/usr/share/gdm/themes/circles/help.png
/usr/share/gdm/themes/circles/options.png
/usr/share/gdm/themes/circles/screenshot.png

```

---

### Post by brandoncolorado on 2006-04-07
Hi,

Sorry about the slow response, but I am on a dual boot.

It looks to me like the circles directory isn't even there.

I followed your instructions and I see only 5 other themes (that I had downloaded and installed)  

Maybe I deleted circles and thats the problem?

---

### Post by brandoncolorado on 2006-04-07
Is there any way I can force a login to the desktop so I can get back into gdmsetup?

---

### Post by aysiu on 2006-04-07
Okay.

Do this.

Press Control-Alt-F1.

Log in.

Type ```
sudo cp /etc/gdm/gdm.conf /etc/gdm/gdm.conf_backup
sudo nano /etc/gdm/gdm.conf
``` Replace this line ```
GraphicalThemeRand=true
``` with this line ```
GraphicalThemeRand=false
``` and change what I'm guessing is this line ```
GraphicalTheme=Circles
``` to whatever's appropriate (you may want to see exactly what themes you have in /usr/share/gdm/themes first). When you're done, save (control-x), confirm (y), and exit (Enter). ```
sudo /etc/init.d/gdm restart
```

---

### Post by aysiu on 2006-04-08
If that doesn't work, you can try ```
sudo apt-get update
sudo apt-get install kdm
``` and replace GDM with KDM. Use KDM to log into Gnome and change the GDM setup. Then replace KDM with GDM .

---

### Post by brandoncolorado on 2006-04-08
Ok, thanks that worked.  I am still a bit frustrated that I can't select random.  Whenever I do, it chooses the same theme over and over.  At least I can get into Ubuntu again!

Thanks aysiu

---

### Post by brandoncolorado on 2006-04-08
Got it!

I think I found what I did wrong.  When you select random, you have to select multiple themes (I just assumed it did this for you).  I think maybe this is what caused the problem initally.  Maybe a little newbie Linux user problem.

---

