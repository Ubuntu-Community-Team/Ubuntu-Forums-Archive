---
title: "[SOLVED] kino question"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by anewguy on 2008-04-21
I have several small video clips I need to merge.  I used kino for a test and it seems to do what I want, except for one small thing.  Is there a way to cause some kind of effect (fading or whatever) between clips so when you watch the combined video you still know there were breaks for new clips?

Thanks!:)

---

### Post by squaregoldfish on 2008-04-21
The answer to your question is "yes". I did this a while ago, but I'm afraid the details are a little sketchy in my memory. I'll do the best I can, but you can always experiment :)


Import your two clips as normal.
Click the FX tab on the right.
You can then select Audio Transition and Video Transition to determine how the two movies are joined. 
I think I used the Dissolve video transition with the Frames Following option, but I can't be sure. Play around and see what you like.

Steve.

---

### Post by squaregoldfish on 2008-04-21
I forgot to mention - once you're happy with the effect, don't forget to click the Render button in the bottom right corner to add the transition to the main video!

---

### Post by anewguy on 2008-04-21
Thanks!!  I'll play around with it tonight!  :)

---

### Post by anewguy on 2008-04-22
Well, I've got one *tiny* problem - for some reason kino isn't importing my videos.  It SAYS it is importing them, but it never finishes.  This was never fast before, but I could wait and see it complete.  I am importing .avi files (I think they are actually xvid or something like that).  Any ideas?

:)

---

### Post by indiecast on 2008-04-22
try getting them out of that xvid format first.

it sounds to me like kino doesnt like that kind of file

---

### Post by squaregoldfish on 2008-04-22
Kino calls ffmpeg and/or mencoder to convert the videos, so you can always take a look at top/ps to see if either of those are running.

Alternatively, run kino from a console and see if anything interesting is dumped to stdout when it's running.

---

### Post by anewguy on 2008-04-27
I forgot about ffmpeg - I did have that installed before.  So, after the 8.04 upgrade, I went in to synaptics and installed the ffmpeg stuff and now Kino works as I need.  Strange that ffmpeg is not included in the dependencies for Kino.

Thanks!

---

### Post by squaregoldfish on 2008-04-28
Yes, it is strange that the dependencies are missing. Might be worth filing a bug report.

---

### Post by encompass on 2008-04-28
You should also check if it\s in the recommended to install files in the package.  If it is not there then deffinetly needs to be mentioned.  Sadly, kino is a nice program but doesn\t do very good error checking.
Thanks for the info.

---

