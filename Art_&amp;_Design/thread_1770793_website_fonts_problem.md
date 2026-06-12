---
title: "website fonts problem"
date: 2011-05-29
forum: Art &amp; Design
---

### Post by meredith_fer on 2011-05-29
hi everyone,

I am using Kompozer to create a website with URW Chancery font, but, either with firefox or chromiun the font visualized is Times New Roman or so. It happens in linux and windows internet navigators.

any ideas?

thank you so much

---

### Post by babybean on 2011-05-29
With this sort of thing I would usually assume the problem is that the font is not installed in the computers viewing the webpage. This may not be the case with you as you are I assume looking at the page on the same machine as you made the page on?

---

### Post by meredith_fer on 2011-05-30
> **babybean said:**
> With this sort of thing I would usually assume the problem is that the font is not installed in the computers viewing the webpage. This may not be the case with you as you are I assume looking at the page on the same machine as you made the page on?

exactly. I am on the same machine. I have even uploaded the font to the server, just in case but nothing :(

---

### Post by Skawt_S on 2011-05-30
I don't think that uploading the fonts to the server will help since they are used off of the machine viewing the web page, You can check if the font is installed by checking in ~/.fonts or ~/.fonts/library for your user fonts. Place the font in the ~/.fonts folder to make it usable for your user.

you can also install the font manager to help you get your fonts accessible to all users.

---

### Post by MooseDog on 2011-05-30
research the css3 use of @fontface, as well as the google font api.  

keep in mind that a browser's capability in rendering fonts is very limited compared to an installed desktop application.

---

### Post by babybean on 2011-05-30
Check that the css actually works (use a really common but distinguishable font)
As moosedog says give @fontface a go. It allows you to have the font embedded on the page so that people who do not have the font installed can see it. Also keep in mind that that is quite a fancy font and may not be ideal for large portions of text. If you are only planning on using it for a title or two, it would be easier and possibly more efficient to just save the title as a picture file. Another advantage is that pictures are more compatible with most browsers at the moment.
Good luck.

---

### Post by meredith_fer on 2011-05-30
> **babybean said:**
> Check that the css actually works (use a really common but distinguishable font)
As moosedog says give @fontface a go. It allows you to have the font embedded on the page so that people who do not have the font installed can see it. Also keep in mind that that is quite a fancy font and may not be ideal for large portions of text. If you are only planning on using it for a title or two, it would be easier and possibly more efficient to just save the title as a picture file. Another advantage is that pictures are more compatible with most browsers at the moment.
Good luck.

Ok, I qill give it a try, as soon as I understand what "css" and "@fontface" are ;)

thank you all of youu

---

### Post by meredith_fer on 2011-06-01
> **MooseDog said:**
> research the css3 use of @fontface, as well as the google font api.  

keep in mind that a browser's capability in rendering fonts is very limited compared to an installed desktop application.

quite wired but, in Chromium I can see the font, but using Firefox, I can not... in my own computer both cases... strange, isn't it?

---

