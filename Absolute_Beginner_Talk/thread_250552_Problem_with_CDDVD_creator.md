---
title: "Problem with CD/DVD creator"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by nelsonak on 2006-09-04
Not sure exactly where the problem is but decided to post to see if anyone has had a similar issue.  I want to burn a cd from an ISO image.  I have tried different ways of getting to the point where the cd is made but every time the burning process starts it keeps telling me to insert a blank cd though there is already one in there.  I tried different cds and different brands all with the same result.  If I just place the blank cd into the desired cd drive, Ubuntu will pop up a message telling me that a blank drive is in the burner and asks me if I want to do anything with it, so it appears that the cd drive works fine with unbuntu.  Anyone have a similar experience?

---

### Post by catlett on 2006-09-04
What app are you using. I use gnomebaker and haven't had any issues. If you do not have it installed, install it with```
 sudo apt-get install gnomebaker
```
If that app has an issue post yout /etc/fstab , use ```
cat /etc/fstab
```, and we'll see if we can tweak the entry for better results.

---

### Post by meborc on 2006-09-04
do you have 1 or 2 cd-drives? ... sometimes there is a mixup in the drives... just pointing out the most obvious... and probably wrong solution :biggrin:

---

### Post by wpshooter on 2006-09-04
> **nelsonak said:**
> Not sure exactly where the problem is but decided to post to see if anyone has had a similar issue.  I want to burn a cd from an ISO image.  I have tried different ways of getting to the point where the cd is made but every time the burning process starts it keeps telling me to insert a blank cd though there is already one in there.  I tried different cds and different brands all with the same result.  If I just place the blank cd into the desired cd drive, Ubuntu will pop up a message telling me that a blank drive is in the burner and asks me if I want to do anything with it, so it appears that the cd drive works fine with unbuntu.  Anyone have a similar experience?

Yes, I had a very similar experience when I started with Ubuntu.

My suggestion is that you go to add/remove programs and install K3b and forget about the built-in CD program and forget GnomeBaker also, I could never get it to work correctly.

Good luck.

---

### Post by catlett on 2006-09-04
> **meborc said:**
> do you have 1 or 2 cd-drives? ... sometimes there is a mixup in the drives... just pointing out the most obvious... and probably wrong solution :biggrin:

Actually that definately pertains to this. I have a dvd-rom and a dvd-writer. I can only play dvd's in the rom. When I pu a dvd in the writer, it gives the popup about what to do but when I launch the movie player, it says no media present. If I switch the dvd into the rom, it plays.

---

### Post by ripster on 2007-01-10
This is the thread that was closest to describe my problem. I recently installed a new dvd/cd player/burner after having had only a cd player for years (that worked fine). After installing I can only play DVDs. When inserting a CD it isn't even detected. Doesn't matter if it's a blank or a full disk. You can hear the drive work to read it but nothing happens. I thought maybe I had some loose cables or something but that's not it. Do I have to change some kind of properties and in that case how? I thought all driver routines came automatically with ubuntu. If anyone can help me I'd appreciate if you guided me as if I were a 5 year old (only 5 year olds probably knows more about this stuff than I do).

---

