---
title: "Mac OSx 10.5.8"
date: 2010-03-21
forum: Apple Hardware Users
---

### Post by Drenriza on 2010-03-21
A friend of mine. After upgrading to Mac OS x 10.5.8 has lost audio. Is this a common happening? and is their something we can do.

Like getting new audio drivers or something?
Thanks on advance

EDIT
Neither lspci |grep Audio nor aplay --list-devices apprently works in mac.
For checking what audio controller he has.

---

### Post by tyre_ on 2010-03-21
Try this:
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

I ended up adding
 ```
options snd-hda-intel model=mbp3
```to the end of my ala-base.conf file and my speakers and mic jac work now.

---

### Post by Drenriza on 2010-03-21
when trying to use the command. The terminal/konsole says
bash: options: command not found

???

---

### Post by linuxopjemac on 2010-03-22
replace lenovo-sky by mpb3, if you like to try that:
[http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32](http://mac.linux.be/phpBB3/viewtopic.php?f=3&t=32)

By the way, what kind of machine are we talking about? which Mac ?

---

### Post by Drenriza on 2010-03-22
Modelname:    iMac
  Model-id:    iMac4,1
  Processorname:    Intel Core Duo
  Processorspeed:    2 GHz
  Number processors:    1
  Number cores:    2
  L2-buffer:    2 MB
  Memmory:    2 GB
  Busspeed:    667 MHz
  SMC-version (system):    1.1f5

Will this code work for this mac?
```
 options snd-hda-intel model=lenovo-sky
```

---

### Post by linuxopjemac on 2010-03-22
I don't think so. I will have to digg a bit about your solution.

---

### Post by linuxopjemac on 2010-03-22
can you find out which soundcard you are using ? Model and type.

---

### Post by Drenriza on 2010-03-22
i have tryed to use
Neither lspci |grep Audio nor aplay --list-devices apprently works in mac

but doesnt work. how do i find out what soundcard he has?

---

### Post by linuxopjemac on 2010-03-22
```
 arecord -l
```

---

### Post by linuxopjemac on 2010-03-22
[http://www.cyberciti.biz/tips/howto-display-soundcards-digital-audio-devices.html](http://www.cyberciti.biz/tips/howto-display-soundcards-digital-audio-devices.html)

---

### Post by Drenriza on 2010-03-22
-bash: arecord: command not found

---

### Post by linuxopjemac on 2010-03-22
I would think with lspci you would get that audio card...just issue
```
lspci
```

and see if you see something...

---

### Post by Drenriza on 2010-03-22
when we tryed to use lspci it sayd

-bash: lspci: command not found

---

### Post by linuxopjemac on 2010-03-22
Are you sure you are in Ubuntu ? This is very weird.

---

### Post by jamesey on 2010-03-22
> **linuxopjemac said:**
> Are you sure you are in Ubuntu ? This is very weird.

haha! I think you are helping someone in MacOSX.

---

### Post by Drenriza on 2010-03-23
#1
> a friend of mine. After upgrading to mac os x 10.5.8 has lost audio. Is this a common happening? And is their something we can do.

:)

---

### Post by linuxopjemac on 2010-03-23
Oops, I don't expect to help people working in OSX ;) Thanks for that !

---

### Post by Drenriza on 2010-03-23
So your leaving the topic?

Mac OS x runs on the linux kernel. So can it be so hard to figur out a way to get the information about the sound card.

---

### Post by linuxopjemac on 2010-03-23
> Mac OS x runs on the linux kernel. So can it be so hard to figur out a way to get the information about the sound card. 

OSX does not run on the linux kernel, you are wrong. You better ask help in a Mac related forum, like mac-forums.com. We are dealing with Ubuntu Linux, you are dealing with OSX 10.5.8.

---

