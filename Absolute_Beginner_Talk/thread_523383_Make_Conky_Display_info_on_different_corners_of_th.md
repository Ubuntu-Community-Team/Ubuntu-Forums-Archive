---
title: "Make Conky Display info on different corners of the monitor"
date: 2007-08-11
forum: Absolute Beginner Talk
---

### Post by AegisTalons on 2007-08-11
How do you get conky to display information in different corners of the monitor. For example, I want the time on the bottom right and Comp info on the Bottom left, how do I do that in the .conkyrc file?
Thanks

---

### Post by felicity on 2007-08-11
You should probably make more than one .conkyrc file, one for each location you want on your desktop. Then use conky -c /location/of/specific/.conkyrc to start the conky variations.

---

### Post by AegisTalons on 2007-08-11
So I would have to run two instances of conky?

---

### Post by felicity on 2007-08-11
That's my suggestion though someone else might know another way. :D

---

### Post by AegisTalons on 2007-08-11
Do you know how to change the font size and the font itself in conky? I've looked at the variables page and it says to use font, but doesn't say how to exactly with an example.

---

### Post by felicity on 2007-08-11
Here's an example: ${font Terminus:Bold:size=11}${time %H:%M:%S}

---

### Post by AegisTalons on 2007-08-11
THANK YOU SO MUCH. you don't know how long i've been trying to figure it out.

---

### Post by felicity on 2007-08-11
No problem, have fun! :)

---

### Post by AegisTalons on 2007-08-12
How do you define your default font before the TEXT cmd?

---

### Post by felicity on 2007-08-22
font Terminus:size=12
or
xftfont Terminus:size=12

Here's a link to the conky config settings: [http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

---

### Post by Ek0nomik on 2007-08-22
> **felicity said:**
> font Terminus:size=12
or
xftfont Terminus:size=12

Here's a link to the conky config settings: [http://conky.sourceforge.net/config_settings.html]("http://conky.sourceforge.net/config_settings.html")

Thanks for the link to all the settings.

I actually meant to look at up awhile ago and then I forgot.  Luckily this thread caught my eye.  :)

---

