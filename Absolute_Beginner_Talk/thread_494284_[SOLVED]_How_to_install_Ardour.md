---
title: "[SOLVED] How to install Ardour?"
date: 2007-07-06
forum: Absolute Beginner Talk
---

### Post by sab0403 on 2007-07-06
Ok, I've been searching and I can't find a single guide or how-to for Ardour installation. I don't want to upgrade to Studio; I want to keep *regular* Ubuntu, but I want to install a video and an audio editor. I've seen Ardour mentioned as *the* audio editor, so...

Anyway, when I try the "Add/Remove" app, it tells me that "Ardour can't be installed in your kind of computer (i386). Either the app requires special hardware functions, or the maker has decided not to support your kind of computer" (rough translation from spanish). So... what do I need to do? Ardour's web site doesn't specify a particular architecture...

Thanks in advance.

---

### Post by por100pre1 on 2007-07-06
Add the Ubuntu studio repos there are two versions of Ardour there. Check adding it with Synaptic, if  it doesn't ask to install ubuntustudio-desktop package you are good to go.

---

### Post by sab0403 on 2007-07-06
Ok... well, what are the Studio repos? I mean, not *what* are they, but... where can I find them?

Also, is Ardour the right choice? I just saw on their website that they claim it's "not a sound editor", which is what I'm looking for...

---

### Post by kpkeerthi on 2007-07-06
You can find the instructions here .. [www.ubuntustudio.com](www.ubuntustudio.com)

---

### Post by por100pre1 on 2007-07-06
```
sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'
wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update
```

I think Audacity is a simpler way to edit audio files...

---

### Post by kpkeerthi on 2007-07-06
You may also try audacious

---

### Post by sab0403 on 2007-07-06
Alright.

Thanks for all the help, guys! :D

---

