---
title: "XGL with radeon 9200"
date: 2006-06-05
forum: Apple PPC Users
---

### Post by jackoverfull on 2006-06-05
Hi, I have an ibook with an ati radeon 9200 card and now the acceleration works using the open source driver.
i noticed users having xgl/compiz on similar macs, how can i get theese things to work?

---

### Post by JackosKing on 2006-06-05
Did you read the ubuntu Wiki?
Maybe the solution is here:
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=xgl&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=xgl&titlesearch=Titles)

---

### Post by jackoverfull on 2006-06-05
yes, i looked at the wiki some days ago. all theese solutions are for proprietary drivers.

---

### Post by autocrosser on 2006-06-05
I found a tut not long ago that worked with the radeon driver in Xorg--I'm at work right now, but when I get home-I'll post the link here...

---

### Post by DeadSamurai on 2006-06-05
Hi,
I had to try it :) I thought that at least it'll run as "well" as on my old Dell C400 (i830). 
Xgl is currently running on my system Mac mini ppc with RV280 chipset. Well running is probably saying to much it is horribly sluggish and not ready for primetime on this hardware. The thing might be that I am currently using a 23" widescreen at 1920x1200 and that might be the reason to why it's sluggish and I'll try it.... Back a little bit later and no, that was not the reason. It was still very unresponsive when I lowered the resolution and from the looks of it using the xgl server didn't take any load of the CPU either (which seems to be the case with i830). I have not triet to tweak any of my settings and there is possibly much to be done. I'll look in to it when I have more time.
I followed the link above and chose to use the server alternative

Machine specs:
Linux themac 2.6.15-23-powerpc #1 Tue May 23 13:46:54 UTC 2006 ppc

Attaching xorg config and gdm.conf-custom files plus output from lspci -v and cpuinfo

Hope it helps and please ask for more should you need it

---

### Post by autocrosser on 2006-06-06
Take a look at this post from the dapper development forums-- [FONT=Arial][SIZE=2][FONT=Arial]http://www.ubuntuforums.org/showthread.php?t=176582&highlight=xgl[/FONT][/SIZE][/FONT]

---

