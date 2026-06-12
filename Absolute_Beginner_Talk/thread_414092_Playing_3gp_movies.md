---
title: "Playing 3gp movies"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-19
I tried playing a clip ending in .3gp in VLC player and I've got video and no audio. Does anyone know what I need to do to get audio also?

---

### Post by bloodniece on 2007-04-19
I assume works fine for all other media files, system files, etc . . .?
  
I guess 3gp could be encoded with AAC or AMR.

Extensions:
.3gp 3GPP standard, GSM Network, Video: MPEG-4, H.263, Audio: AAC, AMR 


I would download any/all codecs, free and non-free, via Automatix.

[http://getautomatix.com]("http://getautomatix.com")

---

### Post by x-ray vision on 2007-04-19
I had plenty of problems with automatix before and I don't want to go down that route again.

---

### Post by x-ray vision on 2007-04-19
Anyone?

---

### Post by bloodniece on 2007-04-19
3gp uses 1 of 2 different audio codecs. you need the AMR or AAC codecs or both.  

[http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

```
sudo apt-get install libfaad2-0 
```


What kind of problem could you have with Automatix?  Easy Ubuntu? Oh, well, its all stuff in the repos. aptitude away.

---

### Post by x-ray vision on 2007-04-20
> **bloodniece said:**
> 3gp uses 1 of 2 different audio codecs. you need the AMR or AAC codecs or both.  

[http://www.penguin.cz/~utx/amr](http://www.penguin.cz/~utx/amr)

```
sudo apt-get install libfaad2-0 
```
I entered 'sudo apt-get install libfaad2-0 ' into a terminal and that didn't solve the audio problem. Is there anything else I'm supposed to do.


> **bloodniece said:**
> What kind of problem could you have with Automatix?  Easy Ubuntu? Oh, well, its all stuff in the repos. aptitude away.
The last time I installed it against the advice of others here, LimeWire refused to open for me. I had to uninstall and reinstall it to get it to work again.

---

### Post by x-ray vision on 2007-04-20
bump

---

### Post by x-ray vision on 2007-04-20
bumpety bump bump

---

### Post by noneofthem on 2007-04-20
Hey everyone!

The only thing that was working for me was installing realplayer. This seems to be the only way to get the audio working on those files. I couldn´t find a different solution yet.

Hope that helps...

greetz

none of them

---

### Post by n3tfury on 2007-04-20
you say "a clip".  so *just* one or *no* 3gp clips have audio on your system?

---

### Post by x-ray vision on 2007-04-20
No 3gp clips have audio.

---

### Post by rowanparker on 2007-05-30
> **x-ray vision said:**
> No 3gp clips have audio.

Might be late but oh well.

VLC doesn't support all the types of 3GP.

---

