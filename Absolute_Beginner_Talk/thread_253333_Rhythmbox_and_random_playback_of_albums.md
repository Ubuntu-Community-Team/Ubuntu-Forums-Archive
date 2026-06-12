---
title: "Rhythmbox and random playback of albums"
date: 2006-09-08
forum: Absolute Beginner Talk
---

### Post by boon on 2006-09-08
I like to play music in a random shuffle except for selected albums (eg, concept albums) where I prefer to play it through.

Is there some way to 'connect' tracks from an album so that when Rhythmbox is set to random playback it will play that album's songs sequentially before moving randomly to the next song or album?

---

### Post by davmac on 2006-09-08
I'm not aware of a way of doing this in Rhythmbox but you could concatenate the individual tracks from the concept albums into one using mp3wrap. You can find out more at [http://mp3wrap.sourceforge.net/](http://mp3wrap.sourceforge.net/)

Once it is installed you need to open up a terminal windows, navigate to the relevant directory and type "mp3wrap albumname.mp3 trackprefix*.mp3"

Hope this helps,

Dave Mac

---

### Post by dbd on 2006-09-08
I don't know about Rhythmbox, but I do know that Amarok has this feature, if you haven't yet given it a go I'd recommend that you do, it's a really great media played :)

---

### Post by skymt on 2006-09-08
Quod Libet also has album shuffle, through a plugin.

---

### Post by terminatingzero on 2006-09-08
I think this app may have what you're looking for but I'm not certain I have only slightly experimented with it so far. Though I do like it alot.
[http://listengnome.free.fr/]("http://listengnome.free.fr/")
Hope it helps.

---

### Post by boon on 2006-09-08
thanks for your replies.

Re mp3wrap, does this or something similar work with ogg files? Most of my files are ogg because its a free format and (reportedly) gives better quality for the same space.

re amarok, is there a gnome version of this or do i need to install Kde?

---

### Post by skymt on 2006-09-08
There is no GNOME version of Amarok. Install it through apt (apt-get, aptitude, synaptic, or whatever) and it'll only pull in the bits of KDE it needs.

You can join ogg files on the command line. Like this:```
cat ogg-1.ogg ogg-2.ogg ogg-3.ogg ogg-n.ogg > big-ogg-file.ogg
```

---

### Post by boon on 2006-09-15
> **skymt said:**
> There is no GNOME version of Amarok. Install it through apt (apt-get, aptitude, synaptic, or whatever) and it'll only pull in the bits of KDE it needs.

You can join ogg files on the command line. Like this:```
cat ogg-1.ogg ogg-2.ogg ogg-3.ogg ogg-n.ogg > big-ogg-file.ogg
```

I've done this and created a bigoggfile.ogg but it doesnt play at all in Rhythmbox and in Movie Player it plays the first track but then gives an error: "An error occurred: Could not decode stream."

I tried mp3wrap and that works as desired with mp3 files but not with ogg. ie, I can 'wrap' ogg files ok but they wont play in either of the players above, even if i rename them as .ogg files.

Is there an ogg cd ripper that will rip a whole cd as 'one track'?

---

### Post by boon on 2006-09-15
> **skymt said:**
> There is no GNOME version of Amarok. Install it through apt (apt-get, aptitude, synaptic, or whatever) and it'll only pull in the bits of KDE it needs.

You can join ogg files on the command line. Like this:```
cat ogg-1.ogg ogg-2.ogg ogg-3.ogg ogg-n.ogg > big-ogg-file.ogg
```

I've done this and created a bigoggfile.ogg but it doesnt play at all in Rhythmbox and in Movie Player it plays the first track but then gives an error: "An error occurred: Could not decode stream."

I tried mp3wrap and that works as desired with mp3 files but not with ogg. ie, I can 'wrap' ogg files ok but they wont play in either of the players above, even if i rename them as .ogg files.

Is there an ogg cd ripper that will rip a whole cd as 'one track'?

---

### Post by alsbergt on 2007-06-17
> **skymt said:**
> Quod Libet also has album shuffle, through a plugin.

Care to give a link to where I can find this plugin?  I installed Quod Libet, found it nice, but could not find an album shuffle plugin for it anywhere.

  -- Tom

---

