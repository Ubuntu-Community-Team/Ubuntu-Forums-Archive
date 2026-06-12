---
title: "Login?"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by tdaman927 on 2006-07-07
hello i just installed ubuntu and it booted up and it asks for a login so i type it in and it wont let me type my pw in so i hit enter and it Login incorrect 


What should i do?!?!?

Thanks Tyler

---

### Post by shoot2kill on 2006-07-07
did you enter the password and username during setup...?

make sure you have no CAPS...

---

### Post by Albi on 2006-07-07
If it didn't ask for username during installation, I'm afraid you'll have to reinstall like this:
[http://psychocats.net/ubuntu/xubuntu.php](http://psychocats.net/ubuntu/xubuntu.php)

Just replace xubuntu-desktop with ubuntu-desktop after the server install if u don't want xubuntu.

Edit: And don't do step 8, and you need to dl the server cd

---

### Post by tdaman927 on 2006-07-07
is there a way to reset the login ?

or just reinstall?

---

### Post by PriceChild on 2006-07-07
> **tdaman927 said:**
> it wont let me type my pw in so i hit enter and it Login incorrect

Is this a graphical log in screen?

If you're at a terminal for some reason, then your password won't be shown when you type it in (no asterisks), so just type it in and hit enter. Then we should be able to help you get to a graphical screen.

---

### Post by aysiu on 2006-07-07
Boot into recovery mode.

This will make you root.

Then type ```
passwd tdaman
``` and set your password.

Type ```
reboot
``` to reboot and go into normal mode and log in.

---

### Post by tdaman927 on 2006-07-07
if i reinstall what mode should i install text,OEM,server?

---

### Post by aysiu on 2006-07-07
> **tdaman927 said:**
> if i reinstall what mode should i install text,OEM,server?
It depends on what you want.

I'm assuming you're using the Alternate CD, since the Desktop CD doesn't have those options.

**Install to the Hard Disk** will give you a regular home user graphical environment

**OEM** allows you to configure and install Ubuntu without creating a username or password. This is for resellers who will allow consumers to create their own usernames and passwords after they buy the Ubuntu computer.

**Server** is for... servers. If you want to host your own web space.

---

### Post by crystal on 2006-07-07
EDIT: better reply above

---

### Post by tdaman927 on 2006-07-07
i isstalled OEm and it still asked for a ubuntu login


wat should i do to have no login?

---

### Post by PriceChild on 2006-07-07
So using oem as your username worked? And you don't want to have to log in each time? :S

Sorry can't quite understand you.

---

### Post by bigjack on 2006-07-07
> **aysiu said:**
> Boot into recovery mode.

This will make you root.

Then type ```
passwd tdaman
``` and set your password.

Type ```
reboot
``` to reboot and go into normal mode and log in.



How do I boot into recovery mode with Xubuntu?  Just lost ability to log in.  Won't recognize PW.  Tried to do recovery with Xubuntu disk, but can't correct login problem until reformat etc.

---

### Post by aysiu on 2006-07-07
> **bigjack said:**
> How do I boot into recovery mode with Xubuntu?  Just lost ability to log in.  Won't recognize PW.  Tried to do recovery with Xubuntu disk, but can't correct login problem until reformat etc. When you first boot up, there should be several Grub entries: a normal kernel, a recovery mode kernel, and then memtest.

Select the recovery mode.

---

### Post by tdaman927 on 2006-07-07
how would i boot in recovery mode ?  like wat would i need to type

---

### Post by aysiu on 2006-07-07
You don't need to type anything.

You reboot.

Then the first screen you see should be a Grub menu if you're dual-booting.

If you're not dual-booting, press **Escape** to see the Grub menu.

The Grub menu is the screenshot I attached to my last post.

---

### Post by tdaman927 on 2006-07-07
ok so im at root@ubuntu :~#     so wat do i do after that

---

### Post by aysiu on 2006-07-07
Well, if your username is *tdaman*, and it exists, you would do ```
passwd tdaman
``` to change the password.

If the account doesn't exist, add it: ```
adduser tdaman admin
``` In fact, that may not be such a bad command to run anyway, as it will make sure you're in the *admin* (sudo) group.

---

### Post by tdaman927 on 2006-07-07
and wat if it doesnt exist wat should i do ?

---

### Post by aysiu on 2006-07-07
If it doesn't exist: ```
adduser tdaman admin
```

---

### Post by tdaman927 on 2006-07-07
it doesnt work it says adduser: The user 'tdaman' does not exist

---

### Post by aysiu on 2006-07-07
How about just this, then? ```
adduser tdaman
```

---

### Post by tdaman927 on 2006-07-07
ok  that works but now it wont let me type aanything when it says unix pwd

---

### Post by aysiu on 2006-07-07
Yes, it will. It's just not showing you what you're typing.

Type the password and hit **Enter**.

---

### Post by steve.horsley on 2006-07-07
You're doing a great job, Aysiu. 

As a side question, does the live CD have a rescue mode like the alternate installer? I couldn't find one, and couldn't figure out how to chroot to the hard drive like the rescue mode seems to - I gave in and downloaded the laternate installer with a working puter.

---

### Post by aysiu on 2006-07-07
That's a bit beyond me, unfortunately.

---

### Post by tdaman927 on 2006-07-07
it say says "The programs included with theubuntu system are free software; the exact distribution terms for each program are described in the individual files in /usr/share/doc/*/copyright.

Ubuntu coms with absolutely no warranty, to the extent permitted by appilcable law.
tyler@ubuntu :~$

---

### Post by aysiu on 2006-07-08
Is that *after* you've added the user...? What's the problem? Did you get something like this first? ```
**adduser tdaman**
Password:
Adding user `tdaman'...
Adding new group `tdaman' (1002).
Adding new user `tdaman' (1002) with group `tdaman'.
Creating home directory `/home/tdaman'.
Copying files from `/etc/skel'
Enter new UNIX password:
Retype new UNIX password:
passwd: password updated successfully
Changing the user information for test
Enter the new value, or press ENTER for the default
        Full Name []: **tdaman**
        Room Number []:
        Work Phone []:
        Home Phone []:
        Other []:
Is the information correct? [y/N] y
``` If so, you're good. Next step is this: ```
**adduser tdaman admin**
Adding user `tdaman' to group `admin'...
Done.

```

---

### Post by tdaman927 on 2006-07-08
wat should i do all i want to do is use the damn os so after the tyler@ubuntu:~$      wat should i type to boot or whatever

---

### Post by aysiu on 2006-07-08
Oh! So user's already added? Rebooted out of recovery mode? Well, if you're using Gnome, type ```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
``` If you're using KDE, type ```
sudo aptitude update
sudo aptitude install kubuntu-desktop
sudo /etc/init.d/kdm start
```

---

### Post by tdaman927 on 2006-07-08
ok i did all of that and it is still sittting there saying tyler@ubunt :~$_ what should i type to boot to the desktop after i login?

---

### Post by cyberlite on 2006-07-08
Hey
I had the same problem this moning when I installed the OS.
Install in text mode then it will ask you for the user name and pw.8)

---

### Post by tdaman927 on 2006-07-08
ok i did all the install and typed in my user name and it still goes to tyler@ubuntu:~$

---

### Post by aysiu on 2006-07-08
> **tdaman927 said:**
> ok i did all the install and typed in my user name and it still goes to tyler@ubuntu:~$
This may help:
[http://www.psychocats.net/ubuntu/nox](http://www.psychocats.net/ubuntu/nox)

---

### Post by tdaman927 on 2006-07-08
Thanks u all i finally got it to work and i love !!!!!! Tyler

---

