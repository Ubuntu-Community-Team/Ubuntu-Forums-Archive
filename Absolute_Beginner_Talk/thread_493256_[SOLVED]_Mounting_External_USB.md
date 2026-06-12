---
title: "[SOLVED] Mounting External USB"
date: 2007-07-05
forum: Absolute Beginner Talk
---

### Post by drogers on 2007-07-05
Hi all,

I'm going to try and give as much information as possible since this is one big mess (probably due to the fact that I haven't given enough information in the past).

I was running Ubuntu Ultimate (6.10 Edgy?) because I liked all the programs that came with it. My update manager told me to upgrade to Fiesty and since I'm a noob beyond all noobs, I hit the forums and asked people how that would go down... I was really reluctant to do this because this is the computer I use for work and there's tons of important information I need! So, the general consensus was pretty much to go for it. I did and what a mistake! I had (and have) many problems. With out going into too much detail, I can't see the screen on my laptop; it's just a bunch of lines of different colour...

So I ran my Live CD of Fiesty (7.04??) and went out and bought a Maxtor OneTouch III USB external harddrive. I thought all was well because I could see all of my documents but when I tried to write to the USB drive, I wasn't able to. The problem with the Live CD is that I cannot write to any harddrives; okay so that's been established. I went back and ran the Ultimate CD (which is Live) and am able to write to the harddrives (including the USB) but now the problem is that it wont show that drive with all of my documents. It only shows the file system and the USB. I'm assuming that I need to mount it but don't know how.

So the question is; using the Ubuntu Ultimate Live CD, how can I mount my drive (hda1) which is labeled as 'disk-1' so that I can copy the files from there, onto my USB?

Any help with this would be greatly appreciated!

Side note: I hope to god that someone can help me; it will be the first bit of luck in the past two weeks. The gf left me with a ton of bills, my trany on my car went, I lost my cell phone, and my computer has pretty much crapped out since I can't get to any of my files... :(

---

### Post by annda on 2007-07-05
in the terminal:

```
sudo fdisk -l
```

find if your drive is really hda1 (compare size). then

```
sudo mkdir /media/my_old_drive
sudo mount /dev/hda1 /media/my_old_drive
```

now you should see the contents of your old disk.

---

### Post by drogers on 2007-07-05
Thanks man!

I'm going to try that out and I'll post the results... If this works out I should be sending you my bonus (provided I get one)... haha

---

### Post by drogers on 2007-07-05
Thanks a lot! It seems to be working...
I don't know how to thank you...

I hope that in the future I'll be able to help someone out similarly to the way you just helped me out... You've saved me at least a year's worth of work.

Thanks again!

---

