---
title: "Partitions not detected by the Live CD installer"
date: 2012-10-14
forum: Any Other OS
---

### Post by Baladya on 2012-10-14
Hello,

Althought this is Ubuntu's forum, but since it worked on Mint too, I would like to ask for your help.

So I am trying to install Mint on my new Dell Laptop. When I click on "Install Linux Mint" on the desktop and the window opens and asks me to choose language, etc... However It doesn't let me choose If I wanna "install along with windows" or " Remove OS and install Linux" or warever those choises are... It straight ahead goes to the partitioning table and for some reason doesn't show my partitions. GParted, on the other hand, shows the partitions.

Now surprisingly I had the same problem on my desktop pc and I found the solution here:
[http://ubuntuforums.org/showthread.php?t=1897023](http://ubuntuforums.org/showthread.php?t=1897023)
It says it has to do something with RAID metadata. Now when I tried the solution it worked fine.

Now my Dell laptop has a 500 GB HDD + 32 GB SSD Cache (notice its cache not a normal SSD). 
Now I know so little about Linux and little about SSD's (especially cache) so I am not sure If I should apply the same fix on my laptop. Maybe there is a RAID connection between the HDD and the SSD that with that code might stop working. Is this even the right solution for my problem?

Hope someone can help... Thanks in advance


Installation window:
[IMG]http://i.imgur.com/lr7Zp.png[/IMG]
*Notice also that the installer only detects the sdb (SSD cache)



500 GB HDD:
[IMG]http://i.imgur.com/CvYQo.png[/IMG]



32 SSD cache:
[IMG]http://i.imgur.com/lbOo0.png[/IMG]

---

### Post by howefield on 2012-10-14
Thread moved to "*Other OS/Distro Talk*"

---

### Post by oldfred on 2012-10-14
It looks like another one of these. I do not have it but saved these links.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.


---

### Post by Baladya on 2012-10-15
Alright thanks mate...

I have a few questions I hope you can answer tho:

 
1) Will this break my Windows installation like Darkrod says?

2) Will Boot-Repair work with Mint?

3) What's the point of installing the / on the SSD instead of HDD? Will it make the starting up faster? Is it safe?

4) Should I install Linux on the HDD normally or better off install it on the SSD like Tall Person did here:
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
Note: I have 8 GB RAM. Will it be possible to install the OS on the SSD with that much swap or will I run out of space?

5) Looks like [asymptoticFault]("http://ubuntuforums.org/member.php?u=1734568") turned on the IRST successfully here
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
The question here... If I install Linux on the SSD cache, will Windows still be able to use it for cache (IRST)?

Sorry for the many questions but I am afraid of screwing things up :/
Thanks

---

### Post by oldfred on 2012-10-15
It primarily depends on whether you are primarily a Windows user or a Linux user. If Windows then keep the SSD for use with Windows, I really do not know how that works, but it is for Windows.

But if you like & use Ubuntu a lot then installing in the SSD makes sense. I have a 60GB SSD and have Ubuntu (actually two / partitions) in the SSD. Do not put swap on the SSD. With 8GB of RAM you almost never will use the swap  but system seems to like to find some, so just create a small 2GB swap on the hard drive.

Boot-Repair I believe works with all Debian versions, not sure about others. It is more the default commands that are included that the scripts rely on.

---

### Post by Baladya on 2012-10-15
hmm....

Alright If I choose to install Linux on the SSD, 

1)I won't be installing that much programs on linux
2) When I mentioned swap, it's cuz I would like to be hibernating... should I still use only 2 GB on the HDD?
3) 19 GB free on the SSD so I can try using the IRST on Windows
4) Gonna be installing bootloader on it too.

With the above requirments, could you please  draw up a partition table for me including the "/" "/home", "swap", "/boot" or/and whatever I need.
* Also if you look at the partitions (above in the pic above) the SSD, is already partitioned into a 8 GB partition and another 22 GB one... What should I do about them?

---

### Post by oldfred on 2012-10-15
It looks like the SSD is only configured to use the 8GB and all the rest is unallocated and not used or wasted??

You do not need /boot and I would only install / (root) on the SSD. Not sure if you can keep the 8GB for use with Windows as you can easily fit / into the 22GB unallocated. I use about 9GB with my /home inside my / on the SSD but have all data and some of the hidden folders like Firefox & Thunderbird in data partiitons on the rotating drives. My /home is about 2GB of the 9GB on my SSD. My other install is 12.10 with just apps installed and is only 6GB used of the other 27GB.

I do not understand enough on how the RAID and Intel configuration works. But I might try turning RAID off as the one poster suggested create a sdb2 and make that / and install to that. Put swap and /home or a data partition on the rotating drive.

You need to use Windows to shrink the Windows OS partition and reboot several times  so it can run chkdsk and update itself to its new size. Use sda4 as an extended partition and put swap, /home and/or data partitions into sda4 as logical partitions. I often suggest another NTFS data partition for shared data but again not sure how that works with your configuration.

If you do not modify the sdb1, you may be able to turn the Intel RAID thing back on??

---

### Post by Baladya on 2012-10-15
wow this is getting more complicated :popcorn:  I think I should just install it on the HDD for now and look into the SSD later when I get more experienced with Linux

If I install it on the HDD, should I jst open the live installer and let it do the partitioning for me and save myself the hassle and confusion?
Edit:If I let the installer do the partitioning, will it make a swap paritition?

---

### Post by oldfred on 2012-10-15
You may still have to turn the RAID off or use Alternative installer. You still need to use Windows to shrink its system partition to make room. Ubuntu will install to unallocated space just fine with just a / and swap. Not sure what rules it uses to create partitions, as I prefer to have more control & create partitions in advance.

---

### Post by Baladya on 2012-10-16
Question: Why can't I shrink windows from the live installer?

---

### Post by oldfred on 2012-10-16
Windows has inside the NTFS partition info on the start & size of the NTFS partition. That has to match partition table. When you change the size of the NTFS partition on reboot Windows has to run chkdsk to update the size info. 

Sometimes with the resizing by Linux tools Windows does not run chkdsk on reboot and has issues. 

Always best to use Linux tools for Linux and Windows tools for Windows.

---

### Post by Baladya on 2012-10-16
Alright so I should go to disk management... Shrink C: (remove 20 GB for / and 8 GB for swap [use it for hibernation] ).

Restart a few times then go to the live CD and install linux and use the 20 GB and 8 GB?

---

### Post by oldfred on 2012-10-16
Sounds good to me. 

I just never use hibernation as Ubuntu boots pretty fast anyway.

---

