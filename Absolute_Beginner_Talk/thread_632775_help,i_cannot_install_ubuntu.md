---
title: "help,i cannot install ubuntu"
date: 2007-12-05
forum: Absolute Beginner Talk
---

### Post by tehmanwhos0ldtheworld on 2007-12-05
im trying to install ubuntu from live cd

im choosing language,timezone etc but when it comes to the partition preparation i cant see any partitions,the field is empty

what can i do?

please help and thanks in advance

---

### Post by briansvgs on 2007-12-05
Just out of curiosity, what is the make and model of the computer that you are using? On my dell vostro 1400, there is a hidden parititon for the dell mediadirect system that makes it so that the linux partition programs can not see or partition any of the partitions on the hard drive. One solution that I have found is to click create new partion table. This allows you to partition your hard drive and install ubuntu. **Caution: this solution removes all data from your hard drive.**

---

### Post by iris-n on 2007-12-05
I also have a Dell, and my solution was to manually partition the hard drive, through the gparted available on the Live CD.

---

### Post by tehmanwhos0ldtheworld on 2007-12-06
yes but im trying to triple boot,erasing the data doesnt sound good

---

### Post by iris-n on 2007-12-06
You don't need to. With gparted I just shrank the partitions, without deleting anything.
From the live CD, can you access your files (you might have to mount the devices)?
Were you able to see the partitions from the gparted?

If not, type df on the terminal and paste the result here.

---

### Post by tehmanwhos0ldtheworld on 2007-12-06
i cant see the partitions or the hard drive it self nowhere in the live cd

in my old pc everything went perfect

im lost,no hope?

---

### Post by scrooge_74 on 2007-12-06
If you dont have anything of value in that HD then ask the system to make a manual partition.  Another way is to get another HD and installed instead of the one you have right now

---

### Post by tehmanwhos0ldtheworld on 2007-12-06
new hd and deleting the data are two things  i want to avoid

---

