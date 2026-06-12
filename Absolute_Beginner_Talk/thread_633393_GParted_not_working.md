---
title: "GParted not working"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Rezistik on 2007-12-06
I decided I want to give ubuntu a try and torrented it,burned it and popped it in. I opened GParted ti partition my C Drive but it refused to read it, said it was physically damaged (Windows reads it fine..) So I figured I would use my secondary drive, so I cleaned my secondary drive on windows and then I popped ubuntu back in and Gparted read the drive and then I did the partitioning and when I pressed apply, I got an error. So I have two questions one Can I dual boot using two separate drives, Two is it okay that all my drives are NTFS, and I lied i have a few more questions....What software should I use since Gparted either does not work on NTFS or I fail at using it.

Oh and I cant wipe my secondary drive entirely I freed 17 gigs and am aiming to only use 10 gigs for ubuntu, its my media drive all my music, pictures and .psds so I was also hoping ubuntu could read it.

Thanks in advance  :)

---

### Post by celticbhoy on 2007-12-06
The Install from the Live CD works with NTFS formatted drives OK. 
Dual boot on 2 drives also works fine (thats my setup)
You should not need to completely wipe second drive, Just make sure you run Defrag a couple of times over it.

---

### Post by Rezistik on 2007-12-06
I just finished defragging it, I'll try again and see if GParted works alright thanks...I shall return if it refuses to work still

---

### Post by bobpur on 2007-12-06
I use two different drives as well. Install Windows first (This is important!) on hda (or sda) and linux on hdb (or sdb). 
Ubuntu, once you show it the proper drive, will take care of the correct formatting. All you have to do is moniter and answer prompts with the correct info.
You can get a stand-alone copy of Gparted at: [www.distrowatch.com](www.distrowatch.com). There is a list of distros on the right side of thje screen. Just scroll down untill you find Gparted. Burn it as a regular ISO image.

Good Luck!

---

