---
title: "Dosemu-freedos"
date: 2007-11-05
forum: Absolute Beginner Talk
---

### Post by jamillikan on 2007-11-05
I have spent the entire day trying to install dosemu-freedos for Gutsy to no avail.  I'm wondering if there is anyone here who knows how to do this or some workaround.

It seems this is currently not available or not working or something.  I worked fine in Feisty and Edgy, but so far NOT HERE.

Any thoughts?

---

### Post by Cochise on 2007-11-05
you could get dosbox 0.72 from getdeb.net instead. you could also install virtualbox and install freedos in that

---

### Post by jamillikan on 2007-11-05
Thank you.  I realize that; however, we've been using DOSEMU on Edgy and Feisty, so I assumed, perhaps speciously, that it would naturally be part of the upgrade which, of course, it is not at this point.  (They will probably say it's not something they support or some other tragic response.)

This "issue" needs to be addressed quickly as many businesses still rely on programs running in dosemu and dosemu-freedos.  I guess it's back to Feisty and/or Edgy (both of which work perfectly) until Gutsy gets with the program and resolves this issue.

I'm really ticked that I've wasted an entire day on this with no resolution.

---

### Post by emendelson on 2007-11-05
The current version of DOSEMU includes FreeDOS already installed - you absolutely should NOT try to install dosemu-freedos separately, and dosemu-freedos shouldn't even be in the repositories, because it only confuses people who don't know that the two installations have been combined into dosemu alone.

Simply install DOSEMU 1.4.0 from the repositories and you've got FreeDOS installed with it. (Might be a good idea to completely remove any previous version.)

This is not an issue that needs to be fixed. It's already fixed, and there is no problem - except that dosemu-freedos is confusingly still in the repertories, even though it's obsolete.

---

### Post by jamillikan on 2007-11-11
Thank you so much for your post.  I had no idea that DOSEMU 1.4 included dosemu-freedos by default.  You've just resolved my issue.  It's working perfectly now.  

Joe

---

### Post by emendelson on 2007-11-11
The fact that dosemu-freedos is in the repositories is extremely confusing - because it's now absolutely useless, both on its own, and in relation to anything else. You're not the only person who's been bitten by this one!

I'm glad it's all sorted out now...

---

