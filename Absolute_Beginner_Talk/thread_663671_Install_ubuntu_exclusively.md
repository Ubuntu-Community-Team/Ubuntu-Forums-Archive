---
title: "Install ubuntu exclusively"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by linux phreak on 2008-01-10
Hi friends,I am attempting to install ubuntu exclusively on my system for the second time after a failed attempt.The problem is that i have two hard disks attached and dont know which hard drive to which i have to install ubuntu.Please help me

---

### Post by oldb0y on 2008-01-10
Just install it on one of them.
Btw: How big are they?

---

### Post by linux phreak on 2008-01-10
Thank you. i have one which is 40 gb and other 160 gb

---

### Post by linux phreak on 2008-01-10
If i install on the 160 gb drive what will happen to the other one?.It has XP in it.I dont want it.

---

### Post by oldb0y on 2008-01-10
Well then you can install it on the 40GB, and use the 160GB for other fun stuff:)

---

### Post by linux phreak on 2008-01-10
I purchased an external usb HD today and backedup all stuff which was there and need to make it a part of ubuntu installation.Sorry for the odd explanation.Can it be done

---

### Post by oldb0y on 2008-01-10
You can install Ubuntu on your internal hardrive, and then after you have finished the installation, you can mount the external and transfer everything you need.

---

### Post by linux phreak on 2008-01-10
Thanks.So which drive to install to?.Can i fuse the file system to 200gb total(160+40)

---

### Post by eolson on 2008-01-10
Thats one of the beauties of Linux/Unix,  you can do it any way you want to do it.  The system will let you.

---

### Post by Perpetual on 2008-01-10
Please clarify:

40 GB HDD - Internal
160 GB HDD - External

Edit:  I won't be able to check back on this for a little while.  So, assuming my above scenario is correct, I would:

Disconnect the external.
Install Ubuntu on the 40 GB with the following Partitions (do the manual option at the Partitioning step).
     Partition 1 - 8 to 10 GB /
     Partition 2 - 28 GB /home
     Partition 3 - 2 GB Swap

Then once all is installed, you can plug in the external drive and Ubuntu will mount it and you can read/write to it.

(I have the same set-up at home, different size drives but same scenario.)

---

### Post by oldb0y on 2008-01-10
> **linux phreak said:**
> So which drive to install to?

I would use the 40GB, the 160GB you can keep separate, and when/if you upgrade your system you don't have to worry about messing it up.

---

### Post by linux phreak on 2008-01-10
Ok i have the install screen on the back ground with 4 options.Should i choose use continous free space or should i reformat all the drives to ext3 using Gparted

---

### Post by linux phreak on 2008-01-10
Both drives are internal and i want a complete installation because earlier i installed onto the 40 gb and later i had problems.my music are in 160 one and the library in rythm box would disappear  on each restart and the wallpapers selected from the 160 would not stay there after restart.I dont know why.Sorry for my bad english

---

### Post by oldb0y on 2008-01-10
If you reformat your harddrives, you will loose all your data, keep that in mind. About the other issue, I'm not quite sure, you could make a new thread with that matter in the title, and get more response. Good luck!

---

### Post by Perpetual on 2008-01-10
I would do

Install Ubuntu on the 40 GB with the following Partitions (do the manual option at the Partitioning step).
Partition 1 - 8 to 10 GB / format as ext3
Partition 2 - 28 GB /home format as ext3
Partition 3 - 2 GB Swap

160 GB Drive
Partition 4 - 160 GB /media/MyData (or whatever you want to call it) format as ext3

---

### Post by linux phreak on 2008-01-10
ok i have three partitions in 160 gb So must reformat and rename itself as /media?

---

### Post by Perpetual on 2008-01-10
As I said above, I would put the 3 partitions on the 40 GB and the 160 GB as 1 partition /media/MyData and you could create more partitions there if you want.  I just don't see a reason to break up the 160 with / and /home and swap.  

Just how I would do it and I am sure others would have their own ideas.  Do what you want though, it's a learning experience.  If you don't like it, reinstall.

---

### Post by linux phreak on 2008-01-10
I am having trouble making the 160 gb/media partition .Is it  primary or logical?.please help. I appreciate your help so much.Thank you.

---

### Post by Perpetual on 2008-01-10
> **linux phreak said:**
> I am having trouble making the 160 gb/media partition .Is it  primary or logical?.please help. I appreciate your help so much.Thank you.

I believe you can only have 2 primary partitions?  So, make the /media a logical partition.

Edit: I am not positive on the number of partitions.  I had a problem with it not letting me create 3 if I recall so on my laptop I have:

Primary /
Extended: /home and /media
Swap

It would not let me have / and /home and /media all as primary, hence creating the extended partition and putting /home and /media within.

---

### Post by linux phreak on 2008-01-10
Ok i have done everything as per you mentioned and installed ubuntu.Im so happy now.There is a small niggle though icannot create a new folder in /media/mydata.Why is that.

---

### Post by Perpetual on 2008-01-10
First, check to see what the ownership is by going to /media/mydata

```
 cd /media/mydata
```

and

```
ls -la
```

then

```
sudo chown -R username:username /media/mydata
sudo chmod -R 755 /media/mydata
```

This is off the top of my head and I can't check it at the moment.

Better yet [read this.]("http://www.psychocats.net/ubuntu/mountlinux")

---

### Post by linux phreak on 2008-01-10
Thank you.But i realised that i had chosen all of my partitions as primary(oops) and have decided to reinstall.Sorry for sounding stupid.I have one final question.How do i create an extended partition?I cannot see any options on g-parted and these are two physical drives.

---

### Post by Perpetual on 2008-01-10
That's something I can't explain without doing.  [Here]("http://gparted.sourceforge.net/larry/generalities/gparted.htm") is the gparted documentation that should explain it all.

---

