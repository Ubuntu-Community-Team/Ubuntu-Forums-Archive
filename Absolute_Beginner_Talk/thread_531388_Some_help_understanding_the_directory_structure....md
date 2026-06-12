---
title: "Some help understanding the directory structure..."
date: 2007-08-21
forum: Absolute Beginner Talk
---

### Post by jammadave on 2007-08-21
Hi again - 

Read a couple threads on this and am wondering a couple specific things.   I'm really trying not to double-post things that have been beaten to death, so I apologize if I need to get answers in a specific way here.

1. When installing, the first user is automatically root, with RWX access to everything under /, correct?

2. but I should then make a second user for myself so that I don't screw anything up, right?

3. if I want to have separate photos, music, movies, etc folders, I can/should just set those up under /home/user1/(photos, music, movies...), /home/user2/(photos, music, movies...), etc?

and lastly, if I'm sharing with Windows, even temporarily dual-booting, will I have to make a duplicate of each of my music, photo, etc files in order to be able to see or use them with ubuntu?   I'm not very familiar with partitioning at all.

thanks again
Dave

---

### Post by igknighted on 2007-08-21
> **jammadave said:**
> Hi again - 

Read a couple threads on this and am wondering a couple specific things.   I'm really trying not to double-post things that have been beaten to death, so I apologize if I need to get answers in a specific way here.

1. When installing, the first user is automatically root, with RWX access to everything under /, correct?

2. but I should then make a second user for myself so that I don't screw anything up, right?

3. if I want to have separate photos, music, movies, etc folders, I can/should just set those up under /home/user1/(photos, music, movies...), /home/user2/(photos, music, movies...), etc?

and lastly, if I'm sharing with Windows, even temporarily dual-booting, will I have to make a duplicate of each of my music, photo, etc files in order to be able to see or use them with ubuntu?   I'm not very familiar with partitioning at all.

thanks again
Dave

1) Yes, sort of.  Ubuntu does not activate the root user account by default, but most distros do and this would be true.

2) Your user is this second user account.  In Ubuntu, instead of using "su -" to become root (or loging in as root), you prefix any command you want to run as root with "sudo".  This, after you enter your user password, gives your user temporary root power.

3) Yes, precisely.

4) You can install drivers for the linux ext3 file system in windows and read/write off of your Ubuntu drive.  Also you can also install drivers for the windows NTFS file system in linux to read/write those drives.  In short, no, you do not need to duplicate.

---

### Post by Jimmyfj on 2007-08-21
Yest - All you have to do is to create the folders you need for photos, music etc. (In 7.04 that is - In 7.10 Gutsy Gibbon those folders are made by the installer) 

The user you create during install is a normal user - The password you give the installer is your root password after install - Just open a terminal and write sudo su, or make an update and the system will ask for the root password, the one you gave during install.

You don't have to make a second user for safety reasons. Use sudo in a terminal, or gksu nautilus, for root access/privileges during config of your new system. Don't EVER leave the root logged in for longer periods this will compromise your serurity.

---

### Post by mcduck on 2007-08-21
1. No. The first user belongs to admin group, which allows him/her to gain temporary root privileges (using sudo) to do admin tasks. [https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

2. No need for that, look above :)

3. Yes, that's correct. And you can actually acces your windows files from Ubuntu, and with Ext3 drivers, your Linux files from Windows.

---

### Post by UltraMathMan on 2007-08-21
1. The first user created has the ability to use the command prefix sudo to temporarily become root, ie. ```
sudo cp /home/user1/file /etc
``` will allow you to copy "file" to the root owed /etc directory however ```
cp /home/user1/file /etc
``` will not allow you to copy "file" to /etc.

2. Because of sudo you do not need to create a seperate account - you normally run as a regular user.

3. Yes

4. To see files on your Windows partition you will need to mount it (or make sure it is mounted) sometimes with special options. To view your Ubuntu partition in Windows you can install [an ext3 driver]("http://www.fs-driver.org/index.html").

-Hope this helps :)

---

### Post by jammadave on 2007-08-21
Thanks guys - 

Question:  if I don't want any of the other user accounts to be able to "sudo" - what would I do to them?

---

### Post by jordanmthomas on 2007-08-21
Just make sure they are not in the group called 'wheel' or 'admin'.

(To be honest, I am not sure if Ubuntu uses admin or wheel for superuser access, but if the new user isn't in either you'll be good to go)

---

### Post by mcduck on 2007-08-21
> **jammadave said:**
> Thanks guys - 

Question:  if I don't want any of the other user accounts to be able to "sudo" - what would I do to them?

If you don't change any settings new users created won't be able to use 'sudo' by default. So you don't need to do anything.

---

