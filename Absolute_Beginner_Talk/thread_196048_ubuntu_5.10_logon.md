---
title: "ubuntu 5.10 logon"
date: 2006-06-13
forum: Absolute Beginner Talk
---

### Post by spm9999 on 2006-06-13
My dad gave me a CD with the Ubuntu software to try out. I installed it and while installing it asked for a password for I guess the administrator. But it never asked for username. 

Now when I boot and when the ubuntu logon screen comes up it asks for user name and password.. I have no Idea. I don't remember putting in a username.  Is there something I missed or did wrong?

---

### Post by boleyn on 2006-06-13
[QUOTE=spm9999]My dad gave me a CD with the Ubuntu software to try out. I installed it and while installing it asked for a password for I guess the administrator. But it never asked for username. 

Now when I boot and when the ubuntu logon screen comes up it asks for user name and password.. I have no Idea. I don't remember putting in a username.  Is there something I missed or did wrong?[/QUOTE]
Ihad the same problem on one install and couldn't remember other than my usual password etc. which wouldn;t work. Had to put it down to a typo error as I was also cooking during install. I had to re-install being careful about typo's. Not too long a job but well worth the effort.

---

### Post by Harleen on 2006-06-13
During installation you should be asked for a user name and a password.
If you are sure that you weren't asked for a password, than you may have installed the server version of Ubuntu. As far as I remember, you are asked for the root password only than (or administrator, to speak in Windows terms;) ).
If you did the server install, you can login with username "root" and your given password and will end up on a command line interface in text only mode. To turn the server install to a usual installation all you have to type "apt-get install ubuntu-desktop".
If you already start into the graphical mode, than you already have done the standard installation and obviously missed the user name question. You can also correct this, but a new installation seems to be the easier way for a beginner.

---

### Post by catlett on 2006-06-13
I don't believe the install will let you go past the username part. There is NO administrator pasword in Ubuntu. There is only your user password. That is why it is highly unlikely that you didn't create a username.
THE password in Ubuntu is the users password. It is used for log in and to get administrative powers. (using the term "sudo" before a command invokes administrative powers. You are asked for your user  password to confirm that you want to make the next command as an administrator). Again this is why the making of a user name and password is a BIG deal during install. 
Try to think of what name you would have put in for an account. Maybe you mistook it as a place to enter your name.
Now that I think of it.  During Ubuntu's install it will ask you for your full name and then it will ask you for a user name BUT the thing to be careful of is Ubuntu will offer you a user name in the next screen. It is possible that you just hit enter and accepted the user name they gave by default.
Maybe you can figure it out. When you go through the install it will ask for your username . If you enter "John Doe" the installer on the next screen will offer you "John" as a user name. Did you enter your first and last name during install? If you did your first name may be the user name a.k.a login name.
Even if you get to that you will have a password problem. You could try just hitting enter after you enter your name . I never tried it but you may be able to leave the password section blank and your password will be activated by just pressing enter.
I don't know of any other way other than reinstalling to bypass the password at login.
Good luckl.

---

### Post by spm9999 on 2006-06-13
thanks for the replies.. I sure don't remember a user name part in the installation.. But I am installing again and will find out what I messed up on..

---

### Post by kurimaw on 2006-06-14
is the username created on installation a root user or not? if not is it safe to use on a daily computing basis...

i'm on a network where most computers have windows on them (and i mean most...)

thanx...

---

