---
title: "! warnings and unable to login"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by Martin Flynn on 2008-04-06
I started getting this warning, after I entered my password, a couple of days ago, after trying to share folders for my network. I think I've removed the share but I kept getting the same warning although the m/c started when I clicked OK.

"Users $HOME/.dmrc file is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. Users $HOME directory must be owned by user and not writale by other users"

Today, I'm also receiving this error/warning (no entry sign);

"The GNOME session manager was unable to lock the file '/home/name/.ICEauthority'. Please report this as a GNOME bug. Sometimes this error may occur if the file's directory is unwritable, you could try logging in via the failsafe session and ensuring that it is."

Now the m/c returns to the login screen after clicking OK on both errors.

I'm lost!

I've also had another problem which I had tried to resolve on an external  forum but the trail has gone cold
[http://forums.computeractive.co.uk/thread.jspa?threadID=132778&tstart=0](http://forums.computeractive.co.uk/thread.jspa?threadID=132778&tstart=0)
:confused:

Upgraded to 7.10. That's when the problems started

---

### Post by viciouslime on 2008-04-06
When you're at the login screen, press ctrl+alt+F1, you will be presented with a text-based login. Enter your user name and password then enter the following commands:

sudo chown -R <your username> /home/<your username>
sudo chgrp -R <your username> /home/<your username>

If either of these commands presents any errors, post those back heere, otherwise, press ctrl+alt+F7 to get back to the graphical login screen and try again :)

---

### Post by scragar on 2008-04-06
ok, first use ctrl+alt+F1 to get to a terminal, and log in there.
try:
```
ls -l ~/.dmrc && ls -l ~/.ICEauthority
```

it should list 2 files like this:
```
-rw------- 1 **user** **user** 28 2008-04-03 18:20 /home/scragar/.dmrc
-rw------- 1 **user** **user** 1231 2008-04-05 14:34 /home/scragar/.ICEauthority
```
where **user** is your username. Let me know what's different about your output.

---

### Post by Martin Flynn on 2008-04-07
> **viciouslime said:**
> When you're at the login screen, press ctrl+alt+F1, you will be presented with a text-based login. Enter your user name and password then enter the following commands:

sudo chown -R <your username> /home/<your username>
sudo chgrp -R <your username> /home/<your username>

If either of these commands presents any errors, post those back heere, otherwise, press ctrl+alt+F7 to get back to the graphical login screen and try again :)

Entered commands as described and returned to another line;
user@user-desktop:~$

---

### Post by Martin Flynn on 2008-04-07
> **scragar said:**
> ok, first use ctrl+alt+F1 to get to a terminal, and log in there.
try:
```
ls -l ~/.dmrc && ls -l ~/.ICEauthority
```

it should list 2 files like this:
```
-rw------- 1 **user** **user** 28 2008-04-03 18:20 /home/scragar/.dmrc
-rw------- 1 **user** **user** 1231 2008-04-05 14:34 /home/scragar/.ICEauthority
```
where **user** is your username. Let me know what's different about your output.

I got;
-rw-rw-rw- 1 user user 28 2008-04-02 15:56 /home/user/.dmrc
-rw------- 1 user user 175 2008-04-04 12:07 /home/user/.ICEauthority

---

### Post by mister_pink on 2008-04-07
Try 
chmod 644 ~/.dmrc
And try renaming the .ICEauthority file, I think it will then generate a new one. If it doesnt then you can rename it back

---

### Post by Martin Flynn on 2008-04-07
> **mister_pink said:**
> Try 
chmod 644 ~/.dmrc
And try renaming the .ICEauthority file, I think it will then generate a new one. If it doesnt then you can rename it back

Didn't seem to do anything. Don't know what to rename the 'ICEauthority' file to.
Now the login screen errors/warnings fill the screen with massive text!:(

---

### Post by viciouslime on 2008-04-07
Rename it to anything you like, it's just better than deleting it, as this way you can always rename it back.

---

### Post by dondad on 2008-04-07
You mentioned that you were setting up some shared folders. One cause for the problem that you describe is using sudo rather than gksudo in a graphical application such as Nautilus. When you do that, it sometimes gets the permissions profiles of root and the user confused and the result is exactly what you have mentioned. Not that I have ever done anything like that or have the instructions for how to fix it in a real easy place to get to from the command line or ... ;-)

---

