---
title: "Partitioning question"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by Bigguy2468 on 2006-09-04
Well I just installed ubuntu on my home computer and I love it. Up until this point I have been using Mandriva 2006 dual booting with Windows XP. What I did is using the partitioning utility I deleted the Linux partitions and left the NTFS partition. Then I created a new Linux ext3 and swap partition and continued to install. During the installation of GRUB ubuntu recognized Windows on the NTFS partition and included that as an optional boot OS. So, everything is great on the home computer. Now, my work computer is exactly set up the same way with XP and Mandriva 2006 on a dual boot setup. My home computer has nothing of importance so I am always willing to take more risk with it, but not the work computer.

Did I follow the proper procedure for doing this. If I break the home computer, who cares, but if I break the work machine I am up the creek.
](*,)

---

### Post by bodhi.zazen on 2006-09-04
> Did I follow the proper procedure for doing this.

Short answer: yes.

Longer answer: you are wise to use a test system at home.

I have a simmilar setup, on my "production" OS I try to avoid ANYTHING without testing. This includes updating (see recent ubuntu problem with X after update) as well as new configuration or program.

I do this vis 2 partitions on my HD, larger production and smaller test. That way I know any update or isntall works on my production box.

---

### Post by meng on 2006-09-04
Your procedure is absolutely correct.
Nevertheless, you ought to have your critical data backed up at all times, and especially before something like a repartition (even though you're leaving the NTFS partition alone). Remember the definition of onosecond: the time that elapses between deleting all your data and realizing what you've done.

---

### Post by whizbaby on 2006-09-04
What are you afraid of ?(or don't you do backup of important informations? Then just start doing this, remember that one day your HD *dies*! If you store work-data I recommend buying a second hard drive used ONLY for backup )

---

### Post by b_martinez on 2006-09-04
So far you have it all okay. If you are going to do the work computer, make sure you back up everything. That includes your Windows stuff. Just in case you ever do the partitioning again, you may want to consider a different partitioning scheme. Try a more advanced scheme:
a root partition - /
a swap partition - /swap
a log partition  - /var
and a home partition - /home
root for the core of the OS
swap for memory
var - holds system logs, and keeps root from filling up
home for all the stuff you want to keep. Music, Pix, settings , and so on.
With the cost of hard drives dropping, it should be fairly simple to get a large drive.
hth
Bill

---

### Post by bodhi.zazen on 2006-09-04
> **b_martinez said:**
> So far you have it all okay. If you are going to do the work computer, make sure you back up everything. That includes your Windows stuff. Just in case you ever do the partitioning again, you may want to consider a different partitioning scheme. Try a more advanced scheme:
a root partition - /
a swap partition - /swap
a log partition  - /var
and a home partition - /home
root for the core of the OS
swap for memory
var - holds system logs, and keeps root from filling up
home for all the stuff you want to keep. Music, Pix, settings , and so on.
With the cost of hard drives dropping, it should be fairly simple to get a large drive.
hth
Bill

Why? I could see /home, but it is not as if he is running a server.

KISS- Keep It Simple Stupid.

---

### Post by Bigguy2468 on 2006-09-04
Well, all of the data is protected already on a second hard drive. I always disconnect that HD before installing Linux anyway. The problem for me is just the programs I run. I have a Contact Management program running on 2 machines and my work computer acts as the server for the program. You know, it's just the hassle of having to reinstall everything.

I did try it on the home computer first and all went well, but sometimes I have gotten something to work and found out later that I didn't follow proper procedures. I just wanted to hear from you guys and gals that I did follow the proper procedure for ubuntu.

I had gotten myself to the point with Mandriva that I felt comfortable with the install, but ubuntu is new to me, you know, it's just the unfamiliar butterflies you get when you try something new. Seems that the overall consenses is that I did follow the right procedure so I will give it a try and report back.

Thanks!

:D

---

### Post by cotcot on 2006-09-04
Why /home ?
Backup a separate /home partition is easy (partimage).
If you want to do an upgrade or a reinstall you do not need to risk  your /home data.

---

