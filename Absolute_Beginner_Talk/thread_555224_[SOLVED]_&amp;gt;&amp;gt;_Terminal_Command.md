---
title: "[SOLVED] &amp;gt;&amp;gt; Terminal Command"
date: 2007-09-19
forum: Absolute Beginner Talk
---

### Post by High Camp on 2007-09-19
Hi All

I will post [this ]("http://ubuntuforums.org/showthread.php?t=552788") question in a different way.

I have written a shell script that looks like this:
```
SHELL=/bin/sh
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin

dir /home/simon/.pics/ >test.list
```

It outputs a file called test.list that looks like that:
```
14,411\ Feet.JPG		 linux-logo.gif
1967Firebird03172007C.gif	 lion1.jpg
29sedan.gif			 lion2
35_Sedan.gif			 lion3
36ChevyLarge.gif		 lucifer-decal-black_LRG.gif
arg_hott_rodd_url.gif		 Marble1.jpg
arg-nomad-70-tr-url.gif		 Marble3.jpg
backdrops.list			 Marble6.jpg
beetle.gif			 n81006847_34480501_2023.jpg
cheetah1			 Om\ Mani\ Padme\ Hum1.gif
Creekrat04232007A.gif		 P1020198.JPG
Creekrat05082007A.gif		 P1020210.JPG
D.C.\ Route\ Mount\ Rainier.jpg  P1020213.JPG
dir.sh				 Photo_051107_001.jpg
DSCN0343.jpg			 ppe.gif
DSCN0357.jpg			 R004-007.JPG
DSCN0359.jpg			 rodkulture2006_LRG.gif
DSCN0364.jpg			 skull.gif
Good\ Morning.JPG		 T004-017.JPG
HenselWheelie.gif		 T004-019.JPG
hot_roc_cartoons_nov67.gif	 test.list
IMGP3304.jpg			 test.txt
IMGP3318.jpg			 Waddington\ 600.jpg
IMGP3331.jpg			 w-black-1_LRG.gif
linux-logo.2.gif
```

Is there anyway I can format the output of this file so it comes as one long list instead of two columns? 

Thanks much for any help, it is much appreciated.

---

### Post by robert_pectol on 2007-09-19
How about just:
```

for i in `dir /home/simon/.pics/`; do echo $i; done > test.list

```
Or maybe I misunderstood.

---

### Post by yabbadabbadont on 2007-09-19
```
dir -1 /home/simon/.pics/ >test.list
```
or
```
ls -1 /home/simon/.pics/ >test.list
```
Either will work.

---

### Post by High Camp on 2007-09-19
yabbadabbadont: Thank you so much, the second option did exactly what I wanted.

robert_pectol's: Thanks for the suggestion, I didn't get a chance to try it because the other ones made more sense in my mind so I tried them first.

Do either of you know where I can get a reference list of all these types of commands so I don't have to bug the community every time I have a question.

Thanks again,

---

### Post by bigboy_pdb on 2007-09-19
This might be helpful.

