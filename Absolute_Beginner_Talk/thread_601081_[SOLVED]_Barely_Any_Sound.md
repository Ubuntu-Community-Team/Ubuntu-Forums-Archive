---
title: "[SOLVED] Barely Any Sound"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by tyler24_11 on 2007-11-02
When I watch Videos on Youtube or anywhere The sound coming out of my speakers is very low I can barley hear anything and they are turned up all of the the way 

please help


Thanks

---

### Post by rsambuca on 2007-11-02
Have you turned up the volume on your top panel (should be near the right side)?

---

### Post by meanburrito920 on 2007-11-02
have you tried the master sound control in the upper right hand corner by the power button?

---

### Post by tyler24_11 on 2007-11-02
Yes i tuned everything all the way up :P

---

### Post by rsambuca on 2007-11-02
Check the sound preferences and make sure that the "pcm" channel is turned up.

---

### Post by tyler24_11 on 2007-11-02
Turned up all the way my friend

---

### Post by rsambuca on 2007-11-02
Are you using Alsa, or Oss?

---

### Post by tyler24_11 on 2007-11-02
Alsa


im not sure what sound card i have is

---

### Post by rsambuca on 2007-11-02
Is it only videos?  Or all sound files?

---

### Post by tyler24_11 on 2007-11-02
aLL SOUND

 nVIDIA GeForce® 6100 and nVIDIA nForce® 430

---

### Post by rsambuca on 2007-11-02
Do you have a liveCD handy - you could boot from that to see if the sound works.

---

### Post by tyler24_11 on 2007-11-02
yah it actually in my dirve right now this is a fresh copy of 7.10 coupl hours old

---

### Post by rsambuca on 2007-11-02
Oh, so this is the liveCD that you are using?  Did you run the CD integrity check first?

---

### Post by tyler24_11 on 2007-11-02
Im on my live cd now ad there still is barley any sound NOW WHAT?! I just put in my live cd and yah i did the check

I WAS NOT ON THE LIVE CD I JUST PUT IT IN

---

### Post by tyler24_11 on 2007-11-02
Does anyone have any ideas ?

---

### Post by rsambuca on 2007-11-02
Sorry, I don't know enough about the nforce 430.  Did you try using OSS at all?

EDIT:  and please don't bump your threads so quickly.  If you need immediate responses use the IRC channel.

---

### Post by tyler24_11 on 2007-11-02
I tried  OSS but when i was running windows im pretty sure it came with Realtek audio mixer so i might have that kind of sound card

---

### Post by LinuxD on 2007-11-02
I had a similar problem with my toshiba laptop when I switched to linux... Apparently it was related to Alsa-mixer and my having an intel sound card. 

I don't know if it's relevant to your case, but my fix was to add a line of code near the end of

/etc/modprobe.d/alsa-base

```
options snd-hda-intel position_fix=1 model=auto
```

I'm still new overall to linux though so mabye this will give a good start point for someone else to explain it in more detail.

---

### Post by tyler24_11 on 2007-11-02
Do i type this line of code in to terminal or where?

I obviously dont have an intel sound card :P

My Cpu is Acer Aspire T180
AST180-ES321M                    



ALL STOCK

---

### Post by LinuxD on 2007-11-02
Sorry, guess I read through the post a little too quickly...

Have you tried looking through [[COLOR="Blue"]http://ubuntuforums.org/showthread.php?t=205449[/COLOR]]("http://ubuntuforums.org/showthread.php?t=205449")

This is the guide I looked through to find my solution, someone had posted my specific fix, mabye there is something there of use for you?

---

### Post by tyler24_11 on 2007-11-02
WOW. That was so damn easy thanks

 [SOLVED]

---

### Post by LinuxD on 2007-11-02
Glad to hear it worked out for you!

Enjoy Ubuntu, I know I am!

---

