---
title: "Is it possible to set a recovery point for further changes... ?"
date: 2006-11-05
forum: Absolute Beginner Talk
---

### Post by LLRNR on 2006-11-05
Hi all, again !

I just managed to bypass a horrible problem I had (I couldn't install software at all)... well that passed away, I'm pleased with my *sigh* evolution, but I spent almost half a day on this fixing problem and now I want to know if it's possible to somehow set up a recovery point for the further changes that I will surely apply to my Dapper.

I don't know if I expressed this in clear terms, but what I really want to know is wether it's possible to backup my system in case I do a stupid thing (for example install another blocking package that would virtually suspend all my efforts to install anything else, or do a stupid thing that could crash xwindows and so on).

I know it's a very dumb question, but since I'm new to Ubuntu I just wonder if that's possible or not.

Thanks in advance,

LLRNR

---

### Post by aysiu on 2006-11-05
Yes, it's very possible.

One of these two links should help:
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage)
[http://ubuntuforums.org/showthread.php?t=81311](http://ubuntuforums.org/showthread.php?t=81311)

---

### Post by podunk on 2006-11-05
[http://www.ubuntuforums.org/showthread.php?t=35087&page=21](http://www.ubuntuforums.org/showthread.php?t=35087&page=21)

See post #210 on that page. It takes one line of code and less than 30 minutes to back up my machine - and you can surf the web or play a game while you're doing it. :)

If you still have Windows installed and have it mounted pay attention to it's mount directory. If it's different than the one of the "exclude=" statements you'll end up with Windows in your back up. Also - remove any movies from your DVD player. :-D

What I do is edit fstab and restart before I do it. Place a # in front of any partition you don't want to back up.

Restores perfectly to.

---

### Post by LLRNR on 2006-11-05
Thanks, guys !! I sure have a whole lot of material to study in order to backup my system before doing anything stupid again !! Thank you very much !

---

