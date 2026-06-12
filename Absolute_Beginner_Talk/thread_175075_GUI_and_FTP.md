---
title: "GUI and FTP"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by jayser on 2006-05-12
Hello all I am new to Ubuntu and any flavor of Linux at that.
I just finished installing v. 5.10 and ran the server install and now I am at the command interface. How do i get into the GUI? Also can Ubuntu act as a FTP server?

Thank you,

Jayser

---

### Post by catlett on 2006-05-12
enter ```
sudo apt-get install ubuntu-desktop
```
That will install gnome. Right now you have no gui. The server install does not come with one.



Just in case you have a gui, enter ```
startx
```
That starts the gui from the command line. If it doesn't start run the other command to install gnome.

---

### Post by jayser on 2006-05-12
Thanks!

I am having one other problem and it's probably something I missed during the setup.

During the install I was asked to create a user and pass, I did this and I can log in as this user but when I use the sudo command I don't have a password for this and my user one does not work for the sudo account. Any clues?

Thanks again.

---

### Post by aysiu on 2006-05-12
[QUOTE=jayser]
During the install I was asked to create a user and pass, I did this and I can log in as this user but when I use the sudo command I don't have a password for this and my user one does not work for the sudo account. Any clues?[/QUOTE] That's weird. Try this:

Reboot and select **recovery mode**
You will then be logged in as root
Type ```
adduser jayser admin
```
Then ```
cp /etc/group /etc/group_backup
nano /etc/group
``` Make sure your username is next to the *admin* group. Reboot into normal mode.

---

### Post by jayser on 2006-05-12
oops..Disreguard that last reply. I got in.

As for the FTP question any thoughts? "can I use Ubuntu for a FTP server" if so how?

Thanks,
Jayser

---

### Post by macdo on 2006-05-12
[http://www.ubuntuforums.org/showthread.php?t=79588]("http://www.ubuntuforums.org/showthread.php?t=79588")

That should do it.

---

