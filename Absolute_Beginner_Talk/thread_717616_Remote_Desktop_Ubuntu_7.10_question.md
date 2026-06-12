---
title: "Remote Desktop Ubuntu 7.10 question"
date: 2008-03-07
forum: Absolute Beginner Talk
---

### Post by fleury29 on 2008-03-07
I setup remote desktop in ubuntu on my home machine.  I was in a hurry this morning and forgot to turn off "Ask you for confirmation."  Now I am at work ssh'd into my machine at home.  Is there a file that stores the settings for remote desktop?  I am at work now and would like to kill some time :P

Thanks

---

### Post by fleury29 on 2008-03-07
Actually I found a command I could use on:
[http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

A poster:
> 
#  Michael Says:
March 19th, 2007 at 1:59 pm

From this thread I figured out you can turn on remote desktop thru a putty window by typing:

```
gconftool-2 -s -t bool /desktop/gnome/remote_access/enabled true
```

and disable the auto prompting by typing:
```
gconftool-2 -s -t bool /desktop/gnome/remote_access/prompt_enabled false
```


In case any1 else had the same questions I had.

Thanks

---

### Post by Rhubarb on 2008-03-07
ssh into your home computer with the -X flag, so it looks something like this:
```
ssh username@home.ip.address -X
```

This allows you run gui apps remotely via ssh.
Then run the same Remote Desktop application :
```
vino-preferences
```

EDIT:  Looks like I'm a bit slow here, someone beat me to the answer (a different way of doing it).

---

