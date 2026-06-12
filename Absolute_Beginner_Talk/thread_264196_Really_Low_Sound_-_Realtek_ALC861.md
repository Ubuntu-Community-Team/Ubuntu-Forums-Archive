---
title: "Really Low Sound - Realtek ALC861"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by 3rr0r on 2006-09-24
Well when I try to play music, I put it at max volume in my music player (XMSS) and it is really low.  So, first I checked the system sound (the little speaker icon on my task bar near the time display).  That was also pushed to the max.

After searching the forums some, I went into APPS>Sound and Video>Volume Control and saw that it had the HDA Intel device listed.  I switched it to my realtek and messed with the bars to maximize my sound.  What I ended up having was slightly louder sound, but nothing really that great at all.  I had to put the VOLUME column to max, and LINE IN column to about a third of the way up.  Any more on the LINE IN and the speakers begin to sound all crackled with static.

Then I went into System>Preferences>Sound.  Under default sound card, it lists HDA Intel, but it doesn't give me the option to switch to my Realtek.  Any ideas on how to improve my sound output?

---

### Post by yacine on 2006-10-02
Try command line 
[PHP]alsamixer[/PHP]
Use the keyboard arrows to navigate through the items highlighted in blue on the bottom of the terminal. Use the up/down arrow to increase/lower the volume, and escape key to exit.

Yacine

---

### Post by Yink on 2007-01-05
ah thank you for this tip sorted the sound out on my dell laptop which has the hda intel soundcard. I just maxed out the pcm and master volume.

---

### Post by dangerpl on 2007-04-19
I have the same sound card and the same problem. It worked fine in Edgy but for some reason is really low in Feisty...

---

### Post by fedorik on 2007-04-20
Try this, I had same issues with realtek, and this fixed it:

```
kill $(lsof -t /dev/dsp* /dev/audio* /dev/mixer* /dev/snd/*)
sudo modprobe -r snd-hda-intel && sudo modprobe snd-hda-intel model=auto
```

---

### Post by petroskhan on 2007-04-20
I had the same problem on my Toshiba A105-S4014, and your solution worked like a charm.  Sound is perfect now.  Just one question.  Is this a permanent thing, or something you have to re-type, or what?  Sorry if that question is a dumb one, but I just upgraded to Feisty, and I am kinda new to Ubuntu in general.

---

### Post by petroskhan on 2007-04-20
Ok, figured out one part myself...when I restart the computer, the sound is back to being really low...how do I set it so this will command will run each time I restart?  I don't really want to have to do this all the time, since I play a lot of music and video on my machine.

---

### Post by fedorik on 2007-04-21
I found a post how to fix sound on ALC861 and Intel HDA sound drivers on startup here:
[[COLOR="DarkOrange"]http://ubuntuforums.org/showthread.php?t=416207&highlight=sound[/COLOR]]("http://ubuntuforums.org/showthread.php?t=416207&highlight=sound")

---

