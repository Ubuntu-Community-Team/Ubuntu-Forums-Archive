---
title: "login sound request"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by oliviacond on 2006-11-30
I'm using Edgy and I like Dapper login sound. How to install Dapper login sound on Edgy?

---

### Post by nickburns on 2006-11-30
mmmmmmmmmmm, how do you change it to any sound?  

anybody?

---

### Post by nickburns on 2006-11-30
Figured it out, the files are in /usr/share/sounds/

the file is login.wav

You can change the default sounds and add new ones with:

System >> Preferences >> Sounds

I guess someone could post the Drapper sound up here for you. (I'm Edgy too)

---

### Post by CatKiller on 2006-11-30
[This]("http://packages.ubuntu.com/dapper/gnome/ubuntu-sounds") should contain the Dapper sounds.

---

### Post by oliviacond on 2006-11-30
How to replace the old sound?

---

### Post by nickburns on 2006-11-30
Once you get the sound you want, I recommend you copy it to /usr/share/sounds/

then go to System >> Preferences >> Sounds

Pick the login combobox and select 'Select sound file'

then you can check that you got the right sound by playing the sound with the little triangle button next to the combobox

---

### Post by nickburns on 2006-11-30
Try this if you still need help.


Download this file to your Desktop

[login.wav]("http://www.flippinsweetdude.com/twiki/pub/Software/UbuntuSounds/login.wav")

then run in terminal

sudo cp /home/YOURNAME/Desktop/login.wav /usr/share/sounds/

(replace YOURNAME with the right word)

and you should be good...

---

### Post by oliviacond on 2006-12-02
problem solved. thank you. :)

---

### Post by roobarb! on 2006-12-12
I don't understand why on earth the Ubuntu folks decided to change those sounds for Edgy - the login (and logout) sounds in Dapper are fantastic.

The login sound they were replaced with in Edgy is nothing short of  cheesy, complete with a little toy cymbal crash at the end. Urgh.

This may sound overly finicky, but I'm a strong believer that the 'fit-and-finish' of an OS is incredibly important, and my first impressions of Edgy weren't as slick as Dapper. One other particularly minor, but irritating, thing is the default screen colour which detracts from the startup splash; on Dapper it's a dark, chocolate background with a light splash (perfect), on Edgy it's a light creamy colour on which the light-coloured splash gets lost.

I'd better put the brakes on before I rant! ;)

---

### Post by howardroark on 2007-02-18
Hey, i'm on dapper, can someone send the edgy sound for me please? it's called ubuntu7-x-fade-rev.**WAV**

---

### Post by wscheer on 2007-03-27
Made a bit of a goof here #-o

I went into System > Preferences > Sounds and changed my login to a WAV file that Ubuntu does not like. Now when I try to login, Ubuntu hangs at the point right before it would usually play the song.

I can get to the terminal, is there any way I can copy a the old login sound back. The login sound that is not working is not called login.wav it's called something else. I tried to do a locate, but it did not bring up any other results besides the file that is on my Desktop.

---

### Post by Mujaheiden on 2007-03-31
Ha, great, topics like these. I upgraded dapper too, and my victim was complaining on the new sound. So I gave her the old one instead.

Here's the [new edgy :mad:]("http://daniel.wikimaas.org/files/ugly_startup_edgy.wav")   sound.

---

