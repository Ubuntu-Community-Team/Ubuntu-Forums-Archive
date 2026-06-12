---
title: "Volume control changes headphone volume not speakers"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by browny254 on 2008-03-20
Hi, I have a problem on my laptop where the master volume control (the icon in the system tray and the physical button on the laptop) changes the volume of the headphones independent of weather any are plugged in or not. How can I change this so it changes the speaker volume instead.

I had previously had problems with my sound card and had to follow these [http://ubuntuforums.org/showthread.php?t=568463](http://ubuntuforums.org/showthread.php?t=568463) instructions to get any sound at all.

Interestingly a lot of ppl have been saying they have a problem where plugging in headphones doesnt mute the speakers, I didnt have that problem at all, just inverse control.

Currently to change the speaker volume I have to open the sound mixer and change PCM.

Also Im using kubuntu, but hopefully that doesnt matter as the instructions I followed to get sound working in the first place worked.

Cheers.

---

### Post by lesergi on 2008-04-04
Hi!

I revive the thread because I have the same problem, the laptop volume control set the headphone volume, not the PCM.

Anybody can help us??

Thanks!

---

### Post by northern lights on 2008-04-04
Can either of you post the output of ```
cat /proc/asound/cards
```

Thanks.

---

### Post by browny254 on 2008-04-04
im using kubuntu so im not sure if it will be the same but i fixed mine by right clicking on the volume control icon in the system tray and there is an option to select master channel...select pcm and it will work.

only problem is now i cant get headphones to work at all, no matter what channel i select, and i get no graphic display what volume im on when i change the volume.

---

### Post by lesergi on 2008-04-05
Hi!

The output of "cat /proc/asound/cards" is:

> 
sjovani@PCSJOVANI:~$ cat /proc/asound/cards
 0 [SB             ]: HDA-Intel - HDA ATI SB
                      HDA ATI SB at 0xf8700000 irq 17


Thanks!

---

### Post by northern lights on 2008-04-05
The problem lies in the nature of your card.

Intel High Definition Audio should work in Hardy out of the box. You basically have three options:

1. be content for four weeks and setup the new Hardy stable
2. try Hardy beta
3. manually compile the latest ALSA from source

Check out these links:
[https://help.ubuntu.com/community/HdaIntelSoundHowto]("https://help.ubuntu.com/community/HdaIntelSoundHowto")
[http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel]("http://www.alsa-project.org/main/index.php/Matrix:Vendor-Intel")

---

### Post by lesergi on 2008-04-28
Hi!

For me, this problem is solved with the new version: 8.04, simply upgrading the system.

Salut!

---

