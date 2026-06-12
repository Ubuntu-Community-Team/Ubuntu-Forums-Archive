---
title: "SU, SUDO, and a root user"
date: 2005-11-07
forum: Absolute Beginner Talk
---

### Post by flipz on 2005-11-07
It's been a while since I've had to post on any newbie forums. :lol:

I have been using Fedora for a year at school, and finally decided to make the switch at home. Well after a bunch of problems and Fedora not installing correctly, Ubuntu was recommended to me by 5 different people. And wow, the installation was a breeze (breezy as a badger I suppose. :p).

My biggest problem is this whole root thing. The first time I tried to SU and login as root, I realized I never even set a root password. I did some googling, and came across other people just as surprised to find there is no root user in Ubuntu.

It is getting extremely annoying having to chown every time I'm trying to edit any file or do anything. I learned the trick of typing sudo before you do something, but that doesn't help when I'm in the GUI and editing files with a text editor. I can't ever save them. Then I have to open a terminal, type sudo chown, blah blah. It's just getting really old. :( 

Is there a way I can setup a root account? Or type some command so that at least temporarily I have full control over the system? I am trying to compile a package right now, and I get an error from gcc saying that it can't create executables. I presume this is due to not being root. As well as many other problems.

Thanks!

-flipz

PS- I posted this in new user because while I may have some experience, it's my first time setting up my own computer with linux, and my first time ever using Ubuntu. Thanks again.

Edit: I suppose I should specify that I installed Ubuntu 5.10 (Breezy Badger).

---

### Post by az on 2005-11-07
Install build-essential and you should get all the tools you need to build executables.

You can create a root account by setting a root password using passwd.

Overall, most people do not do this.  You have complete control over your system using sudo.  It is an elegant alternative.

---

### Post by Freddie.Ruddick on 2005-11-07
[QUOTE=flipz]
It is getting extremely annoying having to chown every time I'm trying to edit any file or do anything. I learned the trick of typing sudo before you do something, but that doesn't help when I'm in the GUI and editing files with a text editor. I can't ever save them. Then I have to open a terminal, type sudo chown, blah blah. It's just getting really old. :( 
Thanks!
[/quote]

As has been said, use build-essential. RE: in a text editor, have you tried sudo gedit, or run as different user?

---

### Post by Kvark on 2005-11-07
So first you open a terminal and type "sudo chown blahblah" and then you open nautilus and navigate to the file to open it with gedit?
It would be easier to just type "sudo gedit /parth/file" in the terminal.

To get root access without opening a command terminal... Add a custom launcher to the panel and enter "gksudo nautilus" as it's command. Then when you want root access you just click it, enter your password and get a nautilus window with root access, you will also have root access to any files you open from that nautilus window.

---

### Post by patrick295767 on 2005-11-07
```
 su - 
```
  
```
  sudo /bin/bash   
```
  
could maybe work ?
  
Pat'

---

### Post by patrick295767 on 2005-11-07
[QUOTE=patrick295767]```
 su - 
```
  
```
  sudo /bin/bash   
```
  
could maybe work ?
  
Pat'[/QUOTE]
  
From the xterm, u can start the rox-filer for instance and use everthg as root (no ?) 
  
```
  sudo /bin/bash 
rox &
  
```

---

### Post by Lambert on 2005-11-07
The wiki is your friend. Link at top of page.

You can go here to read more about root and sudo in ubuntu. They have a different approach then other distros.

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges](https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges)

---

### Post by nitricacid on 2005-11-07
If you are trying to edit text you could always make a folder in the home directory and then CP (copy) the text to the folder (in home dir) and then you can edit & save the text till your hearts content, then once you have edited everything you need to just CP the text doc back to the original place where you got it from.

I too have to edit text and some exec files so what i do is just open the folder where they are located, open a bash window and then just type 'sudo gedit' and drag the file i need to edit in to the bash window and press ENTER (i.e. sudo gedit /etc/apt/sources.list).
The text editor pops up and i can edit & save all my work straight to the folder where it is located.

As far as having to constantly use a bash window and SUDO to edit or install items, i don't see a problem with that since it just give me more of a hands on and a better understanding of linux and the bash window.

---

