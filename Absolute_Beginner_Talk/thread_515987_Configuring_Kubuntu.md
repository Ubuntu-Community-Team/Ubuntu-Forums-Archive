---
title: "Configuring Kubuntu"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Haama on 2007-08-02
Hi!
I'd like to use Firefox and Dolphin (or some other file manager) instead of Konqueror cause I really don't like it.. I think I can easily deal with the web browser issue but how do I change the file manager? I'm using Kubuntu 7.04.
Thanks in advance.

---

### Post by apswartz on 2007-08-02
I'm not sure there is such a thing as a default file manager. Just add an icon to your toolbar.

BTW, why would you prefer Dolphin over Konqueror?

---

### Post by Inxsible on 2007-08-02
you can install any number of file manager simultaneously

```
sudo aptitude install dolphin
```Simply replace the word dolphin with any other file manager that you wish to install

nautilus is the default for Gnome

thunar is the default for Xfce

there maybe hundred others too.

---

### Post by apswartz on 2007-08-02
ok, I just tried out dolphin and it is pretty neat.

---

### Post by maestrobwh1 on 2007-08-02
I am a BIG fan of krusader.  Give it a try if you like the twin panel approach.

---

### Post by n.aggel on 2007-08-02
why you installed kubuntu, if you didn't want to use konqueror?
{question out of curiosity, i don't to play the smart-***}

---

### Post by apswartz on 2007-08-02
n.aggel, dolphin is another KDE file manager (like Krusader) and it takes advantage of the same underlying KDE system that Konqueror does.

---

### Post by n.aggel on 2007-08-02
i didn't know that... using it gives you more options?

---

### Post by Haama on 2007-08-02
Thanks for all the replies.. That was really fast :D

@apswartz
Thanks, I'll go with that.. I guess I'll have to modify few keyboard shortcuts too.
And the reason i prefer Dolphin over Konqueror is that I've been using Windows and Ubuntu and I just like using a seperate web browser and file manager. I could just use konqueror as my file manager but I thought I'd give dolphin a try.

@Inxsible
Thanks, I usually use apt-get though :P

@maestrobwh1
Cool, I'll try it too.

@n.aggel
I really enjoyed using Ubuntu so I also wanted to try Kubuntu. I like it more than Ubuntu, Amarok rules etc.. just don't like Konqueror..

---

### Post by Snipersnest on 2007-08-02
I'm really new to a lot of linux stuff. But honestly I don't like Konquerer, its ugly to me.
 
But thanks for letting me know about Dolphin. Its neat project and I like it a lot.
 
Krusader reminds me of FlashFXP for Windows.. Its a good tool if your wanting more than just a plain file browser. Since my wife uses my computer I'm trying to make it as simple as posible.
 
Are there any other things you can change around to make the look or feel better?  I want to try Beryl but I'm way to new I think to bother. Plus I'm on Gusty Gibbon since its all my laptop would run.
 
Thanks

---

### Post by n.aggel on 2007-08-02
Back in windows is used Directory Opus...personal opinion it was simply the best file browser i 've ever used.... I like Konqueror because it resembles Directory Opus plus it is a LOT faster than firefox when it comes to browsing the web. The only problem is that lately i haven't had KDE, so i got accustomed to nautilus. Which is a nice{and simple!} browser...

---

### Post by apswartz on 2007-08-02
> **n.aggel said:**
> The only problem is that lately i haven't had KDE, so i got accustomed to nautilus. Which is a nice{and simple!} browser...

You can have KDE...
```
sudo aptitude install kubuntu-desktop
```

Before you know it you will be running your favorite desktop, using all of your favorite apps ;-)

---

### Post by n.aggel on 2007-08-03
if install together 2 desktop managers there will be no performance decrease?

---

### Post by Frak on 2007-08-03
Try this, this is Krusader, and firefox together, and dolphin for taste
```
sudo aptitude install krusader firefox dolphin
```

---

### Post by Frak on 2007-08-03
> **n.aggel said:**
> if install together 2 desktop managers there will be no performance decrease?
Fortunately, it won't. Apps are only started when they're needed. Not like in Windows, when they are started because you may use it later.

---

