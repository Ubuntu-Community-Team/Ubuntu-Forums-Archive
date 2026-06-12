---
title: "Subtitles don't work on backports version of mPlayer!"
date: 2008-04-01
forum: Absolute Beginner Talk
---

### Post by Fixman on 2008-04-01
I use DeVeDe for recording movies, but due to an [Ugly bug]("https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314") in mPlayer, feisty, and gutsy, I had to upgrade mPlayer and mencoder to the unsupported version on gutsy-backports.

The audio now works perfectly, but subtitles don't show. Is there any solution/suggestion/something?

---

### Post by shirilover on 2008-04-01
Unless the subtitiles are actually part of the video stream, you will need to activate them.
In MPlayer this is done by using the 'j' key to cycle through available subtitle streams.
In a DVD, subtitles are bitmaps which are overlayed onto the video stream and must still be selected to show.

You might aslo want to fix your link by:
1. removing the space, or
2. using [Ugly bug](https://bugs.launchpad.net/ubuntu/+source/mplayer/+bug/141314)

---

