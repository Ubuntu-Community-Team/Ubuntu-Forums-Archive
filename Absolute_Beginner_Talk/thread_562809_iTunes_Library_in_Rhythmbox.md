---
title: "iTunes Library in Rhythmbox"
date: 2007-09-29
forum: Absolute Beginner Talk
---

### Post by Spacedementia87 on 2007-09-29
How do you import your iTunes library into Rhythmbox player?

I just can't figure it out.

---

### Post by staticvoid on 2007-09-29
> **Spacedementia87 said:**
> How do you import your iTunes library into Rhythmbox player?

I just can't figure it out.
first of all you should use "[banshee]("http://www.getdeb.net/search.php?keywords=banshee")" :P It's the best (dabatable: theres also amarok..)

well, you can try **music>import folder **then find where you're itunes music folder is...
or, go **edit>pereferances>library** and choose where you want your lib to be :)

And you will need to get **gstreamer** codecs so you can actually play your itunes library :D Then you will be able to play ACC and mp3 format audio files. check "Add and Remove" and select all the gstreamer stuff. or googe, "ubunut audio codecs" or something (are'nt I terrible, lol)

ok, found it: go here: [https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")
that should help you on your way to importing and playing you iTunes library.

have a great day!

Static Void

---

### Post by Spacedementia87 on 2007-09-29
Yeah i knew that much.  Was just wondewring if there was a way to import the actual library i use in iTunes.  If i just import the folder it will take a lot of sorting because i don't have all that music in my iTunes library.

---

### Post by tgalati4 on 2007-09-29
There is no direct transfer of iTunes database to Banshee or Rhythmbox database.  You will lose your ratings, volume gain settings (does anybody use this?), EQ, number of plays, etc.  Apple's database is proprietary and not easily translated.

That said, there are a few things you can try:

Take an iPod, dump a bunch of iTunes music on it, then import it from the iPod.  This results in capturing most of the ID3 tag data and a little more control over what to bring over.  Playlists aren't recognized.  They have to be recreated.  Edited:  Some playlist information is recognized.  GTKpod and Rhythmox will recognize playlists but not Banshee.

---

### Post by jslmg on 2008-01-22
I know this is an old thread, but I'm looking for something to do this, too. Looks like someone has offered a solution. Check out this project at Launchpad:

[https://launchpad.net/itunes-export](https://launchpad.net/itunes-export)

Any experience with this?

---

