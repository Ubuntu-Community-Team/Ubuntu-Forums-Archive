---
title: "IcedTea Java - at last native on powerpc?"
date: 2008-01-13
forum: Apple PPC Users
---

### Post by fuoco on 2008-01-13
I stumbled upon this IcedTea new thing which seems to be the OpenJDK by sun (which was recently open source) made completely free and workable on linux, with ports to powerpc too. And there seems to be packages for it for gutsy already. 
Has anyone had success with that? I am actually interested in a browser plugin and I can't seem to find one that goes with it... anyone?

---

### Post by Washer on 2008-01-13
Yeah i spent a few hours trying to get java to work & just gave up.

---

### Post by Washer on 2008-01-14
Should have spent a few more hours. Try apt-get install gcjwebplugin. It's not perfect, but it worked for what I needed.

---

### Post by fuoco on 2008-01-15
> **Washer said:**
> Should have spent a few more hours. Try apt-get install gcjwebplugin. It's not perfect, but it worked for what I needed.

there are three in synaptic: gcjwebplugin, gcjwebplugin-4.1, gcjwebplugin-4.2
which one works? what's the difference?

---

### Post by Auria on 2008-01-15
Well, one is verison 4.1 the other is version 4.2, and I reckon the one with no name is a shortcut to the most recent

---

### Post by Washer on 2008-01-15
The shortcut didn't seem to work for me for some reason so I went with 4.2. YMMV

---

### Post by fuoco on 2008-01-15
> **Washer said:**
> The shortcut didn't seem to work for me for some reason so I went with 4.2. YMMV

for me it's 4.2 that didn't work (no plugin show up in about:config). does it work for you? the normal gcjwebplugin didn't work though it did give a plugin. i tried only with the java test in sun website.

---

### Post by Washer on 2008-01-15
Yeah 4.2 worked for me. I mainly use it [here]("http://www.chessgames.com/perl/chessgame?gid=1151935"). Does the site work for you?

---

### Post by fuoco on 2008-01-15
> **Washer said:**
> Yeah 4.2 worked for me. I mainly use it [here]("http://www.chessgames.com/perl/chessgame?gid=1151935"). Does the site work for you?

with gcjwebplugin-4.2 the symlink i got was broken. did you manually fix it ?

---

### Post by Washer on 2008-01-15
No it was pretty much just click & install though I wouldn't be surprised if more was broken. PPC ubuntu needs some work. I had to get the package names from installing java on my desktop.

---

