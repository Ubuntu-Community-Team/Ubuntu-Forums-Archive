---
title: "change the name of the home folder?"
date: 2007-06-15
forum: Absolute Beginner Talk
---

### Post by locke.dragon on 2007-06-15
well...  not really the home folder...  but i want to change the name of the folder inside it.  at the moment it's /home/link, but i want it to be /home/locke.  is there any way to do this without re-installing?

---

### Post by Golyadkin on 2007-06-15
The names of those folders are the names of the users on the system. As far as I know, you cannot change your username. You can however just make a new user with the name "locke" and it will create your homedirectory in /home/locke.

Go "System > Preferences > Users and Groups" and click Add User.


Also, please use the "Post reply" button to reply to someone in your thread, and do not create a new topic for it.

---

### Post by locke.dragon on 2007-06-15
ok.  i'll try that.  but why did you tell me this?

> 
Also, please use the "Post reply" button to reply to someone in your thread, and do not create a new topic for it.


---

### Post by Golyadkin on 2007-06-15
Oh, I am so sorry, I mixed two threads up. I just replied to someone who asked almost the same question.

Check here: [ this thread ]("http://ubuntuforums.org/showthread.php?t=474964")

I didn't look at the username, I apologize. I thought this was a follow up on that thread. 
I hope I didn't offend you, I meant to be supportive.

---

### Post by locke.dragon on 2007-06-15
lol!  don't worry about it.  you didn't offend me, just got me curious.  :P  thanks for the answer!  :)

---

### Post by kevinlyfellow on 2007-06-15
You can also change your home directory without changing your username.  

System -> Administration -> Users and Groups
Highlight a user and click properties
on the "Advanced" tab, there is an option to change your directory.

Or, you can go to the command line and type
```
usermod --home NewDirectory UserName
```

If you want to just change the user name (and not the home folder)
```
usermod --login NewUserName CurrentUserName
```
(actually you can change the username from the gui thing I gave above)

---

### Post by Golyadkin on 2007-06-15
Oh cool, I didn't know that. Thanks for sharing that Kevin.

---

### Post by locke.dragon on 2007-06-15
i tried doing it that way, but there were no files in the new directory, and i'm afraid that if i move my ENTIRE home directory, it'll screw up settings and the like.

---

### Post by Golyadkin on 2007-06-15
Why not open both home dirs in two windows next to eachother and drag the files from one side to the other?

---

### Post by locke.dragon on 2007-06-15
because all my settings and other stuff is in my current home folder.  i'm afraid that if i move all the files, it'll mess up my wallpapers, toolbars, firefox settings, etc.

---

### Post by kevinlyfellow on 2007-06-15
A warning, if you change your username, you will need to modify your sudoers file... *fixing sudoers file now*

---

### Post by locke.dragon on 2007-06-15
and how do i do that?  and how long is it gonna take me to do this?  i don't want to screw something up just cause i want a new home folder name.

---

### Post by kevinlyfellow on 2007-06-15
lol, sorry, I just jumped in an screwed things up, and I had to fix them.  So, here is what you should do if you want to change your username and and folder still have everything ok.

```

sudo su
usermod --home NewDirectory --login NewUserName CurrentUserName
usermod -aG admin NewUserName
mv /home/OldDirectory /home/NewDirectory

```

edit:
It worked!!! Just to be perfectly clear on how this works, I'll give you exactly what I input into the terminal.

```

sudo su
usermod --home /home/fumblegut --login olegutty newuser #don't be confused, newuser was my current username at the time
usermod -aG admin olegutty
mv /home/kevinly /home/fumblegut

```

And a quick rundown of what I did in english

1)I used a sudo trick to login as root (sudo su)

2)I changed my user name "newuser" to "olegutty" and made the home directory "/home/fumblegut"

3)I added the user olegutty to the "admin" group.  This group is allowed by the sudoers file to use the program sudo.  If you skip this step (like I did at first) and you're new to linux administration, your in deep doodoo.  Keep a live cd on hand just in case.

4)I renamed (or moved) my old home directory "/home/kevinly" to the one I just assigned "/home/fumblegut"

5) Ok there is no 5th command, but there will be some minor things you'll need to clean up, but nothing thats too difficult.  Go to the user and group manager (system -> administration -> Users and Groups) and go to the properties for your user.  Go to the middle tab (Users Privileges) make sure everything is setup correctly.  One minor problem I had were links in the system that pointed to my old home directory and my automatic login was disabled.

You should logout after you have done all these changes.

Oh, and if you don't want a new username, but you do want a new directory, just omit anything that references to a new username.  
```

sudo su
usermod --home NewDirectory CurrentUserName
mv /home/OldDirectory /home/NewDirectory

```

---

### Post by Golyadkin on 2007-06-15
Also, most programs and scripts use ~ as a shortcut for "the homedir of whatever user started the script". 

For instance, if you type cd ~/Documents, you always go to your own Documents folder in the home dir.

---

### Post by kevinlyfellow on 2007-06-15
> **Golyadkin said:**
> Also, most programs and scripts use ~ as a shortcut for "the homedir of whatever user started the script". 

For instance, if you type cd ~/Documents, you always go to your own Documents folder in the home dir.

It should be noted that when using sudo ~ will still point to your home directory and not root, but when using su, it will point to root

To illustrate try these
```
sudo ls ~
sudo su
ls ~

```

---

### Post by Golyadkin on 2007-06-15
Yes, that is true. Good addition kevinlyfellow.

---

### Post by kevinlyfellow on 2007-06-15
> **Golyadkin said:**
> Yes, that is true. Good addition kevinlyfellow.

Thanks... oh the number of times that little fact screwed me up...

---

### Post by arvevans on 2007-06-15
The /home/username directory contains information specific to that user, including a bunch of normally hidden files.  When using the GUI file browser to look at /home/username, hit CTRL-H and you should see a bunch of files and folders that start with ".".  These are the normally hidden files.  Look at some of these and you will find that they contain configuration information for how this particular user runs specific applications (firefox, etc.).  Just dragging hidden configuration files from one user's home directory to another may work and may not.  Some of this configuration info is location dependent (it should not be, but sometimes developers get lazy).

The easiest and most reliable way to change a user's /home/username is to build the new username using tools provided for that purpose.  Once that user has logged into his/her new /home/username, most of the config info will be automatically set up.  Then if you have something particular that you want to bring across from the old /home/old_username, you can do it on an individual file basis and not have to do so much work if something doesn't work as anticipated.

FYI: Now you also know how to make "hidden files" on your system.  Just make the file normally, then edit the filename to include a leading "."
_._

---

### Post by locke.dragon on 2007-06-15
thanks for all the help guys, but this sounds like more trouble than it's worth.  plus, knowing me, i'll be re-installing in the next few weeks cause i screwed something up.  XD

---

### Post by kevinlyfellow on 2007-06-15
> **locke.dragon said:**
> thanks for all the help guys, but this sounds like more trouble than it's worth.  plus, knowing me, i'll be re-installing in the next few weeks cause i screwed something up.  XD

It's not worth much, but it really isn't all that hard.  I screwed up a few times because I never really did it before.  Anyways, keep screwing things up, its how you learn!

---

