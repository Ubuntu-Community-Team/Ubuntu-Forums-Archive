---
title: "how to navigate to a certain directory using the terminal"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by j_evenstar on 2007-05-08
just started booting the live cd and i'm trying to view videos in youtube. i had to install the flash player plugin and since im new to linux i can't understand what the phrases "in terminal, navigate to this directory" and "in terminal, navigate to the desktop" meant. so i still haven't installed the plugin. 
thanks for any responses.

---

### Post by compmodder26 on 2007-05-08
The "cd" (**c**hange **d**irectory) command is what you want.  Usage:

```
cd /new/directory/path
```

---

### Post by FurryNemesis on 2007-05-08
in terminal, type()    \cd  /home/username/desktop

You've just Changed Directory to that place in the filetree and it will be reflected like this:

furry@furry-laptop:~/Desktop$

---

### Post by meborc on 2007-05-08
maybe this will help a bit: [http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

---

### Post by Nythain on 2007-05-08
cd will navigate you around... other usefull tricks
~ = /home/username
\ = how to do spaces in directory and file names
. in file or directory name = hidden (can be shown in terminal with  ls -a)

example
cd ~/.wine/drive_c/Program\ Files
would take me to
/home/rune/.wine/drive_c/Program Files

---

### Post by tru infini on 2008-06-20
I've been having the same problem as this only my problem extends a little farther then the last guy. here's what happens:
i type 
/home/robert# ./flashplayer-installer
in my terminal as root so it should go through right?
but then i brings up this:
-su: ./flashplayer-installer: Permission denied
any ideas or pointers?

---

### Post by AndThenWhat on 2008-06-21
> **j_evenstar said:**
> just started booting the live cd and i'm trying to view videos in youtube. i had to install the flash player plugin and since im new to linux i can't understand what the phrases "in terminal, navigate to this directory" and "in terminal, navigate to the desktop" meant. so i still haven't installed the plugin. 
thanks for any responses.

"In terminal" means that you need to type commands etc into a terminal window.  The way you can get to one is by pressing ALT+F2 and entering "gnome-terminal" and press enter.  Then the command you want to run to make YouTube videos start working is:

```
sudo apt-get install flashplugin-nonfree
```

---

### Post by bigbrovar on 2008-06-21
u know what to make things dead easy .. just install this tool 
[COLOR="DarkSlateBlue"]nautilus-open-terminal[/COLOR] what it does is it puts a "open terminal" in ur context menu .. so when u are in a directory/folder all u have to do is rightclick and it gives u the option to open that directory inside of terminal ..
the tool is in the repos so u can either

sudo apt-get install nautilus-open-terminal

or open synaptic and search for it .. right click mark ..for install ,apply 

u would then need to log out and log in(yeah it wont affect ur live session) back for it to take effect..

---

### Post by tru infini on 2008-06-21
another thing is that when ever i open adept-installer it acts like its in a read only mode or something. is there a way to fix this?

---

