---
title: "need the command for removing everything within a directory"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by bruenig on 2006-07-25
What is a command to remove everything within a directory without deleting the directory itself?

---

### Post by Titus A Duxass on 2006-07-25
Try sudo rm -rf directory name, but be careful there is no undo feature.

---

### Post by bruenig on 2006-07-25
Found the answer on irc, rm -rf directory/*
Titus, doesn't yours delete the directory as well?

---

### Post by IYY on 2006-07-25
Yeah, it would.

---

### Post by Titus A Duxass on 2006-07-25
Sorry, I mis-read your question.  But if you remove everything in the directory you might as well remove the directory and then replace it with mkdir XXX.

---

### Post by forkd on 2006-07-25
try 

deltree c:\windows 

:)  

I thought it was funny.

'til I read this post I used the rm with the recursive and force options then mkdir but now I'll use the /*

Thanks

---

### Post by richbarna on 2006-07-25
> **forkd said:**
> try 

deltree c:\windows 

:)  

I thought it was funny.

'til I read this post I used the rm with the recursive and force options then mkdir but now I'll use the /*

Thanks

Ahh the beauty of *wildcards* :)

---

### Post by bruenig on 2006-07-26
yeah I had this
```
rm -rf directory;mkdir directory
```
and it worked but I figured I should probably figure out a better way to do it for some reason

---

### Post by aysiu on 2006-07-26
> **Titus A Duxass said:**
> Sorry, I mis-read your question.  But if you remove everything in the directory you might as well remove the directory and then replace it with mkdir XXX. Not necessarily. For example, I have a shell script that empties my trash can: ```
#!/bin/bash
rm -rf ~/.Trash/*
``` I certainly don't want to remove the Trash folder--just the stuff inside.

---

### Post by bruenig on 2006-07-26
> **aysiu said:**
> Not necessarily. For example, I have a shell script that empties my trash can: ```
#!/bin/bash
rm -rf ~/.Trash/*
``` I certainly don't want to remove the Trash folder--just the stuff inside.
Aysiu, you could just add mkdir ~/.Trash at the end of the script and it would still work.

---

### Post by aysiu on 2006-07-26
> **bruenig said:**
> Aysiu, you could just add mkdir ~/.Trash at the end of the script and it would still work.
Why would I want to do that?

---

### Post by bruenig on 2006-07-27
> **aysiu said:**
> Why would I want to do that?

I agree with you aysiu, that is why I asked for the better command than removing the directory, then remaking it but his point is also true.

---

