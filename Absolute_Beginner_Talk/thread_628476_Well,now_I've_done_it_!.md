---
title: "Well,now I've done it !"
date: 2007-12-01
forum: Absolute Beginner Talk
---

### Post by Sawman on 2007-12-01
I installed the program "Amule" to transfer large files. My incoming folder (.amule/incoming)was hidden and in my foolish attempt at accessing it, I somehow changed the permissions for my "$Home" folder !
When I rebooted the following message appeared: "User's $Home/.dmrc file is being ignored... File should be owned by user and have 644 permissions. User $Home directory must be owned by user and not writable by other users."
Can this be fixed or am I facing a reinstall of Ubuntu?

HP 5003cl
AMD 64 Turion
Ubuntu Studio 7.1 (64-bit)

Thanks in advance.

---

### Post by PmDematagoda on 2007-12-01
Scratch that, I don't think it works, sorry.

---

### Post by SunnyRabbiera on 2007-12-01
ooh, oww...
I dont think there is a real way to solve this one as root is disabled by default and thats the only way I know how to get permissions right on most linux systems...
you might have to go under the terminal for this, you can try sudo in it and perhaps install konqueror to help you out.
The only reason why I suggest knoqueror is because its better at setting folder permissions then nautilus.
but I really dont know of a good fix for you that doesnt involve command line but you might not have any choice.
you may want in install KDM as it does allow terminal sessions unlike GDM...
who knows the KDE apps can be your salvation here as some gnome apps fall short here and there.
so thats the only real suggestions I can give you, see if its possible to get a failsafe terminal session working

---

### Post by scrooge_74 on 2007-12-01
start in safe mode

then type chown user:user -r /home/username
then chmod 644 /home/username/.dmrc

you dont need to type sudo in front of those commands since you are working as root, if you start the computer in the normal mode then you go to a console [ctrl+alt+f1] log in and then sudo the commands above

---

### Post by PmDematagoda on 2007-12-01
Ok, I think I got it:-
```

sudo chmod u-rwx /home/username
```

---

### Post by PmDematagoda on 2007-12-01
> **scrooge_74 said:**
> start in safe mode

then type chown user:user -r /home/username
then chmod 644 /home/username/.dmrc

you dont need to type sudo in front of those commands since you are working as root, if you start the computer in the normal mode then you go to a console [ctrl+alt+f1] log in and then sudo the commands above

Are you sure that 

chmod 644 /home/username/.dmrc is right?

I tried on one folder and it made the folder writable and readable but the files unreadable and unwritable.

---

### Post by scrooge_74 on 2007-12-01
You said it yourself in your opening post

---

### Post by Harpoon on 2007-12-01
Take heart, you are not the only one seing this message.  I'm running Feisty 64 bit, and while playing with something (probably compiz, but perhaps on one of the wireless network hangs) I crashed my system.   Sure enough, that message appeared at login, but in the end it booted ok.  I chowned everything that needed it and made sure the .dmrc file had 644 permissions, but I still get the error on every boot.

The good news is that all you need do is hit return and ignore this as a minor inconvenience (for now).  So far I have not been able to find a solution, but I have also not seen any serious issues relating to this.

Just one of those quantum physical events, I guess.

BTW, I used the command sudo chown -R username:username and then set the permissions on dmrc using chmod.

---

### Post by glotz on 2007-12-01
Well, acquire root* and then do a chown *yourusername*:*yourusername */home/*yourusername*

*see [http://ubuntuforums.org/showthread.php?t=177984](http://ubuntuforums.org/showthread.php?t=177984)

---

### Post by PmDematagoda on 2007-12-01
> **scrooge_74 said:**
> You said it yourself in your opening post

Yes that's what I thought, until I had a look at the target directory I used it on and then realised that it did not really work properly.

---

### Post by PmDematagoda on 2007-12-01
Damn it, I do not know what is wrong with me right now:mad:.

My sincerest apologies to the OP, I finally found a chmod that works properly:-

```
sudo chmod -R u=rw /home/pramod
```

---

### Post by Sawman on 2007-12-01
No joy. Sudo the chown and chmod. Now I get the same message, but then it gives another saying my session lasted less than 10 seconds and that there is a problem with the installation. It then brings me to a login screen, but anything I type it says is wrong password or username.
Looks like I'll be starting fresh. :(

---

### Post by scrooge_74 on 2007-12-01
you probably mess up the write permissions in the entire folder, I doubt you ran out of space already which is another reason for that kind of message

What permissions do you have for the /tmp folder?

---

### Post by PmDematagoda on 2007-12-01
Post what you get with:-
```

ls -l
```

In /home while in Recovery Mode.

---

### Post by Sawman on 2007-12-01
ls -1 in /home shows my user name "mike"

I don't know how to access /tmp and look at permissions from command line.

---

### Post by scrooge_74 on 2007-12-01
to access directories from a command line 

cd /tmp to go to temp

cd /  to go to root directory

cd /home to go to home

cd will take you to your user home directory

you can ls -la /

for a detail of folders under root including tmp

---

### Post by Sawman on 2007-12-01
Ok, in /temp I ran "ls -la" and got the following:

Total 16
drwxrwxrwt  4  root  root 4096  Dec 1   16:15  .
drwxr-xr-x   22 root  root 4096  Nov 30 07:01  ..
drwxrwxrwt  2  root  root 4096  Dec 1   16:15  .ICE-UNIX
drwxrwxrwt  2  root  root 4096  Dec 1   16:15  .X11-UNIX


All Greek to me !:(

---

### Post by scrooge_74 on 2007-12-01
but did you do it like this

ls -la /

to see the permits of tmp?

d stantds for directory
r is read
w is write
x is execute 
it goes in sets of 3 letters: first set is for the user who owns the file or folder, second set for the group in which other users which belong to the same group has the same permits, and the final set is for other users which do not belong to the group

---

### Post by glotz on 2007-12-01
[QUOTE=Sawman]in /temp I ran "ls -la"
drwxrwxrwt  4  root  root 4096  Dec 1   16:15  .
[/QUOTE]
Isn't it this dottie?

---

### Post by Sawman on 2007-12-04
Sorry, I couldn't reply sooner. . . had to go to work. :(

Anyhow, I booted into recovery and ran "ls -la" again at the beginning and got this:

Total 48
drwxr-xr-x  8  root  root  4096  Dec 1  10:08  .
drwxr-xr-x  22  root  root  4096  Nov 30  07:01  ..
-rw-------  1  root  root  153  Dec 1  16:19  .bash_history
-rw-r--r--  1  root  root  2227  May 15 2007  .bashrc
drwx------  3  root  root  4096  Dec 1  09:19  .gconf
drwx------  2  root  root  4096  Dec 1  09:19  .gconfd
drwx------  4  root  root  4096  Nov 25  15:45  .gnome2
drwx------  2  root  root  4096  Nov 15  15:22  .gnome2_private
-rw-r--r--  1  root  root  141  May 15 2007  .profile
-rw-r--r--  1  root  root  1912  Nov 25  15:45  .recently-used.xbel
drwx-----3  root  root  4096  Dec 1  09:20  .synaptic
drwxr-xr-x  2  root  root  4096  Nov 19  18:52  .wapi

---

### Post by scrooge_74 on 2007-12-04
but you are reading the  folder for root, you need to check is your home folder

---

