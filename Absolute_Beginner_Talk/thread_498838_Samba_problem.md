---
title: "Samba problem"
date: 2007-07-11
forum: Absolute Beginner Talk
---

### Post by Totentanz on 2007-07-11
Hi, everyone, I m a total newbie when it comes to Linux and ofc i already encountered a problem.
I cannot install Samba on Ubuntu 7.04
i try to use:
sudo apt-get install samba

but all i get afterwards is this:

marko@Marko-NAS:~$ sudo apt-get install samba
Reading package lists... Done
Building dependency tree... Done
Package samba is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
However the following packages replace it:
smbclient samba-common
E: Package samba has no installation candidate

:S
I appreciate  your help.

---

### Post by davidsrsb on 2007-07-11
Some of the repositories were unavailable last night for some reason.

I would use synaptic to install samba myself

---

### Post by Totentanz on 2007-07-12
I still can't install it, I also tried t right click some random directory > share and ubuntu offered to install Samba but when i click install the window with install options dissapears for few secs and theh appears again and nothing happens.
I also tried reinstalling Ubuntu and it's still the same.

Help ppl

---

### Post by robertc36 on 2007-07-12
Have you tried to install through synpatic.
Or open software sources and change the server to main

---

### Post by Totentanz on 2007-07-12
I did tried to install it through synpatic but it wasn't there either...
I dont have working internet connection on my linux box, I m writing this from my win box.

---

### Post by robertc36 on 2007-07-12
aha!!!
If its wireless there is plenty of info on that. Good luck .

---

### Post by Totentanz on 2007-07-12
Ah, as it looks to me this is gonna be second time i gave up on linux and got back to dreaded win :/

---

### Post by robertc36 on 2007-07-12
I understand where you are coming from but it is well worth the reward.
No more defragging.
No more viruses.
No more constant rebooting.
There is so much help available here.
Why no internet connection on ubuntu?

---

### Post by Totentanz on 2007-07-12
Beacuse i have Sagem 800 E4 ADSL modem and when i plug it in, nothing happens :)
btw i still dont get whhat were u trying to say with that "aha !wireless" post" :D
i still cant install goddamn samba...

---

### Post by robertc36 on 2007-07-12
Not sure if this is for you but check out post 3 [http://ubuntuforums.org/showthread.php?t=422683&highlight=Sagem+800+E4](http://ubuntuforums.org/showthread.php?t=422683&highlight=Sagem+800+E4)

---

### Post by Totentanz on 2007-07-12
It is for my modem, thanks :D

---

### Post by Totentanz on 2007-07-12
I still have that Samba problem, anyone?

---

### Post by whein on 2007-08-08
How to install without an internet connection:  The first step is to find out exactly what packages you need.  You can do this the long way by going to [http://packages.ubuntu.com/]("http://packages.ubuntu.com/") and finding all the dependencies for your package (in this case samba) or the quick and dirty way, which is to tell Synaptic to install samba, then cut and paste the error message when it fails.  This will give you a bunch of URLs that you can take to a computer with an internet connection and download to a USB drive, etc.
Once you've downloaded all the .deb files you need, copy them into your /var/cache/apt/archives/ directory and rerun Synaptic.  This time the install should work since all the files are already on the hard drive.

One caveat: if you have old repository data, then the files Synaptic tells you to download may be older versions that no longer exist in the repositories.  In this case you may need to do some good old fashioned detective work to figure out what the new versions are, and if there are any new dependencies.
-Will

---

