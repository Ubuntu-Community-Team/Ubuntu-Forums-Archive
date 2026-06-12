---
title: "My sound doesn't work"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by HareBall on 2006-09-24
I have a Dell Dimension E510 desktop with onboard sound. How do I get the sound to work?
I'm not sure exactly what motherboard I have. It is about a year old and has an Intel processor running at 3.0 Gig.

---

### Post by xyz on 2006-09-24
Check this out to start you off:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by HareBall on 2006-09-24
> **xyz said:**
> Check this out to start you off:
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

This is good, but my sound isn't doing anything. I have several different programs to play things, but I don't get any kind of sounds.
Thanx,
Larry

---

### Post by xyz on 2006-09-24
You are certain to have all the codecs, right?
What kind of "different programs to play things"??
Can you stream music? Listen to internet radio?
What I mean is try to discribe your pbm a bit more.

---

### Post by HareBall on 2006-09-24
> **xyz said:**
> You are certain to have all the codecs, right?
What kind of "different programs to play things"??
Can you stream music? Listen to internet radio?
What I mean is try to discribe your pbm a bit more.

I mean I get no sound whatsoever out of my speakers. I have tried to play video files That people have emailed me. They play the video just fine.
I am trying at this moment to play a cd with VLC media player and there is no sound with the volume control set at max. I also tried to play it with sound juicer. Again no sound from the speakers.
I also don't get any of the sounds in the sound preferences.
Appearently the sound card has no driver, but I don't even know what driver to look for. Dell doesn't seem to want you to know.:-s

---

### Post by xyz on 2006-09-24
Try to see if everything is ON and at appropriate levels, type:
```
alsamixer
```
Play with the left/right arrows to get things the right way.
Also:
Application>Sound & Video>Volume Control and check what you've got there.

---

### Post by HareBall on 2006-09-24
> **xyz said:**
> Try to see if everything is ON and at appropriate levels, type:
```
alsamixer
```
Play with the left/right arrows to get things the right way.
Also:
Application>Sound & Video>Volume Control and check what you've got there.

Everything is at 100% in Alsamixer and also the volume control. I just tried the cd again and no change. Sound Juicer shows it playing, but I don't get any sound.

---

### Post by bulldog on 2006-09-24
Did you double click your sound icon for some options and try a right click as wel to see more options.

Just a thought.

---

### Post by bodhi.zazen on 2006-09-24
Can you hear sound in your headphones?

Check options in both gnome-volume-control and in sound juicer.

Try xmms, an oldie but goodie.

---

### Post by deadgobby on 2006-09-24
[http://ubuntuforums.org/showthread.php?t=205449&highlight=PC](http://ubuntuforums.org/showthread.php?t=205449&highlight=PC)
[https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles](https://wiki.ubuntu.com/?action=fullsearch&context=180&value=sound&titlesearch=Titles)
Gobby

---

### Post by HareBall on 2006-09-24
> **bulldog said:**
> Did you double click your sound icon for some options and try a right click as wel to see more options.

Just a thought.

Yes, I double clicked and right clicked. Didn't find anything to be of any help.
How do you turn things on and off in the alsamixer? I have found that my LFE is turned offand all I seem to be able to do is turn the volume up and down.
Also, my input source is set to mic and I can't figure out how to change it either.
Thanx,
Larry

---

### Post by bodhi.zazen on 2006-09-24
LOL :lol: Try this: [How to sound](http://ubuntuforums.org/showthread.php?t=205449)

---

### Post by xpod on 2006-09-24
How about "multimedia system selector"???
You can enable it via alcarte meny editor......it`s good for testing sound issues

---

### Post by bodhi.zazen on 2006-09-24
> **xpod said:**
> How about "multimedia system selector"???
You can enable it via alcarte meny editor......it`s good for testing sound issues

Screenshot ?

---

### Post by xpod on 2006-09-24
ERM...Ive been up the hospital as my son fell out a tree(no comments about ME being out my tree to thank you)....

SOOOO...i aint had a chance yet...

EDIT:am i mistaken or have you just unleashed THAT bean count...It was YOU was`nt it!!!:D

---

### Post by HareBall on 2006-09-24
> **bodhi.zazen said:**
> LOL :lol: Try this: [How to sound](http://ubuntuforums.org/showthread.php?t=205449)

Thanx, I found what I needed here. Sort of anyway. I started playing around with various keys and got into help and atrted pushing the F keys which got me back to playing around with alsamixer and just making changes until I got to hit F4 and I changed the MUX to 100. Just like that sound!!
Thanx,
Larry

---

### Post by HareBall on 2006-09-24
Thanx to everyone.
I got it finally. I need to start plying with stuff more to see what it can do. Especially since I don't really have anything saved here yet and can load the OS again if needed. Already did that once ;)
Larry

---

### Post by xpod on 2006-09-24
Sound can get a bit wonky i have found once you start getting more and more stuff that uses it...
It`s handy to suss out all the wee things that can get it sorted as it seems one of the more common issues..

Good luck anyway mate..

Just ignore us scottish and irish nutjobs....we like to annoy each other

---

### Post by bodhi.zazen on 2006-09-24
> **HareBall said:**
> Thanx, I found what I needed here. Sort of anyway. I started playing around with various keys and got into help and atrted pushing the F keys which got me back to playing around with alsamixer and just making changes until I got to hit F4 and I changed the MUX to 100. Just like that sound!!
Thanx,
Larry

Nothing like hunt-n-peck

---

### Post by HareBall on 2006-09-24
> **bodhi.zazen said:**
> Nothing like hunt-n-peck

I'm a hunt and pecker from way back.
Some just call me a pecker;)

---

### Post by xpod on 2006-09-24
I mabey know you then:D

---

