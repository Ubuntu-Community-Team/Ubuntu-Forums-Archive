---
title: "Disable capslock ?"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by MrKlean on 2006-12-10
Anyone know how I can disable the capslock key ?? In XP it was a registry hack.. but since Edgy has no registry.. I was wondering ??
Thanks ; )

---

### Post by evilghost on 2006-12-10
You should be able to do it with xmodmap.  I don't know the keycode so hopefully I've pointed you in the right direction.  This forum post may be helpful:

[http://www.garayed.com/linux/211810-xmodmap-script-make-caps-lock-work-like-shift.html](http://www.garayed.com/linux/211810-xmodmap-script-make-caps-lock-work-like-shift.html)

---

### Post by drphilngood on 2006-12-10
See here:

[ How to remap the Caps Lock key as another Control key]("http://ubuntuguide.org/wiki/Dapper#How_to_remap_the_Caps_Lock_key_as_another_Control_key")

Hope this helps!

---

### Post by MrKlean on 2006-12-10
Thank you Gentlemen ; )

---

### Post by drphilngood on 2006-12-11
> **MrKlean said:**
> Thank you Gentlemen ; )

You are most welcome.

---

### Post by aseem on 2007-11-05
Or simply using the following line:

> xmodmap -e "remove lock = Caps_Lock"

Paste it in your .bashrc to  permanently disabling  Caps-Lock.  Its a relief!!!!

---

### Post by oldb0y on 2008-01-02
Bumping this thread.
How do I paste the xmod-command in .bashrc?

---

### Post by bdaniel on 2008-01-02
> **oldb0y said:**
> Bumping this thread.
How do I paste the xmod-command in .bashrc?

```
sudo nano ~/.bashrc
```

Just type the line at the end. To save Control O, to exit Control X

---

### Post by oldb0y on 2008-01-02
Uhm, having a bit of trouble. After typing the line, nothing happens when I press control+o.

---

### Post by Whiffle on 2008-01-02
Actually what I'd do, paste this in your Xmodmap, which will enable it for the entire X session:

In a terminal:
```

nano -w ~/.Xmodmap

```

Add this:
```

clear lock

```

Hit F3, logout, login, and you're done.

---

### Post by jken146 on 2008-01-02
Really?  Try Ctrl+X, then answer Y to the question to save, then Enter to use the same file name.

---

### Post by oldb0y on 2008-01-02
Oh! Now it works:) Finally I can leave CapsLock behind!

---

### Post by twizler on 2008-02-19
Twizler : :)  NO caps lock key ! Disable caps lock  - turn off caps lock - shut off caps lock 

/etx/X11/ --- file xorg.conf

>  ADD THE LINE BELOW ‘InputDevice’ section of one’s xorg.conf:

[COLOR="Blue"]Option      "XkbOptions"    "lv3:ralt_switch, ctrl:nocaps"[/COLOR] 

This makes your caps lock key = a CTRL key -- so its USE FULL and no more USELESS Caps lock key.  --->  2.     [COLOR="Blue"]Save the xorg. conf file [/COLOR]--- [COLOR="Blue"]close all windows  and then hit 
> 

[QUOTE]CRTL + ALT+ BackSpace ( alll at same time) [/COLOR]
 [/QUOTE]
Log back in And now you dont have ur caps lock key!

---

