---
title: "Can't start Ubuntu"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by bvsciguy on 2007-04-03
I am trying to install Ubuntu on a IBM Thinkpad w/ a Pentium 2 processor and ~196 Mb RAM. But all but one of the times I have tried to start Unbuntu it slows to a standstill and says error on boot disk. I am on the third disk that this has happened. I burned the disk every time with burnatonce. What could be happening?
Thanks,
bvsciguy

---

### Post by taurus on 2007-04-03
I think the LiveCD needs at least 256MB of RAM to run from it.  Therefore, you should consider installing Xubuntu since it requires less RAM and it runs much faster than Gnome on an older machine.  Also, don't forget to run it at a slow speed like 4x.

[http://www.xubuntu.org](http://www.xubuntu.org)

---

### Post by igknighted on 2007-04-03
Also, get the alternate install CD.  Even the xubuntu live cd probably needs more ram than you have.

---

### Post by bvsciguy on 2007-04-04
Thanks, I finally got Xubuntu installed. Now how do I start the GUI? I have gone through all of the setup procedures, now I just need to know how to start the GUI.

---

### Post by taurus on 2007-04-04
You mean it boots into a console?  What happens when you run this command after you log in with your username and password?

```
startx
```

---

### Post by bvsciguy on 2007-04-04
Yes it boots into the console. 
It replies with command not found.

---

### Post by taurus on 2007-04-04
Try

```
sudo aptitude update
sudo aptitude install xubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by bvsciguy on 2007-04-04
No errors, but nothing happened either.

---

### Post by taurus on 2007-04-04
Were you installing the server or the oem version?  Is it Dapper or Edgy?

What's the output of this command after you log in?

```
ls -la /home
```

---

### Post by bvsciguy on 2007-04-04
Methinks, OEM, Dapper.
Output =
 
total 12
drwxr-xr-x  3 root      root     4096 2007-04-04 10:25.
drwxr-xr-x 21root      root     4096 2007-04-04 10:26..
drwxr-xr-x  2 root      root     4096 2007-04-04 11:05 benjamin

Also, I believe that I installed the alternate install version if that counts for anything.

---

### Post by taurus on 2007-04-04
If you installed the oem version of Dapper, did you remember to run this command the first time you log in with oem as your username and the password that you've created during the installing process?

```
sudo oem-config-prepare
```
And how come root owns directory /home/benjamin?

```
drwxr-xr-x 2 root root 4096 2007-04-04 11:05 benjamin
```

---

### Post by bvsciguy on 2007-04-04
I did run the first sudo code.
As for root owning the directory /home/benjamin, I have no clue.

---

