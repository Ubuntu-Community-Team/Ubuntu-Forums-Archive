---
title: "Problem using sudo"
date: 2006-07-15
forum: Absolute Beginner Talk
---

### Post by gezz on 2006-07-15
I've just installed Ubuntu 5.04 (waiting for the latest one to be shipped to me), and because I have Windows, I used "expert" (huh!) install. I think I survived the partitioning alright, but then it asked me for a root password, which I gave, and gave again. Asked me something about a "shadow" password or something, and I clicked "No". Then it asked for a username and password, which I did, using the same password as root. It continued installing ok.

Now, when I want to get into any root level utilities like synaptic, I get a password request which I fill in - and nothing happens! When I try it again and enter my password, I get a message saying: "Failed to run /usr/sbin/synaptic: Child terminated in 1 status"

I tried editing the /etc/sudoers and /etc/group files as suggested in
[http://psychocats.net/ubuntu/sudo.php](http://psychocats.net/ubuntu/sudo.php)

but still getting error messages. Any ideas anyone? Thanks a lot!

---

### Post by catlett on 2006-07-15
Try changing the root password
```
sudo passwd root
```Hopefully changing the root password will help.
At least you will be able to get a root terminal. Meaning if you want to get into synaptic after you nake trhe new password. Ehter ```
su
```Then give the new password. You will then be at ```
root@ubuntu~:
```Which is the root terminal. No need for sudo. Just enter ```
synaptic
```or anything ales to get it to run.
Usually there is a warning about using the rot password for a user password. Hopefully it was just a conflict anfd changing the root will solve it.

---

### Post by gezz on 2006-07-16
Thanks very much catlett. I'll give it a try...

---

### Post by 3rdalbum on 2006-07-16
Earlier versions of Ubuntu like yours had an annoying bug. I got bitten by it. If you set a root password in the Expert install, then the normal user account can't access the sudo command, and the root user can't log into the GUI because Ubuntu doesn't let you by default.

Go into Rescue mode from GRUB. You will be logged in as root. Now you can go "System > Administration > Users And Groups". Click on your normal user and then the Properties button. In the rightmost tab, check "Allow user to access administration functions" and anything else you want. Close the program, restart the computer into normal Ubuntu, and now it should all be working. (with the normal user being able to use the sudo command, and therefore the gksudo command, and therefore Synaptic).

---

### Post by gezz on 2006-07-16
Thanks catlett and 3rd album. I tried catlett's idea but couldn't get into root to change password. So in recovery mode I edited the /etc/sudoers file, inserting at the bottom:
myusername ALL=(ALL) ALL

Then back in normal mode I could get into Users and Groups and change my  user password.

It seems to be working fine now! I'm not sure what I'm stuffing up in the process!

---

