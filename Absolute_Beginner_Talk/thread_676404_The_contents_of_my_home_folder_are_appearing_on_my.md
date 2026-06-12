---
title: "The contents of my home folder are appearing on my desktop!"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Fraser from Scotland on 2008-01-23
The contents of my home folder are appearing on my desktop! And if i delete them from my desktop they are deleted from my home folder! its reallllly reallllly annoying. Ill show you a screenshot. And the music pictures documents etc... have disappeard from my places bar thing. And if i save something to my home folder it appears on my desktop.

---

### Post by Fraser from Scotland on 2008-01-23
Ok, I just found out when I go to my home folder it shows up as desktop folder instead, there is no home folder anyomore! I might have deleted it, but i don't remember doing anything like that. Anyone know how to revert to normal places menu?

---

### Post by geirha on 2008-01-23
run gconf-editor and browse to /apps/nautilus/preferences/. There should be an option there called desktop_is_home_dir.

---

### Post by Fraser from Scotland on 2008-01-23
it was unticked, am I meant to tick it?

---

### Post by Fraser from Scotland on 2008-01-23
Ok, if the option is ticked or unticked everything stays the same, when i delete a folder off my desktop it is deleted from the places list. It doesnt seem to matter that my desktop is or isn't the home directroy.

---

### Post by geirha on 2008-01-23
No it should be unticked, so $HOME/Desktop becomes the folder it shows on your desktop. I assumed it was ticked. Though tick it, then untick it and close gconf-editor. Log out and back in again to see if it made any difference.

---

