---
title: "Two annoying problems"
date: 2006-10-23
forum: Absolute Beginner Talk
---

### Post by spamzilla on 2006-10-23
1) I cannot get gaim to connect to the internet at all. I read somewhere that if you selected "use http method" then MSN would work. However this isn't the case for me. AIM won't connect either :(

2) I keep getting a message saying that I have 12 new updates to download and install. So I click install updates and the updates refuse to download and install. This is odd as I earlier managed to install 187 updates literally minutes before!

I guess an update is upsetting my (wireless) internet connection so I can no longer donwload updates and conenct to the net with gaim.

Has anyone found a fix or a workaround for this problem?

Cheers :P

---

### Post by pbaehr on 2006-10-23
Regarding #2, try opening the terminal and typing:
```

sudo aptitude update
sudo aptitude dist-upgrade

```

It will either work or give you an error message that you can post here for further help.

EDIT: By the way, you'll have to give it your user password after the first command, if you're not already familiar with sudo.

---

### Post by spamzilla on 2006-10-23
Here's what I got from typing in that command:

```
matt@matt-laptop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Initialising package states... Done
Building tag database... Done
Err http://gb.archive.ubuntu.com dapper Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://security.ubuntu.com dapper-security Release.gpg
  Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
Err http://repository.debuntu.org dapper Release.gpg
  Could not connect to repository.debuntu.org:80 (1.0.0.0), connection timed outErr http://gb.archive.ubuntu.com dapper-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Reading package lists... Done
```

I got a similar output when i entered 

```
sudo aptitude dist-upgrade
```

---

### Post by pbaehr on 2006-10-23
Other than updates and GAIM your internet connection works?

Are you connecting through a proxy?

---

### Post by spamzilla on 2006-10-23
Yep my internet is fine (that's how I'm making these posts ;)) and I am not using any proxies.

---

### Post by spamzilla on 2006-10-23
I also cannot download packages from synaptic package manager, as my connection times out :( Does anyone know what could be at fault?

---

### Post by spamzilla on 2006-10-24
If it helps, I was able to download about 200 updates, and install them before this problem occured.

---

