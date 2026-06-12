---
title: "Boot up problem after chmod entry error"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by thompa on 2007-02-05
Trying to resolve a problem with my boot up which presented a $HOME error message and now I have made things worse!

I entered something like (oh, I hate this command line stuff):-

chmod -R 700 

and this was entered by mistake before I could add the home directory....

Now Ubuntu 6.06 will not boot to the desktop and trying to read the loading messages, I think that 'Kernel Log' and 'Avahi daemon (?)' cannot load.
The machine dumps me into tty and I enter my login and password only to be greeted by the fact that the machine is 'unable to cd to "/home/allan"'

I tried booting to 'Recovery', to older versions of Ubuntu and eventually tried to boot from the Ubuntu cd and reinstall the system files - but got as far as partitioning the drive, chickened out and Cancelled!

This is a bad Monday morning - now afternoon... can anyone help?... or does Ubuntu go out of the window!

Shouldn't all command line actions be available from a GUI?...

---

### Post by taurus on 2007-02-05
Boot into a recovery mode and post the output of this command here?

```
ls -la /home
```

---

### Post by thompa on 2007-02-05
Here's the result:-

drwxr-xr-x   5 root   root  4096 Feb 4 .
drwx------   21 root  root  4096 Jan 24 ..
drwxr-xr-x   2 root  root  4096 Feb 4 Windows
drw-r--r--   60 allan allan 4096 Feb 5 allan
drwxr-xr-x   2 root root 4096 Jan 27 samba

I have left the times out of the list - hope that I have copied it correctly!

Allan

---

### Post by taurus on 2007-02-05
While still in recovery mode, run

```
chmod 755 /home/allan
chmod 644 /home/allen/.dmrc
```
Reboot and see if you can log into your regular account, allan.

```
shutdown -r now
```

---

### Post by thompa on 2007-02-05
Tried logging in but still  'Kernel logging' and 'Avahi daemon' failed to load... and then thrown into the tty1 screen to log in again.

Booted into recovery mode from the boot menu and it stalled at the log in prompt when a stream of characters that would mean something to someone (ie not gibberish) was automatically entered into the login and password. Pressing 'Entre' brought up the login prompt and I could log in to 'root' again to shut down.

As the lines flew by, I did not a  'FATAL module' report on 'cman' - I think that this is the configuration manager ...

I did a ls -la /home request again and these are the results..

total 20
drwxr-xr-x 5 root root 4096 2007-02-04 .
drwx------ 21 root root 4096 2007-01-24 ..
drwxr-xr-x 60 allan allan 4096 2007-02-05 allan
drwxr-xr-x 2 root root 4096 2007-01-27 samba
drwxr-xr-x 2 root root 4096 2007-02-04 Windows

Interestingly I noticed that the date format changed...

---

### Post by thompa on 2007-02-05
Removed cman using:-
apt-get remove cman

Did a shutdown and from the boot menu selected the latest edition of Ubuntu.
Onloading the modules, noticed it was reporting a 'Starting Kernel Log - failed'

Put me into the TTY1 interface and entered login and password which reported that it was still 'unable to cd to "/home/allan"'

Still stuck in this mess...

---

### Post by dimeotane on 2007-02-22
I had the same problem on edgy 6.10 where upon login I got the message:

"User's $HOME/.dmrc fule is being ignored. This prevents the default session and language from being saved. File should be owned by user and have 644 permissions. User's $HOME directory must be owned by user and not writeable by other users"
That problem is discussed in many many threads..

 I was working on fixing the permissions for $home/.drms and I did a chmod 755 to /home/dimeo and a chmod 755 to /home.
But in the process of dealing with that small problem...it's got  far worse; I couldn't  login under my user name. I had to switch to ctrl-alt-f1 (tty1) and login there under root.  If I login under my username  it says "Unable to CD to /home/dimeo".   When booting the progress indicator stops halfway. 

Boot into safemode and enter these commands:  (except use your own username)

sudo chmod 755 /home
sudo chown username /home/username/.dmrc
sudo chmod 644 /home/username/.dmrc
sudo chown username  /home/username
sudo chmod 755 /home/username


It worked for me , and I have my system back only a few hours later....     Much better that way than to have to reinstall from scratch as I've worked on my system for a month, getting it configured.  This little mishap does make me think about making another backup very soon though!

---

### Post by Meserias on 2008-03-20
```

Boot into safemode and enter these commands:  (except use your own username)

sudo chmod 755 /home
sudo chown username /home/username/.dmrc
sudo chmod 644 /home/username/.dmrc
sudo chown username  /home/username
sudo chmod 755 /home/username

```

I got this error when playing with root permisions in HOME folder....witch is very DANGER !!!
**dimeotane **your solution works perfectly ! 
**[COLOR="Red"][SIZE="3"]Thank you very much dimeotane[/SIZE][/COLOR]**
:popcorn:

---

