---
title: "How to change directory"
date: 2008-04-07
forum: Absolute Beginner Talk
---

### Post by webmiester on 2008-04-07
Hi Guys,

I know this sounds really silly,  but from the terminal, I cant seem to change directory when the directory name consistes of 2 words.

My current problem is the directory "Program Files"

When I type: "cd Program Files", it just gives me a "No such directory error"

In windows, I would have resolved this using cd Progra~1, but in Linux,m I dont know how to solve it.

Any tips?

---

### Post by wormser on 2008-04-07
There are a few ways to make this work.

1.  Use the tab key.  Start typing the name then hit tab for auto completion. 
```
cd Pro<tab key>
```

2.  Use "quotes" around the name.  
```
cd "Program Files"
```

3.  Use \ before the space.  
```
cd Program\ Files
```

---

### Post by Paqman on 2008-04-07
The \ will escape any bad characters, btw, not just spaces. But tab autocomplete has is always a winner!

---

### Post by coolen on 2008-04-07
Yeah, the terminal will take separate words as separate arguments (which doesn't make sense for cd).

You need to let it know this is one argument either with quotation marks or by escaping the space.

---

### Post by jakupl on 2008-04-07
the explanation is:

the terminal seas a space as, a seperator between different commands. So it messes up when a filename has a space.

use the "\" or simply encase it with " "" " like wormser says.

the tab key is a great timesaver. And it eliminates potential mistakes :D

---

