---
title: "Can two distros share a home partition?"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by wersdaluv on 2007-05-25
I have a partition that I have been reserving for another distro, a home partition, and a Kubuntu Partition. It is now time for me to install a distro to the partition I reserved for it.

Since the distro that I am going to install is also a KDE distro and I am planning to use the same user name that I currently use in my Kubuntu partition, will the KDE settings and my user name's settings be shared by Kubuntu and the other distro I am going to install if when I install the new distro, I am going to set the same home partition?

---

### Post by Nythain on 2007-05-25
make sure they both use the same versions of kde and apps or you migh run into a few snags/problems, but yes, it can work

---

### Post by vigleik on 2007-05-25
It's not such a good idea, I think. The problem is all kinds of programs store config files on your home partition, and if you use different versions it could mess things up.

A better solution (IMHO) is to have separate home partitions, and store all your data on a different partition.

---

### Post by reacocard on 2007-05-25
It can work, but if apps have different version you could run into snags.

It might be easier to just use two different usernames and just set up symlinks for the config of the apps that you really need synced.

---

### Post by compmodder26 on 2007-05-25
Another issue you could face is a permissions problem due to what number range each distribution used to assign user ids.  I tried sharing a home partition between Ubuntu and Fedora quite a while back and even though the username was the same for each distro, I couldn't write to the home partition in fedora because the id associated with my username was different between the two.  Ubuntu starts its local user id range at 1000 and I believe Fedora starts at 100.

---

### Post by wersdaluv on 2007-05-25
The other distro I was talking about is PCLinuxOS 2007. 

After reading your replies, I guess, it would be best to have a different user name.

---

### Post by bluknight on 2007-05-25
> **wersdaluv said:**
> 
Since the distro that I am going to install is also a KDE distro and I am planning to use the same user name that I currently use in my Kubuntu partition, will the KDE settings and my user name's settings be shared by Kubuntu and the other distro I am going to install if when I install the new distro, I am going to set the same home partition?

Perfectly ok (and space saving) to share home partition provided the different distros have different usernames. The problem is when the /home partition is too small so that if you dnld a large iso file to the Desktop the /home partition gets locked up for space quickly.

Ive just resized my home partition to 10G shared among 4 distros and 6.10 gives me the big problem with .dmrc and permissions, as well as new UUIDs which must be edited to the /etc/fstab file. For login lockouts read all about it in

[http://ubuntuforums.org/showthread.php?t=371052&highlight=.dmrc](http://ubuntuforums.org/showthread.php?t=371052&highlight=.dmrc)

Oh just remember not to format the /home partition when you install the new distro ;)

---

