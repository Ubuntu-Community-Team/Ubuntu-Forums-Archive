---
title: "photo recovery"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by marquee moon on 2008-03-24
I have lost all my family photos.

I intended to back them up onto a cd, but realized I needed 1Gb, so pressed cancel and went to backup onto a memory stick. The folder had gone from my 'home' directory. So I dragged and dropped the newly created folder from the 'create CD/DVD' window back onto my home directory. However, this didn't have any photos in it: the photos have just gone. All I have now is an empty file structure. 

I've tried "recoverjpeg" on sda1, but its not found them- its found all sorts of other junk, but not my family photos. 

I then realized my home directory sits on sda5, which is on sda4. I tried checking both these disks & received this error

"unable to open /dev/sda4 for reading (no such file or directory)"

Please can someone suggest were my photos may have gone or how I can get them back?  (I have not turned the computer off since)

thanks 

James

---

### Post by Ub1476 on 2008-03-24
Did you look in /tmp? And you probably have better luck if you scan /media/disk*, because other partitions is mounted here.

---

### Post by marquee moon on 2008-03-24
Yes, I've looked in /tmp. The folder with the greatest number of files in is entitled "orbit-james". This has 24 files (which are all linc***** apart from two)

sorry for being ignorant, but how does /media/disk fit into the grammar for recoverjpeg? 

I've just tried: 

james@james-laptop:~$ sudo recoverjpeg media/disk/dev/sda4/
Password:
recoverjpeg: unable to open media/disk/dev/sda4/ for reading (No such file or directory)
james@james-laptop:~$ sudo recoverjpeg media/disk/
recoverjpeg: unable to open media/disk/ for reading (No such file or directory)


cheers

James

---

### Post by marquee moon on 2008-03-24
please....anyone?

---

### Post by smoker on 2008-03-24
try downloading and booting from the ubcd, it has various recovery apps included, testdisk, eg, maybe worth a try, info here:
[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

best of luck

---

### Post by TheWizzard on 2008-03-24
> **marquee moon said:**
> please....anyone?

first: don't mount your hdd! 
after deleting a file, the data initially remains, but can be overwritten. 

you can try to recover the data yourself. there's plenty of information on the net ([http://www.google.nl/search?q=linux+data+recovery](http://www.google.nl/search?q=linux+data+recovery)). 

however, since the files seem important to you and you don't have experience with this i'd bring the pc to a professional.

---

### Post by Sef on 2008-03-24
Check out [PhotoRec]("http://www.cgsecurity.org/wiki/PhotoRec").

---

### Post by marquee moon on 2008-03-24
> **TheWizzard said:**
> first: don't mount your hdd!.

my hdd is mounted: I was using at the time, and haven't un-mounted or logged out since

[Quote=Sef]Check out PhotoRec.[/Quote]
Thanks, I've grabbed it from synaptic & am running it at present

---

### Post by Sef on 2008-03-24
Please post if it works for you, and if it does, then mark the post as solved.   (Under Thread Tools.)

---

### Post by TheWizzard on 2008-03-24
if you don't have seperate home and root partitions, installing packages may overwrite your lost photos forever.

---

### Post by marquee moon on 2008-03-24
well I ran photorec on my active partition = sda5

It was set to save the recovered files into root. Unfortunately it ran out of disk space just before it finished (...having used up 10Gb). 
It produced many files which were openable with root privilege (I used pcman file manager for this). These files mostly contained .txt and .html formats

I have been unable to recover any photos. 

[Quote=TheWizzard] if you don't have seperate home and root partitions, installing packages may overwrite your lost photos forever. [/Quote]

I think this is what has happend. :(


I had a backup from a few weeks ago, so I should be able to get most of our photos back. 

thank you all for your help.

---

