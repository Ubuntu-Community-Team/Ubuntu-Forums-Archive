---
title: "fine tuning ubuntu"
date: 2007-05-28
forum: Apple PPC Users
---

### Post by Redneo on 2007-05-28
I just installed Ubuntu on a powerbook G4 and had no problem installing but the the ubuntu page on the loading 
was discolored like the wrong driver was running. After that everything looked normal I tried to play a movie and it said it it needed the plug-ins and I installed them and still it says it needs the the plug-ins anyone have a idea what I'm doing wrong

thanks

---

### Post by depele on 2007-05-28
have you installed all those plugins.

what kind of file do you want to play?

grtz;..

---

### Post by Redneo on 2007-05-28
I'm sorry I knew I for got something it was a movie dvd  I was tryng out

---

### Post by 3rdalbum on 2007-05-28
Okay, that's a different kettle of fish.

DVDs are actually encrypted with DRM. Since you got Ubuntu for free, Canonical can't pay the movie studios for the decryption keys - besides, supporting the practice of DRM is unethical in the FOSS world!

However, you can still get DVDs playing. Visit this page: [http://www.medibuntu.org/repository.php]("http://www.medibuntu.org/repository.php")

Follow the directions on that page. Then, in Synaptic, install the libdvdread3, libdvdplay0, libdvdnav4 and libdvdcss2 packages. Now DVDs will play. Be aware that due to corrupt laws in certain countries (the USA), libdvdcss is probably illegal.

---

### Post by Redneo on 2007-05-28
I've been to the link you put up and I guess means going "under the hood" so I'm using a compiler or am I wrong in my thinking? this is my first use of Gnu/linux outside of a using a cd version I mean having a computer decated to using Gnu/linux on it full time.

---

### Post by stmiller on 2007-05-29
Just follow instructions on the PPCFAQs in the link below:

---

### Post by Redneo on 2007-05-30
I typed the following ing the terminal
"sudo wget [http://medibuntu.sos-sts.com/sources.list.d/feisty.list](http://medibuntu.sos-sts.com/sources.list.d/feisty.list) -O /etc/apt/sources.list.d/medibuntu.list"
and it asked for a password is the password related to the one on the computer or is the password this
"sudo apt-get update" 

and I'm using firefox on the apple for this

---

### Post by 3rdalbum on 2007-05-30
The password is your password.

Sudo apt-get update is a different command that you type afterwards.

You're not really going "under the hood" or "programming", you're just using the computer in a different way than you are probably familiar with. So no, this doesn't involve a compiler. Who knows, sometime in the future when there are voice-based-interface computers, people will regard using a GUI as "programming".

---

### Post by Redneo on 2007-05-31
thank for the help I've still not the movie dvd to play yet. I'm kinda running in different directions for the answer
but I got to start somewhere. I've loaded gxine and the addons for it and it says it it can't get it to stream or something of that nature. so what where am I going wrong?

---

