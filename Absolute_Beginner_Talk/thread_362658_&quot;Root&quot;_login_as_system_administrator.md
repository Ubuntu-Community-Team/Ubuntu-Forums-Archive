---
title: "&quot;Root&quot; login as system administrator"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by travis_b7 on 2007-02-15
I'm trying to change some folders (add files, delete folders I've created) but it says I'm not the owner! Owner is listed as root, and when I try to log in as "root," it says that the system administrator cannot log in under the main screen. How do I transfer all ownership to my personal login?

I just want to manage files (need to add some add-ons to Celestia, et cetera).

Thanks!

Travis

---

### Post by Sklasko on 2007-02-15
It's is DEFINITELY not a good idea to convert all ownership to your account. However, if you need to manipulate files you can use the "sudo" prefix in the terminal or you can run Nautilus as root using "gksu nautilus".

---

### Post by ashmew2 on 2007-02-15
Logging in as root is generally not recommended , but if u want to do so , just goto 

System > Administration > Security and check the box "allow local adminstrator to log in"
You must also specify a password by System > Preferences > User , Double click root and enter the new password.

This shud allow u to login as root graphically , but BE CAREFUL!!

---

### Post by Tomosaur on 2007-02-15
You can't login as root (well you can, but you need to do some fiddling, and it's not worth it really). To gain root priveleges, and thus be able to change root files, you use the 'sudo' command in front of whatever you're trying to do, or gksudo for graphical programs.
```

sudo nano /boot/grub/menu.lst

```
Will open up the menu.lst file with read + write permissions, in a terminal based text editor.

```

gksudo gedit /boot/grub/menu.lst

```
Will open up the menu.lst file with read + write permissions, in a GUI text editor.

In both cases, the password you're asked for is your own. These commands will normally give you root priveleges for around 15 minutes, after which you'll have to enter your password again.

---

### Post by moffa on 2007-02-15
You can login under the main screen by using your account first then going to System menu and find Login manager.

On the Security tab of Login Window Preferences, you can check Allow local administrative login.

Alternatively, from the terminal you can run ```
 sudo chown username:username [filename] [-R] 
``` (Take away the square brackets, the -R is recursive if you have directories.

---

### Post by Dr Small on 2007-02-15
If you want to change files and folders, the easy way to do it, would be to go to either the terminal or Run (Alt+F2) and type:
```
gksudo nautilus
``` 
and this will log you into nautilus as root.
Now you can change and edit files/folders with root permissions.

To make it simpler, add a lancher to the desktop, like me, that points to 'gksudo nautilus' for quick root access ;)

Dr Small

---

### Post by usmcpug82 on 2007-02-15
root is disabled by default as far as i know. If you want to do things that it's tell you that you can't try the command 'sudo' which stand for 'superuser do'. 

If you can't rename a file w/o super user, do the following

Example:
> sudo mv [oldfilename] [newfilename]
The password you're asked for is the password you used to login to the account your using. You can enable root by doing: 

> sudo passwd


[http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way]("http://www.debuntu.org/2006/04/24/34-ubuntu-default-root-password-or-the-sudo-way") explains a lot more about it.

---

### Post by Dr Small on 2007-02-15
You can also read more about RootSudo, from the Ubuntu Help Website:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Dr Small

---

### Post by travis_b7 on 2007-02-15
Thanks for all the help! I will definately try out these as soon as I can get back to my computer (currently on someone else's in another dorm room).

Thanks again for the quick response!

---

### Post by OnlyJedi on 2007-03-06
I know this is a bit late, but the repositories (at least edgy and feisty) have an extension for nautilus called 'nautilus-gksu'. To install it, simply run the command:
```
apt-get install nautilus-gksu
```
Then, either log out or run the command:
```
killall nautilus
```
This is needed because it seems nautilus won't recognize a new extension until it's restarted.

Then, while in nautilus, right-click on a folder and select 'Open as administrator', then type your password at the prompt. This runs 'gksu --no-desktop *location*'.

One tip/suggestion. While nautilus is open as root, browse to / and select 'Edit->Backgrounds and Emblems' from the menu bar. Pick a nice jarring background or color (I chose red) and drag it to the root directory of the file system. What this does, is make the background of all nautilus windows run by root red (or whatever background or color you chose). The idea is similar to why root command prompts are often in different colors and/or have different terminating characters; it reminds you to be careful in whatever you do.

---

