---
title: "How to partition mac HD for linux and osx ??"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Docmac on 2006-10-24
:) This is my first day using linux on my mac. :p  I love running it off the cd, now I want to install it on the HD. What I need help with is this....
I am using a:cool:  PPC  ibook G4  1ghz  256 ram  40gb HD...
1.How many partitions on my ppc mac Hd for ubuntu and osx ?
2. What partition format for linux ?
3. What size partitions to make for linux ?
4. Can linux read off the mac hd ?  Or I read somewhere you should make a fat32 partition to share data ! Is this the easyest way to go ???
5. Many people say airport (wifi) is not on by defult. Easy way to get wifi working on my ibook ?
Thank to all that make linux :KS possible, and in advance for any advice !!!
:rolleyes: Doc

---

### Post by Peter76 on 2006-10-24
Hi, welcome to Ubuntu:-)

I'll assume you'll do a clean install of everything ( ie wipe your HD ) I have no experience with installing Ubuntu on a Mac with an existing OS X. If you want to do that, there is a thread on these forums somewhere on how to resize your mac partitions for free... Do a search; and remember to back up!!!

Ok, now start up from your OS X install disk, and from the file menu choose disk utility and make two partitions. I would make a 30G for Ubuntu and 10G for OSX, but do what you like here, a minimum of 10G should be fine. The thing to remember here is that the Ubuntu partition should be the FIRST one!!!! Just leave it as free space for the moment, and make the OSX partition hfs-plus and do your installation of Mac OS X.

Now boot the Ubuntu cd. When you come to the partitioning, choose to do manually make the partitions. First make a New-word boot partition of 1 MB and make sure the bootable flag is set. Then make a 512 MB swap partition, a 5 GB / partition and use the rest as a /home partition ( or use everything after the swap as / partition, but I prefer to have a separate /home partition to make upgrading easier.

Now finish the installation. I can remember there are some bugs in the Livecd installer ( but I am not sure ) so you might want to use the alternate install cd to be sure...

There is a problem with the fans on G4's which you need to solve first now:
Go to the Applications menu->accesories->terminal and type: lsmod | grep therm. If this doesn't give you something like: therm_adt746x, do ( still in the terminal ): sudo gedit. It will ask you for your password and then start and editor. Choose open and open /etc/modules and at the end of this file add:
therm_adt746x, save and reboot.

For your other questions, yes, you should be able to mount the macosx partition, but be sure journalling is of. I actually never did this, but search the PPC forum about this.
I also don't have any experience with the airport card, but again, check the PPC forum, there's a lot about that there.

Good luck

---

### Post by Docmac on 2006-10-24
Peter76,
   Thank you so very much for the detailed reply! I think I have got the hang of it now. As for the fans in the G4, I read that somewhere but did not really pay much attention to it at the time. So glad you added that in you post, good looking out. I will try everything you stated above. Nice to know there are people out there willing to help, even in the middle of the night !!!

---

### Post by Peter76 on 2006-10-24
Hi, no problem, middle of the night... lol it's morning here.
Good luck and post if something doesn't work

---

