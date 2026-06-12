---
title: "totem won't start"
date: 2005-07-22
forum: Bug Reports / Support
---

### Post by sjmorgan on 2005-07-22
When I attempt to run totem I get an almost Microsoft level of quality error dialog saying "Totem could not startup. No reason."

With this output to the command line:

```
** (totem:23482): WARNING **: No GConf default video sink key and xvimagesink doesn't work
** Message: failed to render default video sink from gconf
```

---

### Post by mr_pouit on 2005-07-23
[QUOTE=sjmorgan]When I attempt to run totem I get an almost Microsoft level of quality error dialog saying "Totem could not startup. No reason."

With this output to the command line:

```
** (totem:23482): WARNING **: No GConf default video sink key and xvimagesink doesn't work
** Message: failed to render default video sink from gconf
```[/QUOTE]
 i have the same problem since the update. But it gives me a reason :lol:

> Totem could not startup
The video output is in use by another application. Please close other video applications, or select another video output in the Multimedia Systems Selector.
... and i don't understand, because the video output isn't in use ](*,)

---

### Post by rwabel on 2005-07-23
I can start totem, but all videos get played jerked!

anyone else have such a problem?

---

### Post by psoleko on 2005-07-23
[QUOTE=rwabel]I can start totem, but all videos get played jerked!

anyone else have such a problem?[/QUOTE]

I am having the same issue since upgrading. It's definitely Totem as Xine works just fine with any video. I am using Totem Xine, I will try Totem GS and see if that has any issues as well.

Just tried Totem GS, not as much jerky playback (still evident in some video) but definitely some sound sync issues.

---

### Post by rwabel on 2005-07-23
[QUOTE=psoleko]I am having the same issue since upgrading. It's definitely Totem as Xine works just fine with any video. I am using Totem Xine, I will try Totem GS and see if that has any issues as well.

Just tried Totem GS, not as much jerky playback (still evident in some video) but definitely some sound sync issues.[/QUOTE]
 I've always used Totem GS. I've tried out now Totem Xine, it does start up. But hell it takes a long while.
Mhh audio and video isn't sync

---

### Post by rwabel on 2005-07-24
how strange...I just did a restart and totem runs perfectly and the videos open very fast!

---

### Post by charlieg on 2005-07-24
Is that with totem-xine or totem-gstreamer?

---

### Post by rwabel on 2005-07-24
[QUOTE=charlieg]Is that with totem-xine or totem-gstreamer?[/QUOTE]
 with both of them, I've checked them both...no difference. Anyway, does someone see an advantage for one over the other?

---

### Post by psoleko on 2005-07-24
[QUOTE=rwabel]with both of them, I've checked them both...no difference. Anyway, does someone see an advantage for one over the other?[/QUOTE]
Gstreamer is a much newer multimedia plugin framework and does not play all media that well. Gstreamer is definitely the future of multimedia on Linux, Xine is the debian grandpa of players. Although it's a bit long in the tooth it tends to play most media, and windows media at that with the win32codecs, very well. Depending on which version of Totem you are using it uses a different backend to play the video.

---

### Post by rwabel on 2005-07-25
[QUOTE=psoleko]Gstreamer is a much newer multimedia plugin framework and does not play all media that well. Gstreamer is definitely the future of multimedia on Linux, Xine is the debian grandpa of players. Although it's a bit long in the tooth it tends to play most media, and windows media at that with the win32codecs, very well. Depending on which version of Totem you are using it uses a different backend to play the video.[/QUOTE]
 thanks for the info, I just can choose between xine and gstreamer for the backend in totem. So far I haven't seen differences...but I should compare in "bad encoded" movies once

---

### Post by sjmorgan on 2005-07-25
I should have mentioned it's totem-xine that I have the problem with. totem-gstreamer loads fine and plays stuff but isn't really an option because it has some nasty bugs like not being able to seek in large files and various crashers.

---

### Post by doclivingston on 2005-07-25
Gstreamer tends not to do so well with badly encoded files - basically it doesn't have all the hacks in place to deal with the horrible things some people do to their files, in an attempt to save space. Most of the issues I've come across are where it loses A/V sync.

---

### Post by rwabel on 2005-07-25
[QUOTE=sjmorgan]I should have mentioned it's totem-xine that I have the problem with. totem-gstreamer loads fine and plays stuff but isn't really an option because it has some nasty bugs like not being able to seek in large files and various crashers.[/QUOTE]
 you also have the newest version from backport?

---

### Post by sjmorgan on 2005-07-25
[QUOTE=rwabel]you also have the newest version from backport?[/QUOTE]Yeah. It's not a problem with totem-gstreamer itself, but rather GStreamer (at least the oldish version that comes with Hoary).

---

### Post by rwabel on 2005-07-25
[QUOTE=sjmorgan]Yeah. It's not a problem with totem-gstreamer itself, but rather GStreamer (at least the oldish version that comes with Hoary).[/QUOTE]
 I never had problems with it. You still have problems with totem-gtstreamer now?

---

### Post by sjmorgan on 2005-07-26
[QUOTE=rwabel]I never had problems with it. You still have problems with totem-gtstreamer now?[/QUOTE]Mmhm.

---

### Post by jdong on 2005-07-26
Are you using:

1.1.1 in stable

or 

1.1.3 in staging


Can everyone try both options to see if they all exhibit this problem?

---

### Post by rwabel on 2005-07-26
I used to have the 1.1.1 in the past and that one worked perfect, but 1.1.3 didn't work fine. After a reboot it worked quit fine. It's still not as fluid as gxine. with xine and gstreamer.

conclusion: totem 1.1.3 is a bit slower than 1.1.1, but it plays the videos

---

