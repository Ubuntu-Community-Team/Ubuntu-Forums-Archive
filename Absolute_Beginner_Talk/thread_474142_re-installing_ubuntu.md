---
title: "re-installing ubuntu"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by ASTP001 on 2007-06-14
I need to re-install ubuntu w/o losing all the data I previously had... I tried to boot windows, since everytime you boot ubuntu, it asks what operating system I want to boot, and when I choose windows, something weird nothing opened, so I'm on ubuntu using my CD, but I'm afraid to install it again because I want to have all the settings I used to have before all this happened....

---

### Post by ASTP001 on 2007-06-14
Anyone....?

---

### Post by mattze on 2007-06-14
I recall installing an new version of Ubuntu over an old one with keeping (most of) the setting and the data. You should just choose the same user name as before. Of course you should not(!) format your partition during re-install.
It is probably a good idea to back up your data before trying this. you can do so from the live cd.

---

### Post by ASTP001 on 2007-06-14
so as long as I don't format, I'll keep all the data if I select the same partition? Changing the mount point doesn't affect anything, right?

---

### Post by mattze on 2007-06-14
right. you can also create a new partition and mount it from your newly installed Ubuntu, but the simplest way should be choosing the partition as root (/) mount point without(!) formatting it.
hope it helps.

---

### Post by ASTP001 on 2007-06-14
Alright, I'll do that right now! I hope it works...

---

### Post by ASTP001 on 2007-06-14
Well, when I tried that, it says "The file system on /dev/sda6 assigned to / has not been marked for formatting. File systems used by the system (/, /boot, /usr, /var) must be reformatted for use by this installer. Other file systems (/home, /media/*, /usr/local, etc.) may be used without reformatting." So, what should I do....?

---

### Post by mattze on 2007-06-14
in that case you should back up your data in /home/[user name] and copy them to that place after you installed Ubuntu again. (be sure to include the files and folders that are hidden - the ones with the . before the name) that should keep your setting however you will have to install the software again that is not part of the standard installation. 
i can not guarantee for that, since i m not an ubuntu/linux expert.

ps: perhaps someone with more experience can verify my thoughts.

---

### Post by ASTP001 on 2007-06-14
so basically copy the whole partition to.... /home/[myname]   ? Well, where is that?

---

### Post by fumduck on 2007-06-14
this may or may not help.. but I recently installed ubuntu onto a partion with Kubuntu and vista.. and what i found while installing  to a new partion is that ubuntu let me migrate all files and users to new install.. It would mean that you would have to do a manual partition.. but it might atleast let you keep your files on a freesh install.. which then you would have to reload programs and  then format old ubuntu.. Cheers and goodluck 
have you tried checking to see if the boot record for windows is corrupt somehow?

---

### Post by mattze on 2007-06-14
no, sorry should have made it clearer. what you should do is back up the folder /home/[your username] which is where the setting and data of your user is stored. then copy it to that location on your new installation.

---

### Post by ASTP001 on 2007-06-14
boot record for windows? How do I check?

---

