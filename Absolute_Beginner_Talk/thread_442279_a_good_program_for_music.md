---
title: "a good program for music?"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by Jorge32 on 2007-05-13
Hi
I was wondering if there is a good program, with equalizations pre configured and quite a good look? something like quintessential player or at least as winamp.... 
in xmms I could not put any presets for equalizations (i tried with quintessential eqpresets.eql) and I had problems with amarok... any recommendation?

---

### Post by Digitallysick on 2007-05-13
xmms is about the best, it does have presets, make sure you go to equalizer, and on the right side it has a presets button.  You can load, import, save, etc presets

or try this

    *  Download the Xmms presets 

 wget [http://xmms.org/misc/winamp_presets.gz](http://xmms.org/misc/winamp_presets.gz)

    * Install the Presets 

 gunzip -c winamp_presets.gz > ~/.xmms/eq.preset

    * Launch XMMS, hit the Preset button, and select load-->Preset 

    * Choose the settings you want to use

---

### Post by Jorge32 on 2007-05-13
hey thanks a lot! that did work out

---

### Post by Jorge32 on 2007-05-13
is there a way of making xmms the prefered application to read mp3 and to open music cds?

---

### Post by Hobo Joe on 2007-05-13
Personally I'm a big fan of Amarok, you can just download it through synaptic.

It's got all sorts of neat features that you should find useful.

---

### Post by Acksys on 2007-05-13
> **Hobo Joe said:**
> Personally I'm a big fan of Amarok, you can just download it through synaptic.

It's got all sorts of neat features that you should find useful.

Don't forget you also have to install the libxine-extracodecs package if you install Amarok under Feisty.

---

### Post by Digitallysick on 2007-05-13
no idea how to make it preferred, all mine play in xmms , i think i right click the mp3z and open with xmms and after a while it just started to open in xmms

---

### Post by hyper_ch on 2007-05-13
Amarok is the best music player (IMHO) available and it's worthing switchting to linux just because of it :)

---

### Post by ss87 on 2007-05-13
Amarok is pretty good. They've made some good improvements in the latest version. I reckon songbird will be the best when it gets going.

---

### Post by Jorge32 on 2007-05-13
what makes amarok best above xmms for example?

Isn't the library difficult (in terms of intuitive and easy and fast)  in comparisson with for example itunes or winamp or quintessential media player?

Could you equalize and take presets in amarok?

is there a way of having a media library like the ones above for xmms?

---

### Post by orb9220 on 2007-05-13
[http://amarok.kde.org/features](http://amarok.kde.org/features)

---

### Post by isaacj87 on 2007-05-13
one word...

Banshee.

excellent player, great looks, and easy to use.

---

### Post by hyper_ch on 2007-05-14
Think of any feature a music player should have and there's a good chance Amarok has that feature already implemented...

---

### Post by muggins on 2007-05-28
> **Digitallysick said:**
> xmms is about the best, it does have presets, make sure you go to equalizer, and on the right side it has a presets button.  You can load, import, save, etc presets

or try this

    *  Download the Xmms presets 

 wget [http://xmms.org/misc/winamp_presets.gz](http://xmms.org/misc/winamp_presets.gz)

    * Install the Presets 

 gunzip -c winamp_presets.gz > ~/.xmms/eq.preset

    * Launch XMMS, hit the Preset button, and select load-->Preset 

    * Choose the settings you want to use

When I use "gunzip -c winamp_presets.gz > ~/.xmms/eq.preset" in xubuntu nothing happens I just get another prompt in terminal, should I be replacing gunzip with something else?

---

### Post by shen-an-doah on 2007-05-28
> **muggins said:**
> When I use "gunzip -c winamp_presets.gz > ~/.xmms/eq.preset" in xubuntu nothing happens I just get another prompt in terminal, should I be replacing gunzip with something else?

You mean it just comes back up with "yourname@computername:~$"? That means it's worked. It will usually only say anything if there's an error.

---

### Post by dunomous on 2007-06-02
> **Jorge32 said:**
> is there a way of making xmms the prefered application to read mp3 and to open music cds?

Yes. Right click any type of audio file (mp3, ogg, etc..) and click "Properties." Then select the "Open With" tab and select whichever program you want to make the default player.

---

### Post by kylor on 2007-06-03
Personally, I think Rhythmbox, which comes packed with Ubuntu, is pretty nice. I like the interface, reminds me of wxMusic (although I don't know which one came first).

I don't like the way XMMS looks at all. I'm not a very big Winamp fan, and this thing looks just like winamp.

I did try Amarok, and it was pretty nice, but it still didn't integrate as well as Rhythmbox did. Maybe I just need to tinker with it a bit more.

---

