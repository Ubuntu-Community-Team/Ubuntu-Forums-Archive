---
title: "Resolution, to no boot problem"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Brudy on 2007-05-17
I changed the settings using sudo dpkg-reconfigure xserver-org, ubuntu made a backup copy calling it /etc/x11/xorg.conf.20070517083410

I have no idea how to reconfigure the system.
as I boot the system I have a failed to start the X server etc. Would you like to view the detailed x server out etc.
X server is now disabled. restart GDM when configured correctly.

Any help would be great

Brudy

---

### Post by bobplano on 2007-05-17
it sounds like you configured it wrong. you can just run the same command again or restore the backup using
```
sudo cp /etc/x11/xorg.conf.20070517083410 /etc/X11/xorg.conf
```

---

### Post by Brudy on 2007-05-17
cp: cannot stat '/etc/x11/xorg.conf.20070517083410' : no such file or directory.

Can I search for the back up file?? and if so how?

and the how do i reinstall that file?

Brudy

---

### Post by bobplano on 2007-05-17
you can go into the directory in the terminal and do an ls command. this lists all the files in the folder. then you can use that same basic syntax to replace your xorg

---

### Post by mikewhatever on 2007-05-17
Please note that the X in X11 is capital.
> sudo cp /etc/X11/xorg.conf.20070517083410 /etc/X11/xorg.conf

---

### Post by jerrylamos on 2007-05-17
Could you post what hardware you are using, what monitor, and what Ubuntu?

Cheers, Jerry

---

### Post by Brudy on 2007-05-17
I have a screen that is back and has asked me for my user name and password.
Then I have a flashing curser after log in.
what can I do to find the file, and restore it?
Brudy

---

### Post by Brudy on 2007-05-17
Dell GX260 
Ubuntu 6.06.0 LTS
Monitor is a HP w19b

---

### Post by Brudy on 2007-05-17
--------------------------------------------------------------------------------

Please note that the X in X11 is capital.

Quote:
sudo cp /etc/X11/xorg.conf.20070517083410 /etc/X11/xorg.conf  

I have tried using the capital X11

I'm able to see usage: file (option).. FIle when I type in file --help

I'm used to DOS comands at best I'm quite rusty

---

### Post by Brudy on 2007-05-17
--------------------------------------------------------------------------------

you can go into the directory in the terminal and do an ls command. this lists all the files in the folder. then you can use that same basic syntax to replace your xorg

I have no idea how to get to the directory, terminal

the sreen shows my login name @ my login name-desktop:"$
Can you tell me how to show files, in DOS the comand was DIR      or DIR/p to stop when the sreen was full of files and press enter to srowl to the next screen ful

Brudy

---

### Post by bobplano on 2007-05-18
```
cd /etc/X11
ls
```
those commands should make you go into the folder with your xorg.conf and then the second one lists all the files.

---

### Post by mikewhatever on 2007-05-18
As already asked above, can you post the output of
> ls /etc/X11

---

