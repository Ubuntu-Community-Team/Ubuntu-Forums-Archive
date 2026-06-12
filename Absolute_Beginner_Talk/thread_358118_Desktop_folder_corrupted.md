---
title: "Desktop folder corrupted"
date: 2007-02-10
forum: Absolute Beginner Talk
---

### Post by Yleeyas on 2007-02-10
Hi folks,

Running latest Dapper (gnome).

This morning I rebooted the system and now when I login I get the following error:

```
Nautilus could not create the required folder "/home/yleeyas/Desktop".

Before running Nautilus, please create the following folder, or set permissions such that Nautilus can create it.
```

When I open a terminal and ls -l, I get:

```
?---------  7   23552   21025 36816 2018-11-29 10:04 Desktop
```

Somehow I've managed to bork the folder. Please How do I recover or replace :confused: 

TIA,
Yleeyas

PS; Before I rebooted there was a 'language pack' update, which I installed, but I don't know if that's a red herring

---

### Post by dbbolton on 2007-02-10
what happens if you do this :
```
sudo mkdir /home/yleeyas/Desktop
```

---

### Post by Yleeyas on 2007-02-10
Hi dbbolton,

Tried that and got:

```
mkdir: cannot create directory `/home/yleeyas/Desktop': File exists
```

That's the problem, the thing exists but the system doesn't see it as a folder  :( 
I'd rather try to recover it (and contents) than try to delete and replace.

Nautilus gives me similiar errors when I try to access my other drives and folders too :confused: 

Thanks for the effort, any other ideas?

Yleeyas

---

### Post by Yleeyas on 2007-02-10
Well I found one reference which, in the end, the guy just ended up deleting the directory file.
So, that's what I did.  Funny message I got from 'rm' asking if I really wanted to delete this 'weird' file :lolflag: 

Once it was gone, running Nautilus just created an empty Desktop directory, so I'm away =D>   
Wish I could remember what I had sitting on my desktop before, this one looks too clean :wink: 

Here's the one relevent reference I found, if anyone's interested:

[http://www.ubuntuforums.org/archive/index.php/t-326533.html](http://www.ubuntuforums.org/archive/index.php/t-326533.html)

Looks like I'm gonna have to read up on fsck and e2fsck :roll:

Does anyone have an idea what caused this, so I can avoid borking myself again :) 
Also if there is a better way to handle this please advise.

Thanx
Yleeyas

---

