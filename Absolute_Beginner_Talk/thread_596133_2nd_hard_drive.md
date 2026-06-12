---
title: "2nd hard drive"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by h0z3r on 2007-10-29
hi out their.
i am wondering how i would go about formatting my second hard drive, and then mounting it? i am on guttsy

---

### Post by taurus on 2007-10-29
Can you post the output of this command from a terminal to see which device is your second harddrive?

```
sudo fdisk -l
```

Also, do you want to format it as ext3 or vfat?

---

### Post by overdrank on 2007-10-29
> **h0z3r said:**
> hi out their.
i am wondering how i would go about formatting my second hard drive, and then mounting it? i am on guttsy

Hi and maybe this link will help
[https://help.ubuntu.com/community/InstallingANewHardDrive](https://help.ubuntu.com/community/InstallingANewHardDrive)
Good luck! :popcorn:
Edit to slow again lol :)

---

### Post by Inxsible on 2007-10-29
> **h0z3r said:**
> hi out their.
i am wondering how i would go about formatting my second hard drive, and then mounting it? i am on guttsyYou can use GParted to format the drive. Its on the live CD.
or you can download the GParted iso and burn it on a cd and then use it to format the drive. You can mount it using the mount command or the pmount command (if its an external drive)

EDIT : me too :)

---

### Post by h0z3r on 2007-10-29
hi again.
wow thanks for all the quick reponses. that link that overdrank sent looks very informative. i think i get!
will try after work.
thanks again

---

### Post by rgiskard01 on 2007-11-08
I have followed the directions at the How To above, and still cannot write to my 2nd hard drive as a regular user.  

**>fdisk -lu**
...

Disk /dev/sdb: 80.0 GB, 80000000000 bytes
255 heads, 63 sectors/track, 9726 cylinders, total 156250000 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x00000081

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   156248189    78124063+  83  Linux


**/etc/fstab**
/dev/sdb1   /media/data  ext3  defaults  0  2

I am running 7.10 64bit.
I have tried changing group ownership to both plugdev and users, but still only super user can write to the drive.

Any help appreciated.

---

### Post by Harpoon on 2007-11-08
This drove me nuts for a while, too.   A quick and dirty solution is to do the following:

Get yourself into a terminal, the get into the drive :

cd /media/data
sudo mkdir <directory-name-of-your-choice>
ls <to do a list and make sure it is there>
chown <your user name> <directory-name-of-your-choice>

The step above changes the ownership of the directory to your user name.  When you format a drive in Linux, it assigns the **drive ownership** to root.  But root can make a file on that drive and grant permissions to anyone . . . 

You should be able to do what you want so long as you do it under the directory name you supplied.

The solution is not ideal, but it is a way to use the drive while you wait for something more elegant.

<I just woke up, so if there are any errors, check my command grammar.  Nothing I told you whould "break" anything.

I need caffein - - -  good luck

---

