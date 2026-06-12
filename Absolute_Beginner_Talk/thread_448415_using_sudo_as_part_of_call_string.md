---
title: "using sudo as part of call string"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by wpshooter on 2007-05-19
Can the SUDO command be used as part of the string to automatically call a program during session startup ?

The reason I ask is because apparently even though I installed my Belkin shutdown software as sub-directory of my home directory, in order to start the program (upsd), I have to use the sudo command.  The same applies for the monitor interface portion of the program, I have to issue sudo ./monitor in order for it to start running.

I know I could just place the command with sudo in front of it in the automatic startup of sessions section but I thought I would ask first before trying it.

Thanks.

P. S. - the reason, of course, that I want to do this is so I don't have to manually issue the command to start the shutdown software every time I might reboot the computer.

---

### Post by Gen2ly on 2007-05-19
Dang, thats crazy.  Hi there wpshooter.  Are you sure you absolutely need sudo?  hmm.. If you type ./monitor do you have to sudo first.  K, your file must have been permissiion problems.  Try to change the ownershitp of the script (in this instance "monitor")

```
sudo chmod 755 monitor
```

You probably installed this program as root and now it has root file permissions.  You'l probably want to change onwership group too:

```
sudo chown username:username monitor
```

Have you tried installing the program as non root?  Also if the above doesnt' work you can  edit visudo to allow the programs you need:

```
sudo visudo
```

```
# Allow non-root user to use program
%user ALL=(root) NOPASSWD: /sbin/myprogram
%user ALL=(root) NOPASSWD: /usr/bin/myotherprogram
```

---

### Post by wpshooter on 2007-05-19
There was an** install** script file in the untarred files.

I had placed and untarred the tar.file in a sub-directory of my home directory.

But yet when I tried ./install it would NOT run, had to use sudo ./install to get it to run.  And even then when it prompted for the place of installation I refused the default /usr/local/bulldog (which I had tried earlier) and opted instead for another subdirectory which I had created off of /home.  And inspite of all this I have to use sudo ./upsd and sudo ./monitor.

How do I get this program to install and run without the requirement of root permissions ?  Or is this a problem due to the fact that it is not specifically written for Ubuntu which works somewhat different from other Linux distributions ?

Thanks.

P.S. - I just looked at the properties of both the sub-directory that I created under home and the files in it.

          The sub-directory is shown as being owned by me the local user but the files in it are shown as owned by root and most of them have a little picture of a LOCK on the file icon.  What does this mean ?

          Here is what I get when I try to run the install command without SUDO.

            :~/bulldog_FILES$ ./install
You must login under root to execute the program.
Bye !

---

### Post by 3rdalbum on 2007-05-19
Change the file's ownership, so it's owned by root. You will need to open Nautilus as root, then right-click on the program's icon and go Properties, then the Permissions tab. Change the ownership, then click the "Set User ID" checkbox.

You can do that with any programs that you need to run as root without a password. Please use this feature carefully.

EDIT: I've just been informed. First, you will need to go into gconf-editor and enable: apps > nautilus > preferences > Show Advanced Permissions to get the proper permissions tab to come up.

---

### Post by wpshooter on 2007-05-19
> **3rdalbum said:**
> Change the file's ownership, so it's owned by root. You will need to open Nautilus as root, then right-click on the program's icon and go Properties, then the Permissions tab. Change the ownership, then click the "Set User ID" checkbox.

You can do that with any programs that you need to run as root without a password. Please use this feature carefully.

EDIT: I've just been informed. First, you will need to go into gconf-editor and enable: apps > nautilus > preferences > Show Advanced Permissions to get the proper permissions tab to come up.

Thanks, but what I really want to accomplish is having this programming setup so that it is NOT owned by ROOT and thus I will be able to place the proper command in the sessions section so that the UPSD program will be started AUTOMATICALLY upon each boot when I come up into the session as the normal NON-root user.

I just think that the people who are writing these programs are not taking into account the difference in the way Ubuntu/Linux handles things as compared to other Linux distributions !!!

---

