---
title: "How to open files in DVDShrink?"
date: 2006-08-07
forum: Absolute Beginner Talk
---

### Post by mrvgarg on 2006-08-07
Hi

How can I open files in DVDShrink using wine?

Thanks

---

### Post by x64Jimbo on 2006-08-07
Can you post screenshots of the problem you're seeing? 
You also might want to check out k9copy. It's a native Linux program that does the same thing.
More info:
[https://help.ubuntu.com/community/K9Copy](https://help.ubuntu.com/community/K9Copy)

---

### Post by mrvgarg on 2006-08-07
The porblem is I have downloaded a dvd-r which contains vob, ifo and bup files. However it is just a bit too big to fit on a dvd-r. The site I downloaded from has told me to shrink it with dvd shrink. I am able to reauthor the movie but I want to keep the menus so have to do a full backup. But due to a bug in wine and dvd shrink the open files does not work.

---

### Post by x64Jimbo on 2006-08-07
Can you put all the files into an iso file? If so, you can then mount the iso image to a virtual drive, map that drive in your winecfg, and then rip the DVD to a new ISO that is the right size.

---

### Post by mrvgarg on 2006-08-08
How do I make it into an iso?

---

### Post by jethro10 on 2006-08-08
You could install K3 burner from the repos this will easily do it for you to burn a disk if its a single layer, ie. less than approx 4.5 Gb

Jeff

---

### Post by orb9220 on 2006-08-08
here is how you do it. Find the video_ts folder where the vob's and other files are copy the video_ts folder to home.

Have you installed dvdshrink with wine and it runs on your desktop?

If so then run dvdshrink select open files and select the folder if it is a valid video_ts folder then dvdshrink will read it in. Then you can  re-encoded back to a new folder or save as a iso.

---

### Post by x64Jimbo on 2006-08-08
Umm. The OP already stated that there is a bug in DVDShrink that is keeping him from opening files. 
mrvgarg, you should look into using DVD Decrypter to get all those files into an ISO that you can then shrink with DVD Shrink. If you want to skip all this hassle, you could try k9copy as I suggested. It's just like DVD Shrink and doesn't have to run through wine.

---

### Post by mrvgarg on 2006-08-08
I can only open a dvd or an iso with dvd decrypeter. k9copy also only opens dvds in dvd drive.

---

### Post by orb9220 on 2006-08-08
There is not a bug in dvdshrink I have done it that way myself on more than one occasion. If I have a marginal disc with read errors at the beginning then I sometimes can get away with copying the video_ts folder to hd then open files in dvdshrink.

If you copy the folder to the hd and then dvdshrink says thier is a  problem then it usally is the contents of the folder are not dvd compliant and  have a coruptg or missing an .ifo or .bup etc.. file which would break the navigation.

That is all I think of and good luck on solving it.

---

### Post by mrvgarg on 2006-08-08
Umm yeh the open files is working now. However it was not working last week. Hmm. :shock: :sad:

---

