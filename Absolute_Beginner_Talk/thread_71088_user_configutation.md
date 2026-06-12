---
title: "user configutation"
date: 2005-10-02
forum: Absolute Beginner Talk
---

### Post by dgrafix on 2005-10-02
im in setup and appear to be going round in circles

it says enter full name which i do ie: bruce wayne¨
then it asks for a username ie: bruce
then a password ie:wayne

but it just seems to go back to the realname screen!!

---

### Post by dgrafix on 2005-10-02
ok, i pressed esc and continued with installation. I saw the graphical ubuntu screen and then it went back to the ascii setup screen saying user password cannot be blank. enter password for root account (which i did) then it its a bad idea using root do u want to create a user? i say yes and it simply asks me for a password over and over again.

So

I press escape and open a shell.
I try from the default root prompt  adduser username
then it says:
chown 1000:1000 /home/username : operation not permitted
then it says below:
groupdel: group username does not exist.

Please help

Im wondering if it may have something to do with my fat32 logical volume i have on there. When i set it up i noticed it gave it the name /home

---

### Post by wishyjr on 2005-10-02
i had the exact same problem when i first installed Ubuntu (about a week ago).  I traced it back to the options on my /home partition. let me explain..

i wanted to setup my partitions so that my /home directory was on a partition of its own (for backup purposes). Trouble was that i didnt set the partiton up correctly so it couldnt create a home for my username. Thing is, you can cancel out of the username setting up screen and ubuntu will carry on installing. I only found out after ubuntu had installed and i'd got to the login screen that i couldnt login. After rebooting into recovery mode i found (thanks to the lovely chaps on these here forums) that i hadnt defined any (loginable) users at all.

Long story short - i had to install ubuntu again and sort out my partitions. It only took another half hour, no biggie.

Hope that helps.

EDIT: [http://www.ubuntuforums.org/showthread.php?t=68055](http://www.ubuntuforums.org/showthread.php?t=68055) thats the thread i used to sort this out -think you've pretty much worked it out mate.

---

### Post by dgrafix on 2005-10-02
ok thanks. 

what do u mean by sort out partitions? i dont want my userspace /home to be on the fat32 drive, i just want that drive to be shared out on the network using smb, so i can store stuff on it from either linux or my windows machines. 
I guess what im trying to do is set up a fat32 fileshare device, i dont want my user home's on that disk

---

### Post by wishyjr on 2005-10-02
yeah, i know what you mean, its just that the first time i tried installing ubuntu i thought it'd be a good idea to setup a seperate FAT32 partition as /home. Second time round i forgot that idea and just used it same as you want to -as a storage which both linux and windows can both access.

I honestly cant remember what it was i forgot to do (it was a flag of some kind) but i'm sure it was only something simple like 'let linux read and write to this partition'. 

If you go back to the partitioning part of the install and check the settings on that partition. I think that you need to mount it as something (like /data or something) but if you leave it then ubuntu automatically mounts it as /home (correct me if im wrong).

I forgot to ask you, did you set the drive up manaully?

---

### Post by dgrafix on 2005-10-02
yes i did and i took the defaults

---

### Post by wishyjr on 2005-10-02
hmmm, well the only thing i can think of right now is try mounting that partition to something other than /home -then it'll put your home directory on the same partition as the base system and it'll let you setup a user.

i'm at work at the mo so i cant check how mine was setup exactly. If i find anything more i'll post it up.

---

