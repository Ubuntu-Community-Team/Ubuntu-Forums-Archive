---
title: "Compiling Help"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by Mangledbmx on 2006-05-09
hello, i just downloaded xine so i can watch some vids i downloaded and i cant figure out how to install. i read the readme and it says to use the terminal to "compile" it using ./configure command then type make. well the problem is it doesnt give you any instructions.... any help would be appreciated!

p.s i have it downloaded to my Desktop and the file name is xine-lib-1.0.3

again thank you

---

### Post by Jagot on 2006-05-09
Yoy can find some instructions on it here:

[http://monkeyblog.org/ubuntu/installing.html#installing_a_package_manually](http://monkeyblog.org/ubuntu/installing.html#installing_a_package_manually)

---

### Post by Mangledbmx on 2006-05-09
ya ive already looked at that. all it says is use ./configure to compile it

ok here is what ive  tried so far.

ok so first off i use cd Desktop to get into the desktop directory cause thats where its located.
second i tried typing JUST ./configure..... didnt work
then i tried XXXX./configure  where XXXX is the file name

so i dont know what im doing wrong.

---

### Post by Jagot on 2006-05-09
Have you installed the build-essential package?

---

### Post by Mangledbmx on 2006-05-09
yes. i saw that it was needed for a few different things.  i have no idea where it is in any of the menu's though. after i installed it, i couldnt find it and i have no idea how to use it

---

### Post by Jagot on 2006-05-09
Right, what extension did the package have?  You have extracted the file before trying to compile it right?

---

### Post by Mangledbmx on 2006-05-09
yep i used extract here. and the extension is tar.gz well was until i extracted haha

---

### Post by linear on 2006-05-09
Why not just use apt-get or Synaptic to install? (You need the Universe repository enabled.)

---

### Post by mostwanted on 2006-05-09
[QUOTE=Mangledbmx]ya ive already looked at that. all it says is use ./configure to compile it

ok here is what ive  tried so far.

ok so first off i use cd Desktop to get into the desktop directory cause thats where its located.
second i tried typing JUST ./configure..... didnt work
then i tried XXXX./configure  where XXXX is the file name

so i dont know what im doing wrong.[/QUOTE]

There's no guarantee that there will be a configure script, the guide also mentions that.

And build-essential is a group of terminal commands, it doesn't show in the menus. All the compilation commands used in the guide come with build-essential, that's why you need it.

I suggest you re-read this passage:

[http://monkeyblog.org/ubuntu/installing.html#source](http://monkeyblog.org/ubuntu/installing.html#source)

---

### Post by Mangledbmx on 2006-05-09
well i actually tried that but after i downloaded automatix it added a bunch of repositories to my list and now when i attempt to add universe it says it cant find it or cant find server!

---

### Post by Mangledbmx on 2006-05-09
ok so i re read the tutorial and your right. i was being dumb and didnt notice that part. so i tried the make command 

ok so i opened up terminal and typed

cd Desktop

sudo make xine-lib-1.0.3 and i got this error " no rule to make target 'INSTALL'.  STOP

---

### Post by linear on 2006-05-09
[quote=Mangledbmx]well i actually tried that but after i downloaded automatix it added a bunch of repositories to my list and now when i attempt to add universe it says it cant find it or cant find server![/quote]
OK, but it might be easier to fix sources.list (and necessary in the long run) than to compile xine from source.

---

### Post by Mangledbmx on 2006-05-09
any ideas on how to do that?

---

### Post by Jagot on 2006-05-09
[http://psychocats.net/ubuntu/sources.php](http://psychocats.net/ubuntu/sources.php)

Use the sources.list on the site above.

---

