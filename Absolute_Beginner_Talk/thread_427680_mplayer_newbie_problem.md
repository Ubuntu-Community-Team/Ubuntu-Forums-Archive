---
title: "mplayer newbie problem"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by WanderingKnight on 2007-04-29
OK, I posted in the Multimedia forum but got no answer. Here's the original thread.

I'm using Ubuntu Feisty 7.04

I get this error when trying to play a simple xvid encoded .avi file with mplayer:

Quote:
Error opening/initializing the selected video_out (-vo) device
Now, I've tried a couple of -vo via command line, but got only sound (sometimes corrupted) and no video.

When using gxine, the player doesn't show a thing and fast-forwards the file till the end.

What should I do?

---

### Post by taurus on 2007-04-29
Fire up mplayer and then go into Preferences and change the video to whatever it is right now to **xv**.  Save it and exit.  

Then, run mplayer again and it should play your movie now.

---

### Post by WanderingKnight on 2007-04-29
Oh, it worked. Thanks.

---

