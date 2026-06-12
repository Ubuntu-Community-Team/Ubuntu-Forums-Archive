---
title: "problems copying files TO computer from iPod using gtkpod"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by orionsbelt on 2007-02-17
I'm having trouble copying files from my iPod to my computer using gtkpod.  (I know people recommend Amarok, but I'm running GNOME.)  It worked fine when I just dragged some files to the desktop and then copied those to a folder.  However, given that I have over 1000 songs, I don't think it's a good idea to do that for everything.

I've been trying to using the recommended commands from the [gtkpod website]("http://www.gtkpod.org/README"), namely: 

[I]Export of Tracks (Copy from iPod)
---------------------------------

- mark the tracks you want to export and select "Export Tracks from
  Database" from the file menu (or use the context sensitive menu)
- A file selection dialog window appears and you can choose the directory
  you'd like the selected files to be written to.
- You can specify the output filename in the prefs dialog by
  specifying a template (e.g. "%A/%a - %t"). You can specify multiple
  templates for different file formats by separating them by a
  semicolon (e.g. "%A/%a - %t.mp3;%t.wav"). See the tooltip in the
  prefs dialog for a list of identifiers.[/I]

i'm still not quite sure about that whole template/identifiers thing -- i think that may be part of my problem.  i tried a couple of variations, and when i used  "%A/%a - %t.mp3;%t.wav", it copied a few songs and then stopped at 1%.  (BTW, i haven't been copying them all at once -- i figured i'd try a few in case i completely overloaded the program.)  

i get this error message:
[I]Template "%A/%a - %t.mp3;%t.wav" does
not match filetype 'media/ipod/IPod_control/Music/F00/IPIQ.mp4'[/I]

(this is why i think it may be the identifiers thing, but i really don't know what the right combo is and i don't want to guess and check all afternoon)

at this point it freezes, and i have to force quit.

don't know if this is relevant, but when i open gtkpod and try to read files from my iPod, it tells me that:
*Could not open "iTunesDB.ext" for reading extended info.  Extended info will not be used.*

does anyone know why this is happening?  does it matter if i have gtkpod or gtkpod-aac?  i've tried both.

---

### Post by Wolftastic on 2007-05-24
i'm having the exact same problem, something to do with m4a files. i've been trying all day to copy my songs from ipod to ubuntu so that i can use songbird, but i can't find a very direct way to do it. help!

---

### Post by JungleBeast on 2008-02-27
Hello there, I'm having similar problems, I'm fine getting it to copy the music, but I'd like it in folder structure.

However orionsbelt, i can see the answer to your problem. 

the file it's got stuck on is an mp4.  

so change :   %A/%a - %t.mp3;%t.wav    to    %A/%a - %t.mp3;%t.wav;%t.mp4

---

### Post by JungleBeast on 2008-02-27
So I guess the only correct way to export a load of mp3's to folders on my computer from my database, would be to export into 1 folder all with filenames as   "artist * album * title"   and then write some sort of awk script to folderise them?       :confused:

other than dragging and dropping 30 gigs worth of mp3age into folders of course?

---

