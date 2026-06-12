---
title: "Installing Ubuntu 7.04 on New Dell with Vista: Any Pointers?"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-06-07
I am about to install Ubuntu 7.04 on a Dell Desktop I just purchased which is loaded with Vista Premium. 

I have found a website which seems to have clear directions:

[http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first](http://apcmag.com/5046/how_to_dual_boot_vista_with_linux_vista_installed_first)

Is there anything I should beware of, or is it straightforward?

Is anyone familiar with the instructions at that website, and are they proper?

Thanks.

---

### Post by swarup on 2007-06-07
One other related question: how do you know whether to use the 386 version or the 64-bit version?

The computer has an intel D925 dual core 3 GHZ chip with 1 GB RAM.  The vista that came with the computer is Home Premium 32BIT. So I assume that I should also use the 32-Bit 386 version of Ubuntu. Is that right?

---

### Post by wormser on 2007-06-07
I  just looked at the directions quickly and they look ok.  The only thing I would add is to defrag the drive before shrinking it.

If you have any questions during the install feel free to ask.

---

### Post by p_quarles on 2007-06-07
The tutorial you have is spot-on. That's exactly what I did, and it works great.

You could research the processor (Intel makes so many processors that I can't keep track of which are 32- and 64-bit), but you should know this: There is not yet a Macromedia Flash plugin for 64 bit systems. If that doesn't matter, then research away. If it does, I understand that some people have had success installing a 32-bit web browser on a 64-bit OS, but I've also heard of people having serious problems with this. The 32-bit version of Ubuntu will run, though, on a 64-bit processor.

EDIT: I second Wormser's point about defragging. Also, make sure you backup all your data. Nothing is likely to go wrong, but you want to be safe.

---

### Post by swarup on 2007-06-07
> **p_quarles said:**
> The tutorial you have is spot-on. That's exactly what I did, and it works great.

You could research the processor (Intel makes so many processors that I can't keep track of which are 32- and 64-bit), but you should know this: There is not yet a Macromedia Flash plugin for 64 bit systems. If that doesn't matter, then research away. If it does, I understand that some people have had success installing a 32-bit web browser on a 64-bit OS, but I've also heard of people having serious problems with this. The 32-bit version of Ubuntu will run, though, on a 64-bit processor.

EDIT: I second Wormser's point about defragging. Also, make sure you backup all your data. Nothing is likely to go wrong, but you want to be safe.

Many thanks to both you and Wormser for your suggestions and help. I feel reassured to know that the tutorial I'm going to use is good. As for defragmenting and drive and backing up data-- let me add that this computer is literally just out of the box. I just now received it, and it's spanking new. Never been used before, and has no data on it. So do you still think I need to defrag the drive before shrinking it?

Thanks again.

---

### Post by silverglade00 on 2007-06-07
I would...

1. Set aside about 1.5 hours and do the whole Vista setup thing. Yes, 1.5 hours.
2. After your nap waiting for the Vista setup, use the partition shrinker in Vista to shrink your partition, not the Ubuntu one.
3. Forget what I wrote and use the instructions you found. They have pretty pictures!







Stupid me not checking the link...

---

### Post by swarup on 2007-06-07
I think I'll probably just go with the 32-bit version. It sounds safer. Is there any down-side to doing that? If a computer has the capacity to run the 64-bit version of Ubuntu, is it a better product than the 32-bit version or what are the advantages of using it? What are the differences in the 32- and 64-bit Ubuntu versions?

---

### Post by p_quarles on 2007-06-07
Yeah, I'd still defrag it. OEM setups of Windows take so long and access the disk so often that I really don't trust them to leave you with a clean install.

Of course, you could just run the defrag utility's "analyze" utility and decide from there. 

One more thing: I only speak for me, but I wish I'd given Ubuntu a bigger partition than I did. I never anticipated how infrequently I would boot into Windows.

---

### Post by swarup on 2007-06-07
> **silverglade00 said:**
> I would...

1. Set aside about 1.5 hours and do the whole Vista setup thing. Yes, 1.5 hours.
2. After your nap waiting for the Vista setup, use the partition shrinker in Vista to shrink your partition, not the Ubuntu one.

This assumes that you want to dualboot.

1. Yes I want to dual boot.
2. I do not understand what you mean about "the Vista setup thing". The computer came with Vista already installed on it. When I turned it on, there was just the usual stuff about setting your user name and pw, setting the clock and stuff. Then it finished booting, came to the desktop and was ready for work. So about Vista setup, what do you mean? Are you suggesting that I uninstall and reinstall Vista? If so, why?
3. Right now I am in the disk management window of Vista, ready to use the partition shrinker in vista to shrink the partition. But I am waiting for your reply before moving ahead. Should I move on with this work, or are you saying that there is something more I need to do first as regards "Vista setup"?

---

### Post by p_quarles on 2007-06-07
> **swarup said:**
> I think I'll probably just go with the 32-bit version. It sounds safer. Is there any down-side to doing that? If a computer has the capacity to run the 64-bit version of Ubuntu, is it a better product than the 32-bit version or what are the advantages of using it? What are the differences in the 32- and 64-bit Ubuntu versions?
My understanding is that in the current versions of Ubuntu, you'll get a *slight* improvement in performance. My processors are 64-bit, and I use the 32-bit version, and have no complaints.

---

### Post by wormser on 2007-06-07
p_quarles he said it is out of the box so he does not need to set up vista.  

Back up if you have any data then defrag.  Just follow the rest of the guide and you should be fine.

---

### Post by durrell on 2007-06-07
Windows comes with so much junk out of the box that I'd suggest deleting some of the spam programs that you aren't going to use, and then defrag. THEN partition. If you don't defrag you run the chance of trying to boot into Windows and getting serious errors about files missing and having to sit through memory tests and other BS. Windows does not like having other OS's on the same hard disk if you don't take the time to do it right..

---

### Post by p_quarles on 2007-06-07
> **wormser said:**
> p_quarles he said it is out of the box so he does not need to set up vista.  

Back up if you have any data then defrag.  Just follow the rest of the guide and you should be fine.
wormser: I think you're confusing me with the other guy. I got that it was already set up

---

### Post by swarup on 2007-06-07
> **p_quarles said:**
> Yeah, I'd still defrag it. OEM setups of Windows take so long and access the disk so often that I really don't trust them to leave you with a clean install.

Of course, you could just run the defrag utility's "analyze" utility and decide from there. 

One more thing: I only speak for me, but I wish I'd given Ubuntu a bigger partition than I did. I never anticipated how infrequently I would boot into Windows.

I see. Ok-- I'll go to the defrag utility and see what sort of picture the "analyze" utility gives.

As for the partition sizes: good point. Actually, it is a 160 GB HD-- fairly sizeable. Because the computer is not actually for my use but a colleague's, I was going to put most of the space with Vista and just a small, say 10 GB partition, with Ubuntu. But I think you're right-- they're also going to come to prefer Ubuntu as they get to know it. Most of that person's work involves sound editing in the windows program, "Sound Forge". But I think they may come to appreciate the audacity application in Ubuntu and start using that instead. So maybe I should give Ubuntu a bigger partition-- say, 30-40 GB.

One question: can Vista see and utilize the space in the Ubuntu partition if space is needed. And can Ubuntu utilize the space in the Vista partition. As I'm thinking about it more, I suppose the answer is probably that Ubuntu can see all the files in Vista but cannot put its own created files on the Vista partition. Is that correct? And as for Vista: I don't know whether Vista can even see the files in Ubuntu, what to speak of utilizing the space.

---

### Post by p_quarles on 2007-06-07
> **swarup said:**
> I see. Ok-- I'll go to the defrag utility and see what sort of picture the "analyze" utility gives.

As for the partition sizes: good point. Actually, it is a 160 GB HD-- fairly sizeable. Because the computer is not actually for my use but a colleague's, I was going to put most of the space with Vista and just a small, say 10 GB partition, with Ubuntu. But I think you're right-- they're also going to come to prefer Ubuntu as they get to know it. Most of that person's work involves sound editing in the windows program, "Sound Forge". But I think they may come to appreciate the audacity application in Ubuntu and start using that instead. So maybe I should give Ubuntu a bigger partition-- say, 30-40 GB.

One question: can Vista see and utilize the space in the Ubuntu partition if space is needed. And can Ubuntu utilize the space in the Vista partition. As I'm thinking about it more, I suppose the answer is probably that Ubuntu can see all the files in Vista but cannot put its own created files on the Vista partition. Is that correct? And as for Vista: I don't know whether Vista can even see the files in Ubuntu, what to speak of utilizing the space.
In a fresh install, Ubuntu can read (but not write to) the Windows partition. Windows can't do anything with the Linux partition There are utilities you can install that will allow you to read/write from both and to both. 

That said, many people just make an extra partition exclusively for files, using the FAT32 file system, [edit] which can be read by and written to from Windows and Linux.

---

### Post by swarup on 2007-06-07
> **p_quarles said:**
> In a fresh install, Ubuntu can read (but not write to) the Windows partition. Windows can't do anything with the Linux partition There are utilities you can install that will allow you to read/write from both and to both. 

That said, many people just make an extra partition exclusively for files, using the FAT32 file system, [edit] which can be read by and written to from Windows and Linux.

It sounds like it may be a very good idea to create an extra partition using the FAT32 file system. That way both OS's could access the space. What would you recommend I do? Are the utilities you mention above effective at bypassing the issue so that there is no need for an extra partition? Or is it better to just hard-wire it with a partition and not try to get by using software? 

And if you think it is better to create an extra partition, then can this be done using the tutorial I am going to follow, or is there some added instruction I would need to seek out. Is it pretty doable using the standard tools?

---

### Post by p_quarles on 2007-06-07
Well... I haven't tried to utilities that allow cross-access, but I also haven't heard any of any problems with them. I know that FAT32 works from firsthand experience. I think either way should work fine. 

Configuration for the latter would also be very simple: just further shrink the Windows partition, and add a new volume. Then you go to the "Computer" window and format the new volume as a FAT32.

---

### Post by swarup on 2007-06-07
> **p_quarles said:**
> Well... I haven't tried to utilities that allow cross-access, but I also haven't heard any of any problems with them. I know that FAT32 works from firsthand experience. I think either way should work fine. 

Configuration for the latter would also be very simple: just further shrink the Windows partition, and add a new volume. Then you go to the "Computer" window and format the new volume as a FAT32.

I see. That sounds easy enough. 

I've been looking for where you can give the order to add a new volume, but haven't found it. Right now the HD is getting defragged. Once it's done, I'll shrink it. Then, I suppose will be able to click on the empty space thereby created, and take part of it to create a new volume. Is that done by just right-clicking on the empty space?

And once I do this, then will the Ubuntu disc understand that there are going to be three partitions, and leave the two alone which I 've created, using the empty space to create its partition?

---

### Post by p_quarles on 2007-06-07
> **swarup said:**
> I see. That sounds easy enough. 

I've been looking for where you can give the order to add a new volume, but haven't found it. Right now the HD is getting defragged. Once it's done, I'll shrink it. Then, I suppose will be able to click on the empty space thereby created, and take part of it to create a new volume. Is that done by just right-clicking on the empty space?

And once I do this, then will the Ubuntu disc understand that there are going to be three partitions, and leave the two alone which I 've created, using the empty space to create its partition?
It's been a while since I did it, but I think you're right. Either you right-click on the empty space, or a new button shows up that allows you to add a volume. 

And, yeah, Linux's Gparted partition manager is pretty good at differentiating between Windows-assigned partitions. During the install process, though, you should just watch out for any discrepancies between the volume sizes you expected and the volume sizes Gparted gives you.

---

### Post by swarup on 2007-06-07
> **p_quarles said:**
> It's been a while since I did it, but I think you're right. Either you right-click on the empty space, or a new button shows up that allows you to add a volume. 

And, yeah, Linux's Gparted partition manager is pretty good at differentiating between Windows-assigned partitions. During the install process, though, you should just watch out for any discrepancies between the volume sizes you expected and the volume sizes Gparted gives you.

Ok, great. thanks.

---

