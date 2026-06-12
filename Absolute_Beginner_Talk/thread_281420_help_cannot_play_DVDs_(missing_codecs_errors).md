---
title: "help: cannot play DVDs (missing codecs errors)"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by alfred_jp on 2006-10-21
based on the book "Ubuntu Linux for Non-Geeks," i tried setting up the necessary codecs/packages that are supposed to allow me to watch encrypted DVDs/foreign DVDs (living in Japan, mostly Region 2).

however, when i do so - i always get the error:

```
Totem cannot play this type of media (DVD) because you do not have the appropriate plugins to handle it.
```

so, how do i know which plugins am i missing?

thanks in advanced...

---

### Post by alfred_jp on 2006-10-21
okay - i find that the DVD plays properly in GXine Movie Player; but for some reason i get the above noted error when I use Totem...

any ideas?

---

### Post by Ocxic on 2006-10-21
install libdvdcss from synaptic; if it's already installed, don't use totem

---

### Post by jqk on 2006-10-21
You could use VLC Media player, which has it's own codec package, and is ready to play almost all types of format.

sudo apt-get install vlc

(If you were wondering)

---

### Post by raul_ on 2006-10-21
Plus, you can try to install Automatix2 and install every single codec they have =P For some reason some codecs are illegal in the US though. But hey, that's up to you ;)

---

### Post by alfred_jp on 2006-10-21
thanks for the replies, guys!!!

i think ill take the easy route, un-install Totem, and just use GXine for my DVD player (since it plays other region's DVDs, too)... and if another error like "no codecs" comes up again - then i may try the others.

btw, what is this vlc app? is it good?

being a noob and all - i usually get stuck with the built-in apps at the moment. ](*,)

---

### Post by raul_ on 2006-10-21
i've used Mplayer, VLC, Totem, and now i use xine, so i guess u're ok :)

---

