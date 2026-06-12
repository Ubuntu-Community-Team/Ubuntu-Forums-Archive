---
title: "Cannot login: home directory not found"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by yoramdavid on 2007-11-06
[B]Hello help!

Every time I want to login into ubuntu, I get the following error message:[/B]
 "Your home directory is listed as:
    '/home/infteach'
    but it does not appear to exist.
    Do you want to log in with the root
    directory as your home directory?

    It is unlikely anything else will work unless
    you use a failsafe session"

**Then when I click yes (if I click no, nothinh happens), I get another error message:**
"User's $HOME/.dmrc file is being ignored.  This prevents the default session "
"and language from being saved.  File should be owned by user and have 644 "
"permissions.  User's $HOME directory must be owned by user and not writable "
"by other users."

**Then I have no choice but to click ok and get the following messa**ge:
"Your session only lasted less than 10 seconds.  If you have not logged out "
"yourself, this could mean that there is some installation problem or that "
"you may be out of diskspace.  Try logging in with one of the failsafe "
"sessions to see if you can fix this problem."

**Under "View details (~/.xsession-errors file)", the following can be read:**

/etc/gdm/PreSession/Default: registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "yo"
/etc/gdm/Xsession: Beginning session setup...
(gnome-session: 6831): Libgnomevfs-Warning ** Unable to create ~/.gnome2 directory: File or Directory does not exist
unable to create configuration directory by the gnome user 'home/yo/.gnome2/' File or Directory does not exist.

I checked from Widows and this directory does exist there.

Any help please?

thank you.

Yoram David

---

### Post by OldTimeTech on 2007-11-06
"that you may be out of diskspace"

That may be your clue...you've run out of disk space on your home partition and need to add more.

---

### Post by Fixman on 2007-11-06
Try to login as a terminal session and write
```

cd /home
mkdir $USER

```

---

### Post by yoramdavid on 2007-11-06
> **OldTimeTech said:**
> "that you may be out of diskspace"

That may be your clue...you've run out of disk space on your home partition and need to add more.

Hello,

Thanks for the reply but I have 1,44 Gb free on y home directory.

---

### Post by taurus on 2007-11-06
Boot into recovery mode from GRUB menu and see if there is a $HOME for your account.  If not sure, post

```
ls -la /home
df -h
```

---

### Post by yoramdavid on 2007-11-07
> **Fixman said:**
> Try to login as a terminal session and write
```

cd /home
mkdir $USER

```

Fixman, thanks for your help,

Doing:
cd /home
mkdir $USER:
I get the error:
Impossible to create the directory 'myusername': permission denied

---

### Post by yoramdavid on 2007-11-07
> **taurus said:**
> Boot into recovery mode from GRUB menu and see if there is a $HOME for your account.  If not sure, post

```
ls -la /home
df -h
```

taurus, thank you for your help :
'la -la /home' gives me:
drwxr~xr~X 2 root root 4096 2007-04-05 18:21
drwxr~xr~X 22 root root 4096 2007-11-05 18:55

df -h gives me:
varrun               1014M 232K 1014M  1% /var/run
varlock              1014M 4,0K 1014M  1% /var/lock
udev                 1014M 236K 1014M  1% /dev
devshm               1014M    0 1014M  0% /dev/shm
/dev/mapper/hda1       99M  60M   34M 64% /boot
/dev/disk/by-uuid/CA1480BC1480ADAF
                      3,1G 2,8G  205M 94% /media/Trabalho

---

### Post by carlosjuero on 2007-11-07
> **yoramdavid said:**
> Fixman, thanks for your help,

Doing:
cd /home
mkdir $USER:
I get the error:
Impossible to create the directory 'myusername': permission denied
```

sudo mkdir /home/<insert user name>
sudo chown -R <username>:<user group> /home/<insert user name>
sudo chmod 755 /home/<insert user name>>

```

The /home folder is not writeable by your base user, the home folder has to be created by root permissions. With the code above you are making the folder as root, changing the owner to the user it is to be home to, and then making sure the permissions are set properly (though that is just a safety precaution, the chown will work fine on an empty folder). Obviously replace the <insert user name>,<user name>, and <group> with the corresponding information from the user you are trying to create the folder for (The default group for a new user created in Ubuntu is the same name as the user; ex. JonDoe is in group JonDoe).

