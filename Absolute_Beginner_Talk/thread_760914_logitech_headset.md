---
title: "logitech headset"
date: 2008-04-20
forum: Absolute Beginner Talk
---

### Post by bschleusner on 2008-04-20
Does anyone know if the _Logitech ClearChat Comfort USB headset_ works under Linux?
here is the link: [http://www.newegg.com/Product/Product.aspx?Item=N82E16826104214](http://www.newegg.com/Product/Product.aspx?Item=N82E16826104214)

I just ran over the cord of my Logitech USB Headset 250 with my roller chair and don't have a left channel anymore... :(

Sooo.... I need a new pair!

---

### Post by wormser on 2008-04-21
My headset just died too.  I just purchased the same model today and will report back when I receive it.

---

### Post by nicedude on 2008-04-21
Found the following review for the headset in question in a minute with google

In the 90 reviews so far I couldn't find any mention of Linux compatibility but for those of you that it matters for - yes this headset worked out of the box for me with Ubuntu Linux 7.04 (Feisty Fawn).

Page that came from
[http://www.amazon.com/review/product/B0007ZFM38?filterBy=addThreeStar](http://www.amazon.com/review/product/B0007ZFM38?filterBy=addThreeStar)


Looks like you can both rest easy I think your covered :-)

---

### Post by wormser on 2008-04-24
I just got mine.  I plugged it in and it is not working on Gusty.  :(   Time to do some trouble shoooting.

---

### Post by wormser on 2008-04-24
Got it working easily with this [thread]("http://ubuntuforums.org/showthread.php?p=4783366#post4783366").  It did require a reboot to get the mic working.

---

### Post by wormser on 2008-04-25
Another update.  I am having issues with it in Gusty.

I started a new thread for troubleshooting it [here]("http://ubuntuforums.org/showthread.php?t=766245").

[B][COLOR=Red]Vote for better support: [http://brainstorm.ubuntu.com/idea/3764/](http://brainstorm.ubuntu.com/idea/3764/)




[/COLOR][/B]

---

### Post by bschleusner on 2008-04-25
I just my set in and it works perfect in 8.04 :-)

THX

---

### Post by poccino on 2008-05-06
I have a problem with Ubuntu 8. My Logitech headset does not work.
Any help?

---

### Post by bschleusner on 2008-05-06
What do you mean by problems? Can't get any sound or just a couple programs won't play through them?

---

### Post by poccino on 2008-05-06
I can get the initial Ubuntu's sound when I switch on my PC but no sounds if I try to play a song or to listen in.
usually, I opened mp3 with VLC.
I came back to Ubuntu 7 (Gutsy)

---

### Post by bschleusner on 2008-05-06
if you are using Gusty, just go to the terminal and type 

```
asoundconf set-default-card Headset
```

just replace 'Headset' with the appropriate device, which you can get by typing 

```
asoundconf list
```

---

### Post by poccino on 2008-05-06
Thanks, but I have no problem with Gutsy.

Does your hint work for Ubuntu 8 too?

---

### Post by bschleusner on 2008-05-07
For Ubuntu 8, I just go into PulseAudio Volume Control (you may have to install it..), right click on the playback stream and tell the stream to move to my headset.

IMO, PulseAudio is the best thing to ever happen to Ubuntu, it lets you redirect audio dynamicaly.

---

