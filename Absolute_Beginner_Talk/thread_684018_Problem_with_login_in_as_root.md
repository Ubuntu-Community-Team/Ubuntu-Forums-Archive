---
title: "Problem with login in as root"
date: 2008-01-31
forum: Absolute Beginner Talk
---

### Post by wiktor91 on 2008-01-31
Hi!
I'm very new to Linux and i have problem with login in as root user. 
Well first my problem was that i didn't knew a root password, i searched how to change password and i changed it. I thought that that's it, but when i try to login on login screen i type username: root and password: mypassword, and than i get message that system administrator don't alow to login from this screen ??? Well i'm not sure that i got it translated right because my Ubuntu is on Croatian but it says to me that i canot login from this screen. What is the problem? Things got even more complicated when i played with users and i deleted my account that i made when i instaled Ubuntu. I thought that maybe than i will be able to login as root but... 

I found tutorial that shows how to make user account from terminal so i made one that i use now but i don't have any rights, i don't have a 2/3 of options in Administration that i had with my previous account. 
Please somoene tell me what to do, how can i login as root or at least how can i make a account with more privileges?

Thanks!

---

### Post by red_Marvin on 2008-01-31
I do not personally use the root account, but use the sudo command,
but anyway if you are able to log in as root i terminal mode, try starting X (the graphics system) with the command *startx*.
Then you should be able to manage users as usual.

---

### Post by Nerdriot on 2008-01-31
Well, I hope I can help you, heh... I can't promise much, though (I'm new, too).

From what I understand, there's no real reason to log in as root anymore, since you can do root stuff using "sudo".

For instance, if you try to modify certain files (for instance, xorg.conf), I believe you have to be root to do it. Well, instead of logging in as root, you can do "sudo gedit /etc/X11/xorg.conf". "Sudo" basically lets you issue commands as superuser, without actually having to log in as such.

I hope this helps you a little. :)

---

### Post by jan quark on 2008-01-31
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

that should leave no questions open

---

### Post by wiktor91 on 2008-01-31
Well apreciate your help but i must login as root to make new account because with one i have now i can't do anything... 
Well i translated the message i get when trying to login on login screen. It says "system administrator is not alowed to login from this screen". What is the problem?

I remind you i don't know a **** about Linux so if you can explain me all in steps. Thank you!

---

### Post by LowSky on 2008-01-31
ubuntu doesnt use root natively, it can be changed but  there is no reason to be root as alll thing can be done with the sudo command
if you want to create new accounts from ubuntu got to

system> administration>users and groups

there should be two account already there, root and your normal user accouint (please dont mess with root account)

you can add new users very easily and select how much computer comtrol they have

---

### Post by wiktor91 on 2008-01-31
But i deleted my first account and now i have only one that i created thru terminal with tutorial but it has no privileges and i canot even go to Administration-Users and Groups because it's not there so i can't create any users....

If somebody can tell me how to create system user from terminal i would be very thankfull!

---

### Post by bodhi.zazen on 2008-01-31
There is no need to log in as root

You will need to be in the admin group, then use sudo (gksu for graphical apps)

To get a root shell, use ```
sudo -i
```

How to fix your current dilema :

boot to recovery mode, at the command line type ```
startx
```

You will now be running gnome (your desktop) as root.

Go to user management, add your new user to the admin (and any other groups), reboot

---

### Post by anaconda on 2008-01-31
graphical root login is disabled by default.. even if you have enabled root account..

so if you want to login graphically(as user root) you will have to go to:
System>Administration>login window
and from the security tab check the "Allow local system administrator login"

and to the other question.. if you are in terminal with root rights you can create a new user by:
```
adduser new_username
```

and then when you have created the user you can add that user to admin group (give him sudo rights) with:
```
adduser new_username admin
```

---

### Post by wiktor91 on 2008-01-31
> **anaconda said:**
> graphical root login is disabled by default.. even if you have enabled root account..

so if you want to login graphically(as user root) you will have to go to:
System>Administration>login window
and from the security tab check the "Allow local system administrator login"

and to the other question.. if you are in terminal with root rights you can create a new user by:
```
adduser new_username
```

and then when you have created the user you can add that user to admin group (give him sudo rights) with:
```
adduser new_username admin
```


THANK YOU SOOO MUCH! It helped me! I created a new user with all privileges as my first user, but i'm not sure now if i can delete my first user that i created on instalation? 

Thank you all!

---

