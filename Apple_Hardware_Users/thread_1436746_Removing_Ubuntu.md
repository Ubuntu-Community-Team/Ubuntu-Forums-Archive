---
title: "Removing Ubuntu"
date: 2010-03-23
forum: Apple Hardware Users
---

### Post by shinderhizzle84 on 2010-03-23
Hello. I'm having some problems with my Ubuntu installation on my Macbook Pro, so I'd like to remove it. However, I can't get back my full hard drive, because when I'm on Mac OS X, it doesn't recognize the Linux partition at all.

I just want to make sure that if I delete the partition with Ubuntu on it, when I load my Mac, I'll have 185 GB free, and not 35.

How would I go about doing this?

Thanks :P

---

### Post by thebigob on 2010-03-23
Use ubuntu to format the partition you have made to unallocated space.

This will then be recognised by your mac.

You will then have to grow your current file system onto it.

This will result in one mac disk.

If you do not grow the filesystem you will still be able to acess the partition but it will effectivly be another disk, which by the sound of it is not what you are looking for.

Steps Summary:

```

Use ubuntu to remove current partition - this will then show as unallocated space.

Use mac to grow existing partition onto the new unallocated space - note you may need to create a partition then grow this.

```

Hope this helps

---

### Post by shinderhizzle84 on 2010-03-23
I just want to be able to un-partition my hard drive so all 185 GB are used up my mac os x, not split into 2 like it is currently.

Will this work? I want to make sure I have enough HD space that is actually recognized by Mac OS X.

---

### Post by Falconer 2010 on 2010-03-23
> **shinderhizzle84 said:**
> I just want to be able to un-partition my hard drive so all 185 GB are used up my mac os x, not split into 2 like it is currently.

Will this work? I want to make sure I have enough HD space that is actually recognized by Mac OS X.

Using Mac OS X, go to Disk Utility. Select your DISK (not your volumes), then select Partition. Find the partition that is called 'disk0s3' or something very similar.

Then at the bottom of the diagram, there is a - button. Click that then drag your OS X volume to fill the entire space.

---

### Post by shinderhizzle84 on 2010-03-25
> **Falconer 2010 said:**
> Using Mac OS X, go to Disk Utility. Select your DISK (not your volumes), then select Partition. Find the partition that is called 'disk0s3' or something very similar.

Then at the bottom of the diagram, there is a - button. Click that then drag your OS X volume to fill the entire space.

This doesn't work.

Whenever I use Disk Utility to do this, either from the Mac OS X Installation disk or from my mac os x installation itself, Disk Utility gets stuck on "Preparing to Erase Volume" or something like that.

I waited for almost an hour and a half and it still had not progressed whatsoever. 

What does this mean and is there any other way to remove my ubuntu installation?

---

### Post by shinderhizzle84 on 2010-03-27
Bump, because I seriously need help.

Sorry if this annoys anybody.

---

### Post by CJN on 2010-03-27
No prob! I dealt with this exact problem recently, what you NEED TO DO is grab a live CD/DVD and pop that in, load up the desktop from the disk and use gparted to DELETE THE LINUX PARTITIONS (everything after the OS X partition probably, I assume you don't have windows on there too) then once everything is deleted (do NOT make new partitions, just leave as blank space) boot back into OS X and then disk utility will be able to reclaim the space as expected.

Hope this helps.

---

