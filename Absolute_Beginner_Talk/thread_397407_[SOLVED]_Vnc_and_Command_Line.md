---
title: "[SOLVED] Vnc and Command Line ?"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by ashmew2 on 2007-03-30
HI Every1 , I needed to know some things....
I have installed ubuntu on many of my friends' PCs using Remote Desktop (when they were on the live cd) by doing this in the terminal :

```
vncviewer <IP>
```

I have also helped them in learning the graphical part by using this but the problem is that whenever there is a need to do something which involves shutting down the X server (on the targeted machine) , i get automatically disconnected...so is there any way so that i could have full control over the tty also ?

Thanks

---

### Post by etank on 2007-03-30
If you want a remote command line connection then you should install openssh-server on the remote machine. Then if the X server stops or is restarted then it doesn't affect you. To do that do```
sudo aptitude install openssh-server
```then on your machine you would run ```
ssh username@remotemachine
```You will have to have a user account on that machine to be able to log in however.

---

### Post by ashmew2 on 2007-03-30
So there isnt anyway like we could share a common tty ? something similar to the remote desktop..only command line instead of graphical ?

---

### Post by ashmew2 on 2007-04-01
ok thanks etank , i logged in just fine using the terminal but how do i use that ssh access ? i mean how do i install applications on my friend's pc etc ?

---

### Post by ashmew2 on 2007-06-22
/bump

---

### Post by wormser on 2007-06-22
You should tunnel your vnc with ssh.

```
ssh -L 5901:localhost:5901 username@ipaddress
```

then in a different shell:

```
vncviewer localhost:5901
```

It might be a different port than 5901 usually 5900-5902.  The first 5901 is your machines local port so you can change it to something different.

In ssh you are on their machine and can run commands like apt-get.

I hope that helps.

---

### Post by ashmew2 on 2007-06-22
Thanks mate , uve solved one of the biggest problems ive faced till now 

Thanks a LOT!!

---

