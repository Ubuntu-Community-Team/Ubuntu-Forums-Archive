---
title: "I've Lost My System. Please Help"
date: 2007-10-31
forum: Absolute Beginner Talk
---

### Post by Puzzled_Pete on 2007-10-31
Due to an injudicious shutdown when logged in as root, I appear to have lost my Dapper Drake system.  I use the 'GRUB' bootloader to boot to Windows XP or Ubuntu, but when I try to log-in to Ubuntu normally, I get a "your home directory is listed as /home/<myusername>, but does not appear to exist.  Do you wish to log on as root /?  It is unlikely anything will work....."   message. I've tried fsck, which reports my filesystem OK, but I still can' t get past the problem.

I can get to a recovery mode command prompt satisfactorily but cannot find my <username> directory from there.  I must I guess have most of the system there on my ext3 partition (/dev/hda5). I have a tar backup of a slightly old version of my system on an SD card which should have my /home/<username> and dependant subdirectories in it, but can't access it from the command line.  What I'd like to do is unzip my home directory and its subdirectories from the tar backup on the SD card to the Ubuntu partition from the command line (using the -k parameter, perhaps).  Can anyone help me to do this?

This I anticipate would give me a working system with all the system updates I've made since the backup was made and without losing any data files I've created since then.  Otherwise it's back to loading a live system from disc and restoring from there, which I know works (with a couple of minor complications), but leaves me with a system with many updates to do and with some fortunately uncritical data loss.

---

### Post by ddrichardson on 2007-10-31
How about creating a new account, giving it admin group and then you can do it from the GUI?

---

### Post by hyper_ch on 2007-10-31
and why do you need to login as root in first place?

---

### Post by Puzzled_Pete on 2007-10-31
to ddrichardson: Thanks but quite simply I don't know how to do what you suggest from the command line - which is all I have. Any tips?

---

### Post by Maestro23 on 2007-10-31
> **Puzzled_Pete said:**
> to ddrichardson: Thanks but quite simply I don't know how to do what you suggest from the command line - which is all I have. Any tips?

Adding Users: Command Line - [https://help.ubuntu.com/community/AddUsersHowto?highlight=%28Users%29](https://help.ubuntu.com/community/AddUsersHowto?highlight=%28Users%29)

---

### Post by Puzzled_Pete on 2007-10-31
to hyper_ch : I dont want to log on as root but I can't log on as anything else!

---

### Post by Puzzled_Pete on 2007-11-01
to ddrichardson & maestro23: ManyThanks for yr assistance. I have got back to a GUI ok by following yr suggestions - BUT I still can't logon under my oriignal username, nor can I access my SD card, so I'm no furher forward.  My old system detected the USB flash device and put it on my Desktop so I could easily use my backup file to restore the system - which I can no longer do.

---

### Post by greg963 on 2007-11-01
Do this from 'recovery mode'

figure out if you deleted your /home/<username> directory

ls /home

if <username is not there.....

cp -R /etc/skel /home/<username>

then
chown -R <username> /home/<username>
chgrp -R <groupname> /home/<usename

<groupname> = <username> unless you have changed it

---

### Post by Puzzled_Pete on 2007-11-06
> **greg963 said:**
> Do this from 'recovery mode'

figure out if you deleted your /home/<username> directory
ls /home
if <username is not there.....
cp -R /etc/skel /home/<username>
then
chown -R <username> /home/<username>
chgrp -R <groupname> /home/<usename>
<groupname> = <username> unless you have changed it

Thanks Greg963.  I tried what you suggested; it didn't work though.  
I had a look at /etc/skel - it didn't contain my old <username>, so I gave up, and restored from my backup and took the data loss hit.  I now have a fully restored system.

Thanks to everyone for all your help.:)

---

