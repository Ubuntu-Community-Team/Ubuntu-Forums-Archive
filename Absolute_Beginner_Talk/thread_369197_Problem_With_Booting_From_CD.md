---
title: "Problem With Booting From CD"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by 03myersd on 2007-02-24
Hey,
      I wanted to try out ubuntu by just booting it from the cd. But for some reason whenever i try i get an almost completely blank screen with a flashing underscore as though i am at some sort of command line but this vanishes after about a second and then continues to boot into xp from my hard drive. How can i get it to boot from the cd? Thanks.

---

### Post by Maestro23 on 2007-02-24
> **03myersd said:**
> Hey,
      I wanted to try out ubuntu by just booting it from the cd. But for some reason whenever i try i get an almost completely blank screen with a flashing underscore as though i am at some sort of command line but this vanishes after about a second and then continues to boot into xp from my hard drive. How can i get it to boot from the cd? Thanks.

In your BIOS, do you have your boot-order set to boot from CD/DVD drive first?

If not, go into your BIOS and change it.

---

### Post by louis_nichols on 2007-02-24
That might also be because the BIOS tries to boot from the CD but fails. This could happen in case there was an error in downloading and/or burning the ISO image. If the BIOS turns out ok, I suggest you check the md5 sum of the ISO image and, if it doesn;t match, download it again. If it matches, just burn it again on a CD.

---

### Post by 03myersd on 2007-02-24
The bios is booting from the cd drive first then the hard drive. I manually selected the cd drive also a couple of times just to make sure. I am going to apologise for being a rookie here but can i ask for an explination of the "md5 sum" thing. Ill just point out that although i am only 15 i am a quick learner. Thanks again.

---

### Post by louis_nichols on 2007-02-24
I think wikipedia explains [what md5 is]("http://en.wikipedia.org/wiki/Md5") better than I could.

as for usage, I will direct you to the [ubuntu wiki]("https://help.ubuntu.com/community/HowToMD5SUM"), which has a lot of info on all sorts of stuff.

---

### Post by 03myersd on 2007-02-24
I assume i am looking for the code to match the code in the file on the cd?

---

### Post by louis_nichols on 2007-02-24
Exactly. You use the utility md5sum to calculate the value for your downloaded value and see if it matches to the one in the ISO.

---

### Post by 03myersd on 2007-02-24
I tried it and found that the first one didnt match. So i downloaded the iso again (torrent this time) and this time there was a match. Unfortunately it still wont boot the cd.....

---

### Post by louis_nichols on 2007-02-24
OK. Are you certain the BIOS is set to boot from CD? You should check this by trying to boot some other CD. Maybe a windows installer (just to check).

On the other hand, it's worth also trying to boot the CD you burned in another computer. It might be a burner issue, in which case this CD won't boot in another PC either.

It can only be one of these 2: either BIOS not set up (or having a problem) or CD not burned correctly. The Ubuntu installers work.

---

### Post by Maestro23 on 2007-02-24
> **louis_nichols said:**
> OK. Are you certain the BIOS is set to boot from CD? You should check this by trying to boot some other CD. Maybe a windows installer (just to check).

On the other hand, it's worth also trying to boot the CD you burned in another computer. It might be a burner issue, in which case this CD won't boot in another PC either.

It can only be one of these 2: either BIOS not set up (or having a problem) or CD not burned correctly. The Ubuntu installers work.

And burn at a slow speed, like (4x).

---

### Post by 03myersd on 2007-02-24
> **louis_nichols said:**
> OK. Are you certain the BIOS is set to boot from CD? You should check this by trying to boot some other CD. Maybe a windows installer (just to check).


yep did that and it works fine

> **Maestro23]And burn at a slow speed, like (4x).[/QUOTE]

Did that too

[QUOTE=louis_nichols said:**
> 
On the other hand, it's worth also trying to boot the CD you burned in another computer. It might be a burner issue, in which case this CD won't boot in another PC 

Em... about that.... It didnt quite work....  *Looks a bit sheepish*


I have tried 7 different disks. Different burning programs, different speeds and even tried unzipping the iso and burning all the files as a data disk. None worked. It has burned plenty of other linux distros before so why not this one? I am very confused....

---

### Post by 03myersd on 2007-02-25
Sorry im having a bit of trouble with editing my last post. Iried it with new CD's this morning but it still didnt work. Must be a hardware problem. Yet it still managed to burn other images....

---

