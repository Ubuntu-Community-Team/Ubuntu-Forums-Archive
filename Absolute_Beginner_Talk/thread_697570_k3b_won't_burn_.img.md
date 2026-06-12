---
title: "k3b won't burn .img?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by Djbb on 2008-02-15
I'm trying to burn a .img file using K3b, I have 3 files sitting in my folder
image.ccd
image.img
image.sub

I open K3b > Burn CD Image, open the .img file and K3b gives me:
Seems not to be a usable image.

Whats going on?

---

### Post by OldGrey on 2008-02-15
I am right in believeing that is a Mac image file? If so that may be your problem.

---

### Post by jaytek13 on 2008-02-15
K3b should be able to burn .img images fine. What happens if you right click on the file and select burn to cd?

---

### Post by Djbb on 2008-02-15
> **jaytek13 said:**
> K3b should be able to burn .img images fine. What happens if you right click on the file and select burn to cd?

Strangely enough, I don't have the option to 'Burn to CD' when I right click on the file, but I don't think its just that file either because I right clicked on some .mp3's and it doesn't give me the Burn to CD option either.

---

### Post by kellemes on 2008-02-15
Have you tried renaming the .img to .iso?
It may seem stupid, but software is stupid ;-)

---

### Post by Djbb on 2008-02-15
> **kellemes said:**
> Have you tried renaming the .img to .iso?
It may seem stupid, but software is stupid ;-)

Yeah I tried that, and when I changed it to .iso it gave me the option to "Write to Disc" when I right-clicked on the now image.iso file, so I chose Write to Disc and it gives me

Unable to create CD/DVD
The file blahblah/blah/image.iso is not a valid disc image

---

### Post by jaytek13 on 2008-02-15
Are you certain it's a valid image file?

---

### Post by Djbb on 2008-02-15
> **jaytek13 said:**
> Are you certain it's a valid image file?

I'm pretty certain its a valid image file, but maybe the download got corrupted somewhere along the way? I could always try re-downloading the file

---

### Post by kellemes on 2008-02-15
> **Djbb said:**
> I'm pretty certain its a valid image file, but maybe the download got corrupted somewhere along the way? I could always try re-downloading the file

Yes, or try using some other burner and see if it works..
[https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d]("https://help.ubuntu.com/community/CdDvdBurning#head-c448095898e6c5c2443974bc3f1120aaa8948f7d")

---

### Post by JROQuinn on 2008-02-18
it will burn with K3b...just right click on the .img, click on Open with other application & choose K3b...works like a charm :)

---

### Post by golojo on 2008-03-19
To use .img file with k3b U have to use .cue file, then it works.

---

