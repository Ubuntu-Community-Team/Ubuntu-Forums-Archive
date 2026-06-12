---
title: "Some questions (Streaming, Video on Compiz and Xen)"
date: 2007-08-10
forum: Absolute Beginner Talk
---

### Post by jcrnan on 2007-08-10
Okey, so I have some questions.

1. Is there a way for straming wmv and wma? I have vlc, but I have problems streaming stuff on places like channelchooser.com And also, I'm not entirley sure if it actually tries to use VLC to stream in the first place.

Also, anyone know why I'm not able to stream from [http://atvs.vg.no/player/index.php?](http://atvs.vg.no/player/index.php?)

Its a norwegian site yes, but you shouldn't need to be able to read the language to understand the problem methinks. The help section mentions needing windows media player to get it working. It also says that theyre working on better linux support but to use the Mplayer plugin to try and get it working.

2. I have problems getting video (and games) working while using compiz. Its not very practical having to do a metacity --replace each time I want to do that. Anyone know how to fix this? I just get a black screen instead of video, though I can somtimes get a glimpse of the video if I move the window a bit. I do get sound fine though. It would be nice to know how to run ghrapical games as well, but thats not as important.

3. Anyone have any guide for me for how I can set Install my XP cd trough Xen?

4. How do I set down the grahpical display thing for better performance in compiz? I remember I used to do it before when I used edgy and beryl. I think I changed something in xconf.org. Is this still done the same way? Was it 12 or 16 I should downgrade it to?

5. Also, I'm gonna try and help a friend install Ubuntu, but he has a Intel core Duo and 4GB ram. Does that mean I have to use a 64bit Ubuntu install to get the use of all the Ram or will a 32bit version work fine? Is the 64 bit version more problematic then the 32bit version?

Thanks for all your help :) I really appreciate this community.

---

### Post by qamelian on 2007-08-10
> **jcrnan said:**
> 2. I have problems getting video (and games) working while using compiz. Its not very practical having to do a metacity --replace each time I want to do that. Anyone know how to fix this? I just get a black screen instead of video, though I can somtimes get a glimpse of the video if I move the window a bit. I do get sound fine though. It would be nice to know how to run ghrapical games as well, but thats not as important.

For video playback, you may need to change video output to use just xv. How you do this is going to vary depending on which player you use. 

For graphical games,  I'm not sure as I don't play many games and compiz doesn't interfer with the ones I play.

> 3. Anyone have any guide for me for how I can set Install my XP cd trough Xen?Unless something has changed, you can't install XP in Xen. Xen requires a specially compiled kernel to operate. Since Microsoft doesn't give a way to compile our own Windows kernel, there is no way to create a Xen-enabled kernel for XP.

> 5. Also, I'm gonna try and help a friend install Ubuntu, but he has a Intel core Duo and 4GB ram. Does that mean I have to use a 64bit Ubuntu install to get the use of all the Ram or will a 32bit version work fine? Is the 64 bit version more problematic then the 32bit version?You can install either version, but somethings don't have a 64-bit version yet and may require a bit of fiddling around to get 32-bit components to work in the 64-bit OS. There are plenty of how-tos on the forums to walk you through any tricky bits you might encounter if you decide to go the 64-bit route.
Thanks for all your help :) I really appreciate this community.[/quote]

---

### Post by ThrobbingBrain66 on 2007-08-10
1. To stream wma and wmv, you should install mplayer and mozilla-mplayer.  Then, remove the totem-mozilla plugin package with Synaptic as it takes precidence over mplayer.

I just tested your site and the streams work for me using mplayer

---

### Post by Steveway on 2007-08-10
You can either use the 64bit version or you have to use a bigmem kernel.
Bigmem kernels allow you to use more than 3GB on a 32bit Linux, dunno if there are precompiled ones for Ubuntu.

---

