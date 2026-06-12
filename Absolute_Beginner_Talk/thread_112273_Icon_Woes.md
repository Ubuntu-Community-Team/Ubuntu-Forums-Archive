---
title: "Icon Woes"
date: 2006-01-04
forum: Absolute Beginner Talk
---

### Post by sabredog on 2006-01-04
Can someone please help?

Below is the download page for an icon set I quite like, however there is an issue with the mozilla-firefox icon. (details in the comments on the linked webpage)

How can I correct this. I cannot find any folders where the theme has been installed to make the changes or to fix the icon up.

[http://www.gnome-look.org/content/show.php?content=25865]("http://www.gnome-look.org/content/show.php?content=25865")

This is a very frustrating exercise! :( 

Cheers and thanks

---

### Post by dcraven on 2006-01-04
Check for the theme in ~/.icons if you installed the theme pack as your regular user.

HTH,
~djc

---

### Post by sabredog on 2006-01-04
The theme is there.

Not sure how to change the link as described in the page I have linked though

cheers and thanks

---

### Post by dcraven on 2006-01-04
[QUOTE=sabredog]The theme is there.

Not sure how to change the link as described in the page I have linked though

cheers and thanks[/QUOTE]
You could use the solution as described in that same page:
```

cd ~/.icons/AquiGnome/128x128/apps/ && ln -s firefox.png mozilla-firefox.png

```
I don't have the iconset, but considering the reported problem, that solution seems relatively sound.

HTH,
~djc

---

