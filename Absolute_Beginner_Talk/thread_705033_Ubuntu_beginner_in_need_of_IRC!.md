---
title: "Ubuntu beginner in need of IRC!"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by bnmjosh on 2008-02-22
Hello everyone! I need some help. Could you have ever guessed?

I need to be able to access IRC channels as I did back in Windows. I read up on some Google results, and I heard of XChat? I put xchat in the Terminal. It said to install it type "sudo apt-get install xchat". I did, and it said   "E: Couldn't find package xchat"
So I tried "sudo apt-get update" and all that jazz. Still didn't work after that.

Now, what I need to know is a simple step by step tutorial (orsomething, please people, I'm becoming desperate) to install some kind of IRC chat program and use it. PLEASE, and thank you all very much. :)

---

### Post by InfinityCircuit on 2008-02-22
First, your problem is very odd since xchat should work:

```
dmoerner@dmoerner-desktop:~$ sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tcl8.4 xchat-common
Suggested packages:
  tclreadline libnet-google-perl
Recommended packages:
  libnotify-bin
The following NEW packages will be installed:
  tcl8.4 xchat xchat-common
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 2528kB of archives.
After this operation, 7217kB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

However, that doesn't matter, since Pidgin has a built-in IRC client:

1. Applications -> Internet -> Pidgin

If this is the first time, it will say Welcome and ask you to add an account.  Click "Add" 

2. Go to protocol and use the drop-down menu to select IRC.

3. Enter your screen name.  Leave the password and local alias blank.  Hit Save.  Pidgin will start up a freenode-connect window.  In the field, type "/join #ubuntu"

You are done!

---

### Post by taurus on 2008-02-22
Do you have all the repos enable in /etc/apt/sources.list?  Open a terminal and edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```
and place the # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  

Now run

```
sudo apt-get update
sudo apt-get install xchat
```

---

### Post by sisco311 on 2008-02-22
please post the output of:
```
cat /etc/apt/sources.list
```
***edit i'm slow

---

### Post by bnmjosh on 2008-02-22
WOW! Thanks so much! Also, if it's not too much to ask... How do I do private chat with someone in the same (or diff) channel? I was in need of talking to someone on IRC but I'm not aware of how to do private chats.

This message was to anyone who can help, but my thanks is to InfinityCircuit, THANKS!

---

### Post by bnmjosh on 2008-02-23
> **sisco311 said:**
> please post the output of:
```
cat /etc/apt/sources.list
```
***edit i'm slow
 Here we are:
>  cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe
# deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted

Sorry it took so long, busy.

---

### Post by sisco311 on 2008-02-23
> **taurus said:**
> Do you have all the repos enable in /etc/apt/sources.list?  Open a terminal and edit /etc/apt/sources.list

```
gksudo gedit /etc/apt/sources.list
```and place the # in front of the first line, cdrom, to comment it out.  Then, remove the # in front of all the lines that start with **deb** & **deb-src**.  Save it and close down gedit window.  

Now run

```
sudo apt-get update
sudo apt-get install xchat
```
the perfect solution:)

---

### Post by bnmjosh on 2008-02-23
> **sisco311 said:**
> the perfect solution:)

Tried that, does the exact same thing.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package xchat


---

### Post by sisco311 on 2008-02-23
backup your source.list:
```
sudo mv /etc/apt/sources.list /etc/apt/sources.list-backup
```create a new one:
```
gksu gedit /etc/apt/sources.list
```copy and paste this in the file:
> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted


deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiversesave and exit.


and run:
```
[FONT=monospace]sudo apt-get update
sudo apt-get install xchat[/FONT]
```

EDIT
if you have problems with the new  repositories, remember you have a backup:
```
sudo cp /etc/apt/sources.list-backup /etc/apt/sources.list
sudo apt-get update
```

---

### Post by bodhi.zazen on 2008-02-23
Not sure about your repos

See this link : [Enable Repositories](https://help.ubuntu.com/community/Repositories/Ubuntu)

I run xchat so it is an option ;)

---

### Post by dustman on 2008-02-23
well, the default IM with which Ubuntu comes : Gaim/Pidgin, has the possibility to connect to IRC channels. I use it all the time. Just open Gaim/Pidgin and create a new account with the protocol IRC. It works best for me cause i also use GTalk and Yahoo Messenger, so i have all  my friends in the same list ;).


Cheers!

Radu

---

### Post by bnmjosh on 2008-02-23
Okay guys, I appreciate all the help! I so far, go it to get passed that stupid error. But now, this is what I get when I type  'sudo apt-get install xchat'

> sudo apt-get install xchat
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  tcl8.4 xchat-common
Suggested packages:
  tclreadline libnet-google-perl
Recommended packages:
  libnotify-bin
