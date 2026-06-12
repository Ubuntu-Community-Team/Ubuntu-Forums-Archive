---
title: "[SOLVED] when will Synaptic be usable?"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by coront on 2007-10-22
I installed gutsy 4 days ago and it's useless right now. I can't play music, download any programs or even install flash player to view websites properly. How much longer will this continue? thank you :)

---

### Post by bigee1212 on 2007-10-22
I'm not exactly sure what you mean by synaptic, but let me help you get those restricted formats working

If you click Applications --> add/remove programs

click in the top right corner in the drop down menu to include all software

search "gstreamer" check off anything you want to be installed (mp3 etc) one of them should be ubuntu restricted or something like that everything should be good to go

---

### Post by riminicat on 2007-10-22
> **coront said:**
> I installed gutsy 4 days ago and it's useless right now. I can't play music, download any programs or even install flash player to view websites properly. How much longer will this continue? thank you :)

Hey have u tried messing around with the universe/multi-universe settings? It does help a little, I can't tell u much about ubuntu 7.10 because its knew and I haven't been messing with Ubuntu for long.  Good luck!! I'll be looking for an answer and I'll let you know if i find one

---

### Post by divague on 2007-10-22
i've installed gutsy the day it was released, and right now it's working fine, i can listen to mp3 files, flash is working, java is working, can play dvd, etc

---

### Post by akiratheoni on 2007-10-22
I only found it 'unusable' the first day, when everyone was downloading and updating and installing etc. from Synaptic. But even then, I was able to get some things done. But it's fine for me now.

---

### Post by coront on 2007-10-22
but why doesn't it work for me??? not even the plug-in installer in firefox works. Could it be another problem?

---

### Post by Maestro23 on 2007-10-22
> **coront said:**
> but why doesn't it work for me??? not even the plug-in installer in firefox works. Could it be another problem?

What is happening when you try and use Synaptic?  Any errors, shutting down, etc...

---

### Post by coront on 2007-10-22
synaptic starts fine, I hit search and search something but no results appear, just a blank screen. Also, when I try to install the GStreamer codecs I hit "confirm" and then a message tells me I need to reload the results page and then click confirm again and again. It seems to have no contact with the servers.

---

### Post by justin whitaker on 2007-10-22
> **coront said:**
> synaptic starts fine, I hit search and search something but no results appear, just a blank screen. Also, when I try to install the GStreamer codecs I hit "confirm" and then a message tells me I need to reload the results page and then click confirm again and again. It seems to have no contact with the servers.

This might be any number of things....first, how is your internet connection? 

Next, are you trying to connect to a local mirror in Chile, or the Main server? 

Next, do you have multiverse and universe enabled? Did you reload the repositories after you enabled them?

Finally, did you try apt or aptitude instead? What did they tell you?

---

### Post by coront on 2007-10-22
I had EVERY repository disabled, now it is fixed. Sorry for the trouble :(

---

