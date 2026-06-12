---
title: "establishing root privileges for /var/lib/dpkg/lock"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by will m. on 2007-01-27
I've re-read some of the sections on root user privileges and installing packages but am still puzzled by the last few lines (pasted below) I got when attempting to install R, a statistical application.  I am logged in with administrative privileges (not as root, of course) and attempted to install by doing the following:

```
aptitude install r-base-core
```

It started out successfully, I thought...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done   
```

But ended with the lines below:

```
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
```

My understanding is that as a user with administrative privileges I am acting as root, in some sense.

Can anyone point me to an explanation that would clarify my role as 'superuser' in this instance?

Thank you,

Will M.

---

### Post by taurus on 2007-01-27
Not until you put the sudo in front of a command!

```
sudo aptitude update
sudo aptitude install r-base-core
```

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by Tomosaur on 2007-01-27
You need to use:
```

sudo aptitude install r-base-core

```
to temporarily grant yourself root powers. This method keeps you 'logged in' (not really) as root for 15 minutes, although the time is configurable. The password it asks you for is your own login password, but you won't see it being typed in for security reasons.

In Ubuntu 'administrator' really means 'able to become root'. You still need to enter your password to do admin stuff, but if you were not an administrator, you wouldn't even get that far.

---

### Post by jvc26 on 2007-01-27
The reason for that error tends to be because you are trying to run both synaptic package manager/update manager/apt-get or aptitude from terminal or another of the similar apps at the same time. You can only run one of them at once, so close the others and re-try running it.

Oh - actually just re-read your issue and I has misread the problem, using the advice above (i.e. only have your terminal open rather than several synaptic windows) then type:
```

sudo aptitude install r-base-core

```
You have to be the superuser to use aptitude. See: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo) for more info on sudo.
Il

---

### Post by will m. on 2007-01-27
Thanks!

I had already tried 

```
sudo aptitude update
```

Followed by

```

sudo aptitude install r-base-core
```

And this was the result I got...

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
```

Nothing appears to have been installed.  Did I miss something?

Will M.

---

### Post by Tomosaur on 2007-01-27
Are you sure it's not already installed then? Try this:
```

dpkg -L r-base-core

```

---

### Post by will m. on 2007-01-27
OK!

I think it is installed after all under usr/share/R

However, it doesn't appear in my Applications menu.  Is there some way to enable its appearance there?  Most of the other apps I have installed have been done via Synaptic.

Will M.

---

### Post by taurus on 2007-01-27
You need to enable both universe & multiverse repos in /etc/apt/sources.list.  Edit /etc/apt/sources.list and remove the # sign in front of all the lines with deb at the beginning.

```
gksudo gedit /etc/apt/sources.list
sudo aptitude update
sudo aptitude install r-base-core
```

---

### Post by Tomosaur on 2007-01-27
Yup, it sure is :)

Now, bear in mind I'm not currently on my own computer here, so I'm working from memory, but I **think** the menu configuration app is in System > Preferences > Menu.

If not that, it's something very, very similar. You will need to add a new item in the menu of your choice, and then type the command you want the machine to use to launch said program. You can also set the application icon there :)

---

### Post by will m. on 2007-01-27
I thought I had done that.  Here's what my sources.list looks like

```

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
```

I appreciate your help.  I troubleshoot media/AV problems for a living but Linux is all new to me.

Will M.

---

### Post by will m. on 2007-01-27
> **Tomosaur said:**
> Yup, it sure is :)

Now, bear in mind I'm not currently on my own computer here, so I'm working from memory, but I **think** the menu configuration app is in System > Preferences > Menu.

If not that, it's something very, very similar. You will need to add a new item in the menu of your choice, and then type the command you want the machine to use to launch said program. You can also set the application icon there :)
  
At the risk of asking yet another dumb question what do I point the menu item to?  I trolled throught the R folder but am not sure what the equivalent .exe file actually is.

Will M.

---

### Post by will m. on 2007-01-27
I should have put this a bit differently.

I am not sure what command to use nor what file to point to to run R.

Been working on this for a little while using Menu Editor and Menu Layout to no avail.

Will M.

---

