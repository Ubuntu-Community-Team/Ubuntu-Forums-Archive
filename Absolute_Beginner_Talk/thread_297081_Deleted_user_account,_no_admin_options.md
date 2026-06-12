---
title: "Deleted user account, no admin options"
date: 2006-11-10
forum: Absolute Beginner Talk
---

### Post by cbkouz on 2006-11-10
Hi everyone.  I installed Ubuntu Edgy on both my laptop and desktop yesterday.  In case it matters, both are dual-booting with Windows XP.  While logged in as root (in recovery mode), I deleted my user account in an attempt to create a new one.  I used:
```
useradd -g root -p [password] -d /home/ckdesk -m ckdesk
```
to create the account.  I can log in on the gnome screen, and can access my home directory.  I cannot, however, access any of the admin tools, including the user/group item on the menu.  I've searched google and these forums extensively, but have had no luck learning how to give a user admin priveledges from the command line (in recovery mode or logged in and using sudo).  Any help would be greatly appreciated. Also, I've been a linux user for oh, 36 hours now...so an explanation of why to use a certain command (or even what I did wrong) would be awesome.  Thanks in advance.
Christina

---

### Post by johnnymac on 2006-11-10
Ewww....yucky....

You may be able to fix it if you used the edgy cd and booted into the rescue mode.  The problem is that your UID probably changed from when you deleted to when you added.  Another possible solution could be to globally change the UID in the /etc/passwd - grasping at straws here -

---

### Post by cbkouz on 2006-11-10
I'm willing to try anything.  > You may be able to fix it if you used the edgy cd and booted into the rescue mode. The problem is that your UID probably changed from when you deleted to when you added. Another possible solution could be to globally change the UID in the /etc/passwd - grasping at straws here - What would booting from the cd into rescue mode accomplish?  What is the UID?  And how do I change it globally?  Would reinstalling solve this problem?  Thanks again.  
Christina

---

### Post by taurus on 2006-11-10
From Grub menu, pick recovery mode and boot from that.  At the prompt, edit /etc/group and add that username to both adm & admin.  Reboot and that user should be able to run sudo again...

```
nano -Bw /etc/group
```

---

### Post by johnnymac on 2006-11-10
oops sorry - /etc/group not /etc/passwd....

---

### Post by cbkouz on 2006-11-10
@Taurus - Thanks for the suggestion, but I can already use sudo from the command line in the terminal.  I can't access the file structure above /home/ckdesk, nor can I access the most of the options in the system - administration menu.  The error message states that I am not allowed to access the system configuration.  What I really need to know is how to make the user "ckdesk" an administrator or create a new user as an administrator from the command line (because I cannot access "users and groups" from the menu).  Otherwise, I need to figure out how to allow root to login to gnome (from recovery mode) so that I _can_ change the user settings via the menu.  I apologize if I was unclear in my first post.  Thanks again.
Christina

---

### Post by taurus on 2006-11-10
What is the output of this little command from a prompt?

```
id
```
If you want to add a new user that can do sudo, then run

```

sudo useradd -m -G adm,admin ckdesk
sudo passwd ckdesk

```
You mean you can't do this!

```
more /etc/X11/xorg.conf
```

p.s.  You can add a user to group adm & admin from a command line.  No need to use the GUI menu!!!  Just use nano as your text editor from a recovery mode...

```
nano -Bw /etc/group
```

---

### Post by cbkouz on 2006-11-10
I figured it out.  From the recovery screen, I was able to access /etc/groups.  The user "ckdesk" was already listed in adm and admin, so I added "ckdesk" to the group root as well.  After logging into gnome, I was able to access the admin menus like I wanted to.  I added an additional new user ("cbk" profile: administrator), and logged in as that user. I can now access then entire file system (above my home directory), and once again have shortcuts to other drive partitions on my desktop.  This is where I wanted to be.  I do have a related question, though - I noticed that I am logged in as cbk, the prompt in the terminal is cbk@cbkouz-desktop:~$.  When I was logged in as ckdesk, though, the prompt was simply $.  Does this indicate which classification (for lack of better word) a user is?  If so, how would I change a user from the "$" class to the cbk@cbkouz-desktop:~$ class?  Thanks again.
Christina

---

