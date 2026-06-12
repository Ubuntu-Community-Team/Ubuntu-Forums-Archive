---
title: "Problem with initial boot MBP"
date: 2008-03-06
forum: Apple Intel Users
---

### Post by alanlindsay on 2008-03-06
Hi everyone,

having some problems installing ubuntu 7.10; Have been following the guide wiki.ubuntu.com/macbookpro and got to the part where I boot up the ubuntu CD. I choose the install option and after a few minutes I get a message telling me I'm in low graphics mode and I can either continue or configure. I can configure fine if needs be but afterwards there is almost no progress. Checking battery status...[OK] running local boot scripts...[OK] comes up and there is no further progree whatsoever.

I'm running the new penryn macbook pro (2.4). Any advice is much appreciated, cheers

Alan Lindsay

---

### Post by alanlindsay on 2008-03-06
I should mention I'm following the triple boot instructions and have already successfully installed XP with bootcamp.

---

### Post by cyberdork33 on 2008-03-06
Try hitting enter to continue, otherwise, you may need to use the alternate install cd..

---

### Post by alanlindsay on 2008-03-06
No luck with pressing enter. Downloading the alternate edition now. Cheers,

Alan

---

### Post by MichaelSwengel on 2008-03-06
After you were told that you were running in low graphics mode, did you try to restart the X-Window manager? (Ctrl-Alt-Backspace)

That can solve a lot of issues right away. I'm also running on a new 2.4 Penryn MBP, and I haven't had that issue. My only problem is getting wireless (Madwifi isn't working) and sound working.

I wish you luck,
MS

---

### Post by cyberdork33 on 2008-03-06
maybe it was just a bad download / burn?

---

### Post by alanlindsay on 2008-03-07
Proceeded with the alternate install. Got to 6% on "Select and install software" screen and it looks like it's crashed there. Says please wait.....frustrating....

---

### Post by alanlindsay on 2008-03-07
oh it just moved. Nice.

---

### Post by Chrisj303 on 2008-04-02
This issue is what made me leave Ubuntu.

Couldn't even get to the desktop with the liveCD on my MBP.

I tried the alternate install disc, but to a noob like me, I didn't have a clue what I was doing...

---

### Post by Chrisj303 on 2008-04-03
I'm going to try again.

My Macbook Pro got stolen last week (my house got broken into) - and the replacement MBP is going to be the new model, so maybe I will have better luck.

Is there a guide on how to install Ubuntu on a MBP using the alternate CD if needed? I can't find anything on these boards, and can't ever remember seeing one in the past or even a link to one.


TR

---

### Post by cyberdork33 on 2008-04-03
> **Chrisj303 said:**
> My Macbook Pro got stolen last week (my house got broken into) - and the replacement MBP is going to be the new model, so maybe I will have better luck.That really sucks sorry to hear it.

> **Chrisj303 said:**
> Is there a guide on how to install Ubuntu on a MBP using the alternate CD if needed? I can't find anything on these boards, and can't ever remember seeing one in the past or even a link to one.Unfortunately, if you are getting a brand new MBP, you will have other issues as there is poor support for the new multitouch trackpads as of yet, and you have to deal with a Broadcom WiFi card. The good news is that I think the Live CD should work fine (Hardy).

There is not guide specifically for the Alt CD that I know of, but there is really not that much difference other than the fact that you are in an ncurses environment. Partition your hard drive beforehand, and then choose the manual partitioner and select the partition to use for the root filesystem and the format that you want to make it.

---