Edit:

Also, since this folder will be devoid of structure - you can copy the data from /etc/skel into the new folder you have created (setting the permissions appropriately like above) so that the user has a basic set up ready to go. /etc/skel is a 'skeleton' structure for all new user home folders.

---

### Post by yoramdavid on 2007-11-07
> **carlosjuero said:**
> ```

sudo mkdir /home/<insert user name>
sudo chown -R <username>:<user group> /home/<insert user name>
sudo chmod 755 /home/<insert user name>>

```

The /home folder is not writeable by your base user, the home folder has to be created by root permissions. With the code above you are making the folder as root, changing the owner to the user it is to be home to, and then making sure the permissions are set properly (though that is just a safety precaution, the chown will work fine on an empty folder). Obviously replace the <insert user name>,<user name>, and <group> with the corresponding information from the user you are trying to create the folder for (The default group for a new user created in Ubuntu is the same name as the user; ex. JonDoe is in group JonDoe).

Edit:

Also, since this folder will be devoid of structure - you can copy the data from /etc/skel into the new folder you have created (setting the permissions appropriately like above) so that the user has a basic set up ready to go. /etc/skel is a 'skeleton' structure for all new user home folders.

carlosjuero,

Thank you for your help, you solved my problem. The /etc/skel was empty, only a link to a folder called examples with a few images are there...

Will have to recreate my personal settings again, but that is the least

Yoram david
Yoram

---

### Post by carlosjuero on 2007-11-07
> **yoramdavid said:**
> carlosjuero,

Thank you for your help, you solved my problem. The /etc/skel was empty, only a link to a folder called examples with a few images are there...

Will have to recreate my personal settings again, but that is the least

Yoram david
Yoram
the /etc/skel isn't truly empty - you need to do an ls -a to see everything though (it contains a .bash profile dir, and 2 more hidden folders); best way to see 'em from the console (if not in the GUI) is to use Midnight Commander (mc from the command line, apt-get install mc if you don't have it installed) and then you can use the 2 columns to copy from the /etc/skel to the new folder. If you can get in the GUI then you can press Ctrl + H to view those files in the folder view and copy them that way.

Edit: and oh, no problem with the info. I ran into a similar situation a long time ago (early Linux distro) and learned the hard way how to get around it :)

---

### Post by yoramdavid on 2007-11-07
> **carlosjuero said:**
> the /etc/skel isn't truly empty - you need to do an ls -a to see everything though (it contains a .bash profile dir, and 2 more hidden folders); best way to see 'em from the console (if not in the GUI) is to use Midnight Commander (mc from the command line, apt-get install mc if you don't have it installed) and then you can use the 2 columns to copy from the /etc/skel to the new folder. If you can get in the GUI then you can press Ctrl + H to view those files in the folder view and copy them that way.

Edit: and oh, no problem with the info. I ran into a similar situation a long time ago (early Linux distro) and learned the hard way how to get around it :)

Thank you,

I have pressed Ctrl+H in Nautilus and saw 4 text files but no folders.
I installed the mc (Midnight Commander) but could not find it on any menu afterwards...

---

### Post by carlosjuero on 2007-11-07
> **yoramdavid said:**
> Thank you,

I have pressed Ctrl+H in Nautilus and saw 4 text files but no folders.
I installed the mc (Midnight Commander) but could not find it on any menu afterwards...
Hmm, sounds like your skeleton folder isn't set up right (/etc/skel = Skeleton :) )

mc is a text mode file browser, you use it by typing in mc in the terminal.

---

### Post by yoramdavid on 2007-11-07
> **carlosjuero said:**
> Hmm, sounds like your skeleton folder isn't set up right (/etc/skel = Skeleton :) )

mc is a text mode file browser, you use it by typing in mc in the terminal.

Ok, I see now. It seems there are lots of problems with my instalation. I am doing the update from Ubuntu 7.04 to 7.10 and I got lots of instalation errors with different files, including some login file... Just got the message that the installation was not successeful and that I might not be able to use the system...

---

