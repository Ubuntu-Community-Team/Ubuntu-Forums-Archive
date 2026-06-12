---
title: "Where do my ripped files go? (Grip)"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Joakim Stokland on 2007-07-14
Hello!
I am trying to rip my CDs with Grip. I have adjusted the settings, and everything seems to work great! The tracks are being ripped and encoded to FAAC, and then placed in my folder (Grip even creates the new folders for me, where I want them, the way I want them). At least as I can read from the status list. But after "successful" ripping and encoding, I can't find my songs! Where are they? It doesn't seem like they are being created at all!

Thanks for any help!
Joakim

---

### Post by crimesaucer on 2007-07-14
In Grip...click: Config-->--Encode-->--Encoder...

...then check out the string on "Encode file format", and that should have the folder where your music is. It should also have the order of how you want the music files to appear. This is mine:

```
~/gripped/%A/%d/%n.%x
```

this should place my files is a folder named "gripped" with Artist name for the disk, disk name, name of track, then a .ogg or .mp3.

---

### Post by Campingman on 2007-07-14
Hi 
A good thread to read all about grip
[http://ubuntuforums.org/showthread.php?t=183125hp%3ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3ft=25151)

They are saved in your home folder and it is determined in grip>config>encode>encoder>encode file format.
My line in this field (only cause I cannot be bothered to change it) is  ~/ogg/%A/%d/%n.%x

All my rips tracked are then stored in home/ogg.  If you change the ogg to mp3 they will then be saved to home/mp3.
I think this is correct, hope it helps.

---

### Post by crimesaucer on 2007-07-14
I find this to be a really good page for Grip: [http://nostatic.org/grip/doc/index.html](http://nostatic.org/grip/doc/index.html)

---

### Post by crimesaucer on 2007-07-14
> **Campingman said:**
> Hi 
A good thread to read all about grip
[http://ubuntuforums.org/showthread.php?t=183125hp%3ft=25151](http://ubuntuforums.org/showthread.php?t=183125hp%3ft=25151)

They are saved in your home folder and it is determined in grip>config>encode>encoder>encode file format.
My line in this field (only cause I cannot be bothered to change it) is  ~/ogg/%A/%d/%n.%x

All my rips tracked are then stored in home/ogg.  If you change the ogg to mp3 they will then be saved to home/mp3.
I think this is correct, hope it helps.

Wow...he really updated that guide a lot since I had last seen it...the poodles still the same though...hahaha...

It's a really good guide and covers basically everything.

---

### Post by Campingman on 2007-07-14
> **crimesaucer said:**
> I find this to be a really good page for Grip: [http://nostatic.org/grip/doc/index.html](http://nostatic.org/grip/doc/index.html)

Nice one thanks, I had not found that one.  One for my bookmarks!!

---

### Post by Joakim Stokland on 2007-07-14
Thanks for your answers!
I'm saving as FAAC, and I've changed the path to "/media/sda2/Musikksamling/%a/%d/%t - %n". This should work, shouldn't it? The thing is, underneath "Musikksamling" the folder %a (Artist) is created automatically as it should. The same goes for %d. But it stops there. No files in %d after ended encoding...
Can I define file names as I have? %t - %n (track number and name). Can I use a space, a score and another space as I have? Have the missing files got anything to do with this?

I'll have a look at your link tomorrow, campingman. It's getting late here, so I better bail.
Thanks for your help so far :)
Joakim

---

### Post by crimesaucer on 2007-07-14
> **Campingman said:**
> Nice one thanks, I had not found that one.  One for my bookmarks!!

It was the original guide that I installed from last fall/winter. I remember reading every post and thinking that I was way out of my league since I didn't know about any of the encoder settings that they were arguing about...but after reading that whole thread, and a few wiki pages on lame and ogg...I learned what I needed to know to rip my music.

---

### Post by crimesaucer on 2007-07-14
You must end your string with:

```
.%x
```

to put a ".mp3" after the title, name, track...


from here: [http://nostatic.org/grip/doc/ar01s04.html#gripswitches](http://nostatic.org/grip/doc/ar01s04.html#gripswitches)

x &#8212; The encoded file extension (ie "mp3")

---

### Post by Joakim Stokland on 2007-07-15
Okay! I'va added the .%x. Thanks again :)
But still, nothing in my folder!

[IMG]http://i187.photobucket.com/albums/x161/jstokland/snapshot6.png[/IMG]
[IMG]http://i187.photobucket.com/albums/x161/jstokland/snapshot7.png[/IMG]

```

ls -a /media/sda2/Musikksamling/Toto/IV/
.  ..

```

See? nothing there... :(

---

### Post by Joakim Stokland on 2007-07-15
Well, that certainly did it! After reading the post you pointed to, I soon figured I used the wrong codec. I don't know what I've been thinking, but there actually wasn't any faac-codec in /usr/share/doc! So to sum it up, Grip ripped the tracks and deleted the wav-files, without encoding them at all! But why didn't it bring an error message, like before I typed in where I thought libfaac0 was?
After installing the faac package from synaptic, and changing to the settings provided in that post, everything works as it should!

Anyway, thanks for your support guys! It's been really helpful! :)
Joakim

---

