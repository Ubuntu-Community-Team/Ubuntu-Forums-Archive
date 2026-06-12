---
title: "Run sh script without terminal"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by Aeauvian on 2008-01-25
Hey all.  I'm trying to use a java compiler (for school) that is executed with an sh script.  I want to be able to make a shortcut to the script, and have that execute the program.  My problem is that when I do that, it opens a terminal window that stays open, and that I can't close without it exiting the program.

There's probably been similar posts, but searching only gives me anything related to bash scripts and the terminal, none of which match what I am looking for.

Thanks in advance!

---

### Post by emarkd on 2008-01-25
If whatever binary your script is calling holds the terminal, it'll stay open until the binary exits.  You can edit the script and force the script to fork the binary from the current shell.  You can usually do this by following the binary with an &

#!/bin/sh
/home/username/binary

becomes

#!/bin/sh
/home/username/binary &

Hope this helps.  If not, maybe you could post the script and we'll see what we can do with it.

---

### Post by bodhi.zazen on 2008-01-25
> **Aeauvian said:**
> Hey all.  I'm trying to use a java compiler (for school) that is executed with an sh script.  I want to be able to make a shortcut to the script, and have that execute the program.  My problem is that when I do that, it opens a terminal window that stays open, and that I can't close without it exiting the program.

There's probably been similar posts, but searching only gives me anything related to bash scripts and the terminal, none of which match what I am looking for.

Thanks in advance!

Several options, NOHUP, (), or {}. More complex is screen. dtach is a simplified screen.

NOHUP *.sh

(*.sh &)

{
*.sh
}

for screen :  

[http://www.linuxjournal.com/article/6340](http://www.linuxjournal.com/article/6340)
		[http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html](http://www.linuxjournal.com/articles/lj/0105/6340/6340t1.html)

	[http://gentoo-wiki.com/TIP_Using_screen](http://gentoo-wiki.com/TIP_Using_screen)

	See also dtach :
		[http://ubuntuforums.org/showpost.php?p=3208354&postcount=10](http://ubuntuforums.org/showpost.php?p=3208354&postcount=10)


So, take your pick.

---

