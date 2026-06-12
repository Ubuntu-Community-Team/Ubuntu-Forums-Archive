---
title: "Install Ubuntu but keep /home...what about accounts?"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by dhughes on 2007-04-21
I made a separate partition for /home and have been happily using my system but now that I am going to upgrade to feisty I didn't think about my accounts on home and what would happen to them.

 If I wipe my root partition and install Feisty what happens to my accounts? The files on /home would be linked to that account and when I reinstall a new version of Ubuntu wouldn't those accounts be wiped as well?

 Anytime I have installed Linux it has always been a complete format and reinstall I've never done it this way before, keeping /home and just reinstalling the OS.

 During install when I'm asked to create a user can I just specify the same user names and passwords again to be able to access the files on /home?

---

### Post by MiCovran on 2007-04-21
First of all, are you using a special home partition or just one for root? Type "sudo fdisk -l" (small letter L, not i), and post the output.

Edit: Sorry, you already said that.

---

### Post by MiCovran on 2007-04-21
My advice is to download a Ubuntu 7.04 CD and boot it up. Then install the new version with leaving the /home unformated.

Edit: Yes, your accounts will stay as they were. They are all kept on a /home partition in hidden folders.

---

### Post by bodhi.zazen on 2007-04-21
> **MiCovran said:**
> Edit: Yes, your accounts will stay as they were. They are all kept on a /home partition in hidden folders.

Actually that is not true. User account informationn is in /etc and will NOT be preserved with a fresh install.

With /home on a separate partition you will preserve your user data.

My advice is :

First save a copy of your users information. You need to know user names and uid, you can change passwords with a fresh install if you like.

Save a copy of /etc/passwd and /etc/group

The format of these files is 


/etc/passwd:> user-name:x:user-number:group-number:comment section:/home-directory:default-shell



/etc/group:> groupname:password:groupid:users

You may want to know each users group membership.

```
groups <user_name>
``` 

Now that you have this informatiion, install Feisty. I would only create 1 user, the admistrator, at the time of installation.

boot feisty and add the users and groups in user management. Point their home directorys to the existing ones in /home

HTH

---

### Post by MiCovran on 2007-04-21
Oh, that account. Sorry, I thought of all those passwords for firefox, gaim etc.
Anyway, I have only one user account on this machine and I installed feisty with keeping the /home partition unformated. I just used the same username and password i had before installation and everything works.

---

### Post by BaffledMollusc on 2007-04-21
> **MiCovran said:**
> Oh, that account. Sorry, I thought of all those passwords for firefox, gaim etc.
Anyway, I have only one user account on this machine and I installed feisty with keeping the /home partition unformated. I just used the same username and password i had before installation and everything works.

Are there drawbacks to this? For example, lots of programs store configuration details in hidden files in your user directory. If new versions of the programs are installed, won't these new versions get confused by the existing config files, especially if the new version of the program uses a slightly different format for its configuration files?

---

### Post by MiCovran on 2007-04-21
> **BaffledMollusc said:**
> Are there drawbacks to this? For example, lots of programs store configuration details in hidden files in your user directory. If new versions of the programs are installed, won't these new versions get confused by the existing config files, especially if the new version of the program uses a slightly different format for its configuration files?
I thought this could happen too, so I mounted the partition with live cd and deleted all hidden folders except those i wanted to keep (like .mozilla and .gaim).

---

### Post by BaffledMollusc on 2007-04-21
> **MiCovran said:**
> I thought this could happen too, so I mounted the partition with live cd and deleted all hidden folders except those i wanted to keep (like .mozilla and .gaim).

Ah, I see. Good plan!

---

### Post by Toxicity999 on 2007-04-21
simple solution, keep the same home, don't worry about it, install the new root OS, and mount the old partition as /home but make sure the user you make at install is the user made last time for the same purpose, and it will be just as you left it, but note something: Not recommended to use the old config, things _could_ go wrong, though not irreversibly so.

---

### Post by bodhi.zazen on 2007-04-21
> **MiCovran said:**
> Oh, that account. Sorry, I thought of all those passwords for firefox, gaim etc.
Anyway, I have only one user account on this machine and I installed feisty with keeping the /home partition unformated. I just used the same username and password i had before installation and everything works.

I agree. As long as you have one user (and do not change the user name) you will  be fine. I was assuming the OP was asking about a system with multiple users which is more complex.

> **MiCovran said:**
> I thought this could happen too, so I mounted the partition with live cd and deleted all hidden folders except those i wanted to keep (like .mozilla and .gaim).

In terms of those pesky . (hidden) files.  I would say that most of the time you will be OK preserving those config files.

However in that rare case where there is a conflict it can be difficult to figure out and resolve the resulting problem.

My solution is to make a data partition rather then a separate home partition. Let ubuntu make a /home on the root partition and keep all your config ( . )  files there. link our data partition to home.

Like this :

[http://ubuntuforums.org/showthread.php?&t=300246](http://ubuntuforums.org/showthread.php?&t=300246)

See my posts (Posts # 10 and 13)

HTH

---

