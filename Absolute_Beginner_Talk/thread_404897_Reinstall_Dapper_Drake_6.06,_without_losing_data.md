---
title: "Reinstall Dapper Drake 6.06, without losing data?"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by CraftyCathy on 2007-04-09
Is there a way I can reinstall Ubuntu Dapper Drake 6.06 and not have to save every thing to CD's 1st? 

I am having a problem with Gramps genealogy program. I have been in contact with the Gramps Project and am told there is something wrong with my system as to why Gramps won't open.

So by this I guess I have to do something to my system to get gramps to work again. I don't have a clue as to what could be wrong.

I have the live CD for Ubuntu Dapper Drake 6.06. 

Thank you, Cathy

---

### Post by Sef on 2007-04-09
1) Do you have a home partition?  If you do then that should not be affected by a reinstall.

2) Have you tried to unistall gramps then reinstall it?  

3) For either of those back up your data first.

---

### Post by CraftyCathy on 2007-04-09
I am not sure what a Home partition is.

---

### Post by CraftyCathy on 2007-04-09
Sorry forgot to commit on the other question. Yes, I have tried reinstalling gramps. I even went as far as deleting gramps, deleting the download and then downloading it again and then reinstalling it. 

When I try to start gramps in the terminal, I get this: Segmentation fault. I am told that gramps should not cause this to happen.

---

### Post by CraftyCathy on 2007-04-09
Also how do I reinstall Ubuntu?

---

### Post by medad on 2007-04-09
When you first installed dapper, you created a Home Folder as part of your setup.  In your home folder will be the desktops for all the users on your system.  There ways to set up the Home Folder on a separate partition so that when you want to reinstall your OS, it won't affect files already on your system.

Please read the following link for a better explanation: [http://www.psychocats.net/ubuntu/separatehome]("http://www.psychocats.net/ubuntu/separatehome").  Hope this helps...

---

### Post by Sef on 2007-04-09
Try this and see if you get a message about what more is not happening.  

Open the Terminal (Applications > Accessories > Terminal) and type gramps.  (type all small letters.)  If you do get any more of a message, please post it here.

---

### Post by CraftyCathy on 2007-04-09
No, all I get is, Segmentation fault. Gramps starts, but then only stays on the screen for maybe a second then is gone.

---

### Post by CraftyCathy on 2007-04-09
Does home include every thing, except for System?

---

### Post by Wim Sturkenboom on 2007-04-09
> **CraftyCathy said:**
> I am not sure what a Home partition is.*/home* is a directory like *documents and settings* in windows (if you're familiar with that). All user stuff is in there.

To check if it's only a directory or a partition, open a terminal and run the df command
```
wim@internet-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda11            15480800   2307584  12386836  16% /
varrun                  485020        92    484928   1% /var/run
varlock                 485020         4    485016   1% /var/lock
udev                    485020       136    484884   1% /dev
devshm                  485020         0    485020   0% /dev/shm
lrm                     485020     18856    466164   4% /lib/modules/2.6.15-28-386/volatile
**/dev/sda12            41286796   1589604  37599908   5% /home**
/dev/sda6             10472136      3320  10468816   1% /media/sda6

```If you have a line like the bold one, it's a partition, else it's just a directory.
In the first case, just make sure that you do not reformat the partition during the install. In the second case you need to make backups.


Further:
make the backups (even if it takes time and cost you an arm and a leg for CDs). One little mistake from your side or a power failure at the wrong moment and it can all be gone.

---

### Post by CraftyCathy on 2007-04-09
Went to  [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome). Printed the instructions.                

Booted in Ubuntu live Cd. Followed the instructions. Got to where, Run Application,  Typed in gksudo gparted, Gparted came up, said it was scanning. Then it froze. I had to shut down system. I restared in Ubuntu, cause now it totally ignores the live Cd in the drive. 

My screen resolution is on 640X480. When I click on the drop down menu to change it, does not drop down. Seems to be the only setting there. 

So... Something happened.. Now what do I do?

---

### Post by CraftyCathy on 2007-04-09
Every thing is so large now on the screen I can't hardly do anything. Even after shutting Ubuntu down. It has not went back to normal and I can't change the screen resolution.

I tried making backups on CD's. But with every thing being so large. I am having troubles seeing the files I want to copy. I can't even see the burn button. Its just a mess.

---

