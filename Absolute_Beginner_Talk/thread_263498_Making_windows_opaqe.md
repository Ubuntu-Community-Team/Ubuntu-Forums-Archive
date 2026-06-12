---
title: "Making windows opaqe"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by IngSoc on 2006-09-23
I see pix with peoples term half opaque how is this done. Also I see what looks like people have there desktops on a cube of sort... How is that done? Thanks.

---

### Post by dbd on 2006-09-23
You need to install xgl and compiz. There is info on how to do this here:

[https://help.ubuntu.com/community/CompositeManager](https://help.ubuntu.com/community/CompositeManager)

Be warned though, it is not easy. Also, it is very early alpha software so may crash your system and cause many problems. And you need a pretty good graphics card to run it, so if you just have some on-board chip it probably wont work.

Also according to the wiki the compiz repositories are currently broken, so don't install yet. Check back at the wiki page and when that message at the top has gone then give it a try, if you want. Just remember there is a chance it will go wrong.

---

### Post by nts on 2006-09-23
3ddesk for the 'cube' effect, you may need to tinker with your xorg.conf file in order to enable hardware acceleration on your graphics card.

---

### Post by CheeseEatingBulldog on 2006-09-23
You could also just right click your term and edit current profile...then goto effects and slide the transparency bar.

Compiz/xgl packages are not availeble at the moment due to a renaming/restructuring of compiz. Packages like csm and the theme mamager aren't in the repos.

---

### Post by K.Mandla on 2006-09-23
If you're using XFCE (Xubuntu), you can make a terminal window transparent. It's under the preferences for the terminal.

---

