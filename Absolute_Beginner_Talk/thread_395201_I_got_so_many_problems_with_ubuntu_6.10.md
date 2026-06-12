---
title: "I got so many problems with ubuntu 6.10"
date: 2007-03-27
forum: Absolute Beginner Talk
---

### Post by rsheth3 on 2007-03-27
my mouse click on stuff i don`t even click on.

i can`t watch videos on nba.com
 i
i can`t scroll down using my touch pad

is their a program on ubuntu to download music for my ipod

---

### Post by lamalex on 2007-03-27
Sorry your post went unanswered for so long. Can you give more detail? What kind of mouse do you have, does it work at all? Can it move but not click? What type of video is nba.com trying to play. you just need some sort of codec/plugin. For your ipod, do you mean transferring music to and from or downloading music from the internet?

---

### Post by jem7v on 2007-03-27
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) for help getting the video to play, probably.

---

### Post by kvonb on 2007-03-27
For the ipod, use Amarok.

Simply click on add/remove from your main menu and type "amarok" (without the quotes) in the search bar.

I've been using it for a while now, it is very nice and does everything you need.  I found that some mp3s wouldn't play on the ipod, it was because the quality was too high or something, if you have this problem, simply install "audacity" (same method as above), open the offending mp3(s) then export as mp3.  That re-writes it and it should now play.

When you first run "export as mp3" it will ask you for the location of libmp3lame.so, in the box that pops up, just change  "libmp3lame.so" to "libmp3lame.so.0" and press enter.

To automatically launch Amarok each time you plug in your ipod, look on the menu under system->preferences and select "removable drives and media", then select the "multimedia" tab and in the "Portable Music Players" type amarok.

---

