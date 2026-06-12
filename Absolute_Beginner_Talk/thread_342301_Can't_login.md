---
title: "Can't login"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by x4nth3r on 2007-01-19
I tried upgrading to the new kernel, everything seems fine but after i restarted i couldn't login. I can get to the login screen, but after typing in the user name and password the screen turned black and went back to the screen that prompts for the user name.. x.x
Anyway to fix this?

---

### Post by taurus on 2007-01-19
Press <Ctrl><Alt>F2 and see if you can log in with your username and password.  Then, post the outputs of these two commands here.

```
df -h
ls -la ~/.dmrc
```

---

### Post by imonlyhuman on 2007-01-19
My pc did that the other day to me:confused: ,

 try changing the sessions until you get into your pc, you have to click on the link on the bottom left hand corner, and it will bring a menu, click change session, and then try logging in.

Worked for me, but I don.t know what caused my problem.

---

### Post by x4nth3r on 2007-01-19
> **taurus said:**
> Press <Ctrl><Alt>F2 and see if you can log in with your username and password.  Then, post the outputs of these two commands here.

```
df -h
ls -la ~/.dmrc
```
How do i copy stuff from there? On to a piece for paper? x.x

---

### Post by x4nth3r on 2007-01-19
> **imonlyhuman said:**
> My pc did that the other day to me:confused: ,

 try changing the sessions until you get into your pc, you have to click on the link on the bottom left hand corner, and it will bring a menu, click change session, and then try logging in.

Worked for me, but I don.t know what caused my problem.
I tried changing the sessions, but none works. Thanks anyway =)

---

### Post by taurus on 2007-01-19
Paste the outputs here would be nice.  What does the first line say with the first command?

```
df -h
```

---

### Post by Paerez on 2007-01-19
df -h will produce something like this:
```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda2             8.1G  3.8G  4.3G  48% /
varrun                506M  144K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb             10M  116K  9.9M   2% /proc/bus/usb
udev                   10M  116K  9.9M   2% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/hda6              21G   14G  7.3G  65% /home
/dev/disk/by-uuid/F63065FB3065C2EB
                      8.0G  2.7G  5.4G  33% /media/windows

```

Take the line that says "/" under "Mounted On" and see if the "Use%" is "100%". Having a full disk can prevent you from logging in.

If it says 100%, run:
```
sudo aptitude clean
```
put in your password if necessary, that should free some space, then press CTRL+ALT+F7 to try to log in again. Good Luck

---

### Post by x4nth3r on 2007-01-19
Thanks alot to everyone who tried to help! I'm logged back in now =D

---

### Post by Paerez on 2007-01-19
Try to keep some free space on the drive, to make sure you can always log in.

---

