---
title: "Online now via LiveCd re: home in it's own partition"
date: 2008-04-16
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2008-04-16
I'm online via LiveCd

I'm trying to follow 

Psychocats:

 Create a separate home partition in Ubuntu
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I've got GParted up, I've written down (on paper) all the /dev/sda1 /dev/sda2, /dev sda5 stuff and the current sizes.

I tried to Move/Resize in GParted, but when Psychocats description shows

Choose the new size you want, Then in the empty space, right click and select New

I can't right click to see the word: New. That is, I right click but don't get a menu of choices, one of which is New

Anybody out there done this and is familiar with the steps?

---

### Post by bumanie on 2008-04-16
I'm slightly confused with exactly where you are up to. Could you state which partition you want you moved /home to go to. As you have gparted up and running, could you post a screenshot of your drive/partition layout.

---

### Post by Mark_in_Hollywood on 2008-04-16
I'm posting the screenshot you asked for.

Could you please open the link I posted above from Psychocats

I'm on page 3 (as it prints on paper)

The top of the page reads:

Choose the new size you want.

---

### Post by philinux on 2008-04-16
I did this a while back, memory fades a bit. Looks like at the moment you've no spare space so you need to make some by right clicking in the box of sda1 and choose resize to make it smaller. I think my root partition is 20 gigs this left the rest of the disk for home.

---

### Post by Mark_in_Hollywood on 2008-04-16
GParted says I have approx. 257 gig unused.

How do I make that partition for the 257 gig?

That is to ask: How do I make a partition that in size is 257 gig, and not change the order or the sizes of 

dev/sda2 extended 2.89 gig

and

/dev/sda5 linux-swap 2.89 gig

???

---

### Post by bumanie on 2008-04-16
Please be aware that partitioning is not 100% safe, so I hope you backed up anything vital first. Having said that, I've never had a filesytem destroyed by gparted - but if you happened to have a momentary power outage, goodbye filesystem. I am at work and cannot print anything out, but I have found the spot you are up to. The screenshot is helpful, a visual of you hard drive indicates that you have missed one important step. 
What you need  to do is right click in the space of the rectangle sda1. This should give you a drop box  where you can left click on Resize/Move. You can then use a slider to reduce the size of sda1 and should be left with unallocated space. Right click on the unallocated space and then you should be given the option to choose 'new'. From there you can format the unallocated space to ext3 and make your /home partition which gparted will probably lable sda6. From there you can follow the rest of the psychocats tutorial which will be command lines in terminal.
Just as a side issue, you can delete that blue extended partition if you wish (personally I would, but its up to you), but on the other hand its not doing any harm. If you ever have to reinstall ubuntu, keep in mind the point that you can choose manual at the partitioning stage and create a separate /home on a new installation (you may have discovered this already). Hope this sorts you out.

---

### Post by philinux on 2008-04-16
Just had a look at gparted on my system.

You click on the partittion to resize then right clik and choose the resize option.

The unused its reporting is just spare disk space within the partition.

---

### Post by Mark_in_Hollywood on 2008-04-16
NUTS

I've followed your lead.

GParted has been trying to

Move /dev/sda1 to the left and shrink it from 295.20 gig to 39.56 gig.

for about 10 minutes now. What is a normal length of time for such an operation?

---

### Post by bumanie on 2008-04-16
Because there is a file system on sda1, gparted can take considerable time - remember it has to keep all those bits and bytes etc in order for you to have a useable system at the end. Last week I used it to resize some partitions (3 operations in all), it took 7-8 hours. For what you are doing, i'd expect at least 2 hours, may be more. The empty space with no file system will only take a few minutes.

---

### Post by Mark_in_Hollywood on 2008-04-16
Thanks, community. 

This is getting a little too hairy for me. I'm not so experienced with partitioning that I'm confortable. 

I canceled the partitioning operation and am leaving the Live CD session, if everything is OK, I'll mark this thread solved.

---

### Post by philinux on 2008-04-16
When I did this I copied home on to a usb stick. Like bumanie said it can take time but it's worth it. Reinstalls are a doddle.

---

### Post by bumanie on 2008-04-16
Cancelling partway is not seen as safe. I hope your filesystem is OK.

---

### Post by kshane on 2008-04-16
> **Mark_in_Hollywood said:**
> Thanks, community. 

This is getting a little too hairy for me. I'm not so experienced with partitioning that I'm confortable. 

I canceled the partitioning operation and am leaving the Live CD session, if everything is OK, I'll mark this thread solved.

Resizing or moving large partitions takes a while.  Much longer than 10 minutes.

You're making this more difficult than it needs to be.

Kevin

---

### Post by Mark_in_Hollywood on 2008-04-16
[QUOTEYou're making this more difficult than it needs to be.

Kevin[/QUOTE]

HOW ON EARTH WOULD I KNOW THAT?

---

### Post by Mark_in_Hollywood on 2008-04-25
I have my entire /dev/sda1 "recovered". By allowing GParted to perform it's "test" function, it has found the multiply-claimed blocks in inode: xxxxx and the 320 gig drive is all good.

I had four or five different posts regarding the problem over the course of several weeks. 

Thread Closed -- Ubuntu Success!!!

---

