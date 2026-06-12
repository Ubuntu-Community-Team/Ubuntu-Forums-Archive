---
title: "Reinstalling and in need of advice"
date: 2008-01-10
forum: Absolute Beginner Talk
---

### Post by MaxVK on 2008-01-10
Hi.

I'm desperately trying to get Ubuntu working properly and I fear that my messing about has broken something, so I plan to reinstall it, however, being very new to this there are a few questions that I need to have answered before I start.

1)
To reinstall, is it a case of doing what I did first time? Boot with the live CD and click install?

2)
This is a dual boot and GRUB finds my Windows installation and allows me to boot to it. If I do the reinstall presumably GRUB will be reinstalled as well. Will it find Windows again or is there something I need to do because this is a reinstall?

3)
The reason that I'm reinstalling is because of some strange conflict between Sunbird and something called libnss3. I'm concerned that this conflict appears in my Home folder somewhere, but I would really like to backup my desktop settings (Theme, colours etc). Is there some way to back up just my system settings without backing up the whole Home folder?

Thanks

Max

---

### Post by Joeb454 on 2008-01-10
1) pretty much yes...BUT....

2) You'll probably need to format the Ubuntu partition **_before_** you hit install :)

3) Back-up the entire home folder, but don't back up the sunbird **and/or** libnss3 folder (chances are it'll be *.sunbird* or something)

Hope this helps, if only a little :)

---

### Post by barbedsaber on 2008-01-10
> **MaxVK said:**
> Hi.

1)
To reinstall, is it a case of doing what I did first time? Boot with the live CD and click install?

2)
This is a dual boot and GRUB finds my Windows installation and allows me to boot to it. If I do the reinstall presumably GRUB will be reinstalled as well. Will it find Windows again or is there something I need to do because this is a reinstall?

Max

I reinstalled because I changed the root password, forgot it, and needed to upgrade from dapper to gutsy anyway. so I just go the new cd, clicked install, and made sure I picked the right partion, and it was all fine, but check with somone who knows what they are talking about first, they can probbobly get you to boot in cli mode, and fix the sunbird thing.

---

### Post by MaxVK on 2008-01-10
Thanks guys.

Joeb454, you have reminded me of something else: If I backup my Home folder, how to I restore it to the new installation? Just copy it all across?

barbedsaber, unfortunately I dont think its a driver problem I'm having. Whatever libnss3 is (Something to do with network security) it has caused quite a few people trouble, and although some have found workarounds for their programs, there seems to be no info on Sunbird.

---

### Post by Joeb454 on 2008-01-10
MaxVK yeah that's  all you need to do, then hit **Ctrl+Alt+Backspace** to take yo back to the login screen (that way all your themes and everything can be loaded properly :)

That's what I did, some things might not copy, but ignore them they'll be files creaed by the system or app's that you've run, and they'll get created again :)

---

### Post by lswest on 2008-01-10
well the definition of libnss3 as described by the ubuntu package site is > This is a set of libraries designed to support cross-platform development of security-enabled client and server applications. It can support SSLv2 and v4, TLS, PKCS #5, #7, #11, #12, S/MIME, X.509 v3 certificates and other security standards. If you have any more information on the error you have, feel free to post it, someone might be able to point something out.

otherwise, when you go to reinstall you can just do install normally, at the partitioner go to manual, choose your / partition and tell it to format it.  (there is a little checkbox in a column "format")  to back up your home folder you can do ```
tar cvpzf backup.tgz --exclude=./.sunbird /home/[username]/
``` and to restore then just use ```
tar xvpfz backup.tgz -C /home/[same username as before]/
```  hope it helps.

ah, someone was faster.  The method described above creates a tar archive with your home folder, which saves space, and the code above can also be used to create a whole backup of "/"  original thread of this method is [here]("http://ubuntuforums.org/showthread.php?t=564836")

---

### Post by MaxVK on 2008-01-10
Thanks, its good to know that all my hard work(?!) setting up the desktop can be restored that easily.

lswest, I wish I had more info to give. Iv already started a thread <[here]("http://ubuntuforums.org/showthread.php?p=4104501")>describing the whole problem, but Iv a feeling this is one of those niggling things that people like to avoid! ;)

This is really my only reason for reinstalling - In the hope that the problem has been caused by my early messing abut with different programs and can be rectified by starting out again.

---

### Post by thelatinist on 2008-01-10
You should definitely use tar to back up and restore your home directory, as lswest suggests, not simply copy over your home directory.  Tar will preserve permissions, dates, and symbolic links that cp won't.  There is a switch to make cp preserve permissions and dates, but it simply doesn't handle symbolic links properly for this task (it copies the file the link points to rather than recreating the link).

---

### Post by lswest on 2008-01-10
@ MaxVK, have a look at the [old thread]("http://ubuntuforums.org/showthread.php?p=4108539#post4108539"), i posted some ideas i had.  hope they help?

---

### Post by MaxVK on 2008-01-10
lswest, thanks, but I just came from that thread! :)

I'm going to reinstall anyway I think, and to heck with the backups. It wont take me more than an hour to get things back the way they were because I keep notes ( ;) ) so I'm just going to go for it, however, I have one last question before I continue (I'm in the LiveCD environment right now!):

I want Home to have its own partition. I am using a partition on a multi-partition, multi-boot system, and I want to know exactly how I go about making Home its own partition. I can make one (Easy enough in the drive setup) but how do I set it so that Home is automatically placed there?

Cheers

Max

---

### Post by ByteJuggler on 2008-01-10
> **MaxVK said:**
> 
I want Home to have its own partition. I am using a partition on a multi-partition, multi-boot system, and I want to know exactly how I go about making Home its own partition. I can make one (Easy enough in the drive setup) but how do I set it so that Home is automatically placed there?


In addition to the root partition and the swap partition, specify that the partition you created for your home folder, is mounted under /home.  Thats all!  See e.g. [here]("http://farm3.static.flickr.com/2133/1589091589_bea72fe8d5.jpg").  That's just an example of where a guy sets a mount point, you would type in "/home" as your mount point for the home partition you created.

---

### Post by jonnywombat on 2008-01-10
Hi

Select the manual partitioning option when you get to it in the install process.First format your old root partition (labbelled /) and create a new root parttion (around 10gigs should be ok). you then need more freespace, You may need to resize another partition that you can stand to be a little smaller, depends how big your old root partition was. 

When you have your desired level of freespace create a new partition, format it in your perfered file type (i use ext3) then add a mountpoint of /home... 

you should then be good to go 

Jonny

---

### Post by MaxVK on 2008-01-10
Oops! Looks like I didn't need to ask that last one! I just love the search function and I found the answer here: [Thread]("http://ubuntuforums.org/showthread.php?t=444953")

Seems I just need to mount one partition as /home.

Thanks guys.

[EDIT]
Wow you guys ARE fast! Thanks all! I'm off to reinstall - With some luck Ill be back soon enough to pester you with more question! ;)

---

