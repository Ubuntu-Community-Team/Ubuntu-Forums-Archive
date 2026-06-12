---
title: "Wine not working"
date: 2006-09-23
forum: Absolute Beginner Talk
---

### Post by thomasaaron on 2006-09-23
OK, so here's where I am.
y
1. I dowlnoaded wine according to the instructions on the wiki, using synaptics manager.

2. I put my microsoft office 2000 cd into my drive and went to a terminal and typed: wine SETUP.EXE

3. The setup seems to work, except I get 4000 error messages along the way. Eventually, I get the little window saying installation was successful.

4. But it was not. There are a bunch of files that were downloaded for office, but not any of the main applications, Word, Excel...

5. I did a pretty thorough search through all of the directories within the .wine folder.

Any ideas?

Thanks,
Tom

---

### Post by Klaidas on 2006-09-23
Dual boot or use Open Office.
I'd prefer dual booting :)

---

### Post by ewl1217 on 2006-09-23
Port the output of the following command (replace user with your username):
```
ls /home/**user**/.wine/drive_c/Program\ Files
```

---

### Post by deadgobby on 2006-09-23
Place in your mind, that Wine does not run every thing of MS. If you do need some more help. All ways go to
[http://www.winehq.com/site/docs/wineusr-guide/index](http://www.winehq.com/site/docs/wineusr-guide/index)
 I know who has time to read through all that and a quick fix as headache cure with out a perscription is what you are looking for. At times, just reading up can solve. 
 Gobby

---

### Post by jcrnan on 2006-09-23
I would advise crossover office. Its a winebased program that will let you run stuff like office 2000 just fine :)

---

### Post by meng on 2006-09-23
Also there's a free demo version of Crossover Office available. But it's a non-free (as in beer) product.

---

