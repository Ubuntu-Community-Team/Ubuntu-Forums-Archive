---
title: "How do I install fonts?"
date: 2007-04-01
forum: Absolute Beginner Talk
---

### Post by Brucey on 2007-04-01
What format should they be in and where do I put them?

And does anyone know where I can get Arial or Times New Roman?

---

### Post by tbroderick on 2007-04-01
Enable multiverse and install the msttcorefonts package. That includes Arial an Times New Roman.

---

### Post by Maestro23 on 2007-04-01
After you enable your extra Repositories:

> 
sudo aptitude update

sudo aptitude install msttcorefonts

---

### Post by Brucey on 2007-04-01
thanks

---

### Post by joeashcraft on 2007-04-04
If I have .ttf files where do I copy them to?

---

### Post by ksenos on 2007-04-04
I would like to ask how to generally install TT Fonts. I have some non-mscore fonts that I need.

---

### Post by Michaelt74 on 2007-04-04
This link may help,

[http://ubuntuforums.org/showthread.php?t=376982](http://ubuntuforums.org/showthread.php?t=376982)

Good luck!

---

### Post by scottdizzle on 2007-04-14
I tried:

sudo aptitude update

sudo aptitude install msttcorefonts

But I get this error:

> sudo aptitude update

sudo aptitude install msttcorefonts

But.. is this possibly cause I don't know how to turn on my Extra Repositories? I don't know how to do that. Could someone help me?

---

### Post by rocknrolf77 on 2007-04-14
System - Administration - software sources - then check the other boxes to. :)

---

### Post by Maestro23 on 2007-04-14
Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

---

### Post by joeashcraft on 2007-04-14
truetype fonts (.ttf) are stored in the /usr/share/fonts/truetype folder.

---

### Post by Bachstelze on 2007-04-14
But obviously requires root access. If you don't have root access or want the fonts installed just for yourself, you can put them in ~/.fonts

---

