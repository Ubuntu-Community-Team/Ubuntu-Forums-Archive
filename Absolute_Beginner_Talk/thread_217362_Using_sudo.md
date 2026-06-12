---
title: "Using sudo"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by RobCai on 2006-07-17
Hi I have just installed Ubuntu, and need to configure GRUB. How does one use sudo? It asks for a password - but only accepts my user one, not the root password. After that I don't get any privileges. Have I set up my normal user as a guest account?

With thanks
Rob

---

### Post by aysiu on 2006-07-17
[http://help.ubuntu.com/community/RootSudo](http://help.ubuntu.com/community/RootSudo)

It should allow you to get privileges. Can you post the output of this command, for example? ```
sudo aptitude update
```

---

### Post by RobCai on 2006-07-17
Will do - thanks aysiu

---

### Post by aysiu on 2006-07-17
For example, if you did not have permission (administrative privileges), this is what you'd get: ```
username@ubuntu:~$ aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied )
E: Couldn't lock list directory..are you root?
``` However, if you *did* have privileges, you'd get something like this: ```
username@ubuntu:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 http://archive.ubuntu.com dapper Release.gpg [189B]
Get:2 http://archive.ubuntu.com dapper-updates Release.gpg [189B]
Get:3 http://archive.canonical.com dapper-commercial Release.gpg [191B]
Get:4 http://security.ubuntu.com dapper-security Release.gpg [189B]
Get:5 http://archive.ubuntu.com dapper-backports Release.gpg [189B]
Hit http://archive.ubuntu.com dapper Release
Hit http://archive.canonical.com dapper-commercial Release
Get:6 http://security.ubuntu.com dapper-security Release [30.9kB]
Get:7 http://archive.ubuntu.com dapper-updates Release [30.9kB]
Hit http://archive.canonical.com dapper-commercial/main Packages
Ign http://packages.freecontrib.org dapper Release.gpg
Ign http://packages.freecontrib.org dapper Release
Get:8 http://archive.ubuntu.com dapper-backports Release [19.6kB]
Ign http://packages.freecontrib.org dapper/free Packages
Hit http://archive.ubuntu.com dapper/main Packages
Hit http://archive.ubuntu.com dapper/restricted Packages
Hit http://archive.ubuntu.com dapper/main Sources
Hit http://archive.ubuntu.com dapper/restricted Sources
Hit http://archive.ubuntu.com dapper/universe Packages
Hit http://archive.ubuntu.com dapper/universe Sources
Hit http://archive.ubuntu.com dapper/multiverse Packages
Hit http://archive.ubuntu.com dapper/multiverse Sources
Ign http://packages.freecontrib.org dapper/non-free Packages
Get:9 http://archive.ubuntu.com dapper-updates/main Packages [42.8kB]
Get:10 http://security.ubuntu.com dapper-security/main Packages [36.8kB]
Ign http://packages.freecontrib.org dapper/free Sources
Ign http://packages.freecontrib.org dapper/non-free Sources
Get:11 http://archive.ubuntu.com dapper-updates/restricted Packages [14B]
Get:12 http://archive.ubuntu.com dapper-updates/main Sources [24.9kB]
Get:13 http://archive.ubuntu.com dapper-updates/restricted Sources [14B]
Get:14 http://archive.ubuntu.com dapper-backports/main Packages [14B]
Get:15 http://archive.ubuntu.com dapper-backports/restricted Packages [14B]
Get:16 http://archive.ubuntu.com dapper-backports/universe Packages [14B]
Get:17 http://archive.ubuntu.com dapper-backports/multiverse Packages [14B]
Hit http://packages.freecontrib.org dapper/free Packages
Hit http://packages.freecontrib.org dapper/non-free Packages
Hit http://packages.freecontrib.org dapper/free Sources
Get:18 http://security.ubuntu.com dapper-security/restricted Packages [4558B]
Get:19 http://security.ubuntu.com dapper-security/main Sources [9118B]
Get:20 http://security.ubuntu.com dapper-security/restricted Sources [974B]
Get:21 http://security.ubuntu.com dapper-security/universe Packages [6951B]
Hit http://packages.freecontrib.org dapper/non-free Sources
Get:22 http://security.ubuntu.com dapper-security/universe Sources [902B]
Fetched 209kB in 3s (69.3kB/s)
Reading package lists... Done
username@ubuntu:~$
```

---

### Post by 3rdalbum on 2006-07-17
I think you're trying to use sudo incorrectly. This is how it should be used:

```

