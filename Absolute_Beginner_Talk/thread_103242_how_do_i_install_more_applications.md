---
title: "how do i install more applications????"
date: 2005-12-13
forum: Absolute Beginner Talk
---

### Post by warrior85 on 2005-12-13
I finally installed ubuntu into my PC, and it looks great. then I went to a cyber and i downloaded more games for linux, (frozen bubble among others), i came back home to install it... and there's where i stopped. :eek:  I don't know how to install it... can somebody help me? :confused:   I've been reading others thread and they say something about typing some commands... i'm new in this:???:  so can somebody explain me inch by inch how to??? and if there's an easy way to do it, I will be more than thanksful.

---

### Post by teaker1s on 2005-12-13
menu applications-add applications
simple gnome installer for more advanced hit advanced tab on gnome installer or terminal
sudo synaptic
change preferences to see recommended packages as dependences(tick box) and you shouldn't have dependencies problems

welcome to the forums

---

### Post by CanadaGradeEh on 2005-12-13
Well if you had the game on a CD or DVD I'd just try transferring it over to your hard drive, then going to 'Applications > Add Applications' then look for your game. I'm pretty newbie though too; I'm just learning all of this with you.

I just learned that the command line for downloading and installing a file is 'sudo apt-get install filenamehere.wtvr' so if you can find the filename.. I think... I guess you could do that.

But yea, wait for someone more experienced. That's just me trying to be helpful even though I know nooooothingggs :P

---

### Post by Sutekh on 2005-12-13
What sort of files are the games? 

Sourcecode - .tar.gz?
Packages - .deb .rpm?

Sourcecode - you will need to type this in a terminal
```

sudo apt-get install build-essential

```
This installs some things you will need to compile the source code

Then to install the game (from the directory the game is in)
```

./configure
make
make install

```
Packages - .deb
```

sudo -i dpkg <packagename>.deb

```
or a double-click from a file browser will do.

Packages - .rpm
```

sudo apt-get install alien
sudo alien <packagename>.rpm

```

Also Frozen Bubble requires some extra packages (PERL, SDL) that will need installing.  That could be extra work.

Of course the easiest way to install anything is through Synaptic, just click what you want and it does the rest.

---

### Post by warrior85 on 2005-12-13
I did what you said about synaptic.  then a window pops up asking for my root password, i wrote it.... and then nothing happened :???: 
the same thing happened when i click on add application in system >> adminstration... nothing happend. :confused: I'll try tomorrow the other way. thanks

---

### Post by aysiu on 2005-12-14
You shouldn't have a root password unless you did an expert install.
Use your user password.

