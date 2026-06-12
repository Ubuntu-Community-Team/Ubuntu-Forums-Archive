---
title: "Stop window dimming on asking for password ?"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-07-29
Just wondering like to work in darken room can see my keyboard except when I have to enter password for sudo stuff then the screen dims so I no longer can
see keyboard.

Any way to have the password dialog without dimming the screen?

Thanks.

---

### Post by orb9220 on 2006-07-30
Anyone ?

---

### Post by prophet11 on 2006-07-30
Apparently its recommended that you leave that on for security reasons....

---

### Post by orb9220 on 2006-07-30
I don't see how dimming the screen behind the dialog prompt is a security issue. 
What on the desktop that needs to be hidden? 
My wallpaper or desktop icons? Makes no sense that I can see.

Just wish I could turn off the dimming.

Thanks for commenting tho.

---

### Post by stiankarlsen on 2006-07-30
How about you learn yourself to write without looking at the keyboard?:cool:

---

### Post by moma on 2006-07-30
Hello,

"gksudo" is the graphical dialog for sudo-password.  E.g
$  [COLOR="Green"]gksudo update-manager[/COLOR]

You can propably manipulate it's behavior this way.

Start gconf-editor 
$ [COLOR="Green"]gconf-editor[/COLOR] 
And browse to "/apps/gksu/"  [COLOR="SlateGray"]  (Press CNTR+F and search for gksu)[/COLOR]
Check-mark the "disable-grab" option.
------------------

[Gconftool-2]("http://www.gnome.org/projects/gconf/") does the same from command line

Get value
$ [COLOR="Green"]gconftool-2 --get /apps/gksu/disable-grab[/COLOR]

Set value
[COLOR="Green"]gconftool-2 --type bool --set /apps/gksu/disable-grab "true"[/COLOR]
------------------

Have a nice day ;-) and visit 
[http://www.futuredesktop.org/AsteriskPBX.html]("http://www.futuredesktop.org/AsteriskPBX.html")
Download and watch the demo video of Asterisk PBX.

---

### Post by orb9220 on 2006-07-30
Thanks moma I'll check that out.

To stiankarlsen that is a sad comment to give somebody. Sarcasm is the only way you can help. I see in your 97 post only 2 was responding to others needing help,and ALL the rest is about you asking for help. And I didn't see them responding with sarcasm. Lucky for you!

---

