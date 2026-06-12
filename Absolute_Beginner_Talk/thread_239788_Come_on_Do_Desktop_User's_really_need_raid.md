---
title: "Come on Do Desktop User's really need raid ?"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by orb9220 on 2006-08-19
I was condidering to build a new system and alot of the mobo's heave raid.

Now I know what raid is I just can't figure out why I would need it.
Also it just adds one more thing to configure or go wrong.

Is it just another overkill excuse to sell more HD's ?
It is just for servers right ?

My hard drives are reliable and I never have lost data even tho I run 24/7  in room temps of 90+ for the last 3 years.

Do I Really NEED raid ?

---

### Post by Tom Brokaw on 2006-08-19
It can increase load times considerably, so gamers like it, and others who load apps frequently.  Hard drive is the second slowest component after optical, so when a faster option comes up, performance junkies want it.

---

### Post by TheMono on 2006-08-19
Short answer - No. Nobody really NEEDS raid.

Having said that, if you're game, RAID0 is kinda cool.

---

### Post by jrjr on 2006-08-19
.

---

### Post by hopstah on 2006-08-19
no, you don't really NEED anything.  one raid setup allows for twice the disk write speed, because the system recognizes it as one volume, and it stripes the data across the drives.

and don't fool yourself into thinking that your hard drives are reliable just because they *have been* reliable.  i don't have any sort of backup system yet, because i'm poor.  it all depends on how valuable your data is.  mine is very valuable, because it is my music library, which i am going to setup a backup server for soon.

---

### Post by David Corrales on 2006-08-19
It depends on the what you use your system for and the data you're manipulating.
If you're working on a lot of IO intensive applications, for example digital video editing. RAID 0 will speed up read/writes considerably.
If you're doing work from home and can't afford to simply "lose the data", RAID 5 is the way to go.
For normal usage and the like, a single drive + external backup sounds good enough for me :)

---

### Post by orb9220 on 2006-08-19
Thanks for the input guys and gals? much appreciated.

---

### Post by catlett on 2006-08-19
It depends on what you do or want
raid0 wil write data to all your disks at once. So if you have 4 disks instead of one, your write speed just went up by 4. But if one drive fails the system fails

raid1 will create exact copies of your disks "on the fly" if you have 4 disks, 2 are used and 2 are exact backups. What do you do? Is your data imperative? Data is totally safe if a drive fails. But it is slower than 0

raid5 is popular because it offers data backup with better performance. It uses a different means of backup. An example is if disk one and two equal 3 and 6, then 9 will be written to the backup drive. Then if either disk fails, it can be recovered by using a backwards method i.e. 9-6 =3 so the first drive's media is recovered.

---

