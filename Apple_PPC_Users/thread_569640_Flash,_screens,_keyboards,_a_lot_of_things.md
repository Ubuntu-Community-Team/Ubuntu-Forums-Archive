---
title: "Flash, screens, keyboards, a lot of things"
date: 2007-10-07
forum: Apple PPC Users
---

### Post by Lo'oris on 2007-10-07
I managed to make mergedfb in non-clone mode work, and i succesfully installed kubuntu-desktop. Now sound works too, I had to load the modules (why weren't they automatically detected?). Fine.

What I couldn't do:
· install flash (and I *DO* have tried, both installing packages, useless, and compiling gnash by hand - but the configure mocks me with random errors);
· make 3d accel works (glxinfo says it's enabled, but it doesn't really work: fullscreengames are totally offscreen, I can see only the leftest part, and kde transparencies simply don't work :()

Also, I'd like to do but I don't know how:
· having a converter between osx keymap and xmodmap files. That's because I completely customized my keyboard layout, and it would be boring having to re-write it from scratch
[COLOR="White"]· enabling Firefox to post forms with a two-key stroke, such as ctrl+key on osx. Here I have to it alt+shift+key and belive me, I really don't like it **(this one is solved)**[/COLOR]
· having something like Exposè, both on screen edges and with mouse keys 4 and 5
[SIZE="1"]· I'm not totally convinced about my X screens configuration. Now it treats them as one single long desktop, but I guess it would do it better if it treated them like two different desktops (I guess I can figure it out how, but if someone have a quick answer, better :))[/SIZE]

So, if somebody wants to help me with some of those, I'll provide more details, thanks :)

---

### Post by Auria on 2007-10-07
> **Lo'oris said:**
> 
What I couldn't do:
· install flash (and I *DO* have tried, both installing packages, useless, and compiling gnash by hand - but the configure mocks me with random errors);

Have you also installed the package that looks like mozilla-gnash-plugin (can't remember its name, use the search feature - just installing the gnash package is not enough)

---

### Post by Lo'oris on 2007-10-07
I've tried every combination possible, and restarting firefox after every attempt. Belive me, it didn't work.

Maybe because, I've read that feisty includes gnash 0.7.x and the "good" version is 0.8.x. That's why I tried installing from source.

But it complained about missing libs (that I *DO* have installed), and kept complaining about them even if I disabled them in the configure!! How unpolite.

---

### Post by Lo'oris on 2007-10-08
ok, looks like topics with multiple issues get ignored. Lock this one if you wish, I'll post separate topics for each, some in more appropriate areas.

---

