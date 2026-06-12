---
title: "Creating an Audio CD in Ubuntu"
date: 2006-05-18
forum: Absolute Beginner Talk
---

### Post by KeyboardJockey on 2006-05-18
OK I'm up and running at last. 

I've downloaded Gnomebaker to create an audio CD from mp3 files but it keeps telling me it needs the mp3 plugin.  How do I get hold of and install the plugin?

Anyone help on this one?

Thanks.

---

### Post by user1397 on 2006-05-18
install the w32 codecs (illegal in u.s.) using: [http://wiki.ubuntu.com/RestrictedFormats](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by macdo on 2006-05-18
Just follow the instructions here:
[https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs]("https://wiki.ubuntu.com/RestrictedFormats?action=show&redirect=Codecs")

Happy listening!

Macdo

---

### Post by KeyboardJockey on 2006-05-18
I don't think I made myself clear (my fault) I can PLAY mp3s fine no problem at all with that.  It is just getting Gnomebaker to convert mp3's to CD Audio for burning.

---

### Post by bluevoodoo1 on 2006-05-18
I'm not certain with this exact problem because gnomebaker always gave me trouble with burning as well. I hate to be that guy that says to use another app... but I guess you could try another program :)... K3B is a great one. It's a KDE app but it will work in gnome. Hasn't ever given me problems.

There's also serpentine. A gnome-based application for audio cd creation.

---

### Post by KeyboardJockey on 2006-05-18
[QUOTE=bluevoodoo1]I'm not certain with this exact problem because gnomebaker always gave me trouble with burning as well. I hate to be that guy that says to use another app... but I guess you could try another program :)... K3B is a great one. It's a KDE app but it will work in gnome. Hasn't ever given me problems.

There's also serpentine. A gnome-based application for audio cd creation.[/QUOTE]

I might try the K3B app.  I had the same problem in Serpentine as in Gnomebaker.  In fact I downloaded andinstalled Gnomebaker because I had the 'can't recognise format' error message in Serpentine.

---

### Post by KeyboardJockey on 2006-05-18
Nope!  KB3 wouldn't load. :(

---

### Post by KeyboardJockey on 2006-05-18
I think I've found a work around.  If I can convert the mp3 files to ogg format I can probably use Serpentine.  What do I use to convert the mp3's to ogg?

---

### Post by macdo on 2006-05-18
Have you tried reinstalling the codecs?

On the subect of Gnomebaker, I managed to write off about 5 CDs - Gnomebaker would write them, I'd take them down to the car, pop them in the cheap mp3 CD player, drive off - and the damn thing would't read them. My first suspicion was that the CD player was broken, so different (older) CD - no problem!
Obviously the disc, right? Popped it into the PC, no problem. 
It turns out that Gnomebaker was doing something to them that stopped them from being read in my car (Linux DRM(TM):D ). K3b gave me no problem.

(5 CDs, mostly because I'm pretty pigheaded... and it makes for interesting beer mats!)

macdo

---

### Post by user1397 on 2006-05-18
try soundconverter to convert mp3 to ogg:
```
sudo apt-get install soundconverter
```
i dont think a cd-player will play ogg though, so...

---

### Post by macdo on 2006-05-18
There's a package named mp32ogg.
I don't know if there's a graphical interface, though...

---

### Post by user1397 on 2006-05-18
[quote=macdo]There's a package named mp32ogg.
I don't know if there's a graphical interface, though...[/quote]
im pretty sure that that is a command-line app, not recommended for beginners

---

### Post by macdo on 2006-05-18
Fair comment: my bad. My geek brother is obviously rubbing off - I found myself opening nano (nano!) to create a text file the other day...

---

### Post by KeyboardJockey on 2006-05-18
Nope!  Soundconverter doesn't work either

---

### Post by user1397 on 2006-05-18
[quote=KeyboardJockey]Nope!  Soundconverter doesn't work either[/quote]
that's strange. make sure you put the correct configurations in preferences

---

### Post by KeyboardJockey on 2006-05-18
[QUOTE=erik1397]that's strange. make sure you put the correct configurations in preferences[/QUOTE]

Still no joy.  Checked the preferences and still doesn't work.  :( 

This is the downside of Linux - simple stuff either doesn't work at all or takes a lot of work to get going.

---

### Post by KeyboardJockey on 2006-05-18
I don't know if this makes a difference but the mp3 files have a little padlock symbol on them.

---

### Post by macdo on 2006-05-18
Gotcha!
You need to change the permissions on them.
Right click, choose the permissions tab, make sure you own them, and give yourself read and write permissions.

---

### Post by KeyboardJockey on 2006-05-18
[QUOTE=macdo]Gotcha!
You need to change the permissions on them.
Right click, choose the permissions tab, make sure you own them, and give yourself read and write permissions.[/QUOTE]

Nope that don't work either. 

Still says in Gnomebaker can't handle mp3 files.

Soundconverter still doesn't convert the files either.

---

### Post by macdo on 2006-05-18
Has the padlock disappeared?

---

### Post by KeyboardJockey on 2006-05-18
Sorted.  reinstalled the codecs.  :)

---

