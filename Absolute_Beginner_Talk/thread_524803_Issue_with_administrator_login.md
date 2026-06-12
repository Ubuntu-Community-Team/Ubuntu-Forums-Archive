---
title: "Issue with administrator login"
date: 2007-08-13
forum: Absolute Beginner Talk
---

### Post by Xenthan on 2007-08-13
Alright, here's the story.  I was trying to change the xorg.conf file to turn of the touchpad on my computer and realized I needed root privileges.  Using my infinite wisdom, I went to System, Admin, Users, and ended up changing the directory for my System Administrator.  I thought that I could change it from /home/**** to /root and that would let me edit files... Unfortunately I was wrong, and it seems to have backfired horribly.  I am unable to log on to the admin account in any of the sessions (maybe it's doable in the failsafe terminal, but I'm not savvy enough to know which commands to use there).   Obviously this poses a problem, because I can't change the directory back without those privileges.  Is there any command that I can type into the terminal to manually change the directory back?  Or is there some way to transfer the administrator title to a different account?

---

### Post by Cypher on 2007-08-13
I'm not sure what you exactly changed? But if you boot into the Recovery version of Ubuntu, you will be logged in as Root. Here you should be able to revert whatever you did. 

If you tell us, step-by-step, what you did we can tell you what commands to use to revert it..

---

### Post by janipewter on 2007-08-13
You need to use sudo to edit the xorg config file. You can edit it on the command line by using the following command:

```
sudo nano /etc/xorg.conf
```

---

### Post by Xenthan on 2007-08-13
I can't remember the exact names of all the buttons I hit, but I can give you a general idea.

I went to System, then went to Administration.  At the very bottom, I clicked the "Users and Login" or something like that.  It brought me to a list of all the Users currently registered on my computer.  I clicked on my System Administrator user, clicked the Advanced tab, and then changed the top box.  It was set to /home/xen before and I changed it to /root.  

Hope that helps.

---

### Post by Arisna on 2007-08-13
It sounds like you changed the home directory of your user account to /root.  Yeah, that would prevent a graphical login.  If that is in fact what you did, the following command, entered in recovery mode, would fix it:

```
usermod -d /home/{account name} {account name}
```

By the way, if you want to edit a file with admin privileges in future, press Alt-F2 and enter the following:

```
gksu gedit {filename}
```

---

### Post by janipewter on 2007-08-13
It sounds like you've just changed your home directory from /home/<username> to /root. Which is definitely not good as you'll find your user does not have permission to write to /root.

As stated above, if you boot into the recovery mode, you'll be able to log in as root and change your user home dir back to what it should be.

---

### Post by Xenthan on 2007-08-13
Yup, that fixed it.  Thank you much.

---

