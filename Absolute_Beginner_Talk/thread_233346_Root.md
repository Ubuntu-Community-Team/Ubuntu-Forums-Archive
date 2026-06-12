---
title: "Root"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by Takeikin on 2006-08-10
I installed Ubuntu months ago, when Breezy was the up-to-date version, before switching to PCLinuxOS for a time. I've had a few issues with PCLOS and decided to try Ubuntu again. I didn't spend much time at all with Ubuntu last time, so I suppose I'm somewhat new to it. 
Anyway, I have a problem with root. Specifically, the fact that it doesn't exist. It seems that I can just type $sudo * and my account's password, and I'm doing things that are apparently supposed to be done only by root. 
When I tried to log in as root, the user didn't exist.
There's no root account.
This, IMO, is a Very Bad Thing.
Is there any way to create a root account with a password different from that of my normal account, which should not be able to use its password for su functions?

---

### Post by Fass on 2006-08-10
```
sudo passwd root
```

Then run visudo and edit the sudoers file to your specs, or remove your user from the admin group.

IMO, there is nothing "bad" about sudo at all. As long as you only keep tabs on which users you allow into the admin group, it's basically the same as having a root user.

---

### Post by Hokputooy on 2006-08-10
To set a root password type into a terminal:
$sudo passwd root
Enter your password and then to login in to root type $su and enter the root password.

---

### Post by skale on 2006-08-10
```
sudo aptitude remove sudo && passwd root
```
I guess that will do it if you really want it so. I believe there is a better way by tinkering with the /etc/sudoers file, I don't know how really.

---

### Post by 5-HT on 2006-08-10
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Also, if you'd like to remove your user's sudo rights you'll need to take yourself out of the adm/admin group, or just remove that entry from /etc/sudoers.

BTW, Ubuntu locks the root account and utilizes sudo for security purposes. If you really feel using sudo is a bad thing, the root account can easily be unlocked and sudo privileges removed.

---

### Post by Takeikin on 2006-08-10
Thanks :D

---

### Post by xenon2000 on 2006-08-10
Thanks for having this simple solution posted. I am a previous Slackware user and while I am fine with sudo and will keep using sudo, I just had an Ubuntu experience where sudo did not work and having the root account would have made the fix easy.

I had an issue today where any sudo command would result in a message about the timestamp being too far in the future.

a check of the log files

ls /var/log -lrt

showed that many logs had a timestamp too far into the future. Of course since sudo didn't work because of this, I could not touch the files to fix it.

Anyways, I posted in another thread about how I got partial sudo back and was able to touch the files and reboot.

but I could have just logged in as root and

touch /var/log/*

rebooted and been done.

Anyways. sudo is great and I will still use it, but I went ahead and enabled the root account for local use only. SSH and other remote access will still be denied for root login. But now I have a local way to be root without sudo. Thanks again.

---

