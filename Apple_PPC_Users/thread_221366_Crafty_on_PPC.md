---
title: "Crafty on PPC"
date: 2006-07-23
forum: Apple PPC Users
---

### Post by billyfoxtrot on 2006-07-23
I was curious if anyone has been able to compile or somehow install the Crafty chess engine on a PowerPC system running Ubuntu.  I can't figure out how to get it, and I would really like to run it along with Xboard.

Thanks!

---

### Post by chasisaac on 2006-07-28
> **billyfoxtrot said:**
> I was curious if anyone has been able to compile or somehow install the Crafty chess engine on a PowerPC system running Ubuntu.  I can't figure out how to get it, and I would really like to run it along with Xboard.

Thanks!

Billy, 
if you get it done let me know. I would guess it would take some programming. My son woud like ths on his iBook

---

### Post by billyfoxtrot on 2006-07-30
I got it done with a little trickery :).  What I did was download the latest source code from [Hyatt's FTP site]("ftp://ftp.cis.uab.edu/pub/hyatt/"), and instead of running:
```
make linux
```
in the Crafty directory, I ran:
```
make darwin
```  
This created a working version of Crafty for PPC.  I then moved the compiled Crafty into /usr/games, so it could now be recognized by eboard (I haven't tried it with xboard yet).  The next thing I did was put my book.bin and books.bin files into /usr/local/share/crafty so they could also be used by eboard.  The only thing I haven't been able to figure out yet is learning.  Supposedly Crafty can save the games you play and learn from them, but every time I use Crafty with eboard, I get the message "learning is disabled."  I'm not sure how to fix this.  But otherwise, it works perfectly.

If anyone can figure out how to get learning to work with Crafty and eboard, please let me know!

---

### Post by Dr. Cox on 2007-03-20
i would like to compile crafty.

i'm using ubuntu edgy and a plain acer intel centrino laptop.

what do i need to do?

thanks for the help?

cheers

---

### Post by Auria on 2007-03-20
> **Dr. Cox said:**
> intel centrino laptop

This is a PPC forum - you seem to be on intel so just follow the regular instructions (i.e. what you read here probably doesn't apply to you, and you're probably not in the right section of the forum either)

---

