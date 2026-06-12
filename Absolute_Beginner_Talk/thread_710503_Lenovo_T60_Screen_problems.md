---
title: "Lenovo T60 Screen problems"
date: 2008-02-28
forum: Absolute Beginner Talk
---

### Post by BigFlatBrook on 2008-02-28
I have a Lenovo T60 with an ATI X1400 graphics card.

When originally installing Ubuntu, the screen resolution was fine, although I can't remember what it was.

However, in trying to get the Laptop to display reasonably on an external monitor, and attempted to change the screen resolution by going through System->Administration->Screens and Graphics.  

Somehow I reset the resolution to 640X480 and now that's the highest resolution allowed in the Screens and Graphics Panel. 

What can I do to get the resolution set to a reasonable level?  I really don't want to install ubuntu over what I have.

If this is the wrong forum for this question, please tell me the right forum?

Thanks!

---

### Post by jucas_lo on 2008-02-28
If you installed the ati drivers from the restricted drivers section, go to the terminal (Applications->Accesories->Terminal) and type the following command

```
sudo aticonfig --initial --input=/etc/X11/xorg.conf
```

Then restart X with Ctrl+Alt+Backspace 

It will try to make a good initial configuration for your laptop..and it will solve most of your graphic problems....

PD to get more info on the aticonfig thing type ```
aticonfig --help
``` also on the terminal....

---

