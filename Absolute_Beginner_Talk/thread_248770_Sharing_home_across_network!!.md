---
title: "Sharing /home across network!!"
date: 2006-09-01
forum: Absolute Beginner Talk
---

### Post by dragze on 2006-09-01
Hi, i would like to share the /home directory across the network of my linux machines, thus making it so that you could save a pic for example on machine 1 and then go on machine 2 and have access to that pic or wotever.

Now so far i have archeived this using NFS by sharing the /home directory on machine 1. and on machine 2. editing the /etc/fstab config to mount the home directory of machine 1. This works fine and does just what i want untill i discovered a little problem, which is rather obvious that i would have this problem and that is programs like firefox access preference files from the home directory etc, which means i cant open firefox on machine 1. and machine 2. at the same time!! + i think this might cause problems wid ssh keys etc??

Im sure there must be a way round this but i dont know wot, so any suggestions on wot would be the best method??

The possible methods around this i have come up with are as follows:
1. Make a share folder inside the /home directory, e.g. /home/user/share and mount share on each /home user of the other pc's. Downfall of this is having to make more mount points in fstab and if a new user account is added then fstab has to be updated aswell.

2. Move the preference files outside of the /home directory which would mean every user has the same preferences, probably not the most desirable method.

3. Make a seperate user account for each user and as long as there not logged on two machines with the same account at the same time problem solved, but my users would rather just be able to use the one account, so not a very desirable method either.

As i said before there must be a better way around this, surely there are people here who have a centralised /home area and just share/mount it on other pc's on the network??

Please help! :D

Cheers in advance,
dragze.

---

### Post by mssever on 2006-09-01
There are two options that I would recommend. One is to create a separate share directory outside of /home and mount that. It could be symlinked to the users' home dirs if they want. Then, either make it writable by everyone, or set the sticky bit on it, which will allow anyone to read files on it but only allow the owner to write to it (this is how /tmp works).

The other option would be to go ahead and create separate users. I think that it is almost always best to have every person have his/her own account.

---

