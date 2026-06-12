---
title: "network sharing Q?"
date: 2008-02-10
forum: Absolute Beginner Talk
---

### Post by antgul3382 on 2008-02-10
ok i have one comp sharing the hard drive in windows an another with ubuntu that i want to transfer the files thru my network. any suggestions??? thanks in advance

---

### Post by antgul3382 on 2008-02-10
please help!!!!!!

---

### Post by spiderbatdad on 2008-02-10
look into samba and smb.conf

---

### Post by antgul3382 on 2008-02-10
yeah that didnt work!?!?!? i dont want to share wityht the ubuntu comp i want it to be able to take from the windows comp whi is doing the sharing

---

### Post by spiderbatdad on 2008-02-10
it is possible via ssh, but that is advanced use, there is a lot to read and learn.

---

### Post by jonkulp on 2008-02-10
You can also access files on your other computers using an ftp app like FileZilla.  I've used both nautilus (with Samba) and FileZilla to get files from my Macs on the network. Be careful when using FileZilla, though, that you choose to copy the files and not "move" them.  I realized after grabbing some audio files from my my eMac the other day that I had moved them (i.e. removed them) and not copied them, so I had to put them back onto the eMac.  Good luck!

Forgot to mention, with FileZilla you'll need to know the IP address, username and password of the target computer to get access.

---

