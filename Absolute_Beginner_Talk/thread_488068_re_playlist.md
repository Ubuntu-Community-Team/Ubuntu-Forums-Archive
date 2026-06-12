---
title: "re playlist"
date: 2007-06-29
forum: Absolute Beginner Talk
---

### Post by robertc36 on 2007-06-29
Have been following this guide [http://ubuntuforums.org/showthread.php?t=73098&page=2](http://ubuntuforums.org/showthread.php?t=73098&page=2)

i do not understand this part about the playlist  

> find /path/to/your/mp3s -type f -name "*.mp3" > /path/to/your/mp3s/play.lst

My mp3s are stored in a mounted drive and so am having trouble getting this to work.
Decided to do it in parts and managed to cd into ntfs drive and then ran>  -type f -name "*.mp3" > /path/to/your/mp3s/play.lst[
I got the following error 
> Usage: command-not-found [options] <command-name>

command-not-found: error: no such option: -t
Help Please lol
No seriously am tearing hair out in clumps

---

### Post by kpkeerthi on 2007-06-29
Change ```
-type f -name "*.mp3" > /path/to/your/mp3s/play.lst[ 
```
to something like ```
find -type f -name "*.mp3" > /path/to/your/mp3s/play.lst
```

Did you notice the difference in the two commands above?

---

### Post by robertc36 on 2007-06-29
Thanks worked 
Yeah noticed that i had left out the find tag from the command .
Sometimes it takes someone else to notice so i appreciate the response

---

