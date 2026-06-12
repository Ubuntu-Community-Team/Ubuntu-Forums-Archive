---
title: "video problem"
date: 2007-08-27
forum: Absolute Beginner Talk
---

### Post by guilly on 2007-08-27
Whenever i play videos with any other player except VLC the colors are off. It seems to be a codec problem, but i just dont know how to determine which ones i'm missing? this also happens when i'm streaming from online. 

If i play the same video in VLC everything is fine though.

Any suggestions??

thanks!

---

### Post by Jimmyfj on 2007-08-27
You can install the codecs from either Synaptic or Add/Remove - or you can open a terminal and write this:

```
 sudo apt-get install ubuntu-restricted-extras
```

---

### Post by guilly on 2007-08-27
> **Jimmyfj said:**
> You can install the codecs from either Synaptic or Add/Remove - or you can open a terminal and write this:

```
 sudo apt-get install ubuntu-restricted-extras
```

i'm pretty sure i've already done this. Is there any way to check if i'm missing certain codecs?

---

### Post by Marat Galiev on 2007-08-27
Maybe problems in you graphics card?

---

### Post by guilly on 2007-08-27
nope. i play the videos fine in Windows so i highly doubt its the vid card

---

### Post by guilly on 2007-08-28
> **Jimmyfj said:**
> You can install the codecs from either Synaptic or Add/Remove - or you can open a terminal and write this:

```
 sudo apt-get install ubuntu-restricted-extras
```

alright so i did these steps last night when i got home but i'm still seeing the same results, are there any other reasons why i would be experiencing this?

---

### Post by Marat Galiev on 2007-08-28
sorry,in you graphics card driver:)
You install driver?

---

### Post by guilly on 2007-08-28
Yea i Highly doubt it has anything to do with my graphics card. i'm running Beryl and i have 2 19 inch widescreens running at 2800X1800 resolution

---

### Post by Marat Galiev on 2007-08-28
yes it is!
shutdown you beryl session,and boot without beryl.
play some videos again.
what you graphics card model?
and what drivers for video card you have installed?

---

### Post by mysticmatrix on 2007-08-28
> **guilly said:**
> Yea i Highly doubt it has anything to do with my graphics card. i'm running Beryl and i have 2 19 inch widescreens running at 2800X1800 resolution

Beryl might be source of trouble. Try these fixes

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_fix_black_windows_during_video_playback)

---

### Post by guilly on 2007-08-28
> **Marat Galiev said:**
> yes it is!
shutdown you beryl session,and boot without beryl.
play some videos again.
what you graphics card model?
and what drivers for video card you have installed?

I have been running it without beryl. I was just simply stating that i can run beryl with no graphics problem. But as we all know Beryl does not run very well with BigScreen. Could my BigScreen be the problem>?

mysticmatrix, 

Thanks i'll give that a try when i get home tonight.

---

### Post by Marat Galiev on 2007-08-28
what is BigScreen?
You mean widescreen monitor?

---

### Post by guilly on 2007-08-28
BigScreen is a "mode" i guess you can call it that Ubuntu uses to configure dual screens

---

