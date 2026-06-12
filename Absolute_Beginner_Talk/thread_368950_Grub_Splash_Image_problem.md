---
title: "Grub Splash Image problem"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by pjones0404 on 2007-02-23
I am having an issue w/ the grub splash image. 

i have assigned a new one following these instructions. [[COLOR="Blue"]here[/COLOR]]("http://ubuntu.wordpress.com/2006/03/21/add-a-grub-splash-image") The image that i selected does not display a highlighted line allowing me to select which os i want to load and i would like to go back to the original grub screen. Either that or select a different splash that does have the "selecting line".

when i try to select a different splash image i rec the following response "[COLOR="Red"]ln: creating symbolic link `splash.xpm.gz' to `splashimages/guitar.xpm.gz': File exists[/COLOR]" i think that means that it can not create the link since there is already a link there but i dont know how to fix it. 

any help would be appreciated.

---

### Post by nereid on 2007-02-24
You have to delete the old splash.xpm.gz file first or, to be save, just rename it

```

mv splash.xpm.gz splash.xpm.gz.old

```

---

