---
title: "rhythmbox and the ipod."
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by CapitanYochua on 2007-11-11
I have it working with my 30 GB fine. I tried my brother´s nano and it automatically crashes when I open rhythmbox. This is the output...
```
joshua@joshua-desktop:~$  rhythmbox

** (rhythmbox:5768): CRITICAL **: ipod_parse_artwork_db: assertion `itdb' failed

(rhythmbox:5768): GLib-GObject-CRITICAL **: g_type_instance_get_private: assertion `instance != NULL && instance->g_class != NULL' failed
Segmentation fault (core dumped)

```
Any help?
-thanks.

---

### Post by stijngysemans on 2007-11-11
maybe you can try it with banshee (applications >> add /remove >> banshee)

---

### Post by laidback on 2007-11-11
Try Amarok.

---

### Post by Keith Hedger on 2007-11-11
scrap the apple software and rythymbox and install rockbox on your ipod and use the rockbox sim on your main machine i did and the combo works great no mucking about

---

### Post by Perpetual on 2007-11-11
Although I don't like how banshee displays your collection (meaning you cant collapse albums, rather it displays the entire album in the window, unlike amarok or exaile) I have found it works best with my ipod as far as copying from collection to ipod, including album art.  I have used exaile and although I like it's layout best, what ended up on my ipod was not always intact or album art was hit or miss.  Rythmbox I wasn't impressed with at all so never spent much time with it.

I suppose Amarok was my fave when using a kde based distribution but thus far I have been trying to stay with gnome apps rather than mixing.  I may decide to change that philosophy in the future.

Off topic a bit, Keith Hedger, I tried rockbox a month ago or so and although I loved it's flac support, I found it kind of problematic.  I was using Amarok to handle my collection and move music to my ipod but after moving music, I was having issues where the music would not show up in the rockbox database but it was there as Amarok would show it and play it.

I did not get to use the rockbox software though as I believe it needs to be compiled and that's something I haven't ventured into in my short linux life.

To the original OP, it looks like it is failing to read the itunes database (assertion `itdb' failed).  You might try first reformatting the ipod with itunes and then attempt work with it again in linux.  I have always found that a clean ipod from the start makes using linux apps much better.

---

