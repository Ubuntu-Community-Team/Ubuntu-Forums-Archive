---
title: "Seperate SSH Logins ?"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by KevinD_Atl on 2008-03-18
- Few SSH Questions -

So I've been up and running great on 7.04 with the SSH server.  I use my only account to login, the one that I log into the desktop with.  I'm using WinSCP as the Windows client from external networks.

Soon, I will need to give others access to just a few directories, but I don't want to give them my credentials, and don't want to setup normal system users.

Can I just setup SSH login accounts for seperate users?

Anyway I can limit them to a chosen directory, like \home\generic\accounting  when they login, and hid the rest of the directories?

---

### Post by jordanmthomas on 2008-03-18
Why are you opposed to creating normal users?  I am a little confused by that.
You can have them all share a home directory.

---

### Post by Xiong Chiamiov on 2008-03-18
To my (limited) knowledge, there is no way to create other user accounts besides, as you say, normal accounts.  Once those are created, you can give/revoke them any permissions on any folders/files, including viewing.

---

### Post by Oldsoldier2003 on 2008-03-18
> **KevinD_Atl said:**
> - Few SSH Questions -

So I've been up and running great on 7.04 with the SSH server.  I use my only account to login, the one that I log into the desktop with.  I'm using WinSCP as the Windows client from external networks.

Soon, I will need to give others access to just a few directories, but I don't want to give them my credentials, and don't want to setup normal system users.

Can I just setup SSH login accounts for seperate users?

Anyway I can limit them to a chosen directory, like \home\generic\accounting  when they login, and hid the rest of the directories?
yes you can point them to the same home directory. If you are really paranoid you can install jailkit and limit their shell access as well as confine them to a jailed directory...

---

### Post by KevinD_Atl on 2008-03-18
[FONT="Verdana"]C'mon guys , I'm lazy!  

I figured that I would have to make seperate users per instance, or just let them share one which is just as worse~[/FONT]

---

### Post by The Cog on 2008-03-18
You can prevent users from getting a shell login by setting their shell executable to /bin/false or some other non-existent file. This is set in the advanced tab of usersand groups management. 

But I don;t think you can limit their access to the filesystem with SSH. Lots of the filesystem is world readable. I gather the latest version of sshd has a ChrootDirectory
option - it's included in Hardy's repos.

---

### Post by Oldsoldier2003 on 2008-03-18
> **The Cog said:**
> You can prevent users from getting a shell login by setting their shell executable to /bin/false or some other non-existent file. This is set in the advanced tab of usersand groups management. 

But I don;t think you can limit their access to the filesystem with SSH. Lots of the filesystem is world readable. I gather the latest version of sshd has a ChrootDirectory
option - it's included in Hardy's repos.

Setting their shell to bin/flase creates another issue. by doing so they cannot ssh in or sftp. you now are faced with using ftp (unsecure) or ftp over ssl ( which is harder to set up).

You can limit shell access over SSH by chrooting/jailkitting the users, but a mis configured chroot is also a security vulnerability. Either way it can be done, just takes a bit of work.

---

### Post by kevdog on 2008-03-19
Linux jailkit although it takes about 10 minutes to setup after you know what you are doing, takes about 1 night to get fairly proficient at -- about 3-4 hours.  Here is the package I use -- once you screw it up a few times (reinstall, etc), you get the hang of it.  Its like anything else:

[http://olivier.sessink.nl/jailkit/](http://olivier.sessink.nl/jailkit/)

---

### Post by hyper_ch on 2008-03-19
I use MySecureShell for that... users can use WinSCP to log but are jailed in their home folder.

---

### Post by kevdog on 2008-03-20
> **hyper_ch said:**
> I use MySecureShell for that... users can use WinSCP to log but are jailed in their home folder.

Link for MySecureShell??  Is it GPL?

---

### Post by hyper_ch on 2008-03-20
[http://mysecureshell.sourceforge.net/](http://mysecureshell.sourceforge.net/)

and here's a little howto that got me started with it:  [http://www.howtoforge.com/mysecureshell_sftp_debian_etch](http://www.howtoforge.com/mysecureshell_sftp_debian_etch)

---

