---
title: "Car MP3-CDR player can't read discs burnt using Gutsy (used to workin Feisty)"
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by ubnewbie2 on 2007-10-28
I have been burning CDRs with mp3 files for playing in my car, quite happily for a while now under  feisty 7.04. After my upgrade to gutsy 7.10 however, the car player just sits trying to read the disc that ubuntu creates, forever, and never finds any files to play.

My method of making these discs has been to put a blank CDR in the computer and wait for gnome to pop up and ask me what I want to do.  I select "Data CD" then use the Nautilus window that appears to copy the files I want to the CDR, then press burn.  Simple, and it has worked.

So, I am still doing the same things as before, but now, under my new gutsy install.  It burns the CDR successfully, and gutsy can read the resulting disc, no problems.  Only the car player can't read them.

I am suspecting that some default setting somewhere has changed with the new version. Is it leaving out something the car player needs, like joliet or rockridge extensions for the filesystem? ( I don't know a whole lot about this,)

I find that I can make a disc using K3B that will work, but I would like to discover how to make the much more simple nautilus system burn them successfully for use in the car too.

---

### Post by tgalati4 on 2007-10-28
It could be your character set.  Perhaps Gnome uses UTF-8 by default and your car CD can't decode the CD text properly.

I think you can change character sets in K3b in preferences.  At least you could burn the disk both ways to isolate the problem.  I'm not sure how to change the charset in Gnome but other folks will chime in.

---

### Post by ubnewbie2 on 2007-10-28
> **tgalati4 said:**
> It could be your character set.  Perhaps Gnome uses UTF-8 by default and your car CD can't decode the CD text properly.

I think you can change character sets in K3b in preferences.  At least you could burn the disk both ways to isolate the problem.  I'm not sure how to change the charset in Gnome but other folks will chime in.

Hmmm, but would gnome have changed from/to UTF-8 between Feisty and Gutsy? ... and when you say "CD text", I want to be sure you aren't thinking of an audio CD.  This is a straightforward DATA CD.  The car reads mp3 files from a normal data CD.

---

### Post by kngcrntrd on 2007-10-30
I am having the same problem.  I was once able to drag and drop whole folders of mp3s onto the cd icon and burn it and the car would read no problem.  Anyone know what's going on?

---

### Post by ubnewbie2 on 2007-10-31
I'm pretty sure they've left out the Joliet extensions by default.  This means the CD is not Windows compatible and I think most car players assume a Windows CD.

It's all assumptions though, so I am willing to be told differently.

Anyway, as I said earlier, you can use another burning program - I like K3B, and thi9ngs will be fine.  K3B will add Joliet by default btw:

---

