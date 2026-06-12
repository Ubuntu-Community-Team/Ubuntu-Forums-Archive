---
title: "Encode issue LAMP"
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by brunoskrebs on 2007-09-14
Ok, I just set up the LAMP on my computer. I used to have AMP with windows before. But since I am moving to linux I had to set up this as well.

So I brought a website from windows, and put on LAMP, and then when accessed this it show a few strange characters like this &#65533;&#65533;...

I guess this is an encode problem or something like this, I have accessed the website from another computer and it showed the same characters. Then I guess it is an encode problem but from my apache...

Does anyone know how to fix it???

Oh by the way, it showed these strange characters in the place of characters with accent (my mother language is Portuguese).

Thank you, 
Bruno Krebs.

---

### Post by peabody on 2007-09-14
Where is the website and are you properly using a content-type meta tag in the header of the html file?  With no content-type meta tag, the web browser will go off of whatever the web server tells it.

---

### Post by brunoskrebs on 2007-09-15
Ahmmm,

yeah it can be that, I am not using content-type, I code everything on hand and I didn`t put this tags. Actually you can`t see the website, because it is not rally a website. Is a software that I made for the company of my father, and it is accessible only in the LAN.

I`ll try puting the content-type, thank you very much.

Bruno Krebs

---

### Post by brunoskrebs on 2007-09-15
Ahm

ok, I am the root of my system, so where is the configuration file of apache to change the encode to support brazilian accents? Because I am trying to find it, but I can`t :P

Thankss...

---

### Post by peabody on 2007-09-15
For apache I'm not sure.  For the content of your web pages, put something like this in the header:

<meta http-equiv="content-type" content="text/html; charset=ENCODING GOES HERE">

examples would be, utf-8, iso-8859-1.  Is Brazilian Portuguese written in some other encoding other than latin-1 or utf-8?

---

### Post by brunoskrebs on 2007-09-15
No I think is in utf 8, and I tried utf-8 and iso-8859 in the tag and both didn`t work...
But thanks for the help anyway

---

