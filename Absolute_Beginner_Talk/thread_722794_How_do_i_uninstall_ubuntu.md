---
title: "How do i uninstall ubuntu"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by total0wnage on 2008-03-12
hey guys, i really like ubuntu but i rarely use it now and when i waz installing it i set it to use the D: data partition on my laptop which is 100gb and i really need that space now so i would like to remove ubuntu i am not sure how to do this tho. could someone please give me the steps to uninstall ubuntu and i also have a small problem of not remebering my username and password is there a way to find out what it is? thanks

---

### Post by scragar on 2008-03-12
boot up the live CD, then go to
system > administration > Partition Editor

find your 2 ubuntu partitions(a small swap and a larger main partition), and delete them, then add freed space to whatever partition you want, apply changes and once it's done reboot(you may want to make sure partition to boot has the boot flag by right clicking and choosing the right option(something like "edit flags"), then make sure boot is checked).



PS: would be intrested to know why you don't want ubuntu any more though.

---

### Post by A$h X on 2008-03-12
Remember then you were installing ubuntu, there was an option to format your partitions? There you go. If that's incorrect then tough, I have a sneaking suspicion that you are trying to screw with someone else's ubuntu partition. And it's so damn easy to remove unwanted stuff from your HD, you obviously want someone to do your thinking for you.

---

### Post by Oldsoldier2003 on 2008-03-12
> **total0wnage said:**
> hey guys, i really like ubuntu but i rarely use it now and when i waz installing it i set it to use the D: data partition on my laptop which is 100gb and i really need that space now so i would like to remove ubuntu i am not sure how to do this tho. could someone please give me the steps to uninstall ubuntu and i also have a small problem of not remebering my username and password is there a way to find out what it is? thanks

The thing to do then would be to boot up your computer using  the Ubuntu live CD or a Gparted live cd and delete the Ubuntu partition. The next step would be to boot up using your windows installation cd and run fixmbr from the recovery console, or boot to a command prompt and run fdisk /mbr . either of those two actions will restore your windows master boot record and allow windows to boot as the default/only operating system.

---

### Post by nick_h on 2008-03-12
If there is no data you want to keep in your Ubuntu partition you can just reformat it.  As already suggested you can also use a partition editor to recover the space.

To recover a lost password - see [Lost Password](https://help.ubuntu.com/community/LostPassword)

---

### Post by louieb on 2008-03-12
[URL="http://www.users.bigpond.net.au/hermanzone/p18.htm"]IDBS Remove/Replace/Uninstal
[/URL]

---

### Post by ferdostar on 2008-03-12
Do you have another OS installed on your computer? I suppose that if you've installed it on "D:" you have a partition C: with windows. You can remove ubuntu by fomating the partition (using Gparted, Partition magic, etc.) or if you have some important data on "D:" you can just remove the directory with ubuntu, but make sure to have the right boot loader from the other OS, in case it's the ubuntu grub you're using now.
EDIT: was posting at the same time :)

---

### Post by total0wnage on 2008-03-12
how do i remove the directory? i might have some info and No im not trying to mess with anyones computer to whom ever said that its just im an idiot and i made my ubuntu username and password something random and i forgot it but im sure i could guess it after a while.

---

### Post by nick_h on 2008-03-13
If you have some data you want to recover from your Ubuntu partition then either recover your password using the link I gave earlier or install an ext2/3 filesystem driver for Windows.

Have a look at [http://www.fs-driver.org/](http://www.fs-driver.org/) - it is very easy to install and use.

---

