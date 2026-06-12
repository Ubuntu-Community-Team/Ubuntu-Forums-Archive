---
title: "grep question"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by benevolent on 2008-03-08
Hi there!

I have 2 questions :)



[LIST][*]I need to print the list from **ps -el** but whithout showing the root processes (uid = 0)

and


[*]I need the list **ls -lc**, but showing only the current day's modified files (ex. only for Mar 8 2008 ) and not showing the directories
[/list]

how can i do that??


ps. A solution for the 2st one is **ps -ef | grep -v root**, but i'm using minix and i don't have the -f option

ps2. A solution that didn't work for the 2nd is **ls -lc | grep date**. Maybe i have to do something with the date format, but i can't figure it out!!




Thank you very much, in advance :)

---

### Post by herbster on 2008-03-08
#1

```
ps -U root -u root -N
```

#2 (perhaps not exactly what you want but does the job)

```
find . -mtime -1 -print
```

Replace "print" with "ls" if you want.

---

### Post by benevolent on 2008-03-08
hm.. first of all, thank you for your answer...


second, i forgot to mention that i am using minix under vmware (under ubuntu :P ) and these commans, doesn't seem to work (obsiously at ubuntu console it's working)..


for the ps command, the only options i have are -aeflx
also the mtime doesn't exist too... maybe something with the ls -lc...

thx again!

---

### Post by herbster on 2008-03-08
I think you're too limited to do it then. "ls -ltr" sorts by modification so at least you can see the files in order of modified date with the most recent at the bottom.

---

### Post by benevolent on 2008-03-09
Eventually, the find . -mtime -1 works ;)

the ps command though has only -aeflx options :/

if i use **top | grep -v root** is it correct?

---

### Post by unutbu on 2008-03-09
Do you have perl?
If so, put this in a file called 'show-no-root'
```

#!/usr/bin/perl
while (<STDIN>) {
      next if (/^root/);
      print;
}

```

then ps -ef | show-no-root works.

---

### Post by benevolent on 2008-03-10
yes, but i'd like using system commands.... thanks anyway :)

---

### Post by unutbu on 2008-03-10
```

ps -ef | sed '/^root/d'

```

This works as long as there is no user named 'rootabaga'
Ah, so I suppose a space after root is called for...

```

ps -ef | sed '/^root /d'

```

---

