---
title: "Have i stuffed my harddrive?"
date: 2006-09-22
forum: Absolute Beginner Talk
---

### Post by insidethevault on 2006-09-22
Hey everyone
My names tim, im very new to ubuntu. 

My dilemma started when i installed my brand new 320gb hard drive, i installed ubuntu and when i rebooted i got GRUB ERROR 18

So following advice on the forums i did a bit of partitioning, changed it to file system 32 (wasnt that a silly idea) had to reformat and install. Suddenly i was in, i dont know how and i dont know why, but now my 320gb harddrive is only 297.00gb??? And its also saying that theres only 275gb left on the harddisk.

How can ubuntu possibly be taking up 22gb of harddrive space. 

I really hope i havnt stuffed my harddrive royally, am i missing something, please help someone!

Many thanks
Tim

---

### Post by jd65pl on 2006-09-22
Could you try reformatting the drive possibly with [gParted live CD]("http://gparted.sourceforge.net/livecd.php") it maybe the cxase that your partition table is incorrect or that zero blocks of data have been written to the disk. I have done both before unknowlingly and ended up with a HD with significantly less space than actual! It should be fixable though.

J

---

### Post by insidethevault on 2006-09-22
tried, but no luck

Looks like ill just have to live with that expensive mistake

Thanks so much for your help

Tim

---

### Post by anaconda on 2006-09-22
No you haven't! And it isn't ubuntus fault either.

The issue here is that hard-disk manufacturers actually tell that their hard-disks are bigger than what they really are.

they use the formula: 1MB = 1000000 B
when what computers really use and what people understand MB to mean is: 1MB =(2^20)B =1048576 B

and from this you get (about)
320000000000/(2^30)= ~298GB

which means that the real size of your hd is about 298GB.. isn't marketing just wonderful.

More info.
[http://en.wikipedia.org/wiki/Megabyte](http://en.wikipedia.org/wiki/Megabyte)

And in addition to this. Ubuntus installer normally reserves 5% of hd-space to the root user. (which actually is waaaay too much nowdays) The purpose of this 5% is that when the disk gets full the root user still has a bit room to work in.. (important in multi-user enviroments, but 5% from 320GB hd is just too much for this purpose.)

but this 5% (14GB) is not a problem, because it can be freed (changed to 0%) later.. atleast with ext2/3 filesystem

and of cource with ANY filesystem some space 1-2% has to go to making the filesystem to the hard disk. sort of like making index of every address of your hd..

---

### Post by insidethevault on 2006-09-22
Wow

:D i cant believe it!! Before you told me that i was down in the dumps because i thought that i had screwed up big time. But that makes so much sense.

Thankyou so much to both people who posted, you have been extremely helpful and have made my day

You both are the reason why im going to soldier on with Ubuntu

Thankyou
Tim

---

### Post by anaconda on 2006-09-22
oh. and if you calculate from the above post you will get

5% reserved for user root
297GB x 0.05 =14.85GB

and 2% for making filesystem
297GB x 0.02 =5.94GB

14.85+5.94=20,79GB

22-20,79=1,21GB left for your ubuntu installation.. which seems about right (=1-2GB)

---

### Post by insidethevault on 2006-09-22
amazing...

im so relieved

Tim:)

---

