---
title: "Automatix2"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by Snoopy1966 on 2006-11-11
Hello,
I installed Automatix2 and I downloaded the binary codecs.  It seemed to work but now it is stopped at setting up and running scripts.  It has been like this for 30 minutes or more.  Is this normal?  I gave up on Easy Ubuntu, and I am trying to fix the broken packages.  Still not clear on that.  I have been reading and it said the Automatix would fix these problems.  Could it be that Easy Ubuntu failed installing these codecs and Automatix can not complete the install?  Any help for this matter?

---

### Post by wpshooter on 2006-11-11
I know this probably does not help you, but IMO, you would be smart to take the same option that you did with Easy Ubuntu.  In my experience trying to use these 3rd party utilities, etc. caused all kind of problems.

Good luck.

---

### Post by Snoopy1966 on 2006-11-11
Hello again,
I was reading about installing KDE desktop and I did the following commands

```
sudo aptitude update && sudo aptitude install kubuntu-desktop x-window-system-core kdm
sudo /etc/init.d/kdm restart

W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
ahmed@ahmed-desktop:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)

```

How do I fix this problem?

My system froze up on me and I had to use the power button to restart.  everthing came back thank God.

I used Synaptic Package manager to try to get the KDE stuff, but I do not see where the JDF desltop is.  That is why I did the commands that I stated at the begining of the post.  I see many things that start with K now in the applications.

---

### Post by Snoopy1966 on 2006-11-11
> **wpshooter said:**
> I know this probably does not help you, but IMO, you would be smart to take the same option that you did with Easy Ubuntu.  In my experience trying to use these 3rd party utilities, etc. caused all kind of problems.

Good luck.


So how do I get all the codecs and stuff then?  To many newbie questions :???:

---

### Post by arnieboy on 2006-11-11
after u have logged out and logged back in, do not run anything (automatix or anything else).
just paste the results of the following command:
```
cat /etc/apt/sources.list
```

---

### Post by Snoopy1966 on 2006-11-11
OK thanks for the reply here are the results...

```
ahmed@ahmed-desktop:~$ cat /etc/apt/sources.list
deb http://packages.freecontrib.org/plf/ dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src http://us.archive.ubuntu.com/ubuntu/ dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://archive.ubuntu.com/ubuntu/ dapper universe main restricted multiversedeb-src http://us.archive.ubuntu.com/ubuntu/ dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ dapper-backports main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted
deb http://security.ubuntu.com/ubuntu dapper-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
deb http://easyubuntu.cafuego.net main easyubuntu
deb http://www.getautomatix.com/apt dapper main



#AUTOMATIX REPOS START

deb http://archive.canonical.com/ubuntu dapper-commercial main

deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-updates main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper-security main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu dapper main restricted universe multiverse
#AUTOMATIX REPOS END
ahmed@ahmed-desktop:~$
```

I see the part where it says - Uncomment the following two lines to add software from the 'backports'.  But what lines are they.  Well I do not know so much yet, but I am trying.

---

### Post by arnieboy on 2006-11-11
no dont uncomment anything. it looks fine to me. just delete the following line:
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
and save your sources.list and do an apt-get update
then post your errors if u get any.

---

### Post by .t. on 2006-11-11
To get the codecs: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)

Hopefully this will be made a lot easier with Feisty (out in April 07).

---

### Post by Snoopy1966 on 2006-11-11
Uumm.  How do I delete that line?  I did the command you told me to again

cat /etc/apt/sources.list

But I can not edit that line to delete it.  Is this saved somewhere so I can remove that line?

---

### Post by .t. on 2006-11-11
Use "nano -w /etc/apt/sources.list".

Cat just prints the file.

---

### Post by Snoopy1966 on 2006-11-11
OK I did that with nano.  How do you save it?  I found the source list in the apt folder.  I tried to edit that but it says I do not have permissions necessary to edit the file.  Man I think I am too dumb to use Linux :confused:

---

### Post by Snoopy1966 on 2006-11-11
Hello,
I get this error.  I was able to save sources.list, but I do not remember how I did it.  I can not edit the sources.list.save.  Anyway this is the error when I get update

```
ahmed@ahmed-desktop:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
ahmed@ahmed-desktop:~$ sudo gedit /etc/apt/sources.list Password:

(gedit:8707): Gdk-WARNING **: locale not supported by Xlib

(gedit:8707): Gdk-WARNING **: cannot set locale modifiers
ahmed@ahmed-desktop:~$ apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
ahmed@ahmed-desktop:~$
```

