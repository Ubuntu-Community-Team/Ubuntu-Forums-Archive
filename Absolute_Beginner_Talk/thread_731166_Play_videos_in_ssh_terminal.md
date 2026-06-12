---
title: "Play videos in ssh terminal"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by Hospadar on 2008-03-21
Hi!

This request for help is of no real importance, but I'd really love to get it working.  The end goal of this project is to get a creepy little ascii video to play when I do a text login into the machine.  I have no trouble playing videos in ascii (I'm using some command like "mplayer -vo aa mymovie.avi" or "mplayer -vo caca mymovie.avi") and I get a fablously creepy ascii video.  If I'm actually sitting at the machine, this video plays in the terminal, just the way I want it to.  The problem is, when I log into the machine with ssh (let's say with putty, from windows) the video plays just fine, but it opens up a seperate window to play it in (through xming) and I want the video to play in the original terminal like it does with a local text login.

Is there any way to disallow mplayer from opening up a window to play the video?  If I close xming, mplayer just complains there is no X window and plays nothing, even though it will play it in the terminal just fine on a local login.

Thanks for the help

---

