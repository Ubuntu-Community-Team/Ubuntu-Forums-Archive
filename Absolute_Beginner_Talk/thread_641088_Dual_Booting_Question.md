---
title: "Dual Booting Question"
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by jumboshrimp11 on 2007-12-15
Okay, so I installed Ubuntu in a dual boot with Vista Home Premium, and it is working quite excellent. Now, after using it for a couple of weeks, I've decided that I would really like to start using Ubuntu as my main operating system. But, the 25 gigs of space that I was allowed to partition during the install process  is just not going to be enough. So, my question is this: Is there any way to increase the size of the Ubuntu partition and decrease the Vista partition? And how would I go about doing this? Thanks!

---

### Post by siciliancasanova on 2007-12-15
I would use the gParted live cd.[http://gparted-livecd.tuxfamily.org/]("http://gparted-livecd.tuxfamily.org/")

Once it's running, resize the Windows partition and grow the Ubuntu partition.

If I'm correct you will be moving the Ubuntu Partition to the left after you decrease your Windows partition.  This will take quite a bit more time to do because it will be copying information.

---

### Post by jumboshrimp11 on 2007-12-15
Awesome! I shall try that
Thank you!

---

### Post by autocrosser on 2007-12-15
Why are you needing more than 25G? Music/video/?  In any case, what I would do is install a second drive & make it your /home---there is a very good HowTo in tutorials about that & you would need to do the /etc/fstab edit as outlined there also....

That way you have the 25 for your system & you can grow your /home as big as the drive you install....

---

### Post by Partyboi2 on 2007-12-15
If you run into a problem with gparted not being able to resize Vista, you may need to resize it with the resizing tool that comes with Vista.

---

### Post by rsambuca on 2007-12-15
Do not use gParted on your Vista partition.  While some people have had success, there have been a lot of reports of problems booting afterwards.  It is much safer to use Vista's Disk Manager to Shrink the Vista partition first, and then expand the Ubuntu partition with gParted. 

Like a previous poster though, I am really curious as to why you would require more than 25GB for Ubuntu.  I have a ton of stuff loaded and it is still less than 4GB.  Media files can be shared with Vista if you need to.

---

### Post by siciliancasanova on 2007-12-15
> **rsambuca said:**
> Do not use gParted on your Vista partition.  While some people have had success, there have been a lot of reports of problems booting afterwards.  It is much safer to use Vista's Disk Manager to Shrink the Vista partition first, and then expand the Ubuntu partition with gParted. 

Like a previous poster though, I am really curious as to why you would require more than 25GB for Ubuntu.  I have a ton of stuff loaded and it is still less than 4GB.  Media files can be shared with Vista if you need to.

Thanks for that, I did not know Vista was partial to its own partitioner.  However, I should have just assumed.  I do agree with the two above posts.  I would shrink vista and leave your root ubuntu partition the same while using the free space to create a partition for your files.

---

### Post by jumboshrimp11 on 2007-12-15
Okay then, Vista partitioner it is! Thanks everyone!
Oh, and it's not so much that I need the extra hard drive space, it's just that I dislike the idea of Vista sitting over there, not being used, and claiming 175 gigs of my hard drive space. If I'm going to start using Ubuntu for everything, I really want to be able to use all my hard drive.

---

### Post by seventhc on 2007-12-15
You should be able to write to the vista partition from ubuntu. I used to always do that until I got rid of windows completley, but when it was there, I used it for storage, thats basically why I decided to get rid of it. I was never booting into it and always transferring files to it. Even on my brand new laptop (it's a week old) Vista was gone on the first day but I did still create the back ups since they didn't give me the disks but I doubt I will install it again. I actually did install it just to verify that my backups worked and it took hours to install only to be wiped 2 minutes after i saw it was successful. lol

---

