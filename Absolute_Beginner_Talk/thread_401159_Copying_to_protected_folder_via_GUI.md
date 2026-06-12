---
title: "Copying to protected folder via GUI"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by Esben Kramer on 2007-04-04
I want to put some more pictures in the /usr/share/backgrounds/ -folder, for the slide show. Only problem is, that I must be root. If I don't want to use the terminal...is there a way to just drag and drop the files there? Please help.

Thanks.

---

### Post by Bachstelze on 2007-04-04
```
sudo chown $(whoami) /usr/share/backgrounds
```

Please don't run nautilus as root.

---

### Post by Esben Kramer on 2007-04-04
Awesome. Thanks! Worked like a charm!

---

### Post by ComplexNumber on 2007-04-04
> **HymnToLife said:**
> ```
sudo chown $(whoami) /usr/share/backgrounds
```Please don't run nautilus as root.
personally, i don't really think thats advisable. i think its best that everything outside of ones home directory should be owned by root, and everything that is normally owned by root should stay that way. 
i dare say that because /usr/share/backgrounds is such a little used and trivial directory that it doesn't make any difference either way, but its good practice to *not *change the permissions/ownership of things outside of ones home directory IMO.
as for running nautilus as root, i do that often :mrgreen:........when i want to make changes to my themes and icons in /usr/share. i use 'gksudo nautilus'. there's nothing wrong with doing things that way.


[B]
Esben Kramer[/B]
i've organised my home directory so that it has a Documents folder, whereby that folder contains other folders such as MEDIA, PROGRAMMING, BACKUP, LITERATURE, etc. the MEDIA is subdivided into WALLPAPER, MUSIC, VIDS, ICONS, etc. 
thats just an idea for you.

is there any good reason why you have to put the pictures in /usr/share/backgrounds rather than placing them in your home directory? for example, do you have more than 1 user on your PC that needs access to them? or maybe short on disk space in your home folder?

---

### Post by Bachstelze on 2007-04-04
Well, I don't think it will be a major security harm if /usr/share/backgrounds is owned by the user... If runing nautilus as root, a single mistake and it's he whole system that's broken, if you just chown the dir, the worst you can to is delete it, which won't harm the system at all.

It's not a good thing to do either, I agree, I just told him what I though was the least bad :p

---

### Post by ComplexNumber on 2007-04-04
well, yes, thats a good point about making mistakes as root. 
for the purpose of running a slide show, i think by far the best option is to place ones pictures in ones home directory.....unless theres a good reason not to.

---

### Post by bodhi.zazen on 2007-04-04
What's wrong with a simple command ?:

```
sudo mv picture.jpg /usr/share/backgrounds
```

Seems simple and less invasive to the overall system then changing permissions of /usr/share/backgrounds or gksudo nautilus.

And I agree that you should give some structure to your home folder.

---

