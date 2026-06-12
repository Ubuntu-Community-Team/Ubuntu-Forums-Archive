---
title: "How do I install mplayer in Kubuntu?"
date: 2006-06-11
forum: Absolute Beginner Talk
---

### Post by henkk78 on 2006-06-11
Hi, 

How do I install mplayer in Kubuntu? 

It's not listed in Adept. (I have enabled universe and multiverse repositories, and added PLF repos as well)

Help much appreciated! 

Henk

---

### Post by hauger on 2006-06-11
funny you should ask....I'm looking for it too.  The real weird part though is that it WAS listed and installed nicely in the 64bit version of 6.06 that I just downgraded from.  How odd is that?  Mplayer isn't fully ported to 64bit yet, but is available where it isn't available in 32bit.

Does anyone know where to find Mplayer (without resorting to downloading it off the Mplayer site)?

---

### Post by ltmon on 2006-06-11
You should be able to simply enable the universe repository and:
```

sudo apt-get install kmplayer

```

Which will drag down mplayer and the KDE frontend to it.

Or follow this: [https://wiki.ubuntu.com/MplayerInstallHowto](https://wiki.ubuntu.com/MplayerInstallHowto)

---

### Post by hauger on 2006-06-12
ahh...so that's the catch.  Kmplayer = mplayer.  But what about the mplayer firefox plugin?  It doesn't seem to be listed.

---

