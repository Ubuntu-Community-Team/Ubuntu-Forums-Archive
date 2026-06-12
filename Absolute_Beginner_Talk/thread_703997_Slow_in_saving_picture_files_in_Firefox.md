---
title: "Slow in saving picture files in Firefox"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by kingtsy on 2008-02-21
Hi everyone,

I have 3 OS in my laptop, windows xp home, pc linux os 2007 and ubuntu 7.10. in all os i uses firefox for my browsing. i observed that it takes longer whenever i save picture files (jpeg) in linux (usually 3 - 4 sec) compared to windows that instantly save picture files. how can i correct this?

thanks

---

### Post by Presto123 on 2008-02-21
Uhh...?:confused:

---

### Post by kingtsy on 2008-02-21
hi presto123

what i mean is that the firefox seems to hang up around 3 sec before the picture starts to save.

thanks.

---

### Post by Presto123 on 2008-02-22
Oh...sorry there kingsty, for some reason, I came into your thread and all I saw was "h". Hence the confused me.

Have you done any updates lately? Mine was doing that on my desktop, but a few updates ago, there was one for Firefox that really sped it up.

---

### Post by kingtsy on 2008-02-25
hi presto123.

thanks for answering my inquiry. yes i always update my os. still saving jpeg in firefox on both pclinux and ubuntu slower by 3 -5 sec compared on saving jpeg in firefox on windows xp.

whenever i save jpeg i usually right click on the picture and choose "save image as" then click save and the "save image" windows pause for about 3 sec before disappearing unlike in windows xp that after i click save,  the "save image" windows instantly disappeared.

i install opera web browser and it could save jpeg files instantly like firefox in windows xp home.
now i'm using opera for saving jpeg files.

thanks again presto123.

---

### Post by tuukos on 2008-03-15
I have found saving image files in Firefox into picture folders containing 1000+ images to be *extremely* slow... about 30-45 seconds. I gather the bottleneck is Nautilus... In Fluxbox the same operation takes only a few seconds.

Is there any option that can be enabled/disabled that can speed up saving images into large folders in Firefox/Gnome/Nautilus? Thanks!

---

### Post by kwidzin on 2008-04-28
Same problem here. I don't have any idea how to savig images faster :-(

---

### Post by x0d on 2008-07-10
I'm bumping this because I found a solution that works for me.

To speed up "save image as" in firefox you actually need to tweak nautilus.

Start nautilus and go to **Edit**/**Preferences**/**Preview**. Set "show text in icons" to *never*, set "show thumbnails" to *never*, and set "count number of items" to *never*.

Now when you try saving an image in firefox it should be much faster, even when you're trying to save images into a directory with a lot of files in it.

---

