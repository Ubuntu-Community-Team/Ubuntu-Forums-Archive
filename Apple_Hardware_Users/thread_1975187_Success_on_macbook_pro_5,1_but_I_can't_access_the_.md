---
title: "Success on macbook pro 5,1 but I can't access the data of my macosx partition"
date: 2012-05-07
forum: Apple Hardware Users
---

### Post by internaciulo on 2012-05-07
Hello,

good news for me, I succeeded to install Ubuntu 12.04 on my Macbook Pro 5,1 which is documented only for Natty right now
[https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty](https://help.ubuntu.com/community/MacBookPro5-1_5-2/Natty)

It was not easy though :
- I had to backup all my data with "Carbon Copy Cloner" [http://www.bombich.com/](http://www.bombich.com/) on my external usb drive (better than TimeMachine because you can boot on your backup)
- Boot on my external usb drive , wipe out all the data on my hardrive, create two partitions
- Restore  the macos x partition with carbon copy cleaner
- reboot and reinstall refit
- boot on the Ubuntu CD by pressing the "c" key
- Here I had to follow the tip given here to press F6 and sed "nomodeset" before booting

> Booting into Ubuntu this way takes many minutes, including a minutes-long period where Ubuntu appears to have locked up on the boot menu. Most likely it has not. Just wait! note I had to set the boot option to nomodeset. If you press function f6 at the boot options screen you can choose that option.

[https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation](https://help.ubuntu.com/community/MactelSupportTeam/AppleIntelInstallation)



So now my problem :

I would like to access my music and photos which are on my hfs+ formatted, read-only mounted, mac os x partition

This won't work except if I login as root because there is a mismatch between the users of my macosx partition and the ubuntu users :

> jmfayard@jmfayard-MacBookPro:~$ cd /media/Macbook/Users/jmfayard
jmfayard@jmfayard-MacBookPro:/media/Macbook/Users/jmfayard$ ls -l
drwxr-xr-x 1 501 dialout       4 mars   9 16:43 Applications
-rw-r--r-- 1  501 dialout 2512154 avril  2 09:48 cerfa_12100-02.pdf

I'm neither user 501 nor in the "dialout" group, so it doesn't work.

What can I do to fix this ?

---

### Post by smurphy on 2012-05-08
yup. That's an issue on unix type OS's.
The user ID. You have 1 option (what I actually did). You will have to change the UID's on one side (Mac OS-X or Linux).

I tend to always change OS side which has the lowest UID. In this cases - MAC OS-X (as the other way around you'll have to change quite loads of other directories, applications eventually etc.).

In Mac OS-X, the user ID's are very low. So - create a new user with the UID you have under linux, and migrate all the content from your old user to the new user. This will work fine if your OS-X installation is not too old. If it is old, you will have to find your old files, and re-chown these too.

Goolge will help you doing it. There are many ways for it.

Since I identified the issue, It's the first thing I do.

---

