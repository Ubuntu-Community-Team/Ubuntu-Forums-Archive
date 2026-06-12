---
title: "[SOLVED] rtorrent"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by Rhaddad on 2008-03-23
I know the ubuntu forums isnt the best place to post this, but i think many of you use rtorrent.

When i add a new torrent and then quite rtorrent when i restart rtorrent the torrent that i added isnt on the list.

So basically rtorrent doesn't save my torrents and everytime i want to resume a download i have to do new hash check. Can anyone here help me??? thanks :D

---

### Post by BL00dFox on 2008-03-23
Have you tried Azureus ? =)

---

### Post by Rhaddad on 2008-03-23
yea, but i don't like it.
I don't like ktorrent as well
i really like rtorrent. (system resources is a big issue for me :P) and java takes up heaps

---

### Post by smartboyathome on 2008-03-23
Another to try is Transmission. It is also very light, and as of hardy is the default client. Also, it sounds like a bug in rtorrent.

---

### Post by Rhaddad on 2008-03-23
Don't worry guys i figured it out

just type
rtorrent -s <cons directory>

each time you want to start rtorrent in the same session

---

### Post by saj0577 on 2008-03-23
Glad to hear it now please mark as solved :)

Saj

---

### Post by Rhaddad on 2008-03-23
How do i do that....

one more question how do i make a shell script that just does it for me, as in the command???

---

### Post by saj0577 on 2008-03-23
Thread tools at the top Mark as solved.

Just on a plain file write the command then you make it executable, double click it.

I think thats what your after.

---

### Post by Rhaddad on 2008-03-23
this is my text file


rtorrent -s '/home/raf/Files/rtorrent sessions'

what extension to i put in the text file

---

### Post by saj0577 on 2008-03-23
You dont give it an extension.

---