The following NEW packages will be installed:
  tcl8.4 xchat xchat-common
0 upgraded, 3 newly installed, 0 to remove and 79 not upgraded.
Need to get 2526kB of archives.
After unpacking 7201kB of additional disk space will be used.
E: You don't have enough free space in /var/cache/apt/archives/.


I don't understand....

---

### Post by taurus on 2008-02-23
Sounds like you are running out of disk space.  Post the output of this command from a terminal.

```
df -h
```

---

### Post by bnmjosh on 2008-02-23
> **taurus said:**
> Sounds like you are running out of disk space.  Post the output of this command from a terminal.

```
df -h
```
Thanks for the quick reply :) Here's what I get.

>  df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 284M   16M  269M   6% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 284M   16M  269M   6% /lib/modules/2.6.22-14-generic/volatile
varrun                284M   92K  284M   1% /var/run
varlock               284M     0  284M   0% /var/lock
udev                  284M   68K  284M   1% /dev
devshm                284M     0  284M   0% /dev/shm
tmpfs                 284M  196K  284M   1% /tmp
/dev/hda1             292G  2.1G  275G   1% /media/disk

Okay, I did the same old 'sudo apt-get install xchat'  and it worked! So far, it's in the process of installing. Thanks so much for the help everyone! I'll edit again if something else happens...

---

### Post by taurus on 2008-02-23
Are you running Ubuntu from a LiveCD?

---

### Post by bnmjosh on 2008-02-23
Okay here's what I get when I put 'sudo apt-get install xchat':

>  sudo apt-get install xchat
Reading package lists... Done
Building dependency tree        
Reading state information... Done
The following extra packages will be installed:
  tcl8.4 xchat-common
Suggested packages:
  tclreadline libnet-google-perl
Recommended packages:
  libnotify-bin
The following NEW packages will be installed:
  tcl8.4 xchat xchat-common
0 upgraded, 3 newly installed, 0 to remove and 79 not upgraded.
Need to get 2526kB of archives.
After unpacking 7201kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main tcl8.4 8.4.15-1build1 [1169kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe xchat-common 2.8.4-0ubuntu5 [1050kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe xchat 2.8.4-0ubuntu5 [308kB]    
Fetched 2526kB in 1m40s (25.1kB/s)                                             
Selecting previously deselected package tcl8.4.
(Reading database ... 92661 files and directories currently installed.)
Unpacking tcl8.4 (from .../tcl8.4_8.4.15-1build1_i386.deb) ...
Selecting previously deselected package xchat-common.
Unpacking xchat-common (from .../xchat-common_2.8.4-0ubuntu5_all.deb) ...
Selecting previously deselected package xchat.
Unpacking xchat (from .../xchat_2.8.4-0ubuntu5_i386.deb) ...
Setting up tcl8.4 (8.4.15-1build1) ...

Setting up xchat-common (2.8.4-0ubuntu5) ...

Setting up xchat (2.8.4-0ubuntu5) ...

Processing triggers for libc6 ...
ldconfig deferred processing now taking place

What now? Just wait?

---

### Post by bnmjosh on 2008-02-23
> **taurus said:**
> Are you running Ubuntu from a LiveCD?

Yes I'm afraid so. I'm guessing that's the reason? I have a 300GB hard drive, but it, for some reason, doesn't work. Getting new one eventually. I Tried to just hit the install thing for Ubuntu on my desktop, but it never works. It just tells me to insert media disk after it installs and I take the CD out.

---

### Post by bnmjosh on 2008-02-23
I just typed xchat in the terminal a second ago, and it's working! Thanks everyone, especially taurus :D

---

### Post by taurus on 2008-02-23
Just wait for ldconfig to finish and xchat should be in Applications -> Internet.  And since you are running Ubuntu from a LiveCD, you know that you have to install xchat again the next time you boot from it.

---

### Post by bnmjosh on 2008-02-23
> **taurus said:**
> Just wait for ldconfig to finish and xchat should be in Applications -> Internet.  And since you are running Ubuntu from a LiveCD, you know that you have to install xchat again the next time you boot from it.

I actually have a nice situation, I'm able to keep my computer running most of the time. It rarely shuts down. So it's not too much trouble. But I'm always aware with my memory of what I will have to do when it does shut down, this is about the 5th thing? Thanks again! Huge help.

---

### Post by taurus on 2008-02-23
Why can't you install Gutsy on your machine with that 300GB harddrive since there is nothing on it?  Any error when you try to install it?

---

### Post by lyceum on 2008-02-23
If you just want to use Pigin try this:

[http://whitetreeevolution.com/chatohio.html](http://whitetreeevolution.com/chatohio.html)

It is for the Ohio LoCo group, but just change where you are going.

---

