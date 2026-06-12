---
title: "Volume will not go loud on laptop"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-04-23
Hi,

I am using a Toshiba Satellite with the new Ubuntu 7.04. When I attempt to play video or sound files the sound stays very soft. I checked the volume dial on my laptop, made sure that nothing was in the head phone jack, checked that the volume was set to loud on the volume control panel. The strange thing is that the volume works just fine on my windows partition and it also worked fine on the previous version of Ubuntu. Does anyone have any ideas as to what might be wrong?

---

### Post by Kobalt on 2007-04-23
Have you tried to change the device in the volume control panel under File > Change device ?
Are both General Volume and PCM set at their max ?
Is the volume of your video/audio player set at its max as well ?

---

### Post by viciouslime on 2007-04-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+bug/102818](https://bugs.launchpad.net/ubuntu/+bug/102818) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				> **noorez said:**
> Hi,

I am using a Toshiba Satellite with the new Ubuntu 7.04. When I attempt to play video or sound files the sound stays very soft. I checked the volume dial on my laptop, made sure that nothing was in the head phone jack, checked that the volume was set to loud on the volume control panel. The strange thing is that the volume works just fine on my windows partition and it also worked fine on the previous version of Ubuntu. Does anyone have any ideas as to what might be wrong?

I believe this is possibly related to the bug I filed for macbooks. Does changing the volume alter the sound in any way? On a macbook it adjust the treble/bass settings.

You might want to try opening a terminal and running alsamixer. Play with that and see if you can achieve the desired effect.

---

### Post by noorez on 2007-04-23
I tried using the alsamixer utility on the command line. For both devices the Master was at zero but I was unable to move it up. Is this a possible bug?

---

### Post by Kyngdom on 2008-03-04
*Bump*

I have the same style laptop, with a winxp partition, and the same exact problem. Very frustrated because no one seems to have an answer. :(

---

### Post by jcarlock on 2008-04-08
Honestly I had the same trouble, the above solution was what I needed...  The PCM mixer volume was only half way up.  I have the volume icon on one of my panels, you can right click it there and 'Open Volume Control'.  You can 'Add to Panel' the volume controls...

I know some people are not having this simple of an issue, sorry, but for those that are.  Also you may want to change your default mixer to OSS from ALSA if you have the option, then try seeing if you have enhance volume controls...

JC

---

### Post by SlappyPappy on 2008-04-08
Yeah, try double clicking the volume control in the bar at the top. That opens up the mixer and you can jack up the PCM volume. This helped me when watching DVDs. 

Just remember to turn it back down when you're done or your system sounds will be crazy loud.

---

