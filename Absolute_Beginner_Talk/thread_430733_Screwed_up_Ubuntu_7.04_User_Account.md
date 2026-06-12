---
title: "Screwed up Ubuntu 7.04 User Account"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by eyemann on 2007-05-02
Hi all,  I'm new to Ubuntu, coming from the PC world.

I was hoping to make my user something akin to an administrator.  

I don't remember exactly what I changed in the Gnome UI, but I think I changed my User to either the Root Group or Root directory thinking it would change my user to administrator.

When I booted again after this change, I was not able to log into Ubuntu.  I instead got an error saying that my user was not accessing it's home directory. (I'll try to find the exact error for you later).  It tells me to login with one of the failsafe sessions.

I've tried logging in through one of the fail safe sessions, but I get the same results. 

I am still able to login via the terminal.  

My question is... is there a way for me to create a new user through the terminal so that I can get back into the Gnome interface?

Thanks in advance for any help.

---

### Post by viciouslime on 2007-05-02
The adduser command will add a user :) Type adduser --help to see how it works.

---

### Post by eyemann on 2007-05-02
I have actually tried the add user function, however, that doesn't get me access to Gnome for some reason.

---

### Post by Carlos Santiago on 2007-05-02
login with an admin account, then:

sudo useradd newuser
sudo passwd newuser
<type password>
<confirm password>

Change newuser to whatever you want

---

### Post by Carlos Santiago on 2007-05-02
If you lost your admin account, boot in super user mode
Boot, and in the grub selection screen, edit the line and add 'single' (without ' )  to the end of the line
Then enter the useradd and passwd commands stated above.
Reboot again

---

### Post by John.Michael.Kane on 2007-05-02
Another option is to boot in to singleuser mode, and type. This should allow you to reset your account.

passwd -d [username]

Next type: 
passwd -k [username]

---

### Post by eyemann on 2007-05-02
All,

I have the new User and new password, but it still won't let me into the Gnome GUI for some reason.  Is there another command to make it a Gnome user?

*Thanks for all the suggestions so far.*


P.S. Mr. Plissken How does one boot into singleuser mode?

---

