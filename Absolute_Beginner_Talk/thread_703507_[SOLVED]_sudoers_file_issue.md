---
title: "[SOLVED] sudoers file issue"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by dgoodma on 2008-02-21
OK, catch 22 here. I edited the sudoers file with sudo visudo. I wanted to add an account to be able to run all commands as "root". I have joined this computer to Active Directory, and this user is logging in with their Domain credentials: AD\xxxx

I added AD\xxxx like root was shown 

Now when I try to sudo, I get a syntax error on line 18, but it does not run the command. So, now I cannot edit the sudoers file to fix it. Would be nice to have "root" su - to fix this... is there some way to fix this?

---

### Post by aysiu on 2008-02-21
> **dgoodma said:**
> OK, catch 22 here. I edited the sudoers file with sudo visudo. I wanted to add an account to be able to run all commands as "root". I have joined this computer to Active Directory, and this user is logging in with their Domain credentials: AD\xxxx

I added AD\xxxx like root was shown 

Now when I try to sudo, I get a syntax error on line 18, but it does not run the command. So, now I cannot edit the sudoers file to fix it. Would be nice to have "root" su - to fix this... is there some way to fix this?
Boot into recovery mode (the second boot option--press Esc to get to the boot menu if you have a single-boot).

This will log you in as root. Then you can ```
sudo nano /etc/sudoers
``` to edit the sudoers file. When you're done, press Control-X, Y, Enter to save. Then type ```
sudo shutdown -r now
``` to reboot into regular mode.

---

### Post by sisco311 on 2008-02-21
> **aysiu said:**
> Boot into recovery mode (the second boot option--press Esc to get to the boot menu if you have a single-boot).

This will log you in as root. Then you can ```
sudo nano /etc/sudoers
``` to edit the sudoers file. When you're done, press Control-X, Y, Enter to save. Then type ```
sudo shutdown -r now
``` to reboot into regular mode.

in recovery mode you are logged in as root. you don't need to use sudo.

after you edit the file set the correct permissions:
```
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
```

---

### Post by aysiu on 2008-02-21
> **sisco311 said:**
> in recovery mode you are logged in as root. you don't need to use sudo.

after you edit the file set the correct permissions:
```
chmod 0440 /etc/sudoers
chown root:root /etc/sudoers
```
Ah, good point. But even though you don't need *sudo*, the commands will still work.

---

### Post by dgoodma on 2008-02-21
I booted into Recovery mode, from there I was able to just use vi /etc/sudoers to fix the issue.

Thanks all.

---

