---
title: "Cutting Movie Segments?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-01-26
Is there any open source (or more simply put:  Free) programs that run on ubuntu that can cut segments out or butt two movies up to one another for "one" movie?

There's just some movies that I have on my computer (which I own the actual DVD which was purchased legally, of course) that I'd like to "clip" a few segments out (fight scenes and the like) - and was wondering if that was possible.

Also, as I'm sure you know - sometimes movies come as a dual package set (part 1 and part 2), so I was wondering if there's any way to butt them up against one another for "one" 1.4gb file (instead of 2 700mb files).  I don't care if there's a pause between or whatever - I just hate changing it, and it's easier to manage 1 file, than 2, obviously.

---

### Post by yabbadabbadont on 2008-01-26
1) Cinelerra.  Don't know if it is in the repositories though.

2) If the files are avi files, then avimerge can do it.  It is part of the transcode package.

---

### Post by jeffus_il on 2008-01-26
Have you tried CineLerra:
[http://heroinewarrior.com/cinelerra.php3](http://heroinewarrior.com/cinelerra.php3)

---

### Post by jeffus_il on 2008-01-26
You can get the .deb here:
[http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/]("http://www.kiberpipa.org/%7Eminmax/cinelerra/builds/pentium4/")
but the install is problematic, lacking library dependencies.

---

### Post by Syndacate on 2008-01-27
> **jeffus_il said:**
> You can get the .deb here:
[http://www.kiberpipa.org/~minmax/cinelerra/builds/pentium4/]("http://www.kiberpipa.org/%7Eminmax/cinelerra/builds/pentium4/")
but the install is problematic, lacking library dependencies.

Is there any way to get around this issue?  All the forum sites with the error msg (**dependancy is not satisfiable:  libguicast**) are in German.

Is there any way to dl avimerge from a deb?  Or transcode from a deb?  I downloaded a transcode.tar.bz2 file but I have no idea how to configure it.

---

### Post by yabbadabbadont on 2008-01-27
transcode is in the repositories.  Just make sure that you have all of them enabled.  (Universe and Multiverse)  Then you should be able to install it using Synaptic or apt-get or aptitude or adept or ...  :D

---

### Post by Syndacate on 2008-01-28
> **yabbadabbadont said:**
> transcode is in the repositories.  Just make sure that you have all of them enabled.  (Universe and Multiverse)  Then you should be able to install it using Synaptic or apt-get or aptitude or adept or ...  :D

Ah thanks, avimerge was EXACTLY what I was looking for - I couldn't think of the word "concatenate" when I posted this.  Usually I HATE console based programs (GUI Wins :P) but the syntaxing was rather simple - and with converIT I was able to convert them from MPG to AVI and slam 'em together so I have a whole 1.4GB movie now O.o.  Which is of course 100% legal since I actually own the DVD.

Thanks a lot, you rule.

Now, for cinelerra - any way to get around the "depency not satisfiable" problem?

---

### Post by yabbadabbadont on 2008-01-28
I don't know.  I'm not running ubuntu currently.  I think that there might be a version of cinelerra in the repos, probably very old.  If there is, you could use ```
sudo apt-get build-dep cinelerra
``` to install all the development libraries needed to build it from source.  Then you could try building the latest and greatest version from source.

---

### Post by Syndacate on 2008-01-28
> **yabbadabbadont said:**
> I don't know.  I'm not running ubuntu currently.  I think that there might be a version of cinelerra in the repos, probably very old.  If there is, you could use ```
sudo apt-get build-dep cinelerra
``` to install all the development libraries needed to build it from source.  Then you could try building the latest and greatest version from source.

I don't know how to build stuff from source 'n such..

Any more advice?

---

### Post by yabbadabbadont on 2008-01-28
A quick search turned up this:

[http://ubuntuforums.org/showthread.php?t=596160&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=596160&highlight=cinelerra)

(You did remember to search, right?  ;))

---

### Post by forrestcupp on 2008-01-28
Cinelerra is an excellent non-linear video editor if you need to do complicated stuff.  But you don't need to do complicated stuff, so I would suggest you don't use it.  That is like buying a Lamborghini just to drive to the corner market once a week.

I suggest using [Kdenlive](http://www.kdenlive.org/).  It is great for simpler things like you need, and it is in the repositories, so you can use apt-get or Synaptic.

---

### Post by Syndacate on 2008-01-29
> **yabbadabbadont said:**
> A quick search turned up this:

[http://ubuntuforums.org/showthread.php?t=596160&highlight=cinelerra](http://ubuntuforums.org/showthread.php?t=596160&highlight=cinelerra)

(You did remember to search, right?  ;))

Yes, I found that, but I kept getting the following error:
**cinelerra: symbol lookup error: /usr/lib/libguicast.so.1: undefined symbol: glDeleteShade**

[quote=forrestcupp]Cinelerra is an excellent non-linear video editor if you need to do complicated stuff. But you don't need to do complicated stuff, so I would suggest you don't use it. That is like buying a Lamborghini just to drive to the corner market once a week.

I suggest using Kdenlive. It is great for simpler things like you need, and it is in the repositories, so you can use apt-get or Synaptic. [/quote]

It seems to do what I need it to - but I can't figure out how to cut it out, lol, I feel like a retard :(.

---

### Post by Syndacate on 2008-01-30
Ha, can anybody give me a quick rundown on how to chop something out with **kdenlive**?  I don't see it necessary to make a whole new post :(.

---

### Post by Syndacate on 2008-01-31
*sniffle sniffle*

Anybody?

---

