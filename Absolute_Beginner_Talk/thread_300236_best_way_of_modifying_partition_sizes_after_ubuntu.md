---
title: "best way of modifying partition sizes after ubuntu install"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by pthickett on 2006-11-15
Chaps,

On my laptop i have installed xp, then ubuntu, but after playing with ubuntu for a while i want to move my music and photos from the xp partition, reduce its size, increase the size of my ubuntu partition and dump the files there. Is this possible? Whats the best way of doing it? I dont need to worry about storing the files between operating systems as i can save them to my ipod, its just a matter of best practice modifying partition sizes.

I am thinking i can do it by using partition magic in windows to reduce the size of that partition, and in theory i could increase the size of the ubuntu partition at the same time, but i am worried it may mess up my ubuntu install.

Any advice would be great.

Regards

Pete Thickett

---

### Post by giants_fan on 2006-11-15
Backup first...

Then, get the Linux System Rescue CD ([http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page)) and run the QtParted application that comes with it.  Basically, it's a Partition Magic clone...but free.

---

### Post by pthickett on 2006-11-15
ok thanks for your suggestion.

But if i have partition magic installed on my windows partition anyway should i just use that? otherwise i will use that qtparted program.

ta

---

### Post by giants_fan on 2006-11-15
If you have PM already installed in Windows, it will likely work fine.  Personally, I'd be cautious about resizing a partition while you're in it (which is what you'd be doing).  That said, there's probably no good reason for me to be skeptical...other than in that "I've got a bad feeling about this" type-of-way.

FYI, using the System Rescue CD, you'd boot into it directly--instead of being in Windows or Ubuntu.

---

### Post by smoker on 2006-11-15
just a comment, it is always better to get rid of all your junk files and defrag before resizing a windows partition.

---

### Post by jd65pl on 2006-11-15
I have used gparted live cd and it is excellent![URL="http://gparted.sourceforge.net/livecd.php"]

http://gparted.sourceforge.net/livecd.php[/URL]

---

### Post by jimbob on 2006-11-15
I second that.  Gparted seems to be a much more polished program and will handle ntfs partitions easily.

Qtparted has a crude GUI which reminds me a lot of MS=DOS.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

