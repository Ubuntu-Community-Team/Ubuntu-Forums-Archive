---
title: "Brand New and Have Questions..."
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by Watchintv on 2006-09-06
Hi there, I am brand new to the forum and am pretty new to Ubuntu.  I have tested the live cd of ubuntu, which I burned myself, and I must say I love it.  So im definitley thinking of setting my notebook up for dual-booting, but before I install it I got a couple of questions.
[LIST=1]
[*]What is the best backup software to use to backup my Windows XP stuff?  I made a full disk backup using Acronis True Image, but the backup takes up wayyy to much space.  I'm just not sure if I should backup files and folders or if I should backup everything, like applications.


[*]Iv'e gone through a bunch of tutorials on dual-booting, pretty much every tutorial known to man, but I still was a bit confused.  When I first tryed to install Ubuntu, I chose the first option in the "prepare disk space" section becuase it seemed like the easiest way to dual-boot.  But then I got a bit confused on what to do with the "new partition size" slider.  I only want to use 10 gigs for the Ubuntu partition so is that what I use the slider for?  Just move it to 10 gigs?  If not, could someone give me a little insight on where I do that or what option I should use.
[/LIST]

I'm brand new to this stuff so use small words;) , please.

Thanks!

---

### Post by deadgobby on 2006-09-06
There is a on line dual boot at 
[http://video.google.com/videoplay?docid=-6104490811311898236](http://video.google.com/videoplay?docid=-6104490811311898236)
 You may hose your HD so try to back up any important inforamtion. Like save files. 
GObby

---

### Post by ruppmeister on 2006-09-06
Well to start, you are using the best backup utility there is for windows already. There is a way to use this program to set a "secure zone" where you backup the entire hard drive to. I would recomend you use this as your option if you have the HDD space. When you use this option it saves the winbloze partition in a new FAT partition along with the MBR (master boot record). Because you have saved it in the "secure zone" you can mess it all up and still go back to windbloze again if you want.

When installing the Ubuntu after setting up the "secure zone" in True Image, when you get to the point where you are selecting the drive and partition and size, you would want to pick the option that says something like "repartition the drive hda1" or something like that (it should be the first option like you said and have a slider). When moving the slider the extreme right it should have the size of your hard drive minus the size of the "secure zone". If this is the case then you can be sure that it will not touch the "secure zone" and resize it to 10 gig like you want. That would be moving the slider to the right until it says 10 gig.

Hope that helps a little. Get back if you have a problem with any of this.

---

