---
title: "Can't Open RhythmBox"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by JonWasHere42 on 2008-02-23
Recently Rhythmbox refuses to open. Just crashes at startup. Ive seen this problem posted up here, but never any answer.
I try to launch it from the terminal and receive:

I/O error : No such device or address
I/O warning : failed to load external entity "/home/jon/.gnome2/rhythmbox/rhythmdb.xml"
Segmentation fault (core dumped)

This started I believe after an automatic update. And I have tried changing my 
sources.list file because there seemed to be a duplicate source error in the installation.


Ive been using Ubuntu Feisty for about 6 months now, in addition to Windows. So Im not a complete beginner but I would say Im fairly incompetent.
Can anyone help me out?

--Jon

---

### Post by Sam Lars on 2008-02-23
You should check that file, rhythmdb.xml
If you have a backup copy, restore that, or try renaming it to something else and see if that fixes it...

---

### Post by wolfen69 on 2008-02-23
if all else fails, just completely remove and re-install it. it cant hurt.

---

### Post by JonWasHere42 on 2008-02-23
Have reinstalled it several times using the Add/Remove Programs.
And Synaptic. Nothing. Was going to reinstall it from source, but wanted to try here first.

--Jon

---

### Post by benerivo on 2008-02-23
Have you tried deleting /home/jon/.gnome2/rhythmbox. You could also try deleting /home/jon/.gconf/apps/rhythmbox.

---

### Post by JonWasHere42 on 2008-02-23
It wont let me delete the files rhythmdb.xml, or playlists.xml.
Have tried su, chmod, and using the gui. Seems that I can not delete them at all. And obviously this means, i can not delete rhythmbox directory, because its nonempty.
These files seem to be unusually large. 
Is it possible this has something to do with the fact that all my music is being imported from the Windows side of my hard drive?

--Jon

---

### Post by Sam Lars on 2008-02-23
I think my rhythmdb is 12 MB, for 13k+ songs.
sudo should delete them... does it say you don't have permission or that they're in use?
And I don't think Rhythmbox imports songs...

---

### Post by JonWasHere42 on 2008-02-23
rm: cannot remove `rhythmbox//playlists.xml': Operation not permitted
rm: cannot remove `rhythmbox//rhythmdb.xml': Operation not permitted

---

### Post by JonWasHere42 on 2008-02-23
And when i du -h rhythmbox (the directory containing these files) i get 966G, which is about 8 times the size of my hard drive.

---

### Post by Sam Lars on 2008-02-23
Dang, that's crazy... what does ls -l say for file sizes in there?
And you're running sudo rm?

---

### Post by JonWasHere42 on 2008-02-23
ls -sh yeilds:

82G playlists.xml  
884G rhythmdb.xml

This is the ls -lh response

?--Sr-S--- 26995  795044198 1416179045    1.8G 2002-01-06 03:17 playlists.xml
br-Sr-xrwx 12147 1869641044 1852404325 117, 98 2022-11-12 02:15 rhythmdb.xml

I tried to do sudo, but as you see the files apperantly belong to.. that nasty string of numbers, which means nothing to me.
These files are in ~/.gnome2/ but can they belong to something on windows?

--Jon

---

### Post by Sam Lars on 2008-02-23
That doesn't look good... what all did you have going on before this started?
I doubt they belong to Windows... though editing from Windows might do that... at least the numbers thing.
What's with it saying "rhythmbox//" in your output?  There should be only one...

---

### Post by JonWasHere42 on 2008-02-24
I dont know what was going on when it started. I dont know why it is "rhythmbox//"
I know that the music itself is on my windows partition, so is it possible that  editing the music over there changes what happens on the linux partition?

This is the rm command output:

[email]jon@jon:~/.gnom[/email]e2/rhythmbox$ rm rhythmdb.xml 
rm: remove block special file `rhythmdb.xml'? y
rm: cannot remove `rhythmdb.xml': Operation not permitted

---

### Post by Sam Lars on 2008-02-24
Yes, Rhythmbox will probably update its library when you change your music.
Try doing sudo rm...

---

### Post by JonWasHere42 on 2008-02-25
have tried sudo rm.

---

