---
title: "Step 4 Beryl"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-13
I am at step 4 of Pricechilds guide to intall Beryl.  

in /etc/X11/xorg.conf (Remember to back it up again just incase)

Add this to Section "Screen"

How do I install code in this.  How do I bring this up?  

Thanks for any help

---

### Post by LLRNR on 2006-11-13
Hi there. You just have to edit your /etc/X11/xorg.conf file -- yes, backup it first -- and you can do this from the command line. Mainly you have to open it with a text editor; and yes you'll need root privileges for this.
```
sudo nano /etc/X11/xorg.conf
```then type in your password and edit the file as stated in the HowTo.

Good luck !

LLRNR

---

### Post by gentlemanmasher on 2006-11-13
How do I back it up and how would I get to the backup if something did happen?  

Thanks for the help

---

### Post by LLRNR on 2006-11-13
To backup a file you simply make a copy of it with another name, that is
```
sudo cp /path/to/file/filename /path/to/file/filename.backup
```so in your case it will be```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

And then, to get it back, you can just overwrite the "bad" file with the backup and then delete the backup (since the bad file has become the good one and the backup is identical to it and you no longer need it):
```
sudo cp /path/to/file/filename.backup /path/to/file/filename
sudo rm /path/to/file/filename.backup
```so in your case this will be
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
sudo rm /etc/X11/xorg.conf_backup
```

Good luck !

LLRNR

---

### Post by gentlemanmasher on 2006-11-13
Well I went ahead with step 4 and do not think I was successfull in making a backup.  I know am getting a black screen on login.  I am able to get to type in my name and password.  How do I fix the edit I made.

Or since my backup didn't work am I out of luck.

---

### Post by LLRNR on 2006-11-13
What do you mean exactly by "my backup didn't work"? Did you try with the code above ? Hmmm I guess you _did_ realise that the X in "X11" is actually an uppercase "X", didn't you? :D

---

### Post by SephirothXIIIX on 2006-11-13
Nah, you are not out of luck.. When you receive the black screen on login, hit Ctrl+Alt+F1 and then login; that will bring you to a command line.

Navigate to the directory where the X11 configuration file is:
```

cd /etc/X11/

```

Type the following:
```
ls
```

And see if there is a file listed named xorg.conf_backup

If so, type the following:
```
sudo cp xorg.conf_backup xorg.conf
```

And that will restore your backup.. Now you can restart or simply type the following:
```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

If the file is not listed, you may type the following to reconfigure X
```
sudo dpkg-reconfigure xserver-xorg
```
(Just follow the steps to reconfigure it, and it'll automatically restore the file for you)

Good luck.

> **LLRNR said:**
> What do you mean exactly by "my backup didn't work"? Did you try with the code above ? Hmmm I guess you _did_ realise that the X in "X11" is actually an uppercase "X", didn't you? :D

I don't know if he could even he to a console before, that may be why (maybe he assumed the backup just worked, too). But, yeah, hopefully one of us can help him out.

---

### Post by gentlemanmasher on 2006-11-13
Well I am back in so thanks for that.  Now what exactly should I put in step 4 to get Beryl going and now that I reconfigured X do I need to go back and redo any of my steps?

Thanks

---

### Post by LLRNR on 2006-11-13
WB! If my guess is right, you must be following [this](http://ubuntuforums.org/showthread.php?t=263851) guide, am I right? If so, then you might just do step 4 again. So:

a) backup your xorg.conf file ;
b) put in the code given in the HowTo (under the "Screen" section);
c) if you try to do it with that extra-line (option triplebuffer or something like that) and doesn't work out for you, then:
   c`) sudo cp /etc/X11/xorg.conf_backup xorg.conf 
       sudo rm /etc/X11/xorg.conf_backup
   c``) back to a) and when you get to b) don't put that line in again!

Basically that's the way to do it. Backup -> Mess up -> Undo -> Retry :D

Good luck (I'm sorry I didn't follow that guide, but another one, so I don't know how things turn out to be, but it's always better to be precaucios...) !

LLRNR

---

### Post by gentlemanmasher on 2006-11-15
Thanks I got Beryl working finally after two days.  It is really cool though thanks for the help.

---

