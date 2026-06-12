---
title: "kaffeine &amp; mp3???"
date: 2006-07-10
forum: Absolute Beginner Talk
---

### Post by cyberlite on 2006-07-10
Hey all

I,ve been trying to get kaffeine to play mp3, but it doesn't..
It plays wma just fine I,ve been installing some codec's but can,t get it to play mp3, realplayer has no problem but no play list......
Any help??

---

### Post by T700 on 2006-07-10
You might give Automatix a try (see my sig for link).  It will make sure you have the right codecs.  Just from a personal standpoint, I'd suggest giving Amarok a try.

Paul

---

### Post by mostwanted on 2006-07-10
I'm guessing that you're in need of the package called *libxine-extracodecs*. No need for all that Automatix jazz, it's probably easier to do it yourself.

---

### Post by cyberlite on 2006-07-10
well in kubuntu that is already installed. amarok is the same does not play mp3??:confused:

---

### Post by Jucato on 2006-07-10
> **cyberlite said:**
> well in kubuntu that is already installed. amarok is the same does not play mp3??:confused:

*libxine-extracodecs*is not installed by default in Kubuntu. You have to enable the the multiverser repository to get it.

Then try checking if Amarok and Kaffeine are using the Xine engine. In Amarok that would be in Settings > Configure Amarok > Engine. In Kaffeine, that would be in Settings > Player Engine.

---

### Post by anubis2814 on 2006-07-10
What is the multipurpose repository and how do I access it?

---

### Post by Jucato on 2006-07-10
It's *multiverse* repository, and it's a repository for programs and packages that are considered non-free or proprietary.

If you are using Kubuntu, this is how you can access that repository:
[https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/kubuntu/desktopguide/C/extra-repositories.html)
(Scroll down towards the end)

In Ubuntu, this is how it's done:
[https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html](https://help.ubuntu.com/ubuntu/desktopguide/C/extra-repositories.html)

---

### Post by erniewinner on 2006-07-10
i suppose that is unprotected wma? i guess if so the ones i have come across are all drm'd up? :confused: 

the multiverse repository is where the files you need are... you need to enable/ tell it to look there by the use of the synaptic package manager... do a quick search on this site. it's one of the simple things you will get used to soon enough! [-o<

---

