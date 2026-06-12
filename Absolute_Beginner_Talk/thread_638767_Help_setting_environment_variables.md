---
title: "Help setting environment variables ????????"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by sjosh_theone on 2007-12-12
Hello guys,
sorry for the title. what can you expect from a guy who has wasted 3 days trying  to figure out how to set environment variable to make his cat(tomcat) run.
this is what I get from catalina.out:
./catalina.sh: 338: usr/lib/jvm/bin/java: not found

I know the path is wrong but where to rectify it. In which .bashrc ???user one or the system one. ??or do I need to make any changes in .profile???A terse reply would be appreciated. 
Thanks in advance.

---

### Post by Dr Small on 2007-12-12
After 3 days of trying, I could expect a plea rather then a vulgar title.
But anyhow, why not post line 338 here, so we can see what it is calling. That would at least be helpful.

Dr Small

---

### Post by sjosh_theone on 2007-12-12
sorry for that Dr Small. coming to the point let me tell you I played around a bit with my .bashrc files. Have a strong hunch that I created blunders. They are littered all over the place. In suse 10.2 its so simple . visit .bashrc from ur home , define paths ,export them and its done. Why do we need to follow a laborious procedure here???

---

### Post by Steveway on 2007-12-12
Why not make a symlink from your java to /usr/lib/jvm/bin/java ?
Or change the path in the catalina.sh file?

---

### Post by sjosh_theone on 2007-12-12
why not TRY using the symlink????????? I told you before. I played a lot . Need some place to rest. Please can anybody suggest me a "bulls eye" answer??

---

### Post by Dr Small on 2007-12-12
When settings $PATH, you would normally do it like this:
```
export PATH=$PATH:/new/path
```

---

### Post by sjosh_theone on 2007-12-12
I know the syntax Dr . But where to put it. in which file  ??.bashrc file or .profile file??

---

### Post by Dr Small on 2007-12-12
Have you tried it in any of them? I thought it was supposed to go in .bashrc

---

### Post by Dr Small on 2007-12-12
Add it to the beginning of .bashrc

It worked for me ;) Or, at least, the export DISPLAY (i was just testing)

Dr Small

---

### Post by sjosh_theone on 2007-12-12
but in which .bashrc file???system one or user one???I had messed up some things before which luckily are restored. But  my woes continue with tomcat.  HELP needed
thanks in advance.

---

### Post by Dr Small on 2007-12-12
I added it to my user one, but if you are running the file as root, then it should probably be placed in the /root/.bashrc

Dr Small

---

### Post by bodhi.zazen on 2007-12-12
:lolflag:

In ~/.profile put ;
> source $HOME/.bashrc

Then in .bashrc :

> export PATH=$PATH:/new/path

OR make a sym link.

We are here to help, but I would expect you to ask for help before you became so frustrated you felt the need to be vulgar :twisted:

Bash config files : 

[http://heimhardt.com/htdocs/bashrcs.html](http://heimhardt.com/htdocs/bashrcs.html)

Arch: [http://bbs.archlinux.org/viewtopic.php?t=21556](http://bbs.archlinux.org/viewtopic.php?t=21556)

---

