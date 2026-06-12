---
title: "Trying to use gparted for partition, but screen not working"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-08-17
I am trying to set up a dual boot with XP and Feisty, and I have XP already on the HD. The Feisty live CD is not giving me an option to create two partitions for a dual boot, so I downloaded the gparted live CD. I put it in the computer and booted it up. The gparted software is starting to work, but then keeps telling me there are "no screens found" to work with its graphical interface. So it recommends me to run the script "Forcevideo" and then select a video driver and resolution. It even tells me which  video driver (vesa) and resolution (1024x768) to select. But selecting those at the prompts, it then proceeds to tell me that, "Fatal server error: no screens found".

I think it is also saying, "Vesa: No matching modes"
It also says, "Screens found, but none have a usable configuration"

My screen works just fine. And it boots up to windows just fine. So why won't it work with gparted???

---

### Post by reckless2k2 on 2007-08-17
give us a make and model....yadda.

---

### Post by swarup on 2007-08-17
> **reckless2k2 said:**
> give us a make and model....yadda.

I am using a Dell Dimensions 3000 Tower, and a Dell monitor. 
It is the latest live CD of gparted.

In the gparted screen, it says the monitor is "Generic Moniter, H:28.0-96Hz, V:50-75.0Hz"
And it says the Video is "Intel Corporation 82865G Integrated Graphics Controller, using Xorg (i810) Server"

---

### Post by swarup on 2007-08-17
Could someone tell me what is the way to shrink the Windows partition in XP? That is all I need to do, to finish this work of setting up a dual boot with XP and Feisty. I did not think it was going to be so difficult to set up a dual boot with XP and Feisty. It was easy to do on computers with Win98 and also on computers with Vista. Why is it so difficult shrink the XP partition? Others who've done it, how did they do it?

I would think that gparted would be a good way, but I can't get it to boot up and run!

---

### Post by DarkW0lf on 2007-08-17
If you have the latest gparted you should have got the message to use ForceVideo script to start Vesa support for X

type ForceVideo in the shell prompt and then VESA when prompted and see if that works.

---

### Post by swarup on 2007-08-17
> **DarkW0lf said:**
> If you have the latest gparted you should have got the message to use ForceVideo script to start Vesa support for X

type ForceVideo in the shell prompt and then VESA when prompted and see if that works.

That is exactly what I did. 

And I've repeated it fifteen times-- Vesa, and also with just about every other video driver they list there as an option. (such as ati, sis, vga, etc) . Nothing seems to work. I don't know what to do. Isn't this gparted just supposed to boot up in a straightforward way and do its job?

---

### Post by yorkie on 2007-08-17
On your live cd you shold have the option to Manually edit partition  you can resize windows partition and create patitions for ubuntu.

---

### Post by louieb on 2007-08-17
Normally the GParted live CD is what I use when I need to partition. But I had the same problem on the last pc I wanted to partition. Gparted live cd never did give me a GUI. I ran GParted off of the [SystemRescueCd]("http://www.sysresccd.org/Main_Page")  to get around the problem.

---

### Post by Paul133 on 2007-08-17
The Feisty Installer should give you an option to manually edit partitions.

---

### Post by swarup on 2007-08-17
The suggestions offered above are all good. But I've tried them already, without success.

1. After I could not get success with the gparted live CD, I download and burned a copy of the rescue CD, but it also gave me similar problems. I tried to open gparted from that cd and it would not open. I also tried to open qtparted from that rescue cd and it would not open. I must be doing something wrong, but I do not know what it is.

2. It is true that there is the option for a manual partition editor in the Feisty installation editor. But it is not self-explanatory how it works.

I would like to downsize ntfs to about 20GB, leaving me about 55GB for Ubuntu.

Here is what the partition menu in the manutal installer says:
/dev/sda1 fat16 /media/sda1 41MB(size)/ 33MB(used)
/dev/sda2 ntfs /media/sda2 76264MB/8500MB
/dev/sda3 fat32 /media/sda3 3684MB/3200MB
free space 8MB

So I guess I need to downsize the ntfs to 20 GB, and then I would need to create another partition for the feisty partition? How is that done? Or is one of the above already meant for it?

And the install partition manager says: I need to "specify a partition for the root system file (mount point "/") with a min size of 2 GB, and a swap partition of at least 256MB"

If someone could translate all this into English, I would do it.

---

### Post by louieb on 2007-08-17
When using the system rescue CD you right click on the icon for the program  you want and select on forgot which open or run.
> **swarup said:**
>  ...And the install partition manager says: I need to "specify a partition for the root system file (mount point "/") with a min size of 2 GB, and a swap partition of at least 256MB"
If someone could translate all this into English, I would do it.
What that means is after you shrink your NTFS partition  You need to create two (2) partitions in the unallocated space.  One for the install and one for swap. You can have up to our (4) primary partitions. You already have 3. 
So how do you add 2 more? 
Extended and logical partitions is how you do it.  [Nuts n Boldt: Partitions 101]("http://louboldt.com/ilinuxpart.htm")
for example say you have 20GB of unallocated space. 
1st you create an extended partition using all 20GB of unallocated space. 
Next you create the 2 logical partitions inside the extended partition. 
Since I'm lazy I would create the swap partition next make it about 512MB or so. and last create the / (root) partition using all the remaining space. 

When you install: at the partitioning section choose manual partitioning. The 1st screen is the partitioner. If you already set up your partition don't do any thing here **click next** Now you set your mount points. If you used my suggestion sda5 should be your swap partition and sda6 should be you / (root) partition. Used th drop down boxes  and tell the install which partition to use for / and swap.  I know this is clear as mud but you'll just have to wallow through it. :)

---

