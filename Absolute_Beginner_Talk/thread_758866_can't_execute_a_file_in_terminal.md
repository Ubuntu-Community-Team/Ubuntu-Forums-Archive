---
title: "can't execute a file in terminal"
date: 2008-04-18
forum: Absolute Beginner Talk
---

### Post by XiaoHu on 2008-04-18
hi,
i have created a basic PERL file from the first 'hello world' example and i can't seem to run it.
the file is marked executable, and when i try to run it i get:
idan-desktop:~/work/test> hi
hi: Command not found.

the file is definitely in the right place:
idan-desktop:~/work/test> ls -ltr
total 4
-rwxr-xr-x 1 idan idan 95 2008-04-18 20:02 hi

also, when i run it explicitly with perl it works:
idan-desktop:~/work/test> perl hi
Hello world.

how can i execute the file? (it is the same for simple shell scripts too...) :(

---

### Post by erlyrisa on 2008-04-18
./hi

PS
have a good day

---

### Post by XiaoHu on 2008-04-18
tried that already, same result...

idan-desktop:~/work/test> ./hi
./hi: Command not found.

---

### Post by SunnyRabbiera on 2008-04-18
If only I knew PEARL...

---

### Post by starcannon on 2008-04-18
Some things that may help

cd /some/directory/where/the/file/is
./thefile
in some cases as you found out you may have to be explicit:
perl ./hi

same for sh

./somefile.sh

or perhaps:

sh ./somefile.sh

direct paths work if your making a link to the file from the desktop or somethiing:

sh /some/directory/where/the/file/is.sh

Hope that helps a little.
GL and have fun scripting :)

---

### Post by seepage87 on 2008-04-18
From ~/work/test/ try ./hi instead of just hi.  The "." means your current directory.  Alternatively you could use ~/work/test/hi and that should work from anywhere.  If you want just "hi" to work from anywhere, it needs to be in a directory where commands are recognized globally, e.g. /bin/ or /usr/bin/.  If you want to keep the script in ~/work/test/, you can make a link in /usr/bin/ called hi that points to ~/work/test/hi.  Hope that helps.  If you have other questions, feel free to ask, or if it doesn't work, let me know.

---

### Post by XiaoHu on 2008-04-18
this is not a PERL question
it is the same if i make any file executable.
for example:
idan-desktop:~/work/test> echo "echo hello" > he
idan-desktop:~/work/test> chmod +x he 
idan-desktop:~/work/test> he
he: Command not found.
idan-desktop:~/work/test> source he
hello

---

### Post by erlyrisa on 2008-04-18
shebang it

[http://en.wikipedia.org/wiki/Shebang_(Unix](http://en.wikipedia.org/wiki/Shebang_(Unix))

---

### Post by XiaoHu on 2008-04-18
i linked the file to /bin/
then removed the link, now it works
did ./hi to execute 
thank you all for your help!

---

### Post by stchman on 2008-04-18
> **XiaoHu said:**
> hi,
i have created a basic PERL file from the first 'hello world' example and i can't seem to run it.
the file is marked executable, and when i try to run it i get:
idan-desktop:~/work/test> hi
hi: Command not found.

the file is definitely in the right place:
idan-desktop:~/work/test> ls -ltr
total 4
-rwxr-xr-x 1 idan idan 95 2008-04-18 20:02 hi

also, when i run it explicitly with perl it works:
idan-desktop:~/work/test> perl hi
Hello world.

how can i execute the file? (it is the same for simple shell scripts too...) :(

IN PERL scripts you need to do

#!/usr/bin/perl as the first line in the script

or 

perl <executable script name>

---