**Linux directories:**
[http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html](http://www.oreilly.com/catalog/debian/chapter/book/appa_01.html)
[http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/](http://ubuntu-tutorials.com/2006/12/20/explanation-of-the-ubuntu-linux-file-structure-ubuntu-all-versions/)
[http://www.linuxcommand.org/lts0040.php](http://www.linuxcommand.org/lts0040.php)
[http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html](http://www.linuxforums.org/forum/linux-tutorials-howtos-reference-material/5022-linux-directory-structure-overview.html)

**The Terminal:**
[http://infohost.nmt.edu/tcc/help/unix/unix_cmd.html](http://infohost.nmt.edu/tcc/help/unix/unix_cmd.html)
[http://www.linuxcommand.org/learning_the_shell.php](http://www.linuxcommand.org/learning_the_shell.php)
[http://www.computerworld.com/action/article.do?command=printArticleBasic&articleId=9030259](http://www.computerworld.com/action/article.do?command=printArticleBasic&articleId=9030259)
[http://www.unixguide.net/linux/linuxshortcuts.shtml](http://www.unixguide.net/linux/linuxshortcuts.shtml)

**GNOME/KDE Shortcut Keys:**
[http://www.novell.com/coolsolutions/tip/2289.html](http://www.novell.com/coolsolutions/tip/2289.html)

**HOWTOs:**
[http://www.linux.com/base/ldp/howto/HOWTO-INDEX/categories.html](http://www.linux.com/base/ldp/howto/HOWTO-INDEX/categories.html)

---

### Post by High Camp on 2007-09-20
Ok, one last thing. Is it possible to print the list as a full path? I.E. /home/simon/.pics/picutre.gif. It turns out the program using the file needs full paths (arg).

Thanks again,

---

### Post by bigboy_pdb on 2007-09-20
The following will do it provided that you're in the directory that you want to list:
```

ls -l | sed '1d; s/\([^ ]* *\)\{7\}/'"${PWD//\//\\/}"'\//; s/^\/\//\//; s/ -> .*//' > test.list

```

If you try to change the command "ls -l" so that a relative path is specified with "ls" (i.e. "ls -l ..") that command will no longer work. Also, you should be aware that if your path names have "[", "]", "\", "$", or "^" within them it could change how the command works because these are special characters in sed (in other words you should double check the output). 

A description of the command is as follows. "ls -l | sed" lists your directories in the long format and sends the output to sed. The string '1d; s/\([^ ]* *\)\{7\}/'"${PWD//\//\\/}"'\//; s/^\/\//\//; s/ -> .*//' tells sed what to do with the input.

```
1d
``` means delete the first line (which is the output from "ls -l" that prints total number of blocks).

```
${PWD//\//\\/}
``` is the directory that you're in, but the forward slashes have been replaced with backslashes followed by forward slashes (because in sed a forward slash is used to end the regular expression unless it is preceded by a backslash). For example, if you're in the directory '/home/billy' it would become '\/home\/billy'.

```
s/\([^ ]* *\)\{7\}/'"${PWD//\//\\/}"'\//
``` substitutes the first 7 occurrences of characters followed by spaces with the current directory followed by a forwardslash (because $PWD does not end in a forwardslash). For example, if you're in the directory "/home/bob" and sed reads the line:
"drwxr-xr-x  1 bob bob   3426 2000-04-11 02:03 bin"
it will change the line to "/home/bob/bin".

```
s/^\/\//\//
``` replaces two backslashes at the front of the line (after substitutions) with a single backslash. This will only occur when you are in the root directory since we had added a forward slash after $PWD (which is "/" when you are in the root directory).

```
s/ -> .*//
``` replaces " -> " and all the characters following it with nothing. This removes the information that is printed for symbolic links. For example, if you're in the directory "/home/bob" it and sed initially read the line
"lrwxrwxrwx  1 bob bob     26 2000-04-11 20:05 Examples -> /usr/share/example-content"
it would first be changed to "/home/bob/Examples -> /usr/share/example-content" and then this expression would change it to "/home/bob/Examples".

```
> test.list
``` redirects the output to a file called "test.list".

I realize that this might not be enough information if you're not familiar with sed and regular expressions, but I'm explaining it in case you are familiar with them or so that you might be able to understand what the expression is doing when learning about those subjects.

---

### Post by yabbadabbadont on 2007-09-20
> **High Camp said:**
> Ok, one last thing. Is it possible to print the list as a full path? I.E. /home/simon/.pics/picutre.gif. It turns out the program using the file needs full paths (arg).

Thanks again,

```
find /home/simon/.pics -type f -print
```

@bigboy_pdb: Waaaay too complicated a solution.  ;)

---

### Post by bigboy_pdb on 2007-09-20
I agree that would work better (I'm not used to all of the Linux commands yet), but he should also add "-maxdepth 1" to the command so it doesn't traverse subdirectories.

---

### Post by yabbadabbadont on 2007-09-20
I was guessing that he wanted to traverse sub-directories (if any).  That's why I told it to only print out files and not directories.  Either way, your additional information would be good for him to know.  :D

---

### Post by High Camp on 2007-09-20
Wow!!!

I can truly mark this as solved. Not only did you solve my problem but I learned a lot. 

bigboy_pdb: Yes it was a long solution but that's how I'll learn and I really appreciate the effort put in.

yabbadabbadont: I think the beauty of programming (and the reason I love it) is there is always a more efficient way of doing something that will move faster, use less processor time, and be easier to use. 

Thanks again for all your help,

---

