---
title: "Newbie Experienced crash!"
date: 2006-06-28
forum: Absolute Beginner Talk
---

### Post by shootdamonkey on 2006-06-28
Hey
I'm extremely new to linux and ubuntu itself, but managed to install it fine from the live cd after liking it so much. The problem is when it was installing the updates everything started to stop responding and it eventually went into a frozen state where i couldnt actually do anything. So i restarted the computer, booted ubuntu up again and logged in, but now all it shows is a brown screen and nothing whatsoever appears.
I have a feeling that the crash i experienced must have done something to the installation so now i guess i have to recover it or re-install
Hence i need serious help

Thnx

](*,)

---

### Post by woedend on 2006-06-28
try pushind ctrl + alt + backspace or else alt + f2   to get to the command line.  Another option is in the gdm(login manager) to select terminal instead of gnome.  Either way, itll ask you to login and password.  Then try the following in this order
sudo apt-get update
sudo apt-get upgrade
sudo apt-get -f install

update to refresh the list, dist upgrade to upgrade where it left off, and -f install forces incomplete installations.

---

### Post by SkyNet2029 on 2006-06-28
Another option for you to try, since you did state the installation
crashed/froze midway is to see if it will continue where it left off, by running this command (from one of the vterms using CTRL+ALT+F1)
```
dpkg --configure -a
```
which, if its possible to continue, would/should get it running again. Note..This worked for me on a Debian Sarge bootstrapped install on this machine, and has also been what the Debian-installer (one U/Kubuntu uses) prompted me for on a few of the bogus installs that have happened here.
Another thing that seems to work here when our machines lock up is to force an interrupt to be passed to the kernel from its backend.. like opening and then closing a cd tray (empty of course). Usually it will force the system to stop what it was waiting on/for and then it will just dump you back into your session (a responsive versus UNresponsive machine)

---

### Post by shootdamonkey on 2006-06-28
yeh when i did what woedend said it gave me the message:
dpkg was interupted manually run "dpkg --configure -a"

so i did and i get a message about needing to be a superuser or something

---

### Post by SkyNet2029 on 2006-06-28
Yeah, my bad. I meant this:

```
$ sudo dpkg --configure -a
```

as you have to make your dpkg runs as a super-user.
Sorry about that. 8)

---

### Post by ajgreeny on 2006-06-28
OK, so type 

sudo dpkg --configure -a

to do this as superuser (root).  When asked for password use your own user password, hit return and everything should start happening.

---

### Post by shootdamonkey on 2006-06-28
that worked perfectly thanks. Just one other question, how can i view my windows files in ubuntu?

---

### Post by ajgreeny on 2006-06-28
You need to mount your windows partition first.  Have a look at the Ubuntu Guide at the following link for details of that, and lots of other things as well.

[http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

When you've done that navigate to /media/windows in nautilus or konqueror.

---

