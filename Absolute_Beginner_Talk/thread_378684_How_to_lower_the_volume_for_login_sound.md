---
title: "How to lower the volume for login sound"
date: 2007-03-07
forum: Absolute Beginner Talk
---

### Post by samadams on 2007-03-07
When I log in to Ubuntu 6.06 the welcome sound is VERY LOUD!  This is NOT because my volume on my speaker is turned up high.  In fact - it's near the bottom.  After the login, if I play any music or sounds, I have to turn the speaker volume way UP to hear it!  It's like there is an internal volume setting in Ubuntu (like windows) that is set to MAX upon login and then it resets itself to whatever the user left it at last session.  How do I lower the log in volume?

*note - I don't mind the sound being played - I almost prefer it, that way I know if I'm in the next room, that the login was complete.

---

### Post by taurus on 2007-03-07
See if you can lower the volumes from a terminal with this command.

```
alsamixer
```

---

### Post by samadams on 2007-03-07
Thanks, I tried that but it didn't solve the problem.  I did however manage to turn on my spatial depth though.  Thanks.

The only pertinent volume controls here are Master and PCM (what's this?)
From what I can gather, the Master is the same as the one on the tool bar in the upper left hand corner of the screen.  When using Rythymbox, I played with adjusting the Master and PCM up and down with my speakers turned up and Rythymbox's volume turned up.  They each functioned exactly the same.

I then tried going into preferences > sounds and doing the same - same results.  But now I need to go turn off my spatial depth because the login sound is horrible.  Oh well, so much for surround emulation.

any other guesses.

---

