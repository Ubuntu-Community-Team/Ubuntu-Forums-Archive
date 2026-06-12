---
title: "Phosphor RSS Screensaver"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Siberia on 2007-04-16
I have searched the forums and other websites for this but I have a feeling I must've missed it as I've seen it working before but I've basically been tring to find a way to implement a RSS feed into the phosphor screensaver, so I can leave it running and rss feeds will display. I'm guessing/hoping it's relatively simple and I've just missed something.

Thanks to anyone for a solution.

---

### Post by earobinson on 2007-04-16
the matrix screensaver lets you run any program for its input, you could find a program that spat out rss feeds then that would do it for you.

---

### Post by Siberia on 2007-04-17
Are you meaning the GLMatrix screensaver? If so is there a way I can configure it to display the RSS from a program (any rss aggregator I'm assuming unless I got the wrong end of the stick)

---

### Post by earobinson on 2007-04-17
oops its called phospor sorry :(

---

### Post by Siberia on 2007-04-17
Ha ha no worries :) Although in 6.06 can you edit the options as I'm guessing there will be a terminal command as I can't see an option button. I still also don't actually have the Phosphor screensaver in 6.06 unless I'm blind. :confused: 

Thanks

---

### Post by earobinson on 2007-04-18
you need to install xscreensaver-data-extra if you want the screensaver , and Im not sure how to change the settings, Ill look into that.

---

### Post by x64Jimbo on 2007-04-19
Does anyone know where to set the RSS feed for the RSS screensavers in Ubuntu? They all seem to be pulling from this RSS feed: [http://ubuntuforums.org/external.php?forumids=122](http://ubuntuforums.org/external.php?forumids=122)
There must be a central config file...

---

### Post by a fenderson on 2007-04-26
edit the .xscreensaver file in your home directory

```
textURL:        http://fridge.ubuntu.com/node/feed

```

---

### Post by x64Jimbo on 2007-04-26
There's nothing in that file right now. Is this normal?

---

### Post by earobinson on 2007-04-27
no. I know that it used to be the .xscreensaver file but im not sure since I started using Feisty where the file is.

---

