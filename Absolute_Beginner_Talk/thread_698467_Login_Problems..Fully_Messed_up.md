---
title: "Login Problems..Fully Messed up"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Paperkraft on 2008-02-16
I recently installed gusty on my PC, I created on user - lets call it xxx1. i went around installing certain themes and got the system messedup, i removed those themes but still the system's appearance wouldnt change. 

So i created a new user - xxx2, gave all privileges and loggedin thru xxx2. the appearance was default. So i deleted the account xxx1 and loggedin again as xxx2. but this time i couldnt see the "user manager" on the "administration" menu. i logged out and tried to login as root, but the GDm said that it cannot login me..


so my question is, Is there anyway to reverse all these or should i install Gusty allover?:confused:

---

### Post by seventhc on 2008-02-16
Did you put the second user in the *Admin* group?

---

### Post by mwx10 on 2008-02-16
did you give "xx2" administrator access?

If you want to login as root goto system > users and groups and edit root's password (is is a random system generated password by default) then goto system > administration > login window > security and tick allow local administrator logon

---

### Post by Paperkraft on 2008-02-16
No.. i didnt..

---

### Post by Paperkraft on 2008-02-16
> **mwx10 said:**
> did you give "xx2" administrator access?

If you want to login as root goto system > users and groups and edit root's password (is is a random system generated password by default) then goto system > administration > login window > security and tick allow local administrator logon


I didnt know it was random.. im new to ubuntu and the last time i used linux was 4 years ago with RHL8 and it asks for the root password during installation itself..

---

### Post by mwx10 on 2008-02-16
well then... do you have any other user accounts with administrative access?

You may want to try logging in as :

Username: ubuntu

Password: ubuntu

and see if that helps at all

---

### Post by mwx10 on 2008-02-16
> **Paperkraft said:**
> I didnt know it was random.. im new to ubuntu and the last time i used linux was 4 years ago with RHL8 and it asks for the root password during installation itself..

if you know root's password you can try logging in from shell

---

### Post by mwx10 on 2008-02-16
shell (terminal)

---

### Post by seventhc on 2008-02-16
Isn't there a way to do this by booting into recovery mode?
I think you have root access and can reset passwords from there. I don't know the command offhand though. Does anybody here know? Please post it if you can. :)

---

### Post by mwx10 on 2008-02-16
same but i can find it quickly

---

### Post by mwx10 on 2008-02-16
> **seventhc said:**
> Isn't there a way to do this by booting into recovery mode?
I think you have root access and can reset passwords from there. I don't know the command offhand though. Does anybody here know? Please post it if you can. :)

 It is "shutdown -hP now"

---

### Post by mwx10 on 2008-02-16
I just realized that you have to be root to exicute that command......

hmmmm ill look in to this

---

### Post by mwx10 on 2008-02-16
> **mwx10 said:**
> It is "shutdown -hP now"


sorry thats to return from single-user (recovery) mode to go into it is

"shutdown now"

---

### Post by mwx10 on 2008-02-16
but you still have to be root

---

### Post by seventhc on 2008-02-16
I'm talking about the command to set root password once in recovery mode.
To get to recovery you can reboot and press the Esc key while it's starting up and you should get a menu then just choose recovery mode.

---

### Post by mwx10 on 2008-02-16
> **seventhc said:**
> I'm talking about the command to set root password once in recovery mode.
To get to recovery you can reboot and press the Esc key while it's starting up and you should get a menu then just choose recovery mode.

just use a simple

passwd *username*

whall in recovery mode


Sorry for the misunderstanding :-)

---

### Post by mwx10 on 2008-02-16
Make sure to enable local administrator login whall in recovery mode

---

### Post by seventhc on 2008-02-16
Thanks for the info :)
So give that a try PaperKraft, hopefully that will get things working.

---

### Post by pebo on 2008-02-16
If that doesn't work, another way to reset sudo admin privileges may be this:
Boot from installation cd to a command line
```
mkdir /mnt/tmp
mount /dev/sdax /mnt/tmp
```(where sdax is your root partition)
Edit the sudoers file:
```
nano /mnt/tmp/etc/sudoers
```
There will probably be a line saying ```
xxx1 ALL=(ALL) ALL
```
Change that to your new user ```
xxx2 ALL=(ALL) ALL
```
Save the file. You need to then ensure the permissions are correct on the sudoers file: ```
chmod 0440 /mnt/tmp/etc/sudoers
```
Then try booting into your installation. Good luck!

---

