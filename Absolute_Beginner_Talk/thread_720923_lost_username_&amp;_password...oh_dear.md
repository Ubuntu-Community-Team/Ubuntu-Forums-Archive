---
title: "lost username &amp; password...oh dear"
date: 2008-03-10
forum: Absolute Beginner Talk
---

### Post by lantana on 2008-03-10
Installed Ubuntu 10 weeks ago  & now have lost username & password....any easy way of fixing....or do I need to reinstall?
Thanks L

---

### Post by chessercizes on 2008-03-10
hey!
i've never actually tried this myself, but try booting up in a recovery mode session and typing in:
```
passwd
```
and it'll give you the option to change your password.


hopefully that works.

have fun!

---

### Post by spiderbatdad on 2008-03-10
Press esc to enter the grub menu when prompted at start up...unless you dual boot. Then you will be brought there automatically. Select Recovery Mode for your Ubuntu kernel. At root prompt ```
cat /etc/passwd | grep 1000
``` You will see a username x:1000:1000:loginname x  (usually the same, like Bob x 1000 : Bob x 1000) Ignore the x (it represents a password.) Next do:
```
passwd -d Bob  (in our example)
``` This temporarily deletes Bob's password. Next, switch from root to Bob: ```
su Bob
passwd
``` That's two separate commands. The second will create a new password for Bob. If you don't create a new password, as far as I know, it will revert next boot. I've tried it, that seems to be what happens. Good luck.:)

---

### Post by JoshuaRL on 2008-03-10
Well, first boot into the Recovery Mode from the GRUB menu.

It show a bunch of stuff while the OS loads and then dump you into a terminal as root.  Something like:
```

root@yourcomputer:~$

```

Once you're there go do:
```

cd /home
ls

```
That will give you a list of all the folders in the /home folder.  If you only had one user, it will be the only folder in there.  The folder name is the username.

Then you could reboot and try guessing the password if you have a good idea.  If not, you'll need to reset the password.  Go into the Recovery Mode again and do:
```

passwd <username>

```
It will ask for the new password twice, then you're set.  Reboot and login to Ubuntu.

---

### Post by lloyd_b on 2008-03-10
> **lantana said:**
> Installed Ubuntu 10 weeks ago  & now have lost username & password....any easy way of fixing....or do I need to reinstall?
Thanks L

Boot up in "Recovery Mode" (If you don't see a menu when the machine first starts, press the <ESC> key when "Loading Grub" appears on the screen to bring up the menu).  Then select the entry that has "(Recovery Mode)" in the name.

This will boot you into a command-line system.  Once you get the prompt, type:
```
grep ":1000:" /etc/passwd
```

This will give you the info for the "default" user.  The part before the first ":" is the username.

Then, "passwd {username}", and enter a new password for that user.

Then reboot the machine, and you should be good to go...

Lloyd B.

---

