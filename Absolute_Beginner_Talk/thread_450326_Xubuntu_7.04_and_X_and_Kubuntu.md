---
title: "Xubuntu 7.04 and X and Kubuntu"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ubuntumaybe on 2007-05-21
Hi,

I have Dapper Kubuntu and I want to install Xubuntu 7.04. I have the alternative cd. When I try to install I receive error messages about the X server, LC_ALL not set and told to pick a display manager. I picked the gdm and I still cannot get the app to install. Now when I reboot into Kubuntu I get all the install messages but I cannot get into the Kubuntu desktop. It just hangs. I think I have to change the display manager back but I do not know how to do that. Thanks for your help.

joe

---

### Post by Happy_Man on 2007-05-21
Load up into the recovery mode, and put this code in:

```
/etc/init.d/gdm start
```

That will start up the login screen, and from there, I assume you can handle getting your settings straight? If not, post back, and we'll see what we can do. ;)

---

### Post by ubuntumaybe on 2007-05-22
Hi,

I found that info on a site and I tried it for both gdm and kdm but no luck with either. I deleted that partion and I tried to load the Xubuntu alternative cd. Now I am having a different problem. When it got to the section on loading the application packages that come with the cd it stopped well before 50% then jumped to 85% then returned a message with a red background that all the packages had not been installed. I think it has something to do with the X server. So now I have no installation what so ever. What is the next step. THanks.

joe

---

### Post by Happy_Man on 2007-05-22
How fast did you burn the CD? Did you burn at the slowest speed possible? Did you check the CD for defects?

---

### Post by ubuntumaybe on 2007-05-23
Hi,

I checked the cd for faults and I received an error about a corrrupted file and invallid checksum. Looks like that is the problem. THanks.

---

### Post by ubuntumaybe on 2007-05-25
Hi,

I managed to recreate the CD. Now I am having a different problem. Xubuntu loaded fine with no erros but I have no application menu and when I try to acces the file system I get an error, Segmentation Fault (core dump). What now. Thanks.

Joe

---