For more on why this is: [https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by warrior85 on 2005-12-14
hello!! it's me again!!! same question... how do i install new applications??? :confused: 
I have frozen-bubble.deb. how do i install it??? :???:  thanks!!!

---

### Post by aysiu on 2005-12-14
[QUOTE=warrior85]hello!! it's me again!!! same question... how do i install new applications??? :confused: 
I have frozen-bubble.deb. how do i install it??? :???:  thanks!!![/QUOTE] 1. Delete the .deb you downloaded. Just throw it in the trash. You don't need it.

2. Make sure you have extra repositories enabled by following these instructions:

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

3a. Then, open a terminal and type these commands ```
sudo apt-get update
sudo apt-get install frozen-bubble frozen-bubble-data
``` The password you'll be asked for is your user password--not the root password.

3b. If you don't like apt-get, use System > Administration > Synaptic Package Manager instead (see attached image).

If you don't know how to use Synaptic Package Manager, read [this](http://www.psychocats.net/essays/winuxinstall.php).

---

### Post by warrior85 on 2005-12-15
when i try synaptic i get this message error on the image and i don't know what to do... i will try the other way... thanks :D



[ATTACH]4527[/ATTACH]

---

### Post by Mustard on 2005-12-15
It looks like gpg key error.  Last time I looked at this link it had a solution for gpg key errors at the bottom of the page...

[http://www.psychocats.net/linux/sources.php](http://www.psychocats.net/linux/sources.php)

-edit-

Yep..its still there.  Follow the instructions at the bottom of the page and see if that fixes your gpg key error.  It's not a fatal error, you can still install something even though the gpg key errors are occuring, but the gpg keys are there to confirm that the packages are authentic, so its not secure to ignore the errors and install anyway.

---

### Post by kaamos on 2005-12-15
[QUOTE=warrior85]then I went to a cyber and i downloaded more games for linux, (frozen bubble among others), i came back home to install it... [/QUOTE]

No reason to talk about gpg key error if his ubuntu box doesn't have internet access, is there? Or did I just get confused?

---

### Post by warrior85 on 2005-12-15
i did all of that and i still have the same problem....
i'm going to take it easy for a while thanks anyway

---

### Post by jagguars on 2005-12-15
i have another problem with installing applications:

how do i get all, for instance, games?

i can remember there is a wget ot get command but no idea what it was. installing games by console or synaptic or what ever is not what i want to do, i want to test the games from kubuntu and install all. as i know that is not that much disk space so i thought of givin it a try.

mfg me

---

### Post by kaamos on 2005-12-15
There is a package in the repos called kdegames. Try that (install with synaptic)? It has a lot of kde-dependencies, but if you want to play these games you'd have to install the dependencies anyway to get them working.

EDIT: if I was being unclear, I meant that kdegames is a metapackage that install all the games that belong to kde. I take it that is what you are trying to do?

---

### Post by linguistix on 2005-12-15
[QUOTE=warrior85]I did what you said about synaptic. then a window pops up asking for my root password, i wrote it.... and then nothing happened
the same thing happened when i click on add application in system >> adminstration... nothing happend.[/QUOTE]

Hi,

I have a similar problem if not the same. Each time I restart the computer (logging off won't make a difference) I only get the password question once. If I put in my user (I used expert install but the root password is the same) password, it still does nothing.

So lets say I go System -> Administration -> Printing.
It will ask me for the password, I enter the password, it does nothing.
I go back and try something else like System -> Administration -> Update Manager.
Still does nothing though sometimes it may put an item in my program list which says "Starting Update Manager" and then that item just disappears in a few seconds

This is something from the system log file, I don't know if it means anything

localhost gdm[30381] (pam_unix) session opened for user farhan by (uid=0)
localhost sudo (pam_unix) authentication failure; logname= uid=0 euid=0 tty= ruser= rhost=  user=farhan
localhost sudo farhan : command not allowed ; TTY=unknown ; PWD=/home/farhan ; USER=root ; COMMAND=validate
localhost  last message repeated 4 times
localhost gdm[30381] (pam_unix) session closed for user farhan

Any suggestions would be appreciated!

Thankyou

Farhan

---

### Post by jagguars on 2005-12-15
jou right baby... this works, for kde games! u can do it with adept or synaptic or whatever search for games, scroll down to kdegames and install... or search for kdegames and take that ;) 
for sure it is possible to type:
```
sudo apt-get update
sudo apt-get install kdegames
```

---

### Post by jagguars on 2005-12-16
i'm not sure if i understand your log file correctly, but if u just want to get the printer settings or any system settings, try to open them in the console with a sudo so i mean:
```
sudo systemsettings
```
you gonna be askef for your password and then you should be able to edit your settings with root rights. sometimes you can just watch settings if u start it with user rights, here u can edit them.
mfg me 
hope it helped

---

### Post by Mustard on 2005-12-16
> **linguistix]Hi,

I have a similar problem if not the same. Each time I restart the computer (logging off won't make a difference) I only get the password question once. If I put in my user (I used expert install but the root password is the same) password, it still does nothing.

So lets say I go System -> Administration -> Printing.
It will ask me for the password, I enter the password, it does nothing.
I go back and try something else like System -> Administration -> Update Manager.
Still does nothing though sometimes it may put an item in my program list which says "Starting Update Manager" and then that item just disappears in a few seconds

This is something from the system log file, I don't know if it means anything

localhost gdm[30381] (pam_unix) session opened for user farhan by (uid=0)
localhost sudo (pam_unix) authentication failure said:**
>  (pam_unix) session closed for user farhan

Any suggestions would be appreciated!

Thankyou

Farhan

In your case, because you installed using expert mode, the first user account was not given superuser privileges ie you can't use sudo.  This is different from the default install which sets up the first account automatically with superuser privileges.

What you will need to do is edit your /etc/sudoers file using the visudo command while logged in as root (through the terminal).  The visudo command has only one function.  It's function is to edit the /etc/sudoers file.  So just log in as root in terminal.  Type visudo and it will open up a text editor that works the same the nano text editor.

Add a line to the bottom of your sudoers file to look something like this below, but substituting your username for mine.

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

# Host alias specification

# User alias specification

# Cmnd alias specification

# Defaults

Defaults        !lecture,tty_tickets,!fqdn

# User privilege specification
root    ALL=(ALL) ALL
mustard ALL=(ALL) ALL

```

---

