---
title: "Apt-get weirdness?"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by rleechb on 2008-01-26
I just tried to install a few programs on my new ubuntu x64 build.  It does nothing.... really odd:

```
rlee@chb:~$ sudo apt-get install kismet
rlee@chb:~$ kismet
The program 'kismet' is currently not installed.  To run 'kismet' please ask your administrator to install the package 'kismet'
You will have to enable component called 'universe'
bash: kismet: command not found
rlee@chb:~$ su - 
Password: 
su: Authentication failure
Sorry.
rlee@chb:~$ 

```

Also, there's no sign of synaptic under "system"...


Any ideas?

---

### Post by jamoo1980 on 2008-01-26
You could try the following:

```
sudo nano /etc/apt/sources.list
```

If any of the repositories are commented out with # symbols, you could try un-commenting them, saving, then doing

```
sudo apt-get update
```

...then try running your original apt-get command again.

---

### Post by taurus on 2008-01-26
When you ran the first command from a terminal, sudo apt-get install kismet, was there any output at all?

```
sudo apt-get update
sudo apt-get install kismet
```

---

### Post by Dr Small on 2008-01-26
And with all of that said from everyone else,
if you want to launch Synaptic, try running:
```
gksudo synaptic
```

Dr Small

---

### Post by rleechb on 2008-01-26
Interesting.  Here's output from sources.list:

```
## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse


```

Thanks for your patience =D

btw.  running gksudo synaptic brought nothing up.  Just brought up a new line...

---

### Post by seventhc on 2008-01-26
If thats your source list, it looks as if every line is commented out..meaning it isn't read as a source to your computer. the # is a comment mark.

---

### Post by rleechb on 2008-01-26
Any idea as to how to remedy?  Should I just open up in vi and start uncommenting?

---

### Post by h0ax on 2008-01-26
Exactly !

Go through and all the lines that say 
```
"#deb ..."
```
change to
```
"deb ..."
```

I wouldn't do it to the cdrom line unless you just want to (:

---

### Post by h0ax on 2008-01-26
Sorry to double post, but I thought I'd explain a little bit of what's going on.

It looks like when it first set the file up it wasn't able to communicate with these sites, be it that you didn't have the internet plugged in or whatnot.
No problem it just commented the lines out (by placing a # in front of them) so that when the aptitude runs, it will ignore those lines.
Now that you have fixed your internet, we need to fix these lines by uncommenting them.
After you have done that do
```
sudo apt-get update
```
then
```
sudo apt-get install kismet
```
you should definitely see something after you type it this time ^_^
Have fun!

---

### Post by rleechb on 2008-01-26
wow.  I can't change the file permissions now?  Thanks for all your help:

```
rlee@chb:/etc/apt$ sudo chmod 666 sources.list
rlee@chb:/etc/apt$ ls -la
total 36
drwxr-xr-x   4 root root 4096 2008-01-26 07:32 .
drwxr-xr-x 111 root root 4096 2008-01-26 17:27 ..
drwxr-xr-x   2 root root 4096 2008-01-26 07:33 apt.conf.d
-rw-------   1 root root    0 2007-10-15 16:18 secring.gpg
-rw-r--r--   1 root root 4203 2008-01-26 07:30 sources.list
drwxr-xr-x   2 root root 4096 2007-10-15 13:44 sources.list.d
-rw-------   1 root root 1200 2007-10-15 16:18 trustdb.gpg
-rw-r--r--   1 root root 2393 2007-10-15 16:19 trusted.gpg
-rw-r--r--   1 root root 2381 2007-10-15 16:18 trusted.gpg
```

---

### Post by taurus on 2008-01-26
You're better be careful changing permissions outside your $HOME directory with the sudo command.  If you change the wrong files or directories, you could trash your system.

---

### Post by rleechb on 2008-01-26
Thanks, I'll keep that in mind; I figured the only way to write to that file was to err.. make it writable.

---

### Post by jamoo1980 on 2008-01-26
...you shouldn't need to change any file permissions, just un-comment the lines in sources.list. Firstly open the file in a text editor...

```
sudo gedit /etc/apt/sources.list
```

Then as h0ax said, delete the # symbol from the beginning of every line that begins with #deb, for example:

```
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

... should be changed to...

```
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
```

Save the file, then update apt-get and try to install your application again, as follows:

```
sudo apt-get update
sudo apt-get install kismet
```

Hope this helps :)

---

### Post by jamoo1980 on 2008-01-26
PS: In order to write to sources.list you'll need to open it as super-user, hence the 'sudo' in the command line. It's better to do it that way that to change it's permissions...

---

### Post by rleechb on 2008-01-26
Yep.  I opened it up as a non-super user, edited, and wasn't able to save (insufficient file permissions).  Trying to chmod w/ "sudo" didn't change the file permissions, and opening up the file in vi using sudo doesn't open up the file:

```
rlee@chb:/etc/apt$ cd
rlee@chb:~$ cd /etc/apt
rlee@chb:/etc/apt$ sudo vi sources.list
rlee@chb:/etc/apt$
```

Finally, logging in as superuser via "su -" gives me "bad password". 

I'm a total noob, if you haven't noticed already  :(

---

### Post by rleechb on 2008-01-26
..... just figured out that I logged in to ubuntu @ startup with a non superuser account.

lol.  Nevermind me...

---

### Post by seventhc on 2008-01-26
No, log in with your normal user...the one you created when you installed the system. When you want to run a command that requires extra permissions you use sudo in fron of the command. for instance if i put
apt-get install <nameofprogram> it won't install, now if i run
sudo apt-get install <nameofprogram> I will be asked for my password and it will install.
The password should be the same as the one you use when you log in as long as thats the account you created when you installed the system.

Unless you have more than one user on your computer, if so..never mind what I said. :D and just log into the main account. :)

---

### Post by rleechb on 2008-01-26
yeah, I got mixed up and logged into the wrong account.  Logged in w/ my account w/ admin, and all is well.  :mad:

---

### Post by h0ax on 2008-01-28
Glad you got it fixed!
enjoy ubuntu linux; post here often! (:

---

