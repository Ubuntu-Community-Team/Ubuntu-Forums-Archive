---
title: "[SOLVED] no sound after update"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by Bargeek on 2008-03-04
Hello again.  Yesterday, after much anticipation, I installed Fiesty from the disk included with The Official Ubuntu Book.  Everything went pretty smashingly, with the exception of not being able to mount my external hard drive.  I am currently futzing about with that.

I am loving Ubuntu, and have had a blast just getting used to the feel of it.  I noticed earlier today that my desktop was letting me know I could update to Gutsy, which I did, with what I thought was little or no problem.  After the update, while I was browsing around on the web, I noticed I had no sound.  I checked the forums, and followed the Comprehensive Sound problems post, but I am still not able to get the system to make a single sound.

I am running a Dell Inspiron 9100 with 1.2 G of ram.  The installed soundcard is the intel AC97.  I have tried rebooting the system multiple times, and made sure that all installed apps were updated.  Is there something I am missing?  

And believe it or not, I did check to make sure nothing was muted, no headphones plugged in, and the like.  Everything is exactly as it was when Fiesty was loaded. 

Any help would be greatly appreciated.

---

### Post by Sid6 on 2008-03-04
Did you check the drivers for the sound card? You may need to roll them back one. I have need to do that a few times. I hope this helps.

---

### Post by Bargeek on 2008-03-04
Sid, I hadn't thought about rolling back the sound card drivers.  Of course, I have no earthly idea how to do that in Ubuntu yet.  But, I will dig around and see if I can figure it out.  I appreciate the suggestion.  I would have NEVER thought of that.  Of course, I am blonde, and have trouble seeing what is on my monitor with all the whiteout and all.

Thanks for the suggestion.  I will take a shot at it and see if that works.

---

### Post by Bargeek on 2008-03-05
Wierdness.  I went into Applications > Add/remove and searched the sound & video catagory.  I installed Alsa mixer, and then ran it as an application.  I turned up the headphones slider, and VIOLA, I have sound.

I find it a little strange that it was the headphone levels that affected the output of my speaker volume, but I have sound, so I am happy.

---

