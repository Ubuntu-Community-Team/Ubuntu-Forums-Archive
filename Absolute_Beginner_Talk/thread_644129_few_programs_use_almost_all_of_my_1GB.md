---
title: "few programs use almost all of my 1GB"
date: 2007-12-18
forum: Absolute Beginner Talk
---

### Post by netimen on 2007-12-18
I have quite a few programs running - I'm just browsing the web and listening to music.
But my computer runs quite slow and swaps often because oprea uses ~200M, amarok 2 instances (why 2?) use ~270MB, nautilus - 130, mysqld - 126, stardict - 100, terminal - 100! (according to top)
I had to unload pidgin wich used ~150 MB
I have disabled compiz and unloaded java and it's applications

Can I help the situation?

---

### Post by spydon on 2007-12-18
> **netimen said:**
> I have quite a few programs running - I'm just browsing the web and listening to music.
But my computer runs quite slow and swaps often because oprea uses ~200M, amarok 2 instances (why 2?) use ~270MB, nautilus - 130, mysqld - 126, stardict - 100, terminal - 100! (according to top)
I had to unload pidgin wich used ~150 MB
I have disabled compiz and unloaded java and it's applications

Can I help the situation?

Do you have little RAM?

---

### Post by netimen on 2007-12-18
I have little **free** RAM =) I thought 1 GB is enough for listnening to music and browsing the web

---

### Post by spydon on 2007-12-18
> **netimen said:**
> I have little **free** RAM =) I thought 1 GB is enough for listnening to music and browsing the web

I thought you said that 1gb was swap? :S

---

### Post by hyper_ch on 2007-12-18
free ram = wasted ram

linux handles ram more efficiently and hence if you have free ram your system isn't performing well... it should cache stuff...

---

### Post by daimaru on 2007-12-18
> **netimen said:**
> I have quite a few programs running - I'm just browsing the web and listening to music.
But my computer runs quite slow and swaps often because oprea uses ~200M, amarok 2 instances (why 2?) use ~270MB, nautilus - 130, mysqld - 126, stardict - 100, terminal - 100! (according to top)
I had to unload pidgin wich used ~150 MB
I have disabled compiz and unloaded java and it's applications

Can I help the situation?


omg you have some weird problems here. i cant answer them but i can tell you that:
amarok uses 2.6 mb on my system...
and quite frankly i would be worried if it used 260mb as i would be worried about all the other programs you are running with +100mb ... wtf
are you sure you did not confuse it for 2.7 1.0 etc instead of 270 and 100mb ?

---

### Post by Majorix on 2007-12-18
I too have a feeling you are confusing some things.

---

### Post by diatribe on 2007-12-18
the numbers in top are percentages not amounts

---

### Post by forestpixie on 2007-12-18
> the numbers in top are percentages not amounts

are they - I've just a quick look at mine 

amarok appears to be using 178M of virtual - more than once :)

perhaps the OP is mistaking the memory types that top reports, but I think that his problem is more likely to be 

> But my computer runs quite slow and swaps often

can't help him with that though

---

### Post by diatribe on 2007-12-18
well the best way to check swap/actual mem usage is free -m, if you really are using 1gb of ram to browse the internet and listen to music I would suggest finding new programs because that is outrageous

---

