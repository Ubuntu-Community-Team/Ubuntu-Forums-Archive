---
title: "Ipod Extraction"
date: 2007-11-03
forum: Absolute Beginner Talk
---

### Post by NonCents on 2007-11-03
Allo all,
The deal is that I had become fed up with Microsoft and was looking at the alternatives when my computer crashed. In a fit of rage I formated and put on Unbuntu. So far I LOVE IT!!! But I lost all my media (About 50 gigs)... I have a backup, but its on my iPod... what program do I use to get it off. I'm a Linux newbie and I'm having trouble finding the right program.

THANKS

---

### Post by Nikitas350 on 2007-11-03
First of all what ipod do you have, and secondly do you have only music or other files in the ipod ?

---

### Post by NonCents on 2007-11-03
Its a 5th gen, I Also Backup some .doc and pics. along with the album covers(not that important). The most important things are the .doc and music files.

---

### Post by ThrobbingBrain66 on 2007-11-03
gtkpod will transfer the music from your ipod to your computer...actually, you should be able to transfer any file from your iPod with gtkpod.

```
sudo apt-get install gtkpod
```

---

### Post by NonCents on 2007-11-03
WOW THANKS!!! That worked a lot faster than I could have imagined. The only problem, is for some reason it doesn't like m4a files. I'd love to convert them too a different format, but i can't get them off the iPod... Any suggestions.

---

### Post by ThrobbingBrain66 on 2007-11-05
If you're using Gutsy, you may have to wait just a little bit for the .m4a files.  There is a version of gtkpod in the repositories called gtkpod-aac.  It allows transfer of .m4a, .aac, etc files to the iPod.  The bad news is that it requires a newer version of the mp4v2 library than what is in Gutsy, so it doesn't currently work.  The good news is that a fixed version is being tested as we speak and should be uploaded into Gutsy within the next week or so.

Here is a link to the bug report if you're interested and/or want to help test the package:
[https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178)

---

### Post by fululian on 2007-11-05
thanks for the insight, i also have the problem with this "not-being-able-to-transfer-mp4". are they going to update gtkpod 0.99.10 in order to work with the old lib mp4v2, or put a new version of mp4v2 into the repositories, or both? who is working on this anyway, the people of gtkpod or those over at launchpad? i would like to test the solution, how may i do this? and last question - will we get this update through ubuntu-updates? thanks a lot...

---

### Post by Darko-TheRaven on 2007-11-05
bah i hate m4a files they too big mp3 FTW!!!!!

oh... and also check out the audio tag tool you might find it useful later

---

### Post by ThrobbingBrain66 on 2007-11-06
> **fululian said:**
> thanks for the insight, i also have the problem with this "not-being-able-to-transfer-mp4". are they going to update gtkpod 0.99.10 in order to work with the old lib mp4v2, or put a new version of mp4v2 into the repositories, or both? who is working on this anyway, the people of gtkpod or those over at launchpad? i would like to test the solution, how may i do this? and last question - will we get this update through ubuntu-updates? thanks a lot...

From what I can gather from the bug report, there is one specific function used in gtkpod that the older version of mp4v2 can't handle.  The generally accepted idea was to remove this function from gtkpod in Gutsy so that we may use the mp4v2 in the repos.  It seems that just upgrading to a newer version of mp4v2 would be a large scale project and this point, so they are saving it for 8.04.

John Dong (jdong here in the forums) is the man spearheading this, so you have him to thank.

Here is a link to the post where jdong attached a Gutsy .deb for the patched version of gtkpod.  I believe the patched package has already been uploaded so I don't know that they need anymore feedback.  The official package should show up in the updates within the next week.
[https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178/comments/11](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/135178/comments/11)

---

### Post by fululian on 2007-11-06
ok, this works. i am now able to move videos to the ipod. installing the package prompts one with the screen that there is an older version available in the repositories (who would have thought that), and gtkpod now does an SAH1-count for a couple of times, but moves movies and video files correctly.

the one thing you are not able to do is to tag your video-files inside gtkpod...i think this is the feature they removed. thanks to all of you. :popcorn:

---

### Post by ThrobbingBrain66 on 2007-11-17
For any of you still keeping tabs on this, this bug has been combined with another at the bug report here:
[https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/163283](https://bugs.launchpad.net/ubuntu/+source/gtkpod-aac/+bug/163283)

A new .deb has also been built for testing.

---

### Post by fululian on 2007-11-17
thanks for the hint...yes at least i am stil keeping tabs on this.

bye

---

