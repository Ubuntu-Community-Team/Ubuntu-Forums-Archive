---
title: "Command line ls voodoo"
date: 2007-03-31
forum: Absolute Beginner Talk
---

### Post by graabein on 2007-03-31
Hi I want to build a playlist for my mom and I have lots of albums on /home/share/mp3. From there I want to do a **ls** and get all filenames with path in a text-file. I've read **ls --help** but the closest I've come is

/home/share/mp3$ **ls -R | grep mp3 > all.txt** 

This gives me all mp3-files in *all.txt* but I lack the full path name, e.g. I get **song name.mp3** when what I want is **/home/share/mp3/artist/album/song name.mp3** -- any helpers?

:guitar: 
jimi ruuuules!!

---

### Post by lloyd_b on 2007-03-31
> Hi I want to build a playlist for my mom and I have lots of albums on /home/share/mp3. From there I want to do a ls and get all filenames with path in a text-file. I've read ls --help but the closest I've come is

/home/share/mp3$ ls -R | grep mp3 > all.txt

This gives me all mp3-files in all.txt but I lack the full path name, e.g. I get song name.mp3 when what I want is /home/share/mp3/artist/album/song name.mp3 -- any helpers?


Try:
```
find /home/share/mp3 -name *.mp3 -print > all.txt
```

The find command is better suited to this type of task that ls/grep.

Lloyd B.

---

### Post by dwisianto on 2007-03-31
find `pwd` -iname "*mp3" -printf "%p\n"

hope it helps

---

### Post by WW on 2007-03-31
Try this:
> 
$ find /home/share/mp3  -name *.mp3  > all.txt


---

### Post by graabein on 2007-03-31
That's excellent guys, thanks!

---

