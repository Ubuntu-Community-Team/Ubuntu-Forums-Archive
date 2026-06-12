---
title: "/etc/sudoers"
date: 2007-09-03
forum: Absolute Beginner Talk
---

### Post by ant2ne on 2007-09-03
> antsvr@antubuntu:/etc$ sudo chmod 0440 /etc/sudoers
sudo: /etc/sudoers is mode 0700, should be 0440
antsvr@antubuntu:/etc$ duh
How can I change a file from read only, but it wont let me change it back again? Did I just break my system again?

---

### Post by taurus on 2007-09-03
Boot into recovery mode from GRUB menu and at the prompt, change it back to the way it was before.

```
chmod 440 /etc/sudoers
```
Reboot and you should be good again.

```
shutdown -r now
```

---

### Post by ant2ne on 2007-09-03
recovery mode did the same thing.

---

### Post by taurus on 2007-09-03
Are you sure you are in the recovery mode?  What does the prompt look like when you are in the recovery mode?

Otherwise, boot your machine from the LiveCD, mount the partition where / is, and change the permission of /etc/sudoers on the harddrive.

---

### Post by ant2ne on 2007-09-03
booting from CD worked, thanks! Now back to my original problem that was the reason for editing this file in the first place...

---

### Post by taurus on 2007-09-03
Absolutely not.  You should never edit /etc/sudoers at all.  And if you have to, you need to use visudo.

```
sudo visudo
```
Any reason you edited /etc/sudoers in the first place?

---

### Post by aysiu on 2007-09-03
More importantly, any reason you changed the permissions on the /etc/sudoers file? You can edit it without changing the permissions to 700 from 440.

---

### Post by ant2ne on 2007-09-03
[http://ubuntuforums.org/showthread.php?t=187899](http://ubuntuforums.org/showthread.php?t=187899)
[http://ubuntuforums.org/showthread.php?t=489662](http://ubuntuforums.org/showthread.php?t=489662)
[http://ubuntuforums.org/showthread.php?p=3302816#post3302816](http://ubuntuforums.org/showthread.php?p=3302816#post3302816)

Then other things started crashing. And I couldn't remember how (or why) I changed sudoers in the first place. So in order to gedit it I had to change the permissions to 700. Oddly, I don't know how I could change the permissions from 0440 to 0700, but I couldn't change it back.  That is friggin' weird.

Now, back to my samba situation...

---

