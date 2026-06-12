---
title: "Printer Driver-Edgy-Mx3215"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by mkjarema on 2007-03-15
I am working with a MX 3215 and trying to get a HP laserjet 1300 working with less bugs.  I am using the driver that comes with Edgy, but the printer isn't working as well as it should.  I have tried running the hplip-1.7.2.run but i get the following error (see image attached)


Thankx!
MKJ

---

### Post by adam s on 2007-03-15
Try looking for the file that is mentioned using cd and ls commands in a terminal window.

Does the file actually exist?
If it does exist who owns it and what are the permissions.

You may just need to do a chown or a chmod on the file.

Adam.

---

### Post by mkjarema on 2007-03-15
HI Adam, please excuse my ignorance, but I do not understand what you mean.  Could you please try to explain it?
THX:confused:

---

### Post by adam s on 2007-03-16
Hi,

Open a terminal and type

cd /
cd home
cd mjar
cd Desktop
ls -l hplip-1.7.2.run

I may be barking up the wrong tree, but this will tell you if the file exists.

The output of the ls command will tell you the permisions - an example would be :

-r-xr-xrwx 1 groupadam adam 316 2007-03-15 09:00 foo.bar

The important part of this information for you is -rwxrwxrwx

the first character here '-' tells you the file is a standard file. The main other options are 'l' for link and 'd' for directory.

The next 9 characters are built up by 3 groups of the three characters rwx.

The r stands for read permission.
The w stands for write permission
the x stands for execute permission

The first group of three tells you the permissions for the "world". This means that anybody who has access to your filesytem (imagine a shared filesystem on a network).
The second group of three tells you the permissions for your group. In the previous scenario, this would be anybody that  is within the same login group as you. In my ls the group is called groupadam, but this could just as easily be a group of specific developers working on a single design.
The third group of three are your permissions.

The ls command will tell you if the file exists, who owns it and how you are allowed to access it.

If you do not have access to the file, this would be the problem, and you can fix it by manipulating the permissions or ownership using chmod or chown respectively.

Hope this helps,

Adam.

---

### Post by mkjarema on 2007-03-17
HI Adam, Thanks for the directions.  Upon completing the chmod
my ls -l is 

mjar@mjar:~/Desktop$ ls -l hplip-1.7.2.run
-rwxrwxr-- 1 mjar mjar 11101677 2007-03-15 11:19 hplip-1.7.2.run

but I am still getting the same error when I click on the icon.....:confused: 

thanks again
-Monica

---

### Post by adam s on 2007-03-19
In the correct directory within a terminal type :

chmod 777 hplip-1.7.2.run

this should solve your problems as you only have read permissions on the file (ie no execute permissions) and therefore cannot run the file.

See if this helps.

Adam.

---

### Post by mkjarema on 2007-03-20
Well, Adam. It worked.  You are so awesome!  I hope my reports print better.  Thanks again for your help.  I have been on MS for...OMG 14 years.  I remember the old DOS days....geez, I am not that old either....

Anyway, 
THX!!!

---

### Post by adam s on 2007-03-20
> **mkjarema said:**
> Well, Adam. It worked.  You are so awesome!  I hope my reports print better.  Thanks again for your help.  I have been on MS for...OMG 14 years.  I remember the old DOS days....geez, I am not that old either....

Anyway, 
THX!!!

No problem - it is nice to help someone rather than be helped!!!! :)

---

### Post by mkjarema on 2007-03-22
well after all this...the driver was worse than the one i had.....ohhh well....I hope i can just delete the printer and then re-add
:(

---

