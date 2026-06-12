---
title: "Fonts rendering in elementary OS"
date: 2012-12-12
forum: Any Other OS
---

### Post by iOmega ARG on 2012-12-12
First of all! Hi! I'm new here.

My problem is that i'm trying elementary OS and the fonts are no that smooth like in Ubuntu stock or how i got 'em in Arch when i installed some patches.

I'm trying to install Infinality patch but i can't get it to work! I got freetype source and both Infinality packages.

I compiled freetype, patched and copied files like it says in Infinality forums that i have to do it but i get something like preloade LD_PRELOAD thing and i can't log in into OS. 

This is the error :

```
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
```

I edited the .sh of Infinality to point lib instead of lib64 that doesn't exist, i pointed to x86_64-linux-gnu folder where is also installed this library and pointed to a created lib64 folder with the library in it, none of 'em worked! 

I don't know that doing that was wrong or right, i just tried. If anyone can help me, i'd appreciate it!

---

### Post by Chdslv on 2012-12-12
> **iOmega ARG said:**
> First of all! Hi! I'm new here.

My problem is that i'm trying elementary OS and the fonts are no that smooth like in Ubuntu stock or how i got 'em in Arch when i installed some patches.

I'm trying to install Infinality patch but i can't get it to work! I got freetype source and both Infinality packages.

I compiled freetype, patched and copied files like it says in Infinality forums that i have to do it but i get something like preloade LD_PRELOAD thing and i can't log in into OS. 

This is the error :

```
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
ERROR: ld.so: object '/usr/lib64/freetype-infinality/libfreetype.so.6.8.0' from LD_PRELOAD cannot be preloaded: ignored.
```I edited the .sh of Infinality to point lib instead of lib64 that doesn't exist, i pointed to x86_64-linux-gnu folder where is also installed this library and pointed to a created lib64 folder with the library in it, none of 'em worked! 

I don't know that doing that was wrong or right, i just tried. If anyone can help me, i'd appreciate it!

There isn't a elementary os yet, you have a beta 1, which the devs themselves say buggy. When, it come out, we might get one with tiny amounts of bugs, so trying out what you have would be a headache. 

The best place right now is to ask here; [http://elementaryos.org/journal/luna-beta-1-released](http://elementaryos.org/journal/luna-beta-1-released)
and the devs might reply to your question, as they know what are the bugs.

Ch

---

### Post by iOmega ARG on 2012-12-12
> **Chdslv said:**
> There isn't a elementary os yet, you have a beta 1, which the devs themselves say buggy. When, it come out, we might get one with tiny amounts of bugs, so trying out what you have would be a headache. 

The best place right now is to ask here; [http://elementaryos.org/journal/luna-beta-1-released](http://elementaryos.org/journal/luna-beta-1-released)
and the devs might reply to your question, as they know what are the bugs.

Ch

error is also in other distros, it's in infinality forums, it doesn't belong to elementary OS, lib64 isn't anymore in Ubuntu 12.10 or .04 i don't remember, so the problem has to be the library or a line in the script, dunno what but i'm pretty sure it's nothing related to elementary being beta.

---