chris@compaq:~$ sudo aptitude
Password:

```

The sudo command runs the rest of the line as root user. So in this instance, the Aptitude program is given root privileges until it quits; subsequent commands in the terminal are still just run as normal user.

If you want a root terminal, you type:
```
sudo su
```

Then subsequent commands you type will be executed as root.

---

### Post by RobCai on 2006-07-17
Hi aysiu and 3rdalbum

Thanks for the tips. Running sudo aptitude - I am prompted for my passwd, thereafter it just gives:

rob@ubuntu:~$ sudo aptitude
rob@ubuntu:~$ aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Couldn't lock list directory..are you root?

I can work around this with su - but something is wrong?

Regards Rob

---

### Post by Frank Golden on 2006-07-17
The command is like aysiu says "sudo aptitude update" on one line
without quotes. Then enter. You will be prompted for the password
you created when you installed Ubuntu. Then you should see something like the output aysiu shows in second example. 
That is your computer updating it's repositories.
After that is done you will be at the command prompt again.
Just like aysiu shows. It looks like you entered "sudo aptitude" on one line then "aptitude update" on the next.

---

### Post by RobCai on 2006-07-17
Hi Frank

No heres the output from your suggestion:

rob@ubuntu:~$ sudo aptitude update
Password:
rob@ubuntu:~$

Thats it - just blinks. Would appreciate any thoughts!

Thanks Rob

---

### Post by Ragazzo on 2006-07-17
> **RobCai said:**
> Hi Frank

No heres the output from your suggestion:

rob@ubuntu:~$ sudo aptitude update
Password:
rob@ubuntu:~$

Thats it - just blinks. Would appreciate any thoughts!

Thanks Rob

Are you the only user on the computer? You perhaps don't have admin rights (only the first user gets them automatically).

Edit: Write "groups" in the command line. One of the groups should be "admin".

Edit2: Better command is "sudo -l". Tell us what it prints.

---

### Post by Frank Golden on 2006-07-17
Hi RobCai,
Dumb question on my part but you did type in a password?
BTW when you do so nothing appears after the prompt not even ****
or anything like that. But data is being entered. A security
feature ??? I guess. I bet Ragazzo is right. I didn't know that about multiusers.

---

### Post by RobCai on 2006-07-17
Frank and Ragazzo

Sorry for the delay - just come out of a work meeting. Here is the output:

rob@ubuntu:~$ groups
rob adm dialout cdrom floppy audio dip video plugdev lpadmin scanner
rob@ubuntu:~$ sudo -l
Password:
Sorry, user rob may not run sudo on localhost.
rob@ubuntu:~$

I am entering my user password at the prompt. Maybe I'm consiered a guest?

Thanks for for time - really appreciated

Rob

---

### Post by Ragazzo on 2006-07-17
You need to add yourself to the group "admin". You do that with the command "sudo usermod -aG admin yourname" but it's a catch-22 because you need admin rights to give admin rights. One way is to use the recovery mode (select during boot) and you will be logged in as root.

---

### Post by RobCai on 2006-07-17
Thanks so much Ragazzo that last advice solved it.

For others with a similar problem here is the complete solution (copied from castaway at [http://www.ubuntuforums.org/archive/index.php/t-78180.htm)](http://www.ubuntuforums.org/archive/index.php/t-78180.htm)). Since I was able to use su I did:

1) At the terminal prompt enter:
su

When requested for the password, enter the root password.

2) Add a new group, admin, to the group file:
groupadd admin

3) Add the user-name to the admin group:
adduser user-name admin

4) Add the new group, admin, to the sudoers file and assign it root privleges:

Start the special editing program for the sudoers file:

visudo

Use the down arrow to go to bottom of the file and add:

%admin ALL=(ALL) ALL

Hit <Ctrl>+<X> to exit.
Hit <Y> to save the file.
Hit <Enter> to confirm the file name and leave the visudo program.

Many thanks to Ragazzo for pointing me to the right solution a the others who helped out - this is a great forum!

Rob

---

### Post by Frank Golden on 2006-07-17
Hi RobCai,
   Congrats. You didn't mention you did the expert install.

---

