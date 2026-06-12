---
title: "How to add USER and root password"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by satimis on 2006-07-29
Hi folks,

I have "ubuntu-6.06-amd64" installed on a AMD64 PC.  It started without problem.  On the login screen it requested inputing USER and password.  During installation it did not request adding USER.  Besides please advise how to add root password.

I can start runlevel 2/3 but without a root password I can't login.  Please help.  TIA

B.R.
satimis

---

### Post by Jagot on 2006-07-29
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by aysiu on 2006-07-29
Did you do an OEM install? Why didn't it ask you to create a user?

---

### Post by catlett on 2006-07-29
I was part of a thread where the person did an oem install. The default username at lgin was ```
oem
```
And after you log in, you have to run this command to make an account.
```
sudo oem-config-prepare
```
I have not tried this myself, so I do not know if it works or not but it couldn't hurt to try it either.
Good luck

---

### Post by satimis on 2006-07-30
Hi folks,

Gnome desktop
=============

Tks for your advice.

What is oem installation?  I ran "Ubuntu-6.06 amd_64" DVD to install Ubuntu.  Installation went through without much problem.  I was requested to input USER password but without USER name indicated.  Neither it required inputing root password.


Hi catlett,

Your advice worked here.  Tks.

Ran;
$ sudo oem-config-prepare

after typing in oem password I created a new USER a/c.  I copied/saved the terminal printout on login_root.txt on oem directory and rebooted the PC.  After reboot I can't find the file and oem directory anymore.


Ran;
System -> Administration -> Users and groups

After typing in USER password and [Enter] it popup "User and Groups" window

highlighted "root /root root" and clicked "properties"  Then entered root password on Password item there.

Now I can "su root"

Tks again.


B.R.
satimis

---

