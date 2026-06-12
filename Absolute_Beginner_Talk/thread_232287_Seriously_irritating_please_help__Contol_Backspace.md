---
title: "Seriously irritating please help / Contol Backspace"
date: 2006-08-08
forum: Absolute Beginner Talk
---

### Post by TFX360 on 2006-08-08
Guys, this is killing me I just tied two fingers together because when I push **SHIFT** Backspace my active Gnome session in Ubuntu logs out without saving anything. I can't find this in Keyboard Shortcuts. Feeling noobish here.

Got ndiswrapper / wpa_supplicant and XGL Compiz working like a charm on my compiled ATI X800XT drivers... and getting myself stressed over two frigging buttons.


Help appriciated.


Kind regards,


TFX

---

### Post by Metacarpal on 2006-08-08
Try [these steps]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_Ctrl.2BAlt.2BBackspace_from_restarting_X_in_GNOME").  That should solve the problem for you.  :)

---

### Post by wpshooter on 2006-08-08
> **TFX360 said:**
> Guys, this is killing me I just tied two fingers together because when I push Control Backspace my active Gnome session in Ubuntu logs out without saving anything. I can't find this in Keyboard Shortcuts. Feeling noobish here.

Got ndiswrapper / wpa_supplicant and XGL Compiz working like a charm on my compiled ATI X800XT drivers... and getting myself stressed over two frigging buttons.


Help appriciated.


Kind regards,


TFX

Does doing this lose your current sessions work/changes regardless of the fact that you had the automatic save session check box marked in the sessions menu ?

Thanks.

---

### Post by TFX360 on 2006-08-08
> **Metacarpal said:**
> Try [these steps]("http://ubuntuguide.org/wiki/Dapper#How_to_disable_Ctrl.2BAlt.2BBackspace_from_restarting_X_in_GNOME").  That should solve the problem for you.  :)

Thanks, looks very helpfull (I'm typing this for the second time :D) I meant to write SHIFT + Backspace and plop there is the logon screen.

Sorry. This didn't help.

---

### Post by TFX360 on 2006-08-08
> **wpshooter said:**
> Does doing this lose your current sessions work/changes regardless of the fact that you had the automatic save session check box marked in the sessions menu ?

Thanks.

Nope this wasn't checked. Should be standard though! :D

PS: Ofcourse I just checked it :D

---

### Post by TFX360 on 2006-08-08
SHIFT + Backspace

Ends my session...

---

### Post by wpshooter on 2006-08-09
> **TFX360 said:**
> Nope this wasn't checked. Should be standard though! :D

PS: Ofcourse I just checked it :D

I stongly agree, this should be **ON by default**.  The option should be to turn this **OFF**, although for the life of me I can't see why any one would hardly ever need it to be off.  

Maybe they will fix this in the near future.

---

### Post by TFX360 on 2006-08-09
SHIFT + Backspace

Still ends my session...

---

### Post by NinjitsuStylee on 2006-08-09
Try this:
[http://ubuntuforums.org/showthread.php?t=230775](http://ubuntuforums.org/showthread.php?t=230775)

---

### Post by UltraMathMan on 2006-08-09
Adding ```
xmodmap /usr/share/xmodmap/xmodmap.us
``` to startup programs disabled the Shift+Backspace logout for me. You can test it by entering it into a terminal first if you like.

-Hope this helps :)

---

### Post by LordTureis on 2006-08-09
UltraMathMan, that disables all Compiz shortcuts for me.

A better one would be:
```
xmodmap -e "keycode  22 = BackSpace"
```

---

### Post by LordTureis on 2006-08-10
Probably the best thing to do is:

```
sudo gedit /usr/local/bin/deathtoshiftbackspace
```

paste in the following:

```
#!/bin/sh 
xmodmap -e "keycode  22 = BackSpace"
```

Save that and then:
```
sudo chmod 755 /usr/local/bin/deathtoshiftbackspace
```

Then you can add "deathtoshiftbackspace" to your startup list.

---

### Post by TFX360 on 2006-08-10
LordTureis I love you, works like a charm!

[IMG]http://home.casema.nl/d.sluijter/Screenshot-Sessions.png[/IMG]

---

