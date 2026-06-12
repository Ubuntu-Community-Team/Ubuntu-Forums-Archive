---
title: "bruning dvd from folders"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by rockinlinux on 2008-01-12
A long time ago when i was till using windows i made some backups of some dvd movies i own. The program i used created audiots and videots files. So all i have is the two file for each movie, they are 6.2 GB (per movie for both folders) so i try to burn them to a dvd 9 and it give me an error while burning. I have tried twice and dvd9 dvd's as you know are not that ceap to be messing up a lot of....how can i burn these movies to watch in my dvd player? also FYI i burned an .iso created with k9copy to the same dvd9's and it worked great.


thanks :)

---

### Post by nikoPSK on 2008-01-12
gnomebaker or k3b will burn dvd's but not quite sure about from a folder.

---

### Post by rockinlinux on 2008-01-13
yeah i know what programs will burn a dvd but im just trying to figure out why i was getting the errors.

thanks :)

---

### Post by nikoPSK on 2008-01-13
> **rockinlinux said:**
> yeah i know what programs will burn a dvd but im just trying to figure out why i was getting the errors.

thanks :)

sorry, what errors?

nikoPSK

---

### Post by rockinlinux on 2008-01-14
it just says "there was an error while burning th disk, operaion aborted."

---

### Post by AndyCooll on 2008-01-14
Have you tried burning it at x1 speed?

:cool:

---

### Post by rockinlinux on 2008-01-14
i was burning i think a 2x...i thought that would be slow enough....maybe i will try it. But if i have the two files i should just be able to burn them and it will play in a dvd player right? I dont know much about the movie backup stuff :(

---

### Post by LeAstrale on 2008-01-14
as far as i know you could just burn a data dvd with the Video_TS and Audio_TS folders on it.. have you tried that?

---

### Post by santaslittlehelper on 2008-01-14
Maybe you could create an iso instead if you can't get it going otherwise.

Drop the Video_TS and Audio_TS folder in yet another folder on you're desktop and call it dvd.

Then from a terminal,
```
sudo aptitude install mkisofs
cd Desktop
mkisofs -dvd-video -o dvd.iso dvd/
```

If it work you should have an iso called dvd, but not completely sure.

---

### Post by vanadium on 2008-01-14
genisoimage is already on your system and is the successor of mkisofs.

---

### Post by santaslittlehelper on 2008-01-14
I see, do you happen to know how you create a duel layer iso with genisoimage as I think that's what the OP needs and I missed that as well.

---

