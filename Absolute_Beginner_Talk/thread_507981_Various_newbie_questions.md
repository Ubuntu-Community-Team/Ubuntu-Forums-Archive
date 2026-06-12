---
title: "Various newbie questions"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by andy675 on 2007-07-23
Hi....I am new to Ubuntu 7.04 in the last 3 weeks. I love the concept. I downloaded Ubuntu via Wubi and now have a dual boot with my Windows XP Home. At this stage, I have successfully set up my new email server(Evolution) and have Firefox installed with my preferred add ons. I would consider myself intermediate level with Windows, but, I am certainly a novice with Linux. I have set myself to complete a new Linux download/accomplishment once per week, and I am seeking advice on the following-
   1. When my web page loads in Firefox and my page in Evolution, the page is about half an inch too big for the screen. I can unmaximise the screen, but the page is still too big. Could someone please direct me where I can adjust the Page size-on basis of using the full screen. I cannot see it in Firefox preferences and/or the Ubuntu menus.
  2. I went to play some CD data videos I had recorded via Windows and the Totem player comes up alright, but I just get a full  colour screen with no movie showing. Some of the movies are AVI and some are mpeg. I installed the necessary codecs when it prompted, but still no success. It was strange that when I minimised the Totem player, and then maximised again, the movie would show correctly for approx. 1 second, then go to the full colour screen again.

Any advice, in beginner Linux terminology would be greatly appreciated.:(

---

### Post by pizzutz on 2007-07-23
hmm, it sounds like those could both be a symptom of the same problem, i.e. incorrect or improperly configured video card drivers.

Could you post the specs or type of video card and monitor you are using,  and also the contents of your /etc/X11/xorg.conf  file?  This may help.

---

### Post by ryanVickers on 2007-07-23
Are you sure you've got *all* the plugins?  there should be about 5 gstreamer, 1 or 2 xine, and the "ubuntu extras" for EVERYthing.  Look them up in Add/remove.  Also, yes, check the video drivers and make sure your monitor settings are correct - try resizing/moving the picture with the buttons on the actual device.  Even if it worked in windows, it might need to be changed once for ubuntu.

---

### Post by andy675 on 2007-07-24
thanks guys

---

### Post by abn91c on 2007-07-27
on forefox and konkeror go to the toolbar>view>set encoding then select automatic detection>semi automatic then restart the browser and try that website again

---

### Post by KyleBrandt on 2007-07-27
You might try VLC (Video Lan Client) for playing your video, that comes with lots of codecs bundled into the program itself.

---

