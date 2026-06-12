---
title: "Mac Mini G4: newbye doubt on graphics..."
date: 2010-08-17
forum: Apple Hardware Users
---

### Post by Yapok on 2010-08-17
Hi everybody,I am a Linux newbye, and actually non-mac user, so I'd like to apoligize in advance for my likely erroneus technical vocabulary, along with my poor English...

I have sucessfully installed Ubuntu Lucid Lynx (10.4, right?) onto an old Mac Mini g4 with 512mb ram to use it as a "multimedia machine", mainly for DVD playback. Everything was straight-forward even for a first-timer, and after a bit of "tweaking" the system was running fairly well. Video playback instead is giving me big troubles: 

at first all kind of videos would be pseudo-pixelated, awful quality of the image although "smooth". Somebody on this forum solved the problem by switching one of the "output video settings" to "x11". I tried that, picture quality improved, but now videos are unwatchable due to stuttering.

Now, I have no clue of how to solve the problem... It seems like it is hardware-related, but it looks strange to me that the 9200 is not even able to play DVDs and similar quality stuff... I have heard somebody else complaining about Lucid Lynx because it has no hardware-acceleration support for this graphic chip, is that the problem?

So, finally: is there a way to make the Mini G4 play decently under 10.4, or maybe downgrading to 9.4-10 or passing to another distro would solve the problem?

Thanks to everybody...

---

### Post by linuxopjemac on 2010-08-17
Maybe this helps:
[http://ubuntuforums.org/showthread.php?t=1385579&highlight=video](http://ubuntuforums.org/showthread.php?t=1385579&highlight=video)

---

### Post by Yapok on 2010-08-18
I had already found that thread by browsing the forum, but I really  can't put my hand on a  libstdc++5 package: I do not know if it is only a  problem related to my browser/machine, but the link in the post and all  the other I found on the web for the  libstdc++5 package appear to be  broken... I tried to search it from synaptics (although I am not too  sure I did it right) but I found only the version 6 of the package....  Any advice?

Now, before figuring out how to install  libstdc++5, I'd like to say  that my CPU usage while "playing" (stuttering) video is always 100% or  around there, in case this might help to understand my problem...

I'll let you know if I am able to install  libstdc++5....

Thx

---

### Post by Yapok on 2010-08-19
OK, problem solved for me... I guessed something was wrong with Lucid and understood it would be easier to switch to a reliable "release" (it's called "release", right?) rather then solve the problem with the one installed. Thus I put on Karmic Koala and after having downloaded few codecs and installed xine, now everything works perfectly.

It is just a shame I was not able to solve the problem and use the newest release of Ubuntu, although for my purpose Karmic is absolutely fine...

Thanks to everybody anyway... ):P

---

