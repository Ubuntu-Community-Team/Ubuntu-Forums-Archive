---
title: "my sounds in gaim stopped working."
date: 2005-11-16
forum: Absolute Beginner Talk
---

### Post by onesojourner on 2005-11-16
I don't think I have changed anything but gaim has stopped displaying any sound when a message is recieved. I have gone through the program options and they are all set to display sounds. what else should a check?

---

### Post by kruz on 2005-11-16
well first look in ur options
sry im at work under xp
i think its something like
tools>preferences?
go into ur sound and check
if all other sounds work
(wave and mp3)
then start it in console and watch for any errors
using the command
gaim
not gaim& so u can watch
see if this does anything and get back with me
hope i help

---

### Post by onesojourner on 2005-11-16
sorry I forgot to add that when I click test under the gaim preferences I get nothing.

---

### Post by kruz on 2005-11-16
oh, hmm ill look into it

---

### Post by kruz on 2005-11-16
[http://gaim.sourceforge.net/faq.php#q24](http://gaim.sourceforge.net/faq.php#q24)

and 

[http://gaim.sourceforge.net/faq.php#q23](http://gaim.sourceforge.net/faq.php#q23)

possibly installing another sound driver
or xmms could have messed it up
i had to set it back to alsa after i installed xmms

am i sure why ? no lol

also other sounds on the os and mp3/wave files work right?

---

### Post by onesojourner on 2005-11-16
ok I am pretty new here so can some one explain this to me

 If you choose "Automatic", you can create a file, either /etc/libao.conf or ~/.libao, and put one of the following lines in it:

default_driver=alsa
default_driver=oss

I need more step by step instructions

---

### Post by kruz on 2005-11-16
I use alsa
use alsa
then type

alsamixer
(if you have 2 sound cards one is 0 and one is 1)

just type
alsamixer
in console then use <- ^ -> (arrow keys) to turn everything up
and see if u get something then

btw STILL can you play other music mp3/waves??!?!?!

---

### Post by onesojourner on 2005-11-16
ya I have sound from everything else. I willl check that out and get back to ya.

---

### Post by onesojourner on 2005-11-16
ok I turned everything up in alsamixer still nothing. 

in the gaim sound settings I have it set to auto. is that right?

---

### Post by onesojourner on 2005-11-17
can some one just tell me how I would open up the text file (or what ever thats called) in gaim so I can type this in 
default_driver=alsa
default_driver=oss

---

### Post by onesojourner on 2005-11-18
any one?

---

### Post by onesojourner on 2005-11-18
this is not that hard is it? I just need to know where these commands(above link) go. Please help me.

---

