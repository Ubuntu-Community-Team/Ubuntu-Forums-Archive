---
title: "has there been a consensus for swap size?"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by JohnJSal on 2006-08-04
I've read several posts and various online articles, but I'm just wondering what the consensus is lately. It seems the 2x RAM is no longer necessary, but is 1.5x recommended? Or does it even need to be 1x? 

I have 1GB of RAM and my HD is 60GB. Keeping it as a dual-boot machine means Ubuntu gets less than the whole drive, obviously, so I want to make sure I'm not wasting any space by making the swap too big, but of course I don't want to cause problems by making it too small. Is 1GB enough for 1GB RAM, or should I make the swap bigger?

Thanks.

---

### Post by Lord Illidan on 2006-08-04
I think 1/2 a gig should be enough. I have 512 mb of RAM and I scarcely use swap space.

---

### Post by aysiu on 2006-08-04
I'd say 2 times RAM but no larger than 1 GB.

Usually 512 MB is plenty... and totally unnecessary.

---

### Post by djsroknrol on 2006-08-04
Everything I've read of late on the subject says 1 1/2 times your actual machine ram...

---

### Post by spier on 2006-08-04
> **aysiu said:**
> I'd say 2 times RAM but no larger than 1 GB.

Usually 512 MB is plenty... and totally unnecessary.

with 1 GB swap partition, I lost suspend and hibernate features (freezing at wake up) after Ram increase from 512 to 1280MB. Had to change swap to 1.5GB to correct it.

---

### Post by Lord Illidan on 2006-08-04
> **djsroknrol said:**
> Everything I've read of late on the subject says 1 1/2 times your actual machine ram...

That's crazy.. who needs 2.5 gigs of swap?

---

### Post by stormblue on 2006-08-04
I would recommend 2 times for laptops up to 1 gig.  The reason for this is that hibernation is written to swap and this should make you fairly safe to not mess it up.

On desktops you can get away with 512 and that's plenty!

---

### Post by Metacarpal on 2006-08-04
> **Lord Illidan said:**
> That's crazy.. who needs 2.5 gigs of swap?

Showoff. :rolleyes:

---

### Post by djsroknrol on 2006-08-04
> **Lord Illidan said:**
> That's crazy.. who needs 2.5 gigs of swap?

Lord Illidan..you're right..anything over 1GB doesn't really need a swap..most people only have an average of 512MB (from all the people I've talked to or asked), which would equate to an 800-950MB swap..and that's what Ubuntu set my first setup as automatically. If I'm wrong, I heed to you sir...:)

EDIT: I really need to read further that the titles these days..or put my glasses on..one or the other...

---

### Post by JohnJSal on 2006-08-04
> **stormblue said:**
> I would recommend 2 times for laptops up to 1 gig.  The reason for this is that hibernation is written to swap and this should make you fairly safe to not mess it up.

On desktops you can get away with 512 and that's plenty!

I think I'll go with 1GB then. I don't even use hibernate anyway, just sleep mode sometimes.

---

### Post by hyperair on 2007-09-30
I've got 1.2GB RAM and 1GB swap and I certainly don't have trouble hibernating =P Using Gutsy by the way.

---

### Post by vikasmk on 2007-09-30
i have 512 ram but 260 mb swap partition , so i cant hibernate.

---

### Post by Sef on 2007-09-30
been thinking of adding more memory, but maybe I will hold off.

---

