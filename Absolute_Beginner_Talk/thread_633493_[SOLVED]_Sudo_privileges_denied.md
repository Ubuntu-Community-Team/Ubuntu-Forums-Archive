---
title: "[SOLVED] Sudo privileges denied"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by crosspicker on 2007-12-06
I'm having a problem figuring out why I don't have any sudo privileges. I only have the 1 user profile that I set up at install, which to my understanding should be given sudo privileges by default. In Terminal any sudo commands that I input come back with an error stating that  I don't have sudo privileges or am not a member of sudoer's. I booted in recovery mode to try and add the user profile to administrators, but recieved an error while trying to open up Users and Groups. I really don't know where to start on a solution, I apologize for not providing the actual errors but will go back and take screen shots if needed.

---

### Post by StephUb on 2007-12-06
Are you on an actual ubuntu install or on a live CD ?

EDIT, sorry my bad i didn't read that part in your message.... so it's an install....

---

### Post by crosspicker on 2007-12-06
I dual boot with XP and Ubuntu 7.10.

---

### Post by Martin Witte on 2007-12-06
file /etc/sudoers determines all users wo can get root access with sudo. can you give the content of that file, and te result of the cmmand 'id'?

---

### Post by Bothered on 2007-12-06
Could you type the following in a terminal and post the results:

```
groups
```

It will display the groups you are in. To be able to administer the system, "admin" must appear on the list. If it doesn't, then it suggests that there is a problem with your /etc/group file. If it does, then it suggests there is a problem with your /etc/sudoers file.

---

### Post by crosspicker on 2007-12-06
/etc/sudoers: regular file, no read permission

That is what I get with  file /etc/sudoers.

---

### Post by crosspicker on 2007-12-06
dbouchard adm dialout cdrom floppy audio dip video plugdev scanner lpadmin

It show's adm which I'm assuming is the same as admin.

---

### Post by taurus on 2007-12-06
> **crosspicker said:**
> dbouchard adm dialout cdrom floppy audio dip video plugdev scanner lpadmin

It show's adm which I'm assuming is the same as admin.

Nope.  Adm is NOT the same as admin.  You need to add yourself to group admin again if you want to use sudo.

Boot into recovery mode from GRUB menu and run

```
adduser *username* admin
```
Replace username with your actual login name.

Then, reboot and see if you can use sudo now.

```
shutdown -r now
```

---

### Post by crosspicker on 2007-12-07
> **taurus said:**
> Nope.  Adm is NOT the same as admin.  You need to add yourself to group admin again if you want to use sudo.

Boot into recovery mode from GRUB menu and run

```
adduser *username* admin
```
Replace username with your actual login name.

Then, reboot and see if you can use sudo now.

```
shutdown -r now
```


This did the trick thank you. Unfortunately I have run into another problem while installing the update's after re-booting. The update's downloaded fine but halfway through the install the machine froze, nothing happened for about ten minutes so I switched off and then re-booted. Now after entering my user name and password it locks up, the background color comes up but nothing loads. This also happen's when I try to boot in safe graphics mode, and it also does this if I boot into recovery mode and at the prompt type "startx". When I try to run the live CD, the Ubuntu logo comes up with a status bar showing something loading and then disappears and leaves me a blinking icon in the upper left corner of the screen. The only thing that work's is booting into recovery mode, I can at least get to a command prompt. The initial reboot has apparently corrupted something, but now I'm stuck because the CD won't run for me to do a reinstall if I wanted to.

---

