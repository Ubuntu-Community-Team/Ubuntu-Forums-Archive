---
title: "How to set $PKG_CONFIG_PATH permanently?"
date: 2006-03-05
forum: Absolute Beginner Talk
---

### Post by shishio on 2006-03-05
I want to permanently set $PKG_CONFIG_PATH and $LD_LIBRARY_PATH using a script that is run at start up. So I wrote a script with two lines in it:

vi bah

export PKG_CONFIG_PATH = "~/Desktop/somedir"
echo $PKG_CONFIG_PATH

then I exit and do:

chmod 755 bah

(what does the 755 mean?)

and I run the script, and it seems like it works fine, it displays: 

~/Desktop/somedir

when I run it. But if I now manually type:

echo $PKG_CONFIG_PATH

It is no longer set to "~/Desktop/somedir"

What's going on? It seems like the environment variable is only set while the script is running?

---

### Post by engla on 2006-03-05
Your file is actually run in a sub-shell and it's changes to environment variables are not carried "to upstream" when the sub-shell exits; even if you type export.

To do what you want, you don't execute the script, you *source* it.

So in the bash shell you do:
$ source bah

There is also a very short alias for source, namely . (a dot!)
$ . bah

---

### Post by shishio on 2006-03-05
Sweet it works... thanks, now how do you make it do this at start up? 

How do you make it run this script at startup?

---

### Post by Iowan on 2006-03-05
[QUOTE=shishio]chmod 755 bah

(what does the 755 mean?)[/QUOTE]Owner can read, write, and execute the file.  
the group members can read and execute, others can read and execute.

---

### Post by torf on 2006-03-05
> 
chmod 755 bah
(what does the 755 mean?)


There's a really great interactive tutorial on chmod  [http://catcode.com/teachmod/index.html]("http://catcode.com/teachmod/index.html"), it helped me a lot. 

A simple way to make something run at startup, (assuming you're using the gui) is to go to System --> Preferences --> Sessions --> Startup Programs
From there you can enter the command or program you want to run at startup.

---

### Post by engla on 2006-03-06
[QUOTE=shishio]export PKG_CONFIG_PATH = "~/Desktop/somedir"
echo $PKG_CONFIG_PATH
[/QUOTE]
If you only want this to apply to your interactive shells (when you use the terminal, not for running applications and gnome and such), you can just put these lines in the file ~/.bash_profile ... if that file does not exist, create it.. the contents there should be *sourced* automatically when a new bash shell is started.

You can choose yourself if you just want to include the lines straight off, or if you put them in a separate file and put "source other_file" in your ~/.bash_profile

---

