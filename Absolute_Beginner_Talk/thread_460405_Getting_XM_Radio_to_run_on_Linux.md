---
title: "Getting XM Radio to run on Linux"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by jonward0690 on 2007-05-31
I was wondering if there was anyway to get XM radio to work on linux.

---

### Post by Cypher on 2007-05-31
You're going to have to provide more information than that..

---

### Post by jonward0690 on 2007-05-31
If you go to xm radio online and launch the music player it never starts playing and the reason is there site says you eather have to have windows or a mac.

---

### Post by Sparkster185 on 2007-05-31
What plugin does it use in the browser to play?  You might have to install Flash/Quicktime/etc. Or it's possible that they use their own custom plugin and it's not available for Linux.

---

### Post by jonward0690 on 2007-05-31
It says you need windows medial player 10 and flash 7

---

### Post by Cypher on 2007-05-31
Not being a XM Subscriber, I'm pretty sure it won't allow me to launch the player. Is it Flash based?

---

### Post by jonward0690 on 2007-05-31
Yes but i already have flash installed

---

### Post by nutz on 2007-05-31
> **jonward0690 said:**
> I was wondering if there was anyway to get XM radio to work on linux.

Install the GStreamer plugins and it will work...

This fixed mine! I use XM online radio all the time.

---

### Post by jonward0690 on 2007-05-31
Well i went into automatix and downloaded common swiftfox plugens because I use swiftfox and know it works.

---

### Post by nutz on 2007-05-31
> **jonward0690 said:**
> Well i went into automatix and downloaded common swiftfox plugens because I use swiftfox and know it works.

I don't know why the GStreamer plugins made it work. Perhaps because of the codec used in their streams. But this did fix it and it now works perfectly...

The page is flash based but it launches your media player in the background to handle the audio stream...

---

### Post by jonward0690 on 2007-05-31
Yea I am glad to just have it working because I hated having to go into windows just to listen to xm radio.

---

### Post by nutz on 2007-05-31
> **jonward0690 said:**
> Yea I am glad to just have it working because I hated having to go into windows just to listen to xm radio.

If you like internet radio you should check out this app...

[http://www.nongnu.org/streamtuner/](http://www.nongnu.org/streamtuner/)

A must have!

---

### Post by nutz on 2007-05-31
Actually I was wrong; it isn't the GStreamer plugins that make it work. It is these two packages...

For future reference to anyone having issues with their xmradio online just install these two packages and you will be straight.

---

### Post by fromgi on 2007-06-02
If I try to install these two applications from the Add/Remove menu, I get this:

[I]Cannot install 'libxine-extracodecs"

This application conflicts with other installed software. To install 'libxine-extracodecs' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
[/I]
If I choose to continue, it will Add "Movie Play Totem (xine backend) and Remove "Movid Player"  Is this correct?

Thanks,
Larry

---

### Post by nutz on 2007-06-02
> **fromgi said:**
> If I try to install these two applications from the Add/Remove menu, I get this:

[I]Cannot install 'libxine-extracodecs"

This application conflicts with other installed software. To install 'libxine-extracodecs' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.
[/I]
If I choose to continue, it will Add "Movie Play Totem (xine backend) and Remove "Movid Player"  Is this correct?

Thanks,
Larry

Yep; sounds normal.

---

### Post by fromgi on 2007-06-02
Thank you!  It worked perfectly!

---

### Post by nutz on 2007-06-03
> **fromgi said:**
> Thank you!  It worked perfectly!

;)

---

### Post by mlehmann on 2007-06-05
I must has missed something.  What software was needed to be able to listen to XM Radio on Ubuntu.  I have a USB connected XM radio and haven't seen the software necessary to listen to it.  I have VMware Server and use my TimeTrax program, but it is having stability problems lately, and the timetrace website it completely unhelpful.  I seem to have no way to renew my annual subscription. PCRCommander and Xeus look like they are the right software, but I cannot get them to install and run.

Help.  Please.

---

### Post by irish_flu on 2007-06-05
I can't be too helpful with your exact problem mlehmann; I'm only posting to let you know that the above posters in this thread are talking about using the "XM Radio Online" service that comes with your account and can be played through a web browser (using your computer's media player), leaving the "hardware" radio out of the loop entirely.

---

### Post by DougieFresh4U on 2007-06-05
I'm not sure if this helps, but I listen AOL-XM RADIO using IE6 on my Ubuntu Gutsy machine :D
Also, as it was suggested in this thread, try "streamtuner" as it has many, many stations and it uses "XMMS" player and both streamtuner and xmms are in the Add/Remove

---

### Post by jonward0690 on 2007-06-05
Well I installed common swiftfox plugens because I use swiftfox and now it all works.

---

### Post by nutz on 2007-06-05
;)

---

### Post by liquoredolce on 2007-07-17
Xine Extra Plugins and Movie Player Totem (or whatever it's called) aren't in my synaptic, where can I get them???

---

### Post by Mogul345 on 2007-11-03
Thanks, installing Totem-Xine got it working! I didn't need the extra codecs either.

---

### Post by Sabot on 2008-02-12
The best way to get xmradio.com to work is to install two packages in Synaptic.

Totem-xine
libxine1-plugins

It works with no issues.

---

