---
title: "creating an image"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by RudolfMDLT on 2007-01-10
Hi there, 

I need to create an image of a drive running Ubuntu server on it. There is no GUI so for a MCSE(Mouse Click System Engineer :) ) this is quite a task.

How could I do this? I know how to backup using tar but I need an Image.

Any help will be very much appreciated!

Thanks,

Rudolf

---

### Post by aysiu on 2007-01-10
[http://www.psychocats.net/ubuntu/partimage](http://www.psychocats.net/ubuntu/partimage) may help.

You could also use *ddrescue* to make a .img of your partition.

---

### Post by RudolfMDLT on 2007-01-10
Thanks aysiu,

I have used your guide on a couple machines. Thanks. But is there no way of imaging a drive onto itself - in other english, save the image of drive hda1 onto hda1?

---

### Post by aysiu on 2007-01-10
I think that's what the *tar* back-up would be.

Any chance you could create a new partition as a place to host the back-up image?

---

### Post by RudolfMDLT on 2007-01-10
Suppose I could - I just thought about it. If you save an image to the drive you are imaging, wont you also image the image and then continue in and endless image of the image of the image... until the drive is full?

I'll try that thanks!

---

### Post by MkfIbK7a on 2007-01-10
> **RudolfMDLT said:**
> Suppose I could - I just thought about it. If you save an image to the drive you are imaging, wont you also image the image and then continue in and endless image of the image of the image... until the drive is full?

I'll try that thanks!

lol some paradox!:mrgreen:

---

### Post by RudolfMDLT on 2007-01-10
:) 

It is, ain't it. Thats why when you tar / you have the exclude command so that you don't start backing up the back up! (Feel like such a noob)

---

### Post by Voxxi on 2007-01-10
> **RudolfMDLT said:**
> :) 

It is, ain't it. Thats why when you tar / you have the exclude command so that you don't start backing up the back up! (Feel like such a noob)

I did that once. Was performing a / backup, set the tar command , and left it for a day. It used up ALL my hard drive space because I had neglected to use exclude. ](*,)

---

### Post by Frank Golden on 2007-01-10
[http://www.ubuntuforums.org/showthread.php?t=287522](http://www.ubuntuforums.org/showthread.php?t=287522)

See this for info on partimage included with the System Rescue CD.

If you can make a partition for your backup on the same drive do it.
Everything will be much quicker. Fat32 or ext3.

The rescue CD has all kinds of neat tools on it. The latest version v0.3.0
Even has Firefox on it so you can access the internet if needed.
You do need to run the setup command at the prompt ```
net-setup eth0
```
as the net isn't setup automatically. To use FF type ```
startx
```

---

### Post by RudolfMDLT on 2007-01-11
Thats very cool!

---

### Post by Frank Golden on 2007-01-11
> **RudolfMDLT said:**
> Thats very cool!
I just finished (using the directions on their site) customizing my copy of
System Rescue CD. I set up Firefox to open to google.com and migrated my
bookmarks. After creating a new customized image I installed on a 1GB Cruzer Titanium
again using the simple instructions on Sysrescue CD's web site. I now have a bootable
thumbdrive version of Sysresccd. My computer can boot off almost anything.
Loads and runs much faster than CD.

Update: the latest version is v0.3.2.

---

