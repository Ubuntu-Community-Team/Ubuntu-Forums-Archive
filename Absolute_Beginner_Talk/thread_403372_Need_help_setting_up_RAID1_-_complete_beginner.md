---
title: "Need help setting up RAID1 - complete beginner"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by somafm on 2007-04-06
Ok before I start I will say I have Googled, searched forums, etc.. for tutorials on raid 1... and found plenty!... but only to eventually become confused with every single one, or lost part way through.

I just purchased 2 500GB Western Digital sata drives that I want to place in RAID 1 (mirroring) under a Ubuntu 6.10 i386 Desktop install for storage/backups. So in case 1 drive takes a crap (or even if  I unplug it), the other drive is there with all my important files and can serve as the main drive until I can replace the failed drive. I am a complete noob when it comes to this, so I am looking for pretty detailed instructions on how to set it up. 

I have the 'fake hardware raid' available on my motherboard, but was told software raid is a much better approach for what I want to do. Also, it would be nice to know how to monitor the raid to see it's status, how to rebuild it if 1 drive fails or if I need to re-sync, etc.

I can take any approach needed, and there are no important files on the drives so I can start from a fresh install, or whatever is required to do this in a clean and simple manner. Both drives are detected in bios and show up in the device manager when the livecd is loaded. "Fake raid" is also turned off in the bios to avoid any conflicts. Thanks, I can give more info if needed :)

---

### Post by mikeyphi on 2007-04-07
Haven't tried this but all the advice found indicates that the best approach is to start from scratch and follow the advice here- [http://www.howtoforge.com/linux_software_raid](http://www.howtoforge.com/linux_software_raid)

Hope you haven't already given up on that page!

---

### Post by somafm on 2007-04-07
Alright after a good night's rest, looking at that link you provided, and playing around with it a little.... I finally got it working! :guitar: I promised myself to write a detailed guide to help others if I got it working, so I will do that soon, but here's a quick rundown of what I did:

I booted from the 'alternate install cd' for 6.10... and told it to install in text mode. At the partition screen it showed my 2 drives, and I told it to "auto partition" both of them...and it did. Then I changed the primary partitions to "physical raid" instead of "ext3" for both drives (i left the SWAP partitions alone though). 

After changing them to physical raid, it enabled the option to "Configure Raid" on the main partition screen. Then I went to that and chose Raid1, and selected both drives, and it did did it's thing and went back to the main partition screen. Now there was a new entry in the partition screen!:   Raid1 - SomethingSomethingBlahBlah..

I selected that new raid entry, and changed the filesystem to Ext3, and continued on with the install. After everything was up and running, it showed the space about 450GB left, which is good because I expected that!

I opened terminal and ran: **watch cat /proc/mdstat**. And I watched it as it was building the mirror. This took a few hours. Now it was done, and time for the real test, I unplugged a random drive after shutting down, and started up again. It booted up fine. Ran cat /proc/mdstat again and noticed 1 drive was missing from the array which is obvious. So I shutdown, plugged the drive back in, rebooted, ran **sudo mdadm --add /dev/md0 /dev/sdb1** to add the drive back into the array, and watched it start to rebuild the raid again with **watch cat /proc/mdstat**. And thats where I am right now. So I assume it's working as it should :) 

Sorry if that's all confusing, but it's as short as I can make the story until I write up my own raid1 guide :)  

Thanks for the help, and heres another good link to check out: [http://users.piuha.net/martti/comp/ubuntu/raid.html](http://users.piuha.net/martti/comp/ubuntu/raid.html)

---

### Post by jts on 2007-07-13
Do you have any raid monitors setup?  Is mdadm the only choice?

---

