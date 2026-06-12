---
title: "dual boot"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by saintj0n on 2006-10-21
Ok..
Please forgive me if I am asking a frequent question... I have installed ubuntu on a pc  and now would like to install win 98 (as an alternative boot option). If I could cut off a chunk of the Linux partition as a small place to run windows programs. Running it from inside linux isnt an option, the user doesn't have any concept of how to use linux. I have heard that this is hard to do because win98 tries to take over the file allocation table. Any thoughts?

---

### Post by james99 on 2006-10-21
As a noob, the easiest way for me would be to,
Install 98 over the whole HD.
Then reinstall ubuntu with dual boot.
This is providing you dont mind reinstalling ubuntu.
Hope this helps somewhat, gotta be a million years of experience on this forum and there will be another way out there.

PS. just patented "a million years of experience".

---

### Post by louieb on 2006-10-21
One thing you might consider is getting a second hard drive. There are lots of small 3 to 10 gig drives on the used market for under ten bucks. 
And there are a lot of post and howto's on how to install the drive, put windows on it and modify the grub configuration file. That is how I added xp to one machine.

---

### Post by saintj0n on 2006-10-21
not sure what the best way to go is going to be just yet. I don't want there to be much more than push 1 for linux or 2 for win 98. My 4 year old will be using it to play his games and he cant do much more than point and click type decisions. I tried installing ubuntu after win 98 but couldnt figure out a way to resize the partition without destroying the win 98 data. So, maybe I can break off a partition for win 98?

---

### Post by Kateikyoushi on 2006-10-21
You can try to resize the partition from the live disc and install 98, then you have to install grub again, but it can be done in a few minutes.
If you fail you can still try to install ubuntu after 98.
The two hard drive solution is the safest for you, but if you are willing to invest time in it you can do without.

---

### Post by Bartender on 2006-10-21
saintjon -
You've got a Dapper CD, right?  Install Win98.  Take a look at [this]("http://www.psychocats.net/ubuntu/installing") guide.
See where aysiu is describing partitioning?  That's Step 6 of 7, "Prepare Disk Space".  He describes the typical Windows dual-boot pretty thoroughly.
That might be easier than figuring out how to do it "backwards".  By backwards, I mean installing Ubuntu first.
EDIT: Once you've got this set up correctly, your PC will open to a B&W GRUB screen asking which OS you wish to load.  You can set up Windows or Ubuntu as the default OS.  Tapping "Enter" or just waiting out the countdown will boot the default.  But to get to the other OS, your young computer operator will have to be able to key down the list, using the "down" arrow key.  Will that be acceptable?

---

### Post by saintj0n on 2006-10-21
Actually, I've got a hoary hedgehog cd and a dapper dvd. My little one's pc is not equipped with a dvd -ROM. That's okay, I can up the kernel version later. I do wish that I had a disk with edubuntu on it though. I had a ubuntu disk sent to me in the mail about three months ago and I can't remember how I did it now. I remember when I installed dapper from dvd on my pc it seemed like the partitioning went a lot more smoothly. Ah well, it worked and I got it figured out. I actually have a little 30 Gig HDD at my parents house and I will put windows on it. I figure win98 is a bigger resource hog, it needs the bigger size.....

---

### Post by AndyCooll on 2006-10-21
See the link in my signature, that's a good place to start.

:cool:

---

