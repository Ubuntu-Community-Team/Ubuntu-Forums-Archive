---
title: "How can I get an &quot;open terminal here&quot; command?"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by jefuchs on 2006-11-13
As I recall, when I used SUSE a few years ago, it allowed me to right click within a folder and select "open terminal here", which opened the terminal with the command prompt already in that directory.

The reason I need this is that some directories don't seem to open by typing their name.  I'm referring to directories with spaces in them, like [COLOR="DarkOrange"]Jeff Desktop[/COLOR], for instance.  Even if I use the [COLOR="DarkOrange"]ls[/COLOR] command, then copy and paste the directory name.

So it seems a solution would be to have an "open terminal here" menu item.

Is there something I can install to get this?

---

### Post by po0f on 2006-11-13
jefuchs,

You could install nautilus-open-terminal.
```
$ sudo aptitude install nautilus-open-terminal
```

[EDIT]

To cd into a directory with a space in its name, either escape the space, or use tab completion (tab completion is your friend).  This folder is in your home folder right?
```
$ cd
$ cd Jef<hit tab>  # the rest of the folder name should pop up
$ cd Jeff\ Desktop  # escape the space with a \
```

---

### Post by george29 on 2006-11-13
Not sure about the 'open terminal here' but to get an option to open a terminal in the right click menu - you need to install the nautilus open terminal package.. that's from memory.

As for the directories with spaces.. 

cd /home/jeff\ \Desktop 

should take you into that folder.


George

---

### Post by jefuchs on 2006-11-13
Thanks.  I'm at work, using Windows right now.  I'll try it when I get home.

---

### Post by SoulSmasher on 2007-11-15
> $ sudo aptitude install nautilus-open-terminal
just running this and restarting with ctrl alt backspace worked like a charm :) thanks :)

---

### Post by cometdog on 2007-11-26
> **SoulSmasher said:**
> just running this and restarting with ctrl alt backspace worked like a charm :) thanks :)

Actually -- instead of <ctrl>-<alt>-<backspace> you can just quit nautilus with
```

nautilus -q
```
and it will be restarted automatically.  That way you don't lose all your open apps.

---

### Post by Dr Small on 2007-11-26
Cool. I just installed it. I have always wanted something like that :D

Dr Small

---

### Post by viking777 on 2007-11-26
> **jefuchs said:**
> As I recall, when I used SUSE a few years ago, it allowed me to right click within a folder and select "open terminal here", which opened the terminal with the command prompt already in that directory.

The reason I need this is that some directories don't seem to open by typing their name.  I'm referring to directories with spaces in them, like [COLOR="DarkOrange"]Jeff Desktop[/COLOR], for instance.  Even if I use the [COLOR="DarkOrange"]ls[/COLOR] command, then copy and paste the directory name.

So it seems a solution would be to have an "open terminal here" menu item.

Is there something I can install to get this?

There sure is, it is called Krusader - the very best file manager I have ever used either in the Linux or the Windows world.

It is in the repositories so no need to search the net for it.

Once it is installed look for the menu item 'Krusader Root Mode', launch that, or better still put it in a quick launch menu or something similar and start to enjoy file management the way it should be.

You may well be overwhelmed with the number of tools and options it presents to begin with but persevere and you will never look at another file manager again.

---

