---
title: "Bittorent Client For Ubuntu??? Need Scheuler feature!!!"
date: 2007-12-27
forum: Absolute Beginner Talk
---

### Post by taekr on 2007-12-27
Hi,

I know the question of best bittorent client has been asked a lot. 

My question is a bit different. 

I need scheduler function but when I used Deluge and Ktorrent,  I coudln't use the feature even though they claim they have the function. I don't know why???  

Anyway, now I reinstalled Azureus.. Yes it's working but it's bloddy buggy..  I mean it seems to use a lot of resources and CPU power..  

So I'm wondering if Delgue and Ktorrent's scheduler work...   and is there any other clients I can try..?

Thanks

---

### Post by FuturePilot on 2007-12-27
The Deluge scheduler seems to work here. Did you enable the Plugin?

---

### Post by shearn89 on 2007-12-27
rtorrent (although its text-based) has a scheduler - it basically just runs commands at specific intervals, but it can also stop once downloading is complete, so it works well enough. Its good - light and fast!

---

### Post by taekr on 2007-12-27
I enabled it 


What I want to do was

00:00 ~ 02:00 Do not download but upload (or both - no download and no upload)
02:00 ~ 12:00 Both download and upload
12:00 ~ 23:59 Do not download but upload (or both - not download and no upload)

This was the setting I had.

00:00 ~ 2:00 Red
02:00 ~ 12:00 Green (-1 for both download upload limit)
12:00 ~ 23:59 Red

But when it was 12:26, it was still downloading. It didn't stop...

---

### Post by hyper_ch on 2007-12-28
I'm using rtorrent and it has a scheduler, but I never used it...

However a simple way could be using cron to start/stop rtorrent (even start with different config files so that different up/download speed limits would apply)

---

### Post by judgejudy on 2007-12-28
Ktorrent has wot you need and works well in Gnome O and it has a GUI so no config files or terminal. I use the scheduler all the time.

---

