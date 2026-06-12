---
title: "Background color for splash screen"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by JeSTeR7 on 2007-10-29
This isn't the normal question you see asked.

I changed my splash to a blue color using the splash screen manager and it works perfectly.  I've changed to a blue GDM theme using the Login Window manager and that works just fine.

This is where my issue is.  I changed the "background" color in the Login Window manager to blue, but it's still brown before the desktop loads.  I've changed the color of the desktop background to blue as well, but still the window behind the splash is the default brown and I can't seem to change it. 

Any ideas?

---

### Post by LowSky on 2007-10-29
I have the same odd issue.

I made my splash screen  black, but in between loading the spash into my desktop it all turns brown. I don't get it, and until now just thought its an error I can live with.

---

### Post by Sbarton on 2007-10-29
Same experience here. Changed login background OK! Cannot change splash background, it remains the Ubuntu light biege colour.Maybe someone might offer a solution soon.
regards.

---

### Post by JeSTeR7 on 2007-10-29
OK, I found it!

You need to edit /etc/gdm/PreSession/Default (using sudo, of course)and change the line that says BACKCOLOR="#DAB082" to the hex code of the color you want.

I can't take credit for it, I just did a little more Googling and found it on [this](http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html) blog.

---

### Post by Sbarton on 2007-10-29
> **JeSTeR7 said:**
> OK, I found it!

You need to edit /etc/gdm/PreSession/Default (using sudo, of course)and change the line that says BACKCOLOR="#DAB082" to the hex code of the color you want.

I can't take credit for it, I just did a little more Googling and found it on [this](http://www.bauer-power.net/2007/10/get-rid-of-ubuntu-brown-in-gutsy.html) blog.

That's great! works fine.Thanks! Maybe you can mark post as solved so others know!
regards:D

---

### Post by LowSky on 2007-10-29
sweet, thanks worked like a charm

---

### Post by mandrill on 2007-11-01
my bad, wrong screen

---

### Post by BigSilly on 2007-11-03
Many thanks for this thread. Excellent find, and solved my own "brown problem" too!

Top stuff, and thanks again. :)

---

### Post by Hartford on 2007-11-03
found something that may be of interest to those looking to change their GDM Splash Background more.

Just below the background color options in gdm.conf at line 472 are comments suggesting that a screensaver or program-operated imaging may be entered.  Does anyone know if this is actually possible, or what may be involved in making it happen?

BTW, i use 7.1 gutsy

---

