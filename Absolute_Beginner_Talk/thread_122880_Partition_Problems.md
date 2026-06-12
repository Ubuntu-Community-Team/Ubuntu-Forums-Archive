---
title: "Partition Problems"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by wsmoser2004 on 2006-01-28
Two days ago, I finally decided to dual-boot my laptop with Kubuntu.  I had no experience whatsoever with dual-booting anything, but I figured I'd give it a shot.  I used Partition Magic 8.0 to free up about 8 GB of my 40 GB hard drive for Kubuntu.  All I did was resize my NTFS Windows partition, I did not format the free space.  Then I installed Kubuntu on the free space and let it worry about partitioning and formatting it.  Now Windows XP, Kubuntu, and Grub are all working great!  Except...when I try to open up Partition Magic it gives me the following error:
> 
PowerQuest Partition Magic has detected an error 116 on the partition starting at sector 77401170 on disk 1.

The starting LBA value is 77401170 and the CHS value is 15483824.
The LBA and CHS values must be equal.
PowerQuest Partition Magic has verified that the LBA value is correct and can fix the CHS value.  

Would you like PowerQuest Partition Magic to fix this error?


There are options for "Yes" and "No".  I wasn't quite sure what this meant, and I didn't want to destroy Grub or anything important like that, so I clicked "No".  I then got this error:
> 
Init failed: Error 117.
Partition's drive letter cannot be identified.


...and Partition Magic just dies.  Has anyone seen this error before?  I tried searching these forums and Google and I see lots of others who have clicked "Yes" and then gotten lots of other errors with Partition Magic.  Should I just leave well enough alone and ignore the problem?  Unfortunately, if I do that, I can never use Partition Magic again if I ever decide to go to completely Kubuntu or decide to go back to Windows-only.

Any help would be greatly appreciated.

---

### Post by agapito on 2006-01-28
I had that error a loooong time ago, before I completely erased Windows out of my life. :)  You can try to say yes, bacause sometimes it fixes the error, but advised: I don't know for sure if it will mess up grub or the linux partition. You are on your own here... 

The partitioning tools of windows and linux are not completelly compatible so, if you are a Patition Magic Fan here's what you can do ( I'm afraid in means a fresh installation of (K)Ubuntu):

1. In patition magic you free up the space for ubuntu, by resizing your windows partition. 

2. Then you create the partitions for linux using patition magic like this:

  - One swap partition (Primary), at the beginning of the free space. (256Mb or 512Mb should do the trick but you can check to see how much swap you have on Ubuntu before doing this)

   - One ext3 (or ext2) partition (primary) for the OS, 7Gb will do.

   - One ext3 (or ext2) partition (primary) using the rest of the space,  for your home. 

This way you get "P.M. friendly" partitions.


3. Ok, the partitions are ready now let's install. I've only done this in old Mandrake Linux 8, but back then I had to manually configure the partitions. I guess the same applies here, but it's really easy. 
Chose, manually configure partitions.

Make sure that...

---The small partition is assigned for swap.

---The filesystem of the 7Gb( or whatever you assigned to it...) partition is ext3, whose mount point should be / (that's right, just a "/". / is the linux equivalent of C:\ )

---The filesystem of the large partition is ext3, whose mount point should be /home (this way you get a partition for your home directory, where all your personal stuff is. This way you may reinstall and not loose your personal stuff. ;) )

Since these are newly created partition they don't need to be formated.

[COLOR="Red"]Be _EXTRA CAREFULL_ and make sure that you won't format your windows partition[/COLOR]!!! Read everything very carefully. Double-double check everything. 

 I don't have to tell you that you should backup you data before installing. "Installing an OS is like a box of chocolate, you never know what you are goin' to get!" Forest Gump ;)

The rest of the installation is standard procedure... 
Have fun.

Backups are your best friends!

------------------------------------------------------------------------------------------------------------------
I edited this to include the stuff about the /home partition. It's just a little bit of extra work and it has saved me from lot's of problems in the past. ;)

---

### Post by lha on 2006-01-28
[QUOTE=wsmoser2004]Two days ago, I finally decided to dual-boot my laptop with Kubuntu.  I had no experience whatsoever with dual-booting anything, but I figured I'd give it a shot.  I used Partition Magic 8.0 to free up about 8 GB of my 40 GB hard drive for Kubuntu.  All I did was resize my NTFS Windows partition, I did not format the free space.  Then I installed Kubuntu on the free space and let it worry about partitioning and formatting it.  Now Windows XP, Kubuntu, and Grub are all working great!  Except...when I try to open up Partition Magic it gives me the following error:


There are options for "Yes" and "No".  I wasn't quite sure what this meant, and I didn't want to destroy Grub or anything important like that, so I clicked "No".  I then got this error:


...and Partition Magic just dies.  Has anyone seen this error before?  I tried searching these forums and Google and I see lots of others who have clicked "Yes" and then gotten lots of other errors with Partition Magic.  Should I just leave well enough alone and ignore the problem?  Unfortunately, if I do that, I can never use Partition Magic again if I ever decide to go to completely Kubuntu or decide to go back to Windows-only.

Any help would be greatly appreciated.[/QUOTE]

Hi,

Those error messages look familiar to me. I let my Partition Magic to fix those errors and it still didn't like my partition table. Maybe your luck is better?

I've heard of many cases where PM has royally screwed hd's with Linux on them and at the moment, I like to keep my PM cd in my drawer where it can't hurt me. :) I prefer tools that come with Linux. (My copy of PM is some sort of limited OEM version which came with my motherboard, so I hardly care for it. If you have paid lots of € for yours, I understand if you want to use it.)

IMHO, if you stay with Ubuntu (or Linux), there's no need for PM. If you want to go Windows-only, removing linux partitions might make Partition Magic happy. Atleast it did the trick for me. (Of course, removing my linux partitions was just to get Windows partition copied during a hard drive upgrade and switch from Debian to Ubuntu. And I really believed Partition Magic would've made it easy. It's a real pain to install Windows...)

---

### Post by wsmoser2004 on 2006-01-28
I used a version of Partition Magic that my school owns a license to...I did not pay for it.  I was a little bit concerned about using the free Linux tools with NTFS.  Now I'm not sure if Partition Magic was a good choice or not...:-k 

At this point, I don't really want to do a complete reinstall of Kubuntu...especially since everything is working.  Thanks for the advice, agapito, and I'll save that information if I do decide to go ahead with the reinstall.  (Or for the future, when I install Linux on another computer :p ).

I should note that I searched Symantec's website for the problem, and their solution was to delete the partitions and recreate them.  I REALLY do not want to go that route, because I am still a pretty dedicated to Windows and the partition it is installed on (Kubuntu is just a toy for the time being :) ). 

Thanks for the advice everybody.  I'll keep watching in case you think of anything else...

---

