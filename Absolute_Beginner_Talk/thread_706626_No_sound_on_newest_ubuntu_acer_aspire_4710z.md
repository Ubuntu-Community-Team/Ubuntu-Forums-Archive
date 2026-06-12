---
title: "No sound on newest ubuntu acer aspire 4710z"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by rajm11 on 2008-02-24
Hello guys, I have neweest version of ubuntu on my ACER aspire 4710z with realtek HD sound card.
Now I used to have sound on speakers but not on headphones, so  I tried searching forum and downloaded realtek linux audio pack5.0 and installed it . 
Now I have lost my speaker sound. So please can any one tell me how to correct it, step by step? I would really appreciate it.

---

### Post by rajm11 on 2008-02-24
ok I opned amarok, and totem and mplayer they all working perfect, they say there is sound , but its not coming out. I checked with my buttons and in preferences sound, its all OKAY, but still no sound :( is there something that has muted all sounds ?

---

### Post by tdrusk on 2008-02-24
Try going into the mixer and turning up the surround.

---

### Post by rajm11 on 2008-02-24
first of all thanks !Ok I opened audio properties  and checked that PCM and master are both fine and at highest level, and the device chosen is HDA intel (alsa mixer) still no sound!

---

### Post by tdrusk on 2008-02-24
> **rajm11 said:**
> first of all thanks !Ok I opened audio properties  and checked that PCM and master are both fine and at highest level, and the device chosen is HDA intel (alsa mixer) still no sound!
Right click the little sound applet in the top right bar, and click "surround"
then crank it up!

If you want to see it in the mixer go into the mixer and go to edit and check surround.

---

### Post by northern lights on 2008-02-24
If the alsa-mixer settings are fine and your still lost, post the output of ```
cat /proc/asound/cards
```

---

### Post by rajm11 on 2008-02-24
Thanks guys but i could not found SURROUND in volume applet. It just has following options 
Mute
Open volume Control
preferences 
about remove from panel
....

any ways here is out put of 
raj@rajl-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc240000 irq 22

---

### Post by tdrusk on 2008-02-24
> **rajm11 said:**
> Thanks guys but i could not found SURROUND in volume applet. It just has following options 
Mute
Open volume Control
preferences 
about remove from panel
....

any ways here is out put of 
raj@rajl-laptop:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xdc240000 irq 22

I'm sorry. Click preferences when you right click the applet.

---

### Post by rajm11 on 2008-02-24
by the way northen lights
One ought, every day at least, to hear a little song, read a good poem, see a fine picture, and, if it were possible, speak a few reasonable words...
Awesome quote!

---

### Post by rajm11 on 2008-02-24
i did that in preferences it just shows HDA Intel(alsa Mixer)
and 
realtek ID 
In HDA intel it shows PCM master and digital thats it

---

### Post by northern lights on 2008-02-25
> **tdrusk said:**
> Try going into the mixer and turning up the surround.
His problem cannot be solved via the alsa-mixer.

> **rajm11 said:**
> by the way northen lights, Awesome quote!
Thanks. Originally said by Johann Wolfgang von Goethe, German poet

Anyways, the problem lies in your type of soundcard, which has been causing trouble in Ubuntu since Lord knows when.

This [HowTo]("https://help.ubuntu.com/community/HdaIntelSoundHowto") should solve your problem.

---

### Post by tdrusk on 2008-02-25
> **rajm11 said:**
> i did that in preferences it just shows HDA Intel(alsa Mixer)
and 
realtek ID 
In HDA intel it shows PCM master and digital thats it

So nothing shows up like this? (look at attachments)

---

### Post by superprash2003 on 2008-02-25
try this- go to system->preferences->sound  change from auto detect to any other option.. any one might work..CS46XX worked for me

---

### Post by dsjohnson6554 on 2008-03-01
I am having a similar problem on my acer aspire 3680. I had sound on both the headphones and speakers with 6.06; but with 7.04 and 7.10 I only have sound on the headphones.

I have opened the ALSA mixer and found nothing muted; rather every slider is at maximum output. I have right clicked on the sound icon on the upper right of the screen and find no settings for surround. I have gone through the terminal procedure suggested by the first responder and still I have sound only through the headphones. 

Help would be appreciated please.

---

### Post by teamkiller87 on 2008-03-01
Had the same problem with a realtek card. This fixed it. Run the following command:

```
sudo nano /etc/modprobe.d/alsa-base
```

And add this line to the end of the file:

```
options snd-hda-intel model=MODEL
```

Hope it helps.

---

### Post by tdrusk on 2008-03-02
> **dsjohnson6554 said:**
> I am having a similar problem on my acer aspire 3680. I had sound on both the headphones and speakers with 6.06; but with 7.04 and 7.10 I only have sound on the headphones.

I have opened the ALSA mixer and found nothing muted; rather every slider is at maximum output. I have right clicked on the sound icon on the upper right of the screen and find no settings for surround. I have gone through the terminal procedure suggested by the first responder and still I have sound only through the headphones. 

Help would be appreciated please.

I have the 3680. You need to turn up the SURROUND slider.

---

