---
title: "hard drive permission"
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by try2lickurelbo on 2007-06-23
So I've completely installed Ubuntu 7.04 and finally got my second hard drive to mount, but now i don't have any permissions to do anything to it unless I'm root :(.

Can someone help?

---

### Post by SendDerek on 2007-06-23
This is something that every newb struggles with... I did too back when.

But, after you realize why it is the way it is, it makes more sence and you tend to accept that it's better and more secure.

BUT... if you absolutly hate it... here's something that might help:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by try2lickurelbo on 2007-06-23
> **SendDerek said:**
> This is something that every newb struggles with... I did too back when.

But, after you realize why it is the way it is, it makes more sence and you tend to accept that it's better and more secure.

BUT... if you absolutly hate it... here's something that might help:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

So am i not able to use this other harddrive for storage?

---

### Post by SendDerek on 2007-06-24
The way I understood it is that you were needing to input a password everytime you wrote to it right?  So, it sounded like you could already write to it with no problem.

Maybe I understood it wrong.  What format is the harddrive?  NTFS?  If that's the case, you'll need to download NTFS-3G and turn on support for NTFS drives by going to Applications->System Tools->NTFS Configuration Tool.

---

### Post by Alex Spencer on 2007-06-24
Don't use root all the time...the NTFS configuration tool worked for me...use that.

---

### Post by bodhi.zazen on 2007-06-24
> **try2lickurelbo said:**
> So I've completely installed Ubuntu 7.04 and finally got my second hard drive to mount, but now i don't have any permissions to do anything to it unless I'm root :(.

Can someone help?

How to set permissions depend on the file type. vfat/ntfs is different from linux file systems (ext3 reiserfs, etc).

Take a look here : [http://ubuntuforums.org/showthread.php?&t=283131](http://ubuntuforums.org/showthread.php?&t=283131)

---

### Post by Thorun on 2007-06-25
@send-Derek

"But, after you realize why it is the way it is, it makes more sence and you tend to accept that it's better and more secure."

I have exactely same problem - but i would like my Ext3 partition to be my document-partition. That's why i don't understand why it's "dangerous" to have user priveliges to that partition when i have to use it all the time. 

As it is now, the device is root:root and i can't do anything with it - which is annoying. 
If i want some files to be protected, i could just use: chmod -R a-rwx /folder/*

But maybe i'm not experienced enough yet to see the pro's and con's. :D
(have been using Ubuntu for 3 weeks and have made 15 re-installs)

---

### Post by bodhi.zazen on 2007-06-25
> **Thorun said:**
> @send-Derek

"But, after you realize why it is the way it is, it makes more sence and you tend to accept that it's better and more secure."

I have exactely same problem - but i would like my Ext3 partition to be my document-partition. That's why i don't understand why it's "dangerous" to have user priveliges to that partition when i have to use it all the time. 

As it is now, the device is root:root and i can't do anything with it - which is annoying. 
If i want some files to be protected, i could just use: chmod -R a-rwx /folder/*

But maybe i'm not experienced enough yet to see the pro's and con's. :D
(have been using Ubuntu for 3 weeks and have made 15 re-installs)

With single user boxes it is less important, but still ...

what I do for shared partitions/directories, using the group "users" as an example, is :

Ownership  user:users (like say root:users) and chmod 770 (rwxrwx---).

Now as most users are also members of users, so not much difference.

But what if we uses something else, like root:secret and permissions of 770 (files inshared directories should likely be user:users [like say Thorun:users] and 640 [660 if you want the group to be able to write to the file] (you should keep executables in $HOME/bin or /usr/local/bin). Now I can share the directory with anyone in the secret group, and now all users are members of secret.

Do you see now ? Imagine a system with say 5 or 50 or 100 users.

See here for the difference between files and directories in terms of permissions:

[http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297](http://www.zzee.com/solutions/linux-permissions.shtml#zzee_link_9_1077830297)

---

