---
title: "How do i make dapper play DVD"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by K-J on 2006-07-19
I have installed codecs so i can play some .avi and other formats aswell but not DVD. i have also installed automatix so how should i do to play thouse DVDs

---

### Post by joft on 2006-07-19
Hi,

I think, you are searching for this:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

There, go to: "Playing encrypted DVDs"

---

### Post by Sonic Alpha on 2006-07-19
I believe Automatix sets everything up that you need to do in order to play DVDs.

You need to use software like VLC to be able to watch them.

If that hasn't worked, you'll need to follow the steps laid out [here]("https://help.ubuntu.com/community/RestrictedFormats").

---

### Post by Frank Golden on 2006-07-19
This may or may not apply to your machine. My laptop an
Acer Aspire 5672 came from factory with the DVD drive 
region not set. XP didn't seem to care but in Ubuntu I 
couldn't play DVD's even with all the needed codec's etc.
until I used one of my region choices. In Ubuntu it won't
automatically select the region of the first DVD you use.
You can install and use regionset from Synaptic to set your DVD
region. Do a search for regionset in Synaptic. Just remember
you only need to do this once unless you use a DVD from a 
different region in the future. You only have 5 changes available at which point the last one becomes permanent.
The USA is region 1.

---

### Post by anschelsc on 2006-07-19
You might want to try Easy Ubuntu. I don't have the exact URL; Google it.

---

### Post by Frank Golden on 2006-07-19
> **anschelsc said:**
> You might want to try Easy Ubuntu. I don't have the exact URL; Google it.
[http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) It is supposed to be safer
than automatix.?

---

### Post by Furball666 on 2006-07-19
I used Easy Ubuntu and it didnt download all the codecs I needed nor did it set up my OS to be able to play encrypted DVD's. I still had to go in there and manually do those so it may not work perfectly on everyone's system

---

### Post by Anduu on 2006-07-19
What are you trying to play them with...Totem?

Forget Totem is even on your computer.It is useless.

For months now I have been playing DVD's with MPlayer or VLC no problems but Totem still doesn't have a clue :rolleyes:

---

### Post by Turtle.net on 2006-07-19
To play the DVDs with totem I have done (and I am not saying that's the solution ... I only say that it woked for me)
```
sudo apt-get install totem-xine libdvdcss2 libdvdnav4 libdvdread3 libxine-extracodecs
```
as I said...it worked for me
Note : I also installed xine

Hope this help :)

---

### Post by Frank Golden on 2006-07-20
> **Turtle.net said:**
> To play the DVDs with totem I have done (and I am not saying that's the solution ... I only say that it woked for me)
```
sudo apt-get install totem-xine libdvdcss2 libdvdnav4 libdvdread3 libxine-extracodecs
```
as I said...it worked for me
Note : I also installed xine

Hope this help :)I like xine totem sucks playback
is jerky on my machine with totem if I can get it to play
at all.

---