Now what.  How do I give access to my own stuff.  I am very confused.

---

### Post by .t. on 2006-11-11
No: it's hard at first, but, :): You'll learn.

Because of the security system in Linux, all files except for those in your home directory are by default read-only by your normal user. The root user has read-write access to all files, and she is like the Administrator on Windows. However, unlike Windows, you cannot log in as root with Ubuntu as root has no password. In many Linux distributions, you use "su" to gain access as the root user. This logs you in as her, and gives you a shell (like you get when you run a terminal) with the full permissions that root has. In Ubuntu however, we use sudo. This by default lets you run one command as root, using your own password. You can also get a log-in shell (as it is called) by running "sudo -i". To run a graphical application as root, run "gksudo" (or gksu, which is a link to it).

So, to edit /etc/apt/sources.list you need to use sudo: "sudo nano -w /etc/apt/sources.list". Or for a graphical editor: "gksudo gedit /etc/apt/sources.list".

To save a file in nano, press Ctrl+X.

apt needs root permissions as well, as it modifies your system: so, again, you'll need to use sudo.

---

### Post by Snoopy1966 on 2006-11-11
OK thanks for the help>  I edited every source list and removed the line 
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

Then I did this:
sudo apt-get update

W: GPG error: [http://packages.freecontrib.org](http://packages.freecontrib.org) dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems



ahmed@ahmed-desktop:~$  apt-get update
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory
ahmed@ahmed-desktop:~$

So now what?

EDIT:  Here is my source list now

deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main



#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by .t. on 2006-11-11
Right you don't need to run:```
sudo apt-get update
apt-get update
```
Remember that apt-get update will always require root permissions, as it modifies files outside of your home directory. So it'll always be "sudo apt-get update".

```
W: GPG error: http://packages.freecontrib.org dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F120156012B83718
W: You may want to run apt-get update to correct these problems
```
Lots of repositories on the internet are signed to prove the authenticity of the packages. They are signed by a machine with a private key, that only that machine knows. This can be decrypted by others with the public key, which is public. The message above shows that you do not have the public key for the repository, so you cannot test the packages. You will need to find the public key, and import it so that it can be used by apt. The easiest way to do this is to find the public key, and run "apt-key add <file> on it". In this case, the recommended method is to run:```
wget http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg -O- | sudo apt-key add -
```

This will download and install the key for you. :)

---

### Post by Snoopy1966 on 2006-11-11
Excellent!!  No errors now when I did that.  I had to do it twice, but it worked the second time.  

Now will I be able to get codecs and stuff like that now or is there something else I need to do?  Still use Automix?  There is this link you gave me
To get the codecs: [https://wiki.ubuntu.com/RestrictedFormats](https://wiki.ubuntu.com/RestrictedFormats)
I did not check it out yet.  I wanted to get all this resolved first.  So all my broken packages are fixed now too?  Anything esle I should do before I proceed?
Thanks again for all the help :)

---

### Post by strabes on 2006-11-11
if you prefer, you can use gedit instead of nano to edit text files. gedit is like notepad in windows if that helps you out. BTW Ctrl + O saves files in nano. Ctrl + X exits.

---

### Post by .t. on 2006-11-11
Do check out RestrictedFormats. It'll be of great use. I suggest not to use quick-fix solutions such as Automatix or EasyUbuntu as they **will** break your system in the long-term. Especially if you ever want to upgrade. Apart from that, you should be set to go!

---

### Post by Rainmaker91 on 2007-11-19
hello 
I am totally noob in ubuntu and I want Automatix2
but I can not find a site that says how to install it (a site that works) 
can someone tell me how to install Automatix2.

:confused:

thanks for helping :)

---

### Post by bodhi.zazen on 2007-11-19
> **Rainmaker91 said:**
> hello 
I am totally noob in ubuntu and I want Automatix2
but I can not find a site that says how to install it (a site that works) 
can someone tell me how to install Automatix2.

:confused:

thanks for helping :)

This is an old thread you have found :)

Automatix is not maintained by Ubuntu and so the Ubuntu forums are not the best source of information.

Look here :

[http://www.getautomatix.com/](http://www.getautomatix.com/)

[http://www.getautomatix.com/wiki/index.php?title=Installation](http://www.getautomatix.com/wiki/index.php?title=Installation)

If you still have questions, see the Automatix forums.

---