### Post by catlett on 2006-07-30
I never used the oem installmyself so I don't have personal experience. If I had to guess, I would say the oem directory may be a hidden directory. There are lots of hidden directories and files. The may have created the oem process to hide the directory after it is setup. That could be totally wrong.
For the heck of it you can enable "show hidden files" in the file browser. Go to Places<Computer. When nautilus (i.e. the file browser) opens up, go to "view" and check off "show hidden files". Now anytyhing that was hidden can be seen in nautilus. (putting a . (period) in front of a file/folder's name makes it hidden.
Now that you are at Places<Computer enter Filesystem and browse to your directory. /etc/ holds most of the systems files but it could be anywhere really.

---

### Post by satimis on 2006-07-30
Hi catlett,

Tks for your advice.

checked "show hidden files" displaying all hidden file with a "." in front.  But I can't find oem directory and the file saved on it.

B.R.
satimim

---

### Post by catlett on 2006-07-30
Now that you are at least in Ubuntu, you may want to refer to the Dapper Guide [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
It has a good section on Administrative actions, including add users/new passwords [http://doc.gwos.org/index.php/DapperGuide#User_Administration](http://doc.gwos.org/index.php/DapperGuide#User_Administration)

I only say it because it appears you do not have any sudoers (meaning you cannot use sudo and you are getting a root terminal with su)It isn't a huge issue but Ubuntu is setup around sudo and if you are following any ubuntu guides it will be using sudo.
I would follow the  Dapper guides commands and add a user [http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users](http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users)
and then add the user to the sudoers and to the admin group [http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users](http://doc.gwos.org/index.php/DapperGuide#How_to_add.2Fedit.2Fdelete_system_users)
You may not have these files. Usually if a file doesn't exist, the text editor will open a blank file and put that heading on it. If yours comes up blank I would still follow through with the actions. You will be creating the file and it should do what you need it to.

Actually I was just thinking about the fact that you may not have sudo powers. In the guide, when you see sudo... you will have to su (enter), get to a root terminal and then enter the command that is given after sudo.
Opening up the sudoer file may be an issue because the guide says you can only do it with ```
sudo visudo
```Hopefully you can su to a root terminal and then enter ```
visudo
```
For instance you couldn't do this part of the guide without sudo 
```
export EDITOR=gedit && sudo visudo
```
Hopefully you could do it like this 
```
su
```
Press enter and enter your root password. Then issue the command like this
```
export EDITOR=gedit && visudo
```You can live without sudo but I would try to set one up since everything you are going to be referring to will use sudo for ubuntu.

---

### Post by satimis on 2006-07-30
Hi catlett,

Tks for your advice.

$ sudo visudo
it opened /etc/sudoers.tmp
file without requesting for password.


However I'm going to wipe out this "Ubuntu-6.06 amd_64" OS and reintall it from "ubuntu-6.06-alternate-amd64".  Afterwards I'll continue testing your advice.

Tks

B.R.
satimis

---

### Post by satimis on 2006-08-02
Hi catlett,

Now I have Ubuntu-6.06 amd64 running which was installed from "ubuntu-6.06-alternate-amd64".

Continued the test as follows;

$ sudo visudo
Password:
started /etc/sudoers.tmp

$ visudo
visudo: /etc/sudoers: Permission denied

$ export EDITOR=gedit && sudo visudo
started gedit opening /etc/sudoers

$ su
Password:
su: Authentication failure
Sorry.


During working here PC hanged.  This happened occasionally.  I have no idea how to prevent/fix this problem nor how it happened/was caused.  Therefore I have to force-reboot the PC and started again.

B.R.
satimis

---

### Post by catlett on 2006-08-02
Now that you have Ubuntu installed correctly, you do not need su. Sudo is the command used in Ubuntu.
In most linux systems, you become root by entering su, the root password and then you are root.
With ubuntu there is only sudo and your user pasword. If you wanted to open a file as root, you do not su, password and then give the comand i.e.
```
su
```
enter root password
```
gedit /etc/apt/sources.list
```
In ubuntu to open /etc/apt/sources.list as root there is only one string
```
sudo gedit /etc/apt/sources.list
```
Enter user password (i.e. the password you log on with)

This is why I wanted you to create a user with sudo powers. In ubuntu the first user from the installation has sudo powers aka is a superuser. After that, any user added is not automatically a superuser. They are just a user until a superuser or administrator edits the sudo file to include them.
Now that you have a new install and you have superuser priveleges, you do not need to have a root paswword and you do not ned to su to a root terminal.
But if you still want a root password and to be able to su to root, here is how you do it.

To create a root password (i.e. also called a unix password)
```
sudo passwd root
```You will be prompted to enter a new unix password twice. After you will be able to su...enter the pasword you just made

You can also get to a root terminal without su/root password with
```
sudo -s -H
```Then enter your user password (i.e. the login password)

To add a user (just a user not a superuser)
```
sudo useradd ???
```
To delete a user
```
sudo userdel ???
```

You can also edit users and groups by going into the top panel at System<Administration<Users and Groups

How to add more superusers 
```
export EDITOR=gedit && sudo visudo
```
Then edit the file with the user's name you want to be added.(obviously ??? represents the user's name you want to add)
```
 ???     ALL=(ALL) ALL
```

That is just for your info. You do not need to change anythinmg if sudo is working. The crash is a little troubling. Linux systems are very stable. Crashes should not occur regularly.
Try updating. Maybe there is a "bug fix" that you haven't installed yet
```
sudo aptitude update
```
```
sudo aptitude upgrade
```

---

### Post by terry.turner on 2006-08-03
I have at last managed to install usign a downloaded alternate CD.

I ahd the same problem, and have now successfully managed to log in as "OEM" but how do I run the command "sudo oem-config-prepare"?

Alos I am finding it rather difficult to read the desktop as the test is so small.  I have a large monitor but can´t find the manufacturer on it. How do I change that?

It is also not connecting tot he internet (I am connecting via a network card and cable to a router and then to ADSL).  I guess I have to configure it smemhow, but when I was runnign Windows 2000 it did it automatically.

---

### Post by catlett on 2006-08-03
> **terry.turner said:**
> I have at last managed to install usign a downloaded alternate CD.

I ahd the same problem, and have now successfully managed to log in as "OEM" but how do I run the command "sudo oem-config-prepare"?

Alos I am finding it rather difficult to read the desktop as the test is so small.  I have a large monitor but can´t find the manufacturer on it. How do I change that?

It is also not connecting tot he internet (I am connecting via a network card and cable to a router and then to ADSL).  I guess I have to configure it smemhow, but when I was runnign Windows 2000 it did it automatically.

Go to the top panel and enter into Applications<Accessories<Terminal. The terminbal is the command line interface. When it opens enter ```
sudo oem-config-prepare
``` and then press enter.
Whenever you see soimeone talk about giving a comand or enter something in the terminal, that ios what they are talking about.
The resolution settings are in System<Preferences<Screen resolution.
You should try and find out the specs of your monitor and video card. Then run```
 sudo dpkg-reconfigure xserver-xorg
```That takes you through the x server setup. In the setup you can configure the screen resolutions. The more info on your hardware the better.
I have broadband commected straight to my ethernet card so I never had an internet issue, but the place to start is System<Administration<Network

---

