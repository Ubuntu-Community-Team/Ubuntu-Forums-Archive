---
title: "[release] ubuntu.bold GDM theme"
date: 2005-10-12
forum: Art &amp; Design
---

### Post by lost.sync on 2005-10-12
download it from: [http://www.gnomelook.org/content/show.php?content=30095](http://www.gnomelook.org/content/show.php?content=30095)

widescreen and normal aspect ratios supported.  widescreen users consult README located in the tarball for instructions.  people who don't know how to install it, also consult README.  

looks like:

[CENTER][[IMG]http://ubuntuforums.org/gallery/files/3/8/5/0/0/ubuntu.bold-login_thumb.png[/IMG]]("http://ubuntuforums.org/gallery/files/3/8/5/0/0/ubuntu.bold-login_original.png")
click to enlarge
[/CENTER]

---

### Post by Zelin on 2005-10-13
I like it but I think that the login should be below the "ubuntu".

---

### Post by daschl on 2005-10-13
[QUOTE=Zelin]I like it but I think that the login should be below the "ubuntu".[/QUOTE]

yes i agree with that :)

if you can fix that, it will look very nice 

*thumbsup* !

---

### Post by lost.sync on 2005-10-14
i actually placed it there on purpose.  i have problems with things being off center.  besides, being 85% transparent, it's not like you can't see what's behind it.

but! if you'd like to change it, simply edit ubuntu.bold.xml to your liking.  in this case:

1. extract ubuntu.bold.xml
2. open it in your favourite editor
3. scroll to near the bottom and find the line: <!-- password box -->
4. two lines below that, you'll see: <pos x=50% y=50% ... />
5. change the value for y to 70%
6. save and replace original xml file in the archive, then install as you would any other theme.

---

