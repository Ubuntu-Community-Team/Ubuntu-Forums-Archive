---
title: "Automatic Updates Don't Work"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by frotzed on 2006-12-29
Hello all.  I'm very very very new to Ubuntu.  I'm a pretty sharp guy but all this stuff is new to me so please bear with.

I click the little box in the upper right corner of the screen for automatic updates.  A dialog opens up and I tell it to install the 4 updates it's displaying.  Then it doesn't install any of them; it only spits out this error 4 times, once for each update.

W: Failed to fetch [http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78.2ubuntu2+3v1ubuntu1_i386.deb](http://3v1n0.tuxfamily.org/pool/edgy/3v1n0/flashplayer-nonfree_9.0.21.78.2ubuntu2+3v1ubuntu1_i386.deb)
  The HTTP server sent an invalid reply header


Any idea what's going on?  I'm totally stumped and searching on my own has yet to bring an answer.

---

### Post by meng on 2006-12-29
Looks like you've enabled some third-party unofficial repository, it's possible that the repository is experiencing some temporary problems.

---

### Post by frotzed on 2006-12-29
So, the solution is to wait and try again later?

---

### Post by Manzabar on 2006-12-30
> **frotzed said:**
> So, the solution is to wait and try again later?

Either the server is having a temporary problem or it's misconfigured and not sending out the data you want correctly.  According to what I found googling, it looks like you're not the only one having problems with this repository.  A possible solution I saw out there was to replace ```
deb http://3v1n0.tuxfamily.org edgy 3v1n0
```

with 
```
deb http://download.tuxfamily.org/3v1deb/ edgy 3v1n0
```

---

### Post by frotzed on 2006-12-30
OK.  I've had to reinstall Windows so I can continue working while I try to get this fixed.  I've repartitioned my hard disk and am reinstalling Ubuntu.  But I'm downloading the iso from a different location in hopes that my previous install CD was corrupt somehow.  I'll reinstall Ubuntu and be back here to tell you if I'm still having these issues.  

I do sincerely thank you for all the time you've spent on this.

---

### Post by macogw on 2006-12-30
That's nothing to do with your install cd. Just open /etc/apt/sources.list and edit that line in the file.  The repository location changed, so it just needs to have a different FTP address in there.

---

### Post by frotzed on 2006-12-30
Hey Mark, it's working!  Everything's working like a charm man!  This is excellent!  I could literally dance for joy!

---

