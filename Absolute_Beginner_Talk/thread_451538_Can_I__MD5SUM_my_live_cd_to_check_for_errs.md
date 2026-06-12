---
title: "Can I  MD5SUM my live cd to check for errs?"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by drakebarimore on 2007-05-22
[COLOR="RoyalBlue"][SIZE="2"]I am trying to determine why my live cd stopped working all of a sudden.  It worked fine for several loads, but then I started getting stuck at the loading screen.  It gave me an "I/O error can't read boot cd" message, and that was it.  

I tried to run the cd through my external USB cd/rw drive, (changing the boot sequence of course) but that doesn't work either.

My question is:  Is there a way that I could MD5SUM the live cd itself to check for errs on the cd?  When I made the cd (I've made several trying to get it to work) the MD5SUM always matches, so I always have gone ahead and burnt the image.  But when it doesn't work, I'm wondering if the cd has gotten corrupted somehow durring the writing process? 

Any ideas?[/SIZE][/COLOR]

---

### Post by LaRoza on 2007-05-22
Can you not use the cd itself to check for errors? It is an option when it boots.

You can evaluate the md5sum of the cd if you want to.

---

### Post by lazyart on 2007-05-22
If you can't make it to the main menu (where one of the options is to check cd for defects) then I would just burn a new one.  CDs are what, 3 cents each nowadays?

---

### Post by drakebarimore on 2007-05-22
No, I can't check the cd from within the software.  If I click that option, it gives me the same I/O error can't read boot cd.  

And to answer the other post, I have burnt several cds already to the point that I'm  pretty sure thats not the issue.  I was very careful to download the correct version, check to make sure that I had the correct version with MD5SUM and I burnt the image at 4x speed. 

Originally the cd did work.  I was successful at opening ubuntu and using the features (surfing the web playing with openoffice etc.)  So it just stopped allowing me to load at some point with nothing but the I/O error.  When I thought that meant something was wrong with my cd-drive, I tried another external cd drive, but I get the same problem.

---

### Post by viciouslime on 2007-05-22
I think on the boot menu when you select "start/INstal ubuntu" if you press down a few times there is another option, something like "verify cd" or "verify install disc". Failing that, you could rip it to an iso and perform the md5sum check on the iso then compare that to the md5sum in the file on the download server.

---

### Post by LaRoza on 2007-05-22
Is it possible that the disk was physically damaged?

I would try to burn another cd, at a very slow speed. (I do mine at 1x or 2x)

If that cd doesn't work, it is either the ISO or the player/burner.

---

### Post by drakebarimore on 2007-05-22
How do I "rip it to an ISO?"

---

### Post by viciouslime on 2007-05-22
> **drakebarimore said:**
> How do I "rip it to an ISO?"

Using another ubuntu machine, put the disc in, right click it once it appears on the desktop, press copy disc, then select "File Image" in the drop down for "Copy disc to:"

I don't know that that will work though, as the file creation date etc. will be different and if these are taken in to account when producing an md5sum then you will get a different md5sum whether it is corrupt or not. You're best to select the option off the boot menu.

---

