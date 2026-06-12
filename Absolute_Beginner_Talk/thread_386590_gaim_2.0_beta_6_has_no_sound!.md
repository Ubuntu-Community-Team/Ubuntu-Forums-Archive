---
title: "gaim 2.0 beta 6 has no sound!"
date: 2007-03-17
forum: Absolute Beginner Talk
---

### Post by searayman on 2007-03-17
i am using gaim 2.0 beta 6 but it does not have any sound in ubuntu, any ideas?

---

### Post by dabertman on 2007-03-17
Im having the same problem. installed ubuntu a week ago. today no sound in gaim.

---

### Post by fakie_flip on 2007-03-17
In gaim, click on Tools>Preferences and then Sounds tab in the window that pops up. Then put "aplay %s" without quotes where it says "sound command:"

---

### Post by RobertH on 2007-03-31
Have you checked that it's not muted? I had this problem for a couple of hours then I noticed that it was muted. I just unchecked "Mute Sounds" in the right click options. And everything was just dandy :)

---

### Post by FrancoNero on 2007-04-02
what's going on with gaim anyway? as usual, the people on their website haven't said anything about the progress on the way to final yet.
will the final make it into feisty final?

---

### Post by fakie_flip on 2007-04-09
> **FrancoNero said:**
> what's going on with gaim anyway? as usual, the people on their website haven't said anything about the progress on the way to final yet.
will the final make it into feisty final?

You could email the developers or add them to your buddy list to ask them.

---

### Post by Obor on 2007-04-09
> **FrancoNero said:**
> what's going on with gaim anyway? as usual, the people on their website haven't said anything about the progress on the way to final yet.
will the final make it into feisty final?

Its a long story... Their new website is [http://pidgin.im/](http://pidgin.im/)
Thread about it in the [cafe]("http://ubuntuforums.org/showthread.php?t=403857")

---

### Post by ZTiger on 2007-04-20
> **fakie_flip said:**
> In gaim, click on Tools>Preferences and then Sounds tab in the window that pops up. Then put "aplay %s" without quotes where it says "sound command:"

You sir/mam roxxor. That did the trick for me.

---

### Post by Webspot on 2007-05-21
> **RobertH said:**
> Have you checked that it's not muted? I had this problem for a couple of hours then I noticed that it was muted. I just unchecked "Mute Sounds" in the right click options. And everything was just dandy :)

wow! i've been trying to work out this problem for ages. and then i go and find this solution.

i don't even remembering setting that. i wonder what happened

thanks

---

### Post by fakie_flip on 2007-05-21
> **FrancoNero said:**
> what's going on with gaim anyway? as usual, the people on their website haven't said anything about the progress on the way to final yet.
will the final make it into feisty final?

A final release has come out. It is no longer called Gaim. It is Pidgin IM. I had fun compiling it.

---

### Post by zero-9376 on 2007-08-02
for me it was that the pcm volume was down to low, for some reason all other sounds were still loud enough just not gaims, same way the fonts in gaim are WAY smaller than any other application

---

