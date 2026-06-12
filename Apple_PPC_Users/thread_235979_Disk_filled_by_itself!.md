---
title: "Disk filled by itself!"
date: 2006-08-14
forum: Apple PPC Users
---

### Post by ubuntubrian on 2006-08-14
This is really weird. I was doing some DVD authoring in Ubuntu  using transcode and kde DVD author wizard. My usb drive that I use for such things for storage capacity started doing strange things like not having enough storage for a dvd. It's 15GB of free space so that is weird. I noticed that some items in trash were now in directories on the usb partition named .Trashbrianokeefe and .Trash1000. I had not seen these before. I emptied them to free up space. then the name of the partition changed by itself from "For_Linux" to "sda9" but only in a file manager. Still same name on the mounted volume on desktop.
I continued to work on dvd's and I noticed that each time I switched windows in my file manager the info at the bottom showed less space available (in my home directory). First 4GB then 2 and 1 and I got low disk space warnings. I quickly copied some files to the usb drive and shut down and tried to restart but of course I now have no disk space on the Ubuntu partition. I'm writing this from the OS X partition-nice and stable over here! I'm checking the mounted Ubuntu partition to see what is abnormally full. Again, i started the day with 5GB of free space! I have no more DVD's on the Ubuntu partition unless they are hiding somewhere.
Any ideas of what would eat my disk? Also, a backup of my home directory on the usb drive morphed into an unopenable, no content generic gnome icon as did the only dvd I had on the drive.
Help!
Thanks
Dapper LTS ppc  TiBookG4

---

### Post by ubuntubrian on 2006-08-14
I may have found the issue. I was also running MOL and after checking out the ubuntu volume from OS X I found that /var/log was a 4.8 GB hog! The MOL recent log was 3.8GB
so I trashed it and now the volume has that much free space. Do I need any of the log files for any other reason that to check things out? They are accumulating.

---