### Post by flipz on 2005-11-07
Thanks for all of the replies! You guys are hands down the most helpful forum I've ever been on, no matter what the topic!

[QUOTE=azz]Install build-essential and you should get all the tools you need to build executables.

You can create a root account by setting a root password using passwd.
[/QUOTE]

The very first post helped me, thanks azz. :)  I installed build-essential, but also used chown passwd to add a password to the root account. 

Thanks again everyone! My next question is about my wireless adapter. I'm back in windows now.  :(  I'm posting that in a different thread though as it's not related to the root account.

-flipz / brent

---

### Post by Fortigurn on 2005-11-08
[QUOTE=Lambert]The wiki is your friend. Link at top of page.

You can go here to read more about root and sudo in ubuntu. They have a different approach then other distros.

[https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges](https://wiki.ubuntu.com/RootSudo?action=show&redirect=RootPrivileges)[/QUOTE]

I have read this and I am still at sea:

[list][*]  I can't find the terminal
[*]  I have a FAT32 partition which is owned by 'root' so I can't write to it
[*]  The main partition (root), is also owned by 'root', so I can't write to that either (though I can install programs on it using 'Add Applications'
[*]  I'm having problems installing Folding@Home as well, but that might be another issue[/list]

---

### Post by peanut butter on 2005-11-08
do this in terminal to enable root:

sudo passwd root

# System -> Administration -> Login Screen Setup
# Login Screen Setup

Security Tab -> Options -> Allow root to login with GDM (Checked)

then

System -> Administration -> Users and Groups
and click on root, then add it to all groups
from ubuntuguide.org

---

### Post by Lambert on 2005-11-08
> I can't find the terminal
At the top panel, click on applications, and I'm not at my linux box so I don't remember the exact name but it's the first one in the list. Go to it's drop down list and you'll find it there.
> I have a FAT32 partition which is owned by 'root' so I can't write to it
As in most things I find in linux, there are a couple ways to do things (yea for choice:razz: ). You can change owner ship of the partition, you can set up the root account and set up your user in the root group. 
If it's a partition that everyone gets permission to write to you just need to change permissions for the partition. Open nautilus by hitting alt + F2 type [COLOR="Sienna"]gksudo nautilus[/COLOR] and go to that file ( my guess is /mnt/hda?) right click on it and change everyone's permissions to write. Otherwise look at changing and using groups to limit who can write to the partion. You can search more for linux permissions or chown or chmod or chgrp for more info.
> The main partition (root), is also owned by 'root', so I can't write to that either (though I can install programs on it using 'Add Applications'
You want to keep this like this. You will want to set up seperate folders with in the file system where you can save items by changing permissions of those directories. Anything currently owned by root you will want to leave it like that unless it's a directory you know can't messe up the os, things like the fat32 partition if it's just has storage folders on it. For items like config files or other files inside current directories owned by root, if you need to edit those then you just sudo <gedit> (or whatever program) <name of file>
When you install programs you are probably doing it through sudo which gives you temporary access to all necessary files to install. You sudo from a terminal or you can alt+F2 and type [COLOR="#a0522d"]gksudo <name of program>
[/COLOR]

---

### Post by flipz on 2005-11-08
[QUOTE=peanut butter]
# System -> Administration -> Login Screen Setup
# Login Screen Setup
[/QUOTE]

I'm happy I checked back up on this thread.

Thanks peanut butter!

-flipz

---

### Post by Fortigurn on 2005-11-09
Thanks, I'll give that a go.  :)

---

### Post by bluefrog on 2005-11-10
sudo gedit  works fine...
no need to give root a password.
james

---

### Post by kazuya on 2005-11-21
thanks peanut. You are a lifesaver. This is the main reason, I may be staying still with this distro? I shall definitly utilize this as it shall prove most helpful in troubleshooting my other numerous issues.

To the guys that refuse for fear of damage to system, it is afterall my choice to do so. Give me the warning and danger, but give me a choice to do so. Thanks again Peanut. and co.

---

### Post by dubz on 2005-11-21
if you were like me and dont think things through you can  pass the "single" kernel paramater at boot.  this will drop you into a root shell where you can change passwords etc.( im a dumbass , i should of come here first...my impatience will be the death of me)

thanks.

---

