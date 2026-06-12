---
title: "[SOLVED] is there any harm in using chown?"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2008-02-22
I recently installed and mounted a new hard drive ([after some help](http://ubuntuforums.org/showthread.php?t=704054)) and I didn't have permission to access it, so I used the following command:
 ```
sudo chown -R <user> /media/extra_storage1/
```
where **<user>** is my username and **/media/extra_storage1/** is the mount point of ***sdb1*** (my new hard drive) that I set in fstab...
[B][LIST]
[*]Is it ok to set my username as ownership of this mount/hard drive or will that make me susceptible to attacks? 
[*]Also is there a betterway to do this?
[/LIST][/B]

---

### Post by taurus on 2008-02-22
It should be fine as long as it's a backup drive, not root filesystem.

---

### Post by candtalan on 2008-02-22
also consider chmod which I believes deals with access alone rather than ownership.

---

### Post by BassKozz on 2008-02-22
Thanks taurus

---

### Post by Paqman on 2008-02-22
The chown (with -R) command means you've changed the ownership of those files to yourself. That's absolutely fine if it's all your data. It would be a very bad idea for system files.

If you want other people to be able to view those files, you may have to change the premissions using the chmod command candtalan mentioned.

---

### Post by BassKozz on 2008-02-22
> **candtalan said:**
> also consider chmod which I believes deals with access alone rather than ownership.
So which is better chmod or chown?
Why would it be better to set only the access vs. ownership?

How can I undo my chown settings and change it using chmod (if it is the better way to go about it)?

---

### Post by belda on 2008-02-22
if you are a single user of the computer, than having changing the ownership to yours is sufficient, however, if there are more people, who need to acces those files, you still need to set permissions for them with chmod, also, if you are mounting the drive at startup via fstab, you should change the mount rights as well, i think that that is the best place to make it right.

---

### Post by moonlightcheese on 2008-02-22
> **B/-\ssKozz said:**
> So which is better chmod or chown?
Why would it be better to set only the access vs. ownership?

How can I undo my chown settings and change it using chmod (if it is the better way to go about it)?

what do you mean "better"?  they're used for different purposes.  you need to look up a guide on linux user permissions.  this is a very basic concept of the linux directory tree / filesystem that you need to have a firm grasp on.  i guess i can give a short version...

permissions are handled by a10bit (at least i think it's only 10bits) flag that tells how you're allowed to access that file.  there are three groups of permissions in the octet (flag).  you have the owner's permissions (what the owner can do with the file), the groups permissions (what the members of the group that the file belongs to can do with the file) and the global permissions (the permissions that all users of the system can do with the file).  there are three different types of permissions: write, read and execute.  their meanings are obvious and i shouldn't have to explain them here.  now here's the interesting part: each of these settings is represented as a single digit integer corresponding to the "bitmap" for that permission.  usually you'll see user permissions represented thusly:

-rwxrw-r--      root     wheel      filename.txt

the meaning here is fairly obvious.  the first flag just says that the file is not a directory (directories are denoted with 'd' as the first option) the owner (first three settings) can read, write and execute this file.  the users who belong to the group "wheel" can read and write to this file, and everyone else can only read it.  fairly straight forward eh?  now it gets a bit more tricky but it's not difficult.  sometimes you'll see these permissions represented as three integers.  the integers range from values 0 (no permissions) to 7 (full permissions).  this integer represents the "bitmap" value of the permissions.  so we can represent 'rwx' with '7' which is a bit quicker.  but how do you represent... say... '-wx'?

here's where you need to understand binary a bit.  binary numbers, of course, are simply 1's and 0's strung together to represent numbers.  here's how you translate those binary digits into numbers.  here is the representation of the number 7 as an example: 111.  pretty simple huh?  here's what it means.  you read from right to left (usually) and the first bit represents the 1's place, the second bit to the left represents the 2's place (since we are using base 2, not base 10).  so with two binary digits we can represent the numbers 1 through 3 thusly:

1 = 01
2 = 10
3 = 11

for 1, we have 1 in the one's place and nothing in the 2's place.  for 2, we have 1 in the 2's place and 0 in the 1's place.

i think this is more than sufficient explanation on binary, so lets apply it to permissions.  you have 3 different permissions you need to represent and the presence of a 1 or 0 in the correct 'bit position' will produce the permission you want.  here's an example of mapping integer permissions to bitwise permissions:

rwxrw-r--  = 111 110 100 = 764

so the owner can read write and execute this file, the group and read and edit it and everyone else can read it.

so as you can guess, changing who owns the file obviously has an impact on what that user and other users can do with it.  each file has a set of permissions, a group and an owner.  if that doesn't make things clear i dunno what will.

---

### Post by BassKozz on 2008-02-22
> **belda said:**
> also, if you are mounting the drive at startup via fstab, you should change the mount rights as well, i think that that is the best place to make it right.
mounts rights?

---

### Post by moonlightcheese on 2008-02-22
> **B/-\ssKozz said:**
> mounts rights?

don't get confused.  mount rights are totally different.  mount "rights" simply tell the OS how to handle the drive.  in other words, you can mount entire filesystems with read only access ensuring none of the files are changed by anyone after it is mounted.  this over-rides user permissions altogether.

---

### Post by BassKozz on 2008-02-22
> **moonlightcheese said:**
> don't get confused.  mount rights are totally different.  mount "rights" simply tell the OS how to handle the drive.  in other words, you can mount entire filesystems with read only access ensuring none of the files are changed by anyone after it is mounted.  this over-rides user permissions altogether.
Ok so that's probably not the best place to set permissions because that overrides users rights/permissions, correct?

---

### Post by moonlightcheese on 2008-02-22
> **B/-\ssKozz said:**
> Ok so that's probably not the best place to set permissions because that overrides users rights/permissions, correct?

it's not the same at all.  don't worry about fstab, that post sort of threw you off.  it has absolutely nothing to do with what you're asking.

---

### Post by BassKozz on 2008-02-22
Thanks for all the help everyone, and special thanks for the in depth explanation from **moonlightcheese** :D

I think I will leave it as is for now since I am the only user on this computer who will be using this HD, so setting ownership to myself won't hurt anything (i hope)...
But if in the future I add another user to this system I will switch from chown to chmod...
Thanks again, you guys rock :guitar:
-BassKozz

---

