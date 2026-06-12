---
title: "[SOLVED] dual - xp + ubuntu"
date: 2008-01-25
forum: Absolute Beginner Talk
---

### Post by willubunto on 2008-01-25
I'm planning to install ubuntu asap. 
I’ve got 1 hard drive with 3 partitions. 2 of them will be for ubuntu :) the other has xp, which I want to keep up and running.
The questions: 
- are there some relevant disadvantages or issues running xp+ubunto in the same box?
- Is there some additional requirement/procedures during the installation process of ubuntu when it goes along with a live xp os ?

---

### Post by logos34 on 2008-01-25
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by hyper_ch on 2008-01-25
> **willubunto said:**
> 
- are there some relevant disadvantages or issues running xp+ubunto in the same box?

Not really... except if the disk fails (because of age or whatever) you can't boot any OS... but that has nothing to do with the OSes per se...

> **willubunto said:**
> 
- Is there some additional requirement/procedures during the installation process of ubuntu when it goes along with a live xp os ?
Not really... first install windows (which already I think according to your post) and then install ubuntu and have GRUB installed... the install procedure asks you for this I think...

Upon next boot you'll be able to select which one to boot.

---

### Post by Kevbert on 2008-01-25
Use the guided option when you get to the partitioning stage.  If possible use a wired connection (LAN / Ethernet)for the web while installing.  It will make hardware detection and software configuration easier.

---

### Post by agim on 2008-01-25
First of all, have you tried the LiveCD? It will help to see how everything will work, check for compatability and all that. Also, you say you have two partitions for ubuntu, but if you run the guided install, it will only install on one.
I assume you made the second ubuntu partition for your /home folder, correct?

Also, I think its important to save your mbr. I am a huge fan of Ubuntu, it has been a great OS for me, an amazing tool for a lot of different things. But if things don't work out for you and you overwrite the mbr without saving you will run into problems after uninstalling.

This link will show you how to backup your mbr. Go to the section titled "Backing up".

[http://www.freesoftwaremagazine.com/blogs/backing_up_your_master_boot_record](http://www.freesoftwaremagazine.com/blogs/backing_up_your_master_boot_record)

Good luck!

---

### Post by willubunto on 2008-01-25
Thanks Agin, and right. First partition has xp, second (fat32) will ubuntu, third for archive/backup.
I'll follow your sugestion. First action after installing ubuntu, I'll backup de mbr.
Iv been through the dual boot instruction from de live cd but one point is not yet clear for me. What they say is this "Select the partition which contains Windows", resize it, and in the free space created "create a swap partition of around 500 MB". Finish installing ubuntu and at nex at booting I'll have the choise for one or other os. All this is clear for me, but....
As I have already a free partition can I not install ubuntu straight on it ? And if I do so, will I still have the option to choose from xp or ubunto, everytime I boot ?

---

### Post by agim on 2008-01-25
You will have to save the mbr before you install ubuntu, once you install grub, the ubuntu bootloader, it will overwrite your mbr.

I sent you that link and didn't even consider that you aren't using linux yet, so you can't run those commands. I would suggest running the liveCD and saving the mbr to a usb drive, if you have one. If not, there are ways to save it while running windows.

As for your second question, yes, you should be able to put ubuntu onto your free partition and yes you should be able to select ubuntu or windows from a list.

You said that you're ubuntu partition is fat32? Ubuntu needs ext3, as far as I know. The following link has a little more info on fat32. I guess its possible, but not recommended. Whenever I install linux I just leave the partition unformatted and let the installer do it for me. Anyway, the link:

[http://ubuntuforums.org/showthread.php?t=307887](http://ubuntuforums.org/showthread.php?t=307887)

Out of curiousity, are you installing 7.10?

---

### Post by willubunto on 2008-01-25
I&#8217;ve just been through the ubuntu live cd (v 7.10) and what I saw have exceeded my expectations, by far. I&#8217;m very grateful to all who have contributed answering my questions. 
Windows is an expensive giant, made up to cope with everyone needs. As xp is dying and vista looks worst an alternative os has became a big wish.  Light, user friendly and customizable to my own needs.  For me Ubuntu is the first one to try. Although there&#8217;s a few to learn at the end it will worth it, I guess. Also the community looks really fantastic and willing to help.
Thanks again Agim for your information and suggestions. I&#8217;ll surely follow them.

---

### Post by jonabyte on 2008-01-25
> **willubunto said:**
> 
- are there some relevant disadvantages or issues running xp+ubunto in the same box?


I don't see any issues running both, I have a dual boot, but I am running Linux and Windows on separate hard drives, this would help redundancy if one fails, you still have one os running.

---

### Post by agim on 2008-01-25
willubunto, make sure you read the article about saving ht embr carefully, the first command tells you to save 512 bytes, but saving 446 is preferred, as the article says later in the column.

I hope Ubuntu is as great an experience for you as it is for me.

---

