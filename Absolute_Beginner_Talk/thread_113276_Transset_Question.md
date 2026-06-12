---
title: "Transset Question"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by Gray. on 2006-01-06
This probably isn't the place to post it but I couldn't find another place.

Is there anyone that could write a script that will allow me to input a value (using zenity I guess) that would be used in the command 'transset <value entered in zenity>)'. So when I set the script to a button, if I press it, a pop-up box comes up and asks for the value of the transparency I want (e.g. 0.7). When I press OK, it enters that value into the command 'transset 0.7', then I can just click on the window and it applies it.

I hope I made sense with that.

---

### Post by 23meg on 2006-01-06
You can do that more practically with transset-df. 

[http://forchheimer.se/transset-df/](http://forchheimer.se/transset-df/)

(edit: sorry, it seems I misread you; it should still be of interest though)

---

### Post by poofyhairguy on 2006-01-06
[QUOTE=Gray.]This probably isn't the place to post it but I couldn't find another place.

Is there anyone that could write a script that will allow me to input a value (using zenity I guess) that would be used in the command 'transset <value entered in zenity>)'. So when I set the script to a button, if I press it, a pop-up box comes up and asks for the value of the transparency I want (e.g. 0.7). When I press OK, it enters that value into the command 'transset 0.7', then I can just click on the window and it applies it.

I hope I made sense with that.[/QUOTE]

I would try Gcompmgr:

[http://ubuntuforums.org/showpost.php?p=555510&postcount=170](http://ubuntuforums.org/showpost.php?p=555510&postcount=170)

Download to home folder. Right click on it and choose "extract here."

Open the folder made and copy the .deb file inside to your home folder. Install it with this command:

```
sudo dpkg -i gcompmgr_0.21-2_i386.deb
```

And run it with the 

gcompmgr

command.

---

### Post by Gray. on 2006-01-07
Ok I'll try it

---

