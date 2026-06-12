---
title: "the super user"
date: 2006-08-19
forum: Absolute Beginner Talk
---

### Post by salowalker on 2006-08-19
I'm not sure what I did, but all of a sudden I can't log in as su through the command prompt.  It simply prompts for password and after I put in my password it says Authentication Failed.  (I don't have on caps :) ) 

How do I set-up/change the super user?

Thanks,,,

---

### Post by jrjr on 2006-08-19
.

---

### Post by salowalker on 2006-08-19
no, im not really sure where/how to. do i create a new profile in the terminal window?

ive used linux for about three hours now.

---

### Post by jrjr on 2006-08-19
.

---

### Post by salowalker on 2006-08-19
i was trying to set up xampp for linux.  on the install instructions it says 
<blockquote>   1. Go to a Linux shell and login as the system administrator root:

      su

   2. Extract the downloaded archive file to /opt:

      tar xvfz xampp-linux-1.5.3a.tar.gz -C /opt

      Warning: Please use only this command to install XAMPP. DON'T use any Microsoft Windows tools to extract the archive, it won't work.

      Warning 2: already installed XAMPP versions get overwritten by this command.

That's all. XAMPP is now installed below the /opt/lampp directory.</blockquote>

on [http://www.apachefriends.org/en/xampp-linux.html](http://www.apachefriends.org/en/xampp-linux.html)

-------------

---

### Post by jrjr on 2006-08-19
.

---

### Post by jrjr on 2006-08-19
.

---

### Post by salowalker on 2006-08-19
that worked! thanks. it had worked before, and i had the same password as my user login, then all of a sudden it quit working, not sure why...

thanks for the help, im sure ill be back in a few minutes with more ?'s.

---

### Post by catlett on 2006-08-19
If you see instructions on a how to are from an installation read me, you have to remember that Ubuntu is different than most linux distros.
Ubuntu does not use su and does not have a root account. Root is achieved on a per command basis by prefixing the command with sudo.

So if instructions say "su to root and enter apt-get install foo" the other distros would need to commands
```
su
```After pressing enter you would be at a root terminal and then you would enter ```
apt-get install foo
```
In ubuntu you would just enter one command ```
sudo apt-get install foo
```
You can create a root account but it isn't how ubuntu is set up. You can do anything you need with sudo.

---

### Post by steve.horsley on 2006-08-20
My guess is that you were using **sudo su** to become root before. This should still work for you. If so, you may want to re-lock the root account with the command:
**sudo passwd -l root**
and this will get you back to the state things are in when you install.

---

### Post by jimmygoon on 2006-08-20
Or just don't use 'su'... Simply prepend your commands with 'sudo'. That or install xmms from the repositories: 'sudo apt-get install xmms'

---

