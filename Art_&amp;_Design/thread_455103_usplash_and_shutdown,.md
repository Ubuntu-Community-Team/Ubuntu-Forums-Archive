---
title: "usplash and shutdown,"
date: 2007-05-26
forum: Art &amp; Design
---

### Post by Hairy_Palms on 2007-05-26
, im not sure whats wrong with usplash here, it looks and works fine on startup always, but on shutdown its colours turn into a mess of pinks purple and white, im using the default feisty splash, can anyone tell me whats wrong?

Ive found a few bug reports but they all say it happens on startup and shutddown whereas mine are only on shutdown, 

ive tried passing vga codes to the kernel and also running sudo dpkg-reconfigure linux-image-$(uname -r).

---

### Post by exploder on 2007-05-26
It sounds like a graphics card issue. I had the exact same problem you are describing when I ran Fedora Core 6. I never did find a solution....

---

### Post by Hairy_Palms on 2007-05-26
hmm, i have the same trouble with the nvidia and nv graphics drivers, its nothing serious, just a bit annoying but thx anyway :) i remember a similar problem now you said that with mandrake 8.2, but i didn't get to fix it then, and i cant remember exactly now.

---

### Post by freeride on 2007-05-28
I've got the same problem, and it makes me mad! With edgy everything was fine, when I upgraded to feisty the logout issue has appeared. I've tried to uninstall usplash and reinstall it. But it didn't work out. I don't believe it's a graphic card issue, I have an ATI, and if I shut down the computer after one minute of activity, the splash screen works fine; if I use the computer for a longer period, the problem appears.

I would like to solve it, but I'm not an expert at all...if anybody has any clue...

thx

---

### Post by eRadaR on 2007-12-18
a have this problem too.
my sony vaio sz370 have 2 video cards - nvidia 7400go & integrated intel 945gm.
when i shutdowning on nvidia - usplash is perfectly? but when i swithing to intel video card - shutdown usplash is very ugly.
i dont know what to do? i searched all the forum, but i cant find anythink about this issue, only this thread.



I attached 2 files:
1 - booting on intel card
2 - shutdowning on intel card

---

