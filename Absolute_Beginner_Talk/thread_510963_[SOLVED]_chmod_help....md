---
title: "[SOLVED] chmod help..."
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by opossumjack on 2007-07-27
hi, how can I set permissions with chmod for every file there is in one folder and even subfolders? I also need to include hidden files.

Can anyone helo me please?


thanks in advance

---

### Post by Mornedhel on 2007-07-27
People, people, people.


There's an invaluable source of knowledge for CLI commands, let me introduce :

man

Type 'man chmod' to get more info than you ever wanted, then / (that's a slash, yes) followed by an appropriate search term (actually a POSIX regular expression, but English words are fine). Then 'n' to navigate to the next match.

For your particular problem, the answer is easy : add a -R switch, like this : chmod -R <the rest of your arguments>

-r or -R switches, as in recursive, are fairly common. Most of the times both work. In this particular case, as -r already means something (remove read permission), you'll have to use -R. Other commands such as ls, rm or chown also have recursive switches. Some others will need a script to work on a tree.

(Don't forget : RTFMP.)

---

### Post by rich.bradshaw on 2007-07-27
Solid advice there!

Another tip is to use ls in the place of other commands to see what files that will select. i.e. I might type

ls -r

to see what it picks up before

chmod -R ARGUMENTSHERE

This is useful for lots of things, especially rm !

---

### Post by opossumjack on 2007-12-27
thanks a lot for your advices...

very useful..

---

