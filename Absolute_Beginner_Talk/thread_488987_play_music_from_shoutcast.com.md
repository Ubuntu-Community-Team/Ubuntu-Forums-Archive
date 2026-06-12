---
title: "play music from shoutcast.com ?"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by j1234f on 2007-06-30
play music from [http://www.shoutcast.com/](http://www.shoutcast.com/)   ?
Or any set of internet radio stations for that matter.

I clicked on it with my Kubuntu install and it didn't play.
Seems to want to send it to amaroK but no sound.  Funny, my ethernet
led is blinking like crazy after I click on a radio station, so it seems to
be sending music.

Then I thought I would try xmms so I did apt-get install xmms
and it installed with no errors.

Now i right clicked and try to open with
xmms, but xmms comes up with no music and wants me to select
a local file to play;  It does not hookup to the music stream.

Tried manually starting it too:
xmms 'http://www.shoutcast.com/sbin/shoutcast-playlist.pls?rn=1025&file=filename.pl'
but still no blinking lights.

thanks

---

### Post by Empath on 2007-06-30
I use streamtuner in combination with XMMS, streamtuner does the actual locating of the shoutcast stations. XMMS does the playing, I use gnome though. But you could see if streamtuner will work with kubuntu :\

---

### Post by wolfen69 on 2007-06-30
i also recommend streamtuner(wont work without xmms installed). the interface is very well done. it also does other online stations besides shoutcast.

---

### Post by j1234f on 2007-06-30
# apt-get install streamtuner
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package streamtuner

Never heard of streamtuner, but sounds like a good idea.
maybe it's only in ubuntu and not kubuntu?

---

### Post by kerry_s on 2007-06-30
check your settings, make sure all the volumes are turned up and you have your sound card selected in the volume manager.

---

### Post by j1234f on 2007-07-01
I hear konqueror and kmail make a noise on the speakers when I click.
amarok puts up the name of the song.

Played with the volume control in lower right icon and upped all
the sliders.  Clicked and unclicked some buttons.
I still don't hear any radio.

I do see amarok bring up the name of songs as if it were working.

(as a further note: this same computer did a boot as ubuntu rather than kubuntu
on another hard disk and the sound worked for amarok and xmms, so
something is different?)

---

### Post by j1234f on 2007-07-01
One further clue.  I just browsed through amaroks menus and 
it will play the example files on the hard disk that came with
the kubuntu install.  Just shoutcast radio stations still won't play.

---

### Post by wolfen69 on 2007-07-01
did you enable/add all repositories?

---

### Post by j1234f on 2007-07-01
I don't see a button to add repository or enable it?

---

