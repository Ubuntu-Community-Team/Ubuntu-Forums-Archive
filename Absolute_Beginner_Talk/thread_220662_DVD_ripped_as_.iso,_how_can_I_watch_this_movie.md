---
title: "DVD ripped as .iso, how can I watch this movie?"
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by BlueStreak on 2006-07-21
I ripped a DVD to my hard drive as an .iso.  I would like to be able to watch this movie directly from my drive instead of burning it to a disk.  How could I do this?  Thank you.

---

### Post by scxtt on 2006-07-21
try mounting the iso and seeing if you can 'extract' the .vob files ...

mount -t iso9660 /path_to_iso/DVD.iso /media/iso_mount

then navigate to that folder and see if you can find some .vob files ...

NOTE: you'll have to supply "path_to_iso", "DVD.iso", and "iso_mount" ...

---

### Post by Kilz on 2006-07-21
> **BlueStreak said:**
> I ripped a DVD to my hard drive as an .iso.  I would like to be able to watch this movie directly from my drive instead of burning it to a disk.  How could I do this?  Thank you.

Create a folder. Put the iso on the desktop Then open a terminal and type in this
```
sudo mount -o loop -t iso9660 ~/Desktop/YourIsoName.iso /path/to/folder/you/made
```

---

### Post by BlueStreak on 2006-07-21
I tried mounting it and got the separate audio and video directories.  The individual video files played fine but how can I get them to play contiguously?

Sorry, I don't know what you mean by 'extract' the .vob files

---

### Post by scxtt on 2006-07-21
either copy them or move them out of the directory in which the iso has been mounted ...

i'm sure there's something out there to join video files, but you could try:

cat file1.vob file2.vob file3.vob > DVD_ouput.vob

tho i think there's a limit when it comes to overall size ...

---

### Post by Kilz on 2006-07-21
> **BlueStreak said:**
> I tried mounting it and got the separate audio and video directories.  The individual video files played fine but how can I get them to play contiguously?

Sorry, I don't know what you mean by 'extract' the .vob files

Why rip it to a file, then make more work for yourself mounting the .iso when you could just pop in the dvd and watch it play?

---

### Post by BlueStreak on 2006-07-21
> **Kilz said:**
> Why rip it to a file, then make more work for yourself mounting the .iso when you could just pop in the dvd and watch it play?

A good point but I no longer have the DVD in my possession.  I don't want to go through a whole lot of trouble with this, if there's no easy way I'll just wait til tomorrow when I can pick up some DVD-Rs.

---

### Post by scxtt on 2006-07-21
it's not "hard" and most media players have a playlist feature that would allow you to add to the playlist all .vob files that make up the dvd so they'll play one-right-after-the-other ...

---

### Post by BlueStreak on 2006-07-21
Oh yea, that is a simple solution.  I have a tendency to overlook the obvious.  I guess I'll just do that for now.  Thanks all

---

### Post by scxtt on 2006-07-21
happens to us all, that's basically how i know about the 'cat file1.vob file2.vob . . .' suggestion i made above ...

---

### Post by Kilz on 2006-07-21
> **BlueStreak said:**
> A good point but I no longer have the DVD in my possession.  I don't want to go through a whole lot of trouble with this, if there's no easy way I'll just wait til tomorrow when I can pick up some DVD-Rs.

But if you don't have the DVD now. Did you own it to begin with? I would hate to give someone instructions on how to do something illegal.

---

### Post by wana10 on 2006-07-21
> **Kilz said:**
> Why rip it to a file, then make more work for yourself mounting the .iso when you could just pop in the dvd and watch it play?

i do this on my laptop actually. when playing movies i can scale down my system to recieve much longer battery life, however when the dvd player is actively working the battery life plummets. so if i'm going on a trip i rip a couple of my dvd's to my harddrive and problem solved

---

### Post by srunni on 2006-07-21
Just get VLC media player from Synaptic and you can open the .iso as if it were a normal video file. You will still have all the menu options and everything, just as if you'd inserted the DVD.

---

### Post by Kilz on 2006-07-22
> **wana10 said:**
> i do this on my laptop actually. when playing movies i can scale down my system to recieve much longer battery life, however when the dvd player is actively working the battery life plummets. so if i'm going on a trip i rip a couple of my dvd's to my harddrive and problem solved

But you would still have the dvd. The more I read this the more I think the orignal poster riped a movie he rented or downloaded the iso from bit torrent. 
Sometimes I think we should step back and look at whats going on in the rush to help someone do something. FOSS is based on copyright, the GPL works because of copyright. Helping someone violate copyright laws is wrong IMHO.

---

### Post by clarkth on 2006-07-22
> **srunni said:**
> Just get VLC media player from Synaptic and you can open the .iso as if it were a normal video file. You will still have all the menu options and everything, just as if you'd inserted the DVD.

I use VLC on a client laptop to show ISO DVD files stored on my server in the basement.  No need to stream, just share the folder the iso's are stored in (I did try streaming and it works well also).

---

### Post by srunni on 2006-07-22
> **clarkth said:**
> I use VLC on a client laptop to show ISO DVD files stored on my server in the basement.  No need to stream, just share the folder the iso's are stored in (I did try streaming and it works well also).

VLC is not only for streaming files, it is also excellent for playing files stored on your local hard drive. As for the guy not having the DVD: 
1. You don't download .iso's for movies, you download XviD's, so that's most likely not a possibility
2. If he did have access to the DVD then, he could've just watched it, right?
3. You might as well tell him, because he'll just go to another forum and ask the same question, using an excuse for why he doesn't have the DVD
4. Either way, I answered his question: it's his problem whether he uses that knowledge legally or illegally
5. Personally, I think he rented the movie and De-CSSed it, but once again, that's his problem, not mine

---

