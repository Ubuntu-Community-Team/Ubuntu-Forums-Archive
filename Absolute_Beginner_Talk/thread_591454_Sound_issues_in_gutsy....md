---
title: "Sound issues in gutsy..."
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by tweistein on 2007-10-25
Hello everybody..:-)
After trying various potential solutions for enabling sound on my Zepto-notebook, including complete reinstalling alsa drivers i'm stuck. I can see signals in vu-meter in audacity but no sound from speakers... When i go into sound menu and try testing i get this.... 
gconfaudiosrc ! audioconvert ! audioresample ! gconfaudiosink profile=chat: Kunne ikke etablere forbindelse til lydserver
last part ( after"chat) in danish says "could not connect to sound server"
Havent a clue what to do - pleeease help - thanks in advance..:-)

---

### Post by dei on 2007-10-26
you're using a normal ubuntu gutsy, right? Not Kubuntu and not Ubuntu Studio?

Did you tried the headphone-jack(s)? Did it work already with other Ubuntu-Releases? Have you checked the volumes in alsamixer (in console) are all on 100%?
I'd recommend you to compile the newest alsa-drivers by yourself (not these out of the ubuntu-repository but from source from the alsa-website) if you didn't already, there are many hardware-support fixes in it...

---

