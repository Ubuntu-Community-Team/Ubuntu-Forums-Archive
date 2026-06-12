---
title: "automatic rsync scripts for firefox"
date: 2008-01-17
forum: Absolute Beginner Talk
---

### Post by MarkieB on 2008-01-17
I've had trouble accessing firefox settings folder [on the ntfs partition] between windows/ubuntu installations, perhaps it's ntfs-3g perhaps it's firefox perhaps it's neither..

However, a way to resolve the matter would be to [making 2 folders] create a startup script in ubuntu that rsync's the windows folder to the ubuntu folder, then really I'd need to rsync the folder back immediately on shutting down firefox

the startup script is straightforward, just add one to /etc/init.d, it's making a script that'll be called when firefox closes that causes me to write here, does anybody know how?

Basically, there's no need for equivalent scripts in windows, as most of my browsing is from ubuntu; windows only for what ubuntu can't seem to do properly: television with an old usb device, printing with an unsupported printer, dvd's [must work on that.. :KS]


incidentally, as I'm writing, it seemed to me last time I rsync'd that by default it copies files that are not older, is that right? I'd rather set it to only update files that are strictly newer

thanks

---

### Post by tigerplug on 2008-01-17
What is it that you want to do?

Do you want to sync just bookmarks and stuff or do you want to sync EVERYTHING?

---

### Post by hyper_ch on 2008-01-17
maybe better to use a fat32 partition for that stuff...

---

### Post by MarkieB on 2008-01-17
In a perfect world, all that I wouldn't sync would be the path to the downloads folder :)

hyper_ch, do you really think ntfs-3g is that flakey? It had been working so well, perhaps I was persuaded that it really was stable; now I'm not so sure

as my need for a large windows partition is not what it was when I originally partitioned the hard drive, a reorganisation is possible..


cheers

---

### Post by nikoPSK on 2008-01-17
> **hyper_ch said:**
> maybe better to use a fat32 partition for that stuff...

I would recommend

---

