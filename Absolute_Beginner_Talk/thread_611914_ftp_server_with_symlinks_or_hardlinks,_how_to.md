---
title: "ftp server with symlinks or hardlinks, how to?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by bartkl on 2007-11-13
I've recently installed and succesfully configured vsftpd, but I have a few wishes.
First of all, I followed:
[http://ubuntuforums.org/showthread.php?t=518293](http://ubuntuforums.org/showthread.php?t=518293)
Thanks to epimeteo for this handy guide :)

I have a few questions though. I want to share my music with friends, and have multiple physical dirs on my hdd containing music. I'd like to link them to the same location on the ftp server.

Example:
I want the subdirs in  /music/blues0 and /music/blues1 to be linked at the same location /home/ftpuser/Blues on the ftp server. 
I did this (succesfully) using symbolic links. (is this the best way?)
I have also succesfully chmodded the /music/ partition recursively with mask 774, same goes for homedir of ftpuser. Then I made sure my ftpuser config file of vsftpd  (/etc/vsftpd/workers in epimeteo's guide) contained "chroot_local_user=NO".
I did the same thing (even though I don't believe it's necessary) with the general /etc/vsftpd.conf file.

So permissions are fine and the user is not chrooted. Still, if I connect I can't enter the directories. on top of that some files are being seen as dirs in FileZilla (which I used to connect) :S

Please help. Thanks!

---

### Post by bartkl on 2007-11-13
did you just tell me to delete the contents of my homefolder?
damn I should've paid more attention. i deleted a lot of stuff I didn't want to delete :(
i think you meant 

sudo rm -rf /home/ftpuser


ah man this sucks :(. well it's my own fault.
anyways, if you were trying to check permissiosn: they're fine. i can delete and create inside the homedir of ftpuser. I think my linux isn't from now on :(

---

### Post by schorsch on 2007-11-13
> **pclinuxftw87 said:**
> hmmmm

```
******
```

post results need to know some info first ty

DON'T DO THAT!!!!

---

### Post by bartkl on 2007-11-13
can't believe I bought it :(, i actually knew what that would do, but i didn't even read.
blindly trusting that lamer. i do hope you get banned pclinuxftw87. what a bad taste of humor.
thanks for the warning schorsch.

---

### Post by svalding on 2007-11-13
haha, you wait till this community ganks your ip address, and then we'll see how linux-saavy you are. This is a forum to get people started using linux. How exactly are they supposed to learn with an *** like you coming in and having them delete their /home directories. Someone must have plopped your brain into /dev/null as a baby.

---

