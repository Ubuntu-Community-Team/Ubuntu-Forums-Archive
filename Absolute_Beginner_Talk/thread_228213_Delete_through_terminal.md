---
title: "Delete through terminal"
date: 2006-08-02
forum: Absolute Beginner Talk
---

### Post by IrishGangsta on 2006-08-02
I downloaded a Bit Torrent music file
which contained alot of songs. 
What i did was create a folder and add all of these songs in the torrent to the Music Folder.

I mixed all sorts of artists and i was wondering if there is a simple code i could use in the terminal to delete all of the files in that folder containing the one artist.

---

### Post by Tomosaur on 2006-08-02
Depends on how they're named. If they follow a pattern like this:
Bob Dylan - Blowin' in the wind.mp3
Bob Dylan - Subterraenean Homesick Blues.mp3
Bob Dylan - Maggie's Farm.mp3

you could type 'rm Bob\ Dylan*.mp3

And that would delete all of the files with 'Bob Dylan' at the beginning of their name.

---

### Post by jimmygoon on 2006-08-02
This one will scan recursivly through folders

find . -name *NAME_OF_ARTIST* -exec rm -rf {} \;

[B]don't run that command until someone else verifies it!!!!!
[/B]
But that should do it. Make sure you do it in the directory that the music is in, otherwise it will scan any directories below the current one and it will delete any files/(folders???) below the current dir.

---

### Post by IrishGangsta on 2006-08-02
they are varied in name.
It kind of sucks and its all weird.
I am trying to delete this Metallica Bit Torrent. Most of the songs are live and and from a vary of albums that are not to good.
It was a lame torrent.

alot of are like 01 Metallica - blah blah blah.mp3

So if anyone can verify or give me a good code for deleting all metallica songs please help.

---

### Post by IrishGangsta on 2006-08-02
they are varied in name.
It kind of sucks and its all weird.
I am trying to delete this Metallica Bit Torrent. Most of the songs are live and and from a vary of albums that are not to good.
It was a lame torrent.

alot of are like 01 Metallica - blah blah blah.mp3

So if anyone can verify or give me a good code for deleting all metallica songs please help.

---

### Post by Tomosaur on 2006-08-02
If they all have metallica in their name, try this:
rm *etallic*

Basically just search for common patterns in the names, and surround them with wildcards (the asterixes)

---

### Post by IrishGangsta on 2006-08-02
where do i type rm etallica?

---

### Post by Tomosaur on 2006-08-02
in the terminal.

Applications > Accessories > Terminal

If your music folder is in ~/My\ Music/

you would open the terminal, and type 'cd My\ Music/'

Then you would type 'rm *etallica*'

---

### Post by IrishGangsta on 2006-08-02
those directions didnt work.
i have it in  /home/mike/music

Can u tell me what to type in terminal with that?

i tried cd /home/mike/music but it didnt work

---

