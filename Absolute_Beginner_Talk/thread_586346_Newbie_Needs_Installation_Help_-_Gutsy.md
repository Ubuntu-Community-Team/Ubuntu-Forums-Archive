---
title: "Newbie Needs Installation Help - Gutsy"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by keech on 2007-10-22
Hi All,

I wolud like to try out Ubuntu 'Gutsy' on my desktop. I am new to the Linux environment. I am presently using Win XP and want to migrate to Ubuntu eventually, knidly help me with installing Gutsy. 

Firstly let me give my sys breakup

AMD Athlon 64 X2 +4000, 
1GB RAM (128 MB shared for Graphics),
Single 160 GB Hard disk (Partition 40GB,40GB,80GB) Fully NTFS Formated by Win XP,
Gigabyte MB (GA-MA69VM-S2) with Integrated ATI™ Radeon™ X1200-based Graphics Engine
Other standard components

I want to know how I should go about my installation like when I try to install should I use Manual partion or guided

I want to dual boot and want to provide 20 GB and 2 GB Swap drive for Ubuntu from the 80 GB partition .

I just want to know how to go about the installation with this system and such Hard Disk allotment.

Also kindly tell me whether Compiz Fusion work on this system.

Thanks in Advance

Mohan :)

---

### Post by realvz on 2007-10-22
read this guide..

[http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)

let us know if you still have questions.

---

### Post by keech on 2007-10-22
Thanks realvz, but the installation tells me about 7.04 and not 7.1 and in 7.10 the intial partition screen is different. 

I wish to know how I can go about doing it Manually with the 20 GB for ubuntu and 2 GB for Swap in 7.10 and configuring Dual Boot using GRUB

These are my major concerns. It will be helpfull if someone can put some screen shots. The 80 GB is NTFS drive and completely empty I have Win Xp in my 40GB partition.

---

### Post by realvz on 2007-10-22
well...partitioning and stuff is no different in 7.04 than 7.10..so the tutorial still works fine..all you have to do is use 7.10 CD instead of 7.04.

In fact I just used the same tutorial last night to partition and install my wife's laptop with XP and Gutsy.

---

### Post by keech on 2007-10-22
But your a Expert in Ubuntu and I am not, unfortunately I am only exposed to Win environment till now, I just want to know what to select in the Manual partitioning steps after the partion it is asking me Mount or Main disk and things like that, this is giving me doubts.

---

### Post by lonesomecrow on 2007-10-22
yeah partitioning is the same on both versions, just if you get to the part where you have to do it manually and asks for the size of the new partition, there is a tip next to the input box that says 1MB=1000000 or something like it, ignore it as you really dont need it, just put the number of MB that you want for the new partition, i.e. for 40 GB of the 80GB partition just enter 40000.

---

### Post by realvz on 2007-10-22
you know what if you absolutely wanna learn partitioning and do not want 1% risk..
i recommend you download VMWARE and try your hands on ubuntu partioning options in there...then you will become hands on with this..

VMWARE is free and easy...

---

### Post by keech on 2007-10-22
I also need some clarification in the following

My HD is partitioned as 40GB, 40GB and 80 GB
In that my first 40gb has the Windows i dont want to disturb it, I want to install Ubuntu in my last 80GB. 
1.) Suppose if I choose the first option in partition screen, ie let Ubuntu manage the partition, i just choose the disk space allotment with the help of the slider, then will my initial partition with Windows get affected or will it automatically resize my empty partition of 80 GB
2.) If I want to dual boot using GRUB must I necassarily use the first option or can I use manual partition also, in this if I use manual partition should I have to change any GRUB settings afterwards for the installation to take place.

Kindly advice

---

### Post by realvz on 2007-10-22
The default recommendation for the new partition size is optimal, but you can move the slider up and down to change it as you see fit. If you&#8217;re feeling brave, you can also manually edit the partition table, but unless you&#8217;re really confident about what you're doing, this isn&#8217;t recommended.

Click Forward to continue.

Ubuntu now has enough information to install, so click Install and go make a coffee.

When the install is complete the system will reboot. When the GRUB boot menu is displayed, have a look at the last entry in the list.

After the Ubuntu boot options, there will be an entry &#8220;Other operating systems&#8221; and beneath that &#8220;Microsoft Windows XP Professional&#8221; (or Home, whichever version you&#8217;re using). By default Ubuntu will load itself after 10 seconds.

---

### Post by keech on 2007-10-22
That is a bit clear ok tell me if the whole slider shows 80GB and optimal is at 50% which side I have to slide to make it 20GB to ubuntu and rest to general partition ie should I choose 25% or 75% bcos in some forums I read that the slider is for allotment towards free hard disk space and not towards Ubuntu, I hope I am making myslef clear here.

---

### Post by realvz on 2007-10-22
1.) i thought you have 40+40+80 = 160GB HD, how does the slider only show 80GB?
2.) anyway can you see what options and entries you get when you click manual install? and post them here

---

### Post by keech on 2007-10-22
Now I think you are gettting me the slider is in the default 50% and shows 40GB that is the reason for my confusion

when I make the manual partition I have 3 partition showing in it

---

### Post by realvz on 2007-10-22
can you post the details about those partitions.

---

### Post by keech on 2007-10-22
40gb, 40 Gb 80gb

---

### Post by realvz on 2007-10-22
i m getting a bit confused here and dont want to mislead you...can you post a screenshot of the window for manual partition and automatic guided one...thanks

sorry its taking some time...but i just want to be sure it works.

---

### Post by keech on 2007-10-22
I have to apologies to you for taking your valuable time, pls give me some time I will take the screen shot and post it here. It is good to have people like you to help us. I whole heartedly appreciate your efforts.

---

### Post by merlinDwizzard on 2007-10-22
I'm kinda new myself, but i have done this. A dual boot inspiron 1100 with xp and feisty and a triple boot aspire 5601 xp vista gutsy. 80 gig seems a lot to me. But it depends on what your wanting to do with it. Ubuntu does well on smaller partitions. One good thing is gutsy has a partion manager you can easily access from the live cd under >system if you want to make it smaller before you start you actual install. good luck

---

### Post by keech on 2007-10-22
Let me ask you looking at my configaration will Compiz Fusion work on my sys. Just your thoughts

---

### Post by keech on 2007-10-22
Realvz, See I tried to adjust the partitions now it is showing like this, the 'free space' is neither appearing in WinXP or Ubuntu file manager and the 'partition editor' in the 'system menu' is not able to start at all it just in the screen Scanning all devices
I am posting a Screen shot as requested
[[IMG]http://imgbolt.com/public/thumb_471d6c62d423a709764861.png[/IMG]](http://imgbolt.com/public/pview/33425/Screenshot.png)

[[IMG]http://imgbolt.com/public/thumb_471d6d0fe1980583635399.png[/IMG]](http://imgbolt.com/public/pview/33426/Screenshot-1.png)

[[IMG]http://imgbolt.com/public/thumb_471d6e32142b9209804910.png[/IMG]](http://imgbolt.com/public/pview/33427/Screenshot-2.png)

---

