---
title: "Share Music Between XP and Ubuntu?"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by mikaelsnavy on 2008-01-20
Hello,
I have all of my music on my XP partition organized by iTunes. My Ununtu (gusty) install can see the NTFs partition and write to it.  Is there a way to change where my /home/my username/Music folder points too? I have a freind that said something about symbolic links or something. 
Thanks for the help,
Mikael

---

### Post by banewman on 2008-01-20
The only way I know is to open a terminal   applications - accessories - terminal    and type   
sudo ln -s /path/to/folder name
where name is what you want to call it e.g  music
:)

---

### Post by mikaelsnavy on 2008-01-20
OK, here is what I got:
 ```

 sudo ln -s "/media/share/Documents and Settings/Administrator/Mikael/My Music" "/home/mikael/Music"

```

That makes a folder called  "My Music" in my /home/mikael/Music/ folder. Is there a way to get all the files in the My Music folder to be linked?
Thanks,
Mikael

---

### Post by banewman on 2008-01-20
Shouldn't be any quotes in that line.
But linux doesn't like whitespace
Before I posted I tried out that command and it linked the files in the folder. :)

---

### Post by mikaelsnavy on 2008-01-20
Hmm I must be doing something wrong.

I am doing:
```

sudo ln -s "/media/share/Documents and Settings/Administrator/Mikael/My Music" Music

```
from my home directory (if I do not use the quotes on the first path, I get links to files called "and", "settings", and "music" that go nowhere. Here quotes are essential :D) 

A folder named "My Music" is still showing up in my Music folder. Is there some wildcard I need to be using, like *.* in Windows so I can get all the files in the My Music folder?
Thanks,,
Mikael

---

### Post by banewman on 2008-01-20
Sorry - I don't know what else to tell you 
I typed
 ```
Working-@-Command Line:~$ sudo ln -sv /home/somebody/music music
```
and got a link to a folder that contained all the relevant folders and files
From ubuntu can you browse to and open said files?

---

### Post by mikaelsnavy on 2008-01-20
OOPS!! Lol, I had ln -s, not ln -sv. Sorry About that! Thanks for your help!
Thanks,
Mikael

---

### Post by banewman on 2008-01-20
With the v in  -sv you  get a verbose output - it tells what it is doing
the result is the same. :)

---

### Post by mikaelsnavy on 2008-01-20
Lol, n00b alert! All I know is that it works now :D!

---