### Post by Fraser from Scotland on 2008-01-23
Ok, I restarted and everything is still the same :(
Here is a screenshot, look at the places bar at the left.

---

### Post by geirha on 2008-01-23
> **Fraser from Scotland said:**
> Ok, if the option is ticked or unticked everything stays the same, when i delete a folder off my desktop it is deleted from the places list. It doesnt seem to matter that my desktop is or isn't the home directroy.

Sounds like it's displaying the nautilus bookmarks on your desktop then. Can't find any settings for that in gconf-editor, so that's quite weird. What's the output of this run in a terminal? ```
ls -l ~/Desktop
```

---

### Post by Fraser from Scotland on 2008-01-23
```
fraser@fraser-laptop:~$ ls -l ~/Desktop
total 26480
-rw-r--r-- 1 fraser fraser   797904 2008-01-23 22:53 fluxbox_0.9.15.1-1_i386.deb
-rw-r--r-- 1 fraser fraser   525374 2008-01-23 23:35 Screenshot.png
-rw-r--r-- 1 fraser fraser 25746995 2008-01-23 21:35 xfce-4.4.2-src.tar.bz2
fraser@fraser-laptop:~$ 

```

---

### Post by geirha on 2008-01-23
> **Fraser from Scotland said:**
> ```
fraser@fraser-laptop:~$ ls -l ~/Desktop
total 26480
-rw-r--r-- 1 fraser fraser   797904 2008-01-23 22:53 fluxbox_0.9.15.1-1_i386.deb
-rw-r--r-- 1 fraser fraser   525374 2008-01-23 23:35 Screenshot.png
-rw-r--r-- 1 fraser fraser 25746995 2008-01-23 21:35 xfce-4.4.2-src.tar.bz2
fraser@fraser-laptop:~$ 

```

Hm, though this indicates it really does show your home folder, and not your desktop. Can't think of any reason for this. Perhaps there's sneaked in some errors in gconf's xml-files. Try moving away all the nautilus configuration and restart nautilus with the following commands: ```
mv ~/.gconf/apps/nautilus ~/gconf-nautilus-backup
killall nautilus # when nautilus is killed, it will be restarted

```

---

### Post by Fraser from Scotland on 2008-01-23
Still didn't work :(

---

### Post by Fraser from Scotland on 2008-01-23
I might just do a fresh install, if i cant get a fix to this.

---

### Post by Arthur Archnix on 2008-01-23
Don't do a fresh install! Nothing wrong with your install, you've just pulled an Arthur.

I was playing around with making links from my home directory to my data partition, I deleted the Desktop folder and then tried to create a shortcut.

Experienced exactly what you are.

I never managed to fix it, but I did create a new user. Call it temp. Log into temp. Delete he old account and files. Then recreate it.

Log into the new acount and make sure everything works. Then you can delete the temp user.

If you like, you can copy over the settings folders (./mozilla for example) to something like /mnt/tempfiles/  Chown the dir. Once your user name is back up and running copy the settings back onto your new home. 

Be careful about copying over any gnome settings though, as this may be the root of your problem. But if you have VMware or sunbird or whatever, it's probably safe to try and save those. 

I just had fun resetting up my desktop and didn't worry about it though. Plus, I wasn't concerned about my data since it was on a separate partition. But you should make sure you move your pictures and data and stuff out of there. 

Then, if you decide to play around with shortcus and stuff, don't delete the desktop folder.

Try this first. It's 99% likely to fix your problem and faster than reinstalling.

EDIT: I just looked at your screenshot. Make sure you move your data. Also, if you deleted your desktop folder then recreated it, I'm not sure that would solve the problem. Though deleting it may have caused the problem. I think the first thing I tried was recreating the Desktop folder. Didn't work. I can't find anything in gconf either to help, other than the create new user, delete old user and files, create old user, confirm, delete new user. Sorry!

---

### Post by macogw on 2008-01-23
Or, instead of everything Arthur suggested, make the new user like he said, then do this:
```
sudo cp -r /home/newuser/.gconf ~/.gconf
sudo chown -R youruser:youruser ~/.gconf
```
which would copy the gconf configuration from the new user to your account.  Log out / log in, and you should be back to a default configuration for gnome.

First line:  copy (-r = recursively, so everything inside the directory) the new user's .gconf (gnome configuration) to where yours should be
Second line:  make yourself the owner of the new .gconf (again -R means recursively)

---

### Post by Arthur Archnix on 2008-01-23
And where were you two months ago macogw?](*,)

---

### Post by Fraser from Scotland on 2008-01-23
Thanks for the help and it worked but i tried to rename the new users home folder now i can't get into ubuntu due to something or other, it says my session lasted les than ten seconds, im not sure what it is, im on windows just now. But if you know a fix from safe mode i would be veeeerrrrry happy.

---

### Post by Fraser from Scotland on 2008-01-23
I'm going to go to bed in like 5 mins, so any help PM me.

---

### Post by Arthur Archnix on 2008-01-23
Just try rebooting and logging in with the old broken account. Then follow Macogw's instructions. It sounds like you've got two users on there now, and broken both accounts! 

Should be easy to fix though if you can log into the account that was giving you all the trouble to start with.

You probably don't want to manually rename any home folders though. And be careful where you point that sudo!

---

### Post by macogw on 2008-01-23
What *exactly* did you do?  Did you make a new user and then try to change the name of the user's home directory?  That's what it sounds like you're saying you did, but I'm not sure.

Boot into single user mode (command line only, full admin rights, accessed by pressing the down arrow and choosing "Ubuntu...(Recovery)" on the menu where you pick Ubuntu or Windows), and tell me the following info:
1) What username do you login with?  Your original one or the new one?  What is that username?
2) After you login, type "cd ~" (change directory to home) then type "pwd" (prints the _p_resent _w_orking _d_irectory) in the terminal.  What does it say?
3) If you type "less /etc/passwd" then scroll down til you see your username on the left, what directory is listed near the end of the line?  (It'll start with /home/)  Press "q" to quit out of the less command.
4) Type "ls -l /home" (all of the "l" characters are lowercase L's...this gives a long listing of everything inside /home).  What is the output.  Specifically, I'm concerned with the first column of text (lots of drwx-... kind of stuff), columns 3 & 4 (owner and group for the directory), and the last column (the name of the directory).
5) Type "cd ~" (change directory back to home) then "ls -lA | grep .gconf" (lists all files, including hidden ones, with a long-format listing, but only display's .gconf's details)

Enter all of the commands without including the " "s.

Those are all questions to get details about your system and see what permissions are currently set for what files and users, and which user's home directory should be where, etc. so we can see what's going on.

---

### Post by Fraser from Scotland on 2008-01-24
I have to leave for an exam in 20 minutes, so I'll explain what happened.

1. I followed Arthur's instructions, and it worked, so I deleted my origianal user and logged in as the new one which i had named fc, then i deleted the temp user as well.
2. for some odd reason it was annoying me that my home folder was called fc, so I tried to rename it.
3. It then wouldn't let me into my places directory and I restarted and now here i am.


I think i will just do a fresh install, as I have everything that I need backed up on external HD. But thanks for all the help :)

---

### Post by Arthur Archnix on 2008-01-24
Sounds like you just had to switch to tty1, log in with the new user name, rename the home folder back to what it was, then switch back to your xsession and log in. But hey, this is how we learn. :)

---

### Post by glombo on 2008-03-28
I know this is an old post but I found this article not long ago while i had the same problem.
What I did was to open ~/.config/userdirs.dirs in gedit and changed the file to look like this:
```
# This file is written by xdg-user-dirs-update
# If you want to change or add directories, just edit the line you're
# interested in. All local changes will be retained on the next run
# Format is XDG_xxx_DIR="$HOME/yyy", where yyy is a shell-escaped
# homedir-relative path, or XDG_xxx_DIR="/yyy", where /yyy is an
# absolute path. No other format is supported.
# 
XDG_DESKTOP_DIR="$HOME/Desktop"
XDG_DOWNLOAD_DIR="$HOME/"
XDG_TEMPLATES_DIR="$HOME/Templates"
XDG_PUBLICSHARE_DIR="$HOME/Public"
XDG_DOCUMENTS_DIR="$HOME/Documents"
XDG_MUSIC_DIR="$HOME/Music"
XDG_PICTURES_DIR="$HOME/Pictures"
XDG_VIDEOS_DIR="$HOME/Videos"
```

I haven't had the chance to test this yet but thought I'd post it before I forgot. If it doesnt work I will either edit or delete the post in a minute!

---

### Post by glombo on 2008-03-28
It worked! The problem seems to be, in that case that the
```
XDG_DESKTOP_DIR
```
line read
```
XDG_DESKTOP_DIR="$HOME/"
```
instead of
```
XDG_DESKTOP_DIR="$HOME/Desktop"
```

Simple really, eh? (If that is what the problem was?)

---

