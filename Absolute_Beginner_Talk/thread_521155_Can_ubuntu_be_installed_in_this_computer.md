---
title: "Can ubuntu be installed in this computer?"
date: 2007-08-09
forum: Absolute Beginner Talk
---

### Post by billpeace on 2007-08-09
Hardware:  CPU: intel Q6600
                    Mainboard:asus P5B plus
                    memory: 1G*4
                    hard disk:320G*4
                 
           I wang to use Raid array from BIOS, so can ubuntu be setup or booted from RAID?
          Do ubuntu have drivers for these hardware ?
          
         If can, I need to install ubuntu from  alternate install CD?

thanks

---

### Post by Smu on 2007-08-09
Why not just try the Live CD and see if it works?

---

### Post by webjames on 2007-08-09
what raid do you have, there are two types. FakeRaid and Hardware Raid. the latter has its own memory and processor. the former is a device which relies on the hosts computer to process the raid. more details here, linux has great software raid which you ca setup with the alternative cd.

more information: [http://linuxmafia.com/faq/Hardware/sata.html](http://linuxmafia.com/faq/Hardware/sata.html)

and [https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

if you card is hardware raid then it will appear as one hard drive in the ubuntu install, if it is fakeraid then it will appear as the seperate hard drives.  if the latter is the case i would strongly recommend linux software raid, to do this boot up the alternative cd, set you hard drives to type raid the setup your raid partitions. i'm sure there is a more accurate in depth howto somewhere here on the forums.

i wish you the best of luck, tell us how you get on.

---

