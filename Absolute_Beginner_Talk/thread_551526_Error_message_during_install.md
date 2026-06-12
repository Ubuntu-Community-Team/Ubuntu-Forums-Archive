---
title: "Error message during install"
date: 2007-09-15
forum: Absolute Beginner Talk
---

### Post by new2Forum on 2007-09-15
I am trying to install armyops.  I was able to install Tremulous with no problems due to the help from this site, :). For some reason prolly due to me my var/lib area is locked down.  I know the root password but it doesnt give me a chance to enter it. 
Here is the error message I was getting and I did update get-apt.

jeff@jeff-desktop:~$ sudo apt-get install armyops 
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package armyops
jeff@jeff-desktop:~$ apt-get install armyops
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?


thanxs  J

---

### Post by new2Forum on 2007-09-15
Bump

My system says get-apt is a bad command.  I am wondering how it could of dissapeared.

thanxs J

---

### Post by Maestro23 on 2007-09-15
Armyops?  Is this a game?  When you use the **apt-get** command, you are trying to install programs for the Ubuntu repos.  I don not believe armyops is in the repos.  Do you have a link to the programs site?

---

### Post by Daveth on 2007-09-15
this ?

[http://www.linux-gamers.net/modules/news/article.php?storyid=701](http://www.linux-gamers.net/modules/news/article.php?storyid=701)

---

### Post by new2Forum on 2007-09-15
YEs that is the game.

I am having a couple issues...

one being that my get-apt command is now gone from my system...cant seem to find it to re-enable.

The other problem is that part of my root seems to be now locked...

I am such a newb i barely know how to explain my issues.

How would one install something if it is not in the repository

J

---

### Post by Maestro23 on 2007-09-15
> **new2Forum said:**
> YEs that is the game.

I am having a couple issues...

one being that my get-apt command is now gone from my system...cant seem to find it to re-enable.

The other problem is that part of my root seems to be now locked...

I am such a newb i barely know how to explain my issues.

How would one install something if it is not in the repository

J

It's "apt-get".

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

---

### Post by Daveth on 2007-09-15
no, it looks like you have to download the old linux bin file from the likes of 

[http://americasarmy.filefront.com/file/Americas_Army_Operations_Full_Install_Linux;17959x#225639](http://americasarmy.filefront.com/file/Americas_Army_Operations_Full_Install_Linux;17959x#225639)

or other sites. Being a few years old now I'm not sure how many of the sites still hold copies. So no apt-get involved here. You need to navigate into your home folder where the .bin file was downloaded (open Nautilus, navigate to the file, then open terminal in the file drop-down list - is easy for you), then, in the same terminal:

```
 chmod +x  armyops190-linux.bin && ./armyops190-linux.bin
```

if this fails (assuming I have not made an error) then you should try to above with sudo chmod....etc etc.

Some suggestion that the build on that site is a bit flaky, so you may have to hunt around for other copies elsewhere if it falls down.

---

### Post by new2Forum on 2007-09-15
> It's "apt-get".

Thanxs,  I know I will not be forgetting that one again.

Daveth, thanxs that did the trick.  I am having issues still with right to my USR folder as it says permission denied.

Thanxs again everyone.  :)

J

---

### Post by Daveth on 2007-09-15
so, is it installed and running now ?

---

### Post by new2Forum on 2007-09-15
it is installed but would not run.  It wouldnt let me install it too where it wanted to go..USR area.
I uninstalled it and am trying again from scratch.

---

### Post by Daveth on 2007-09-18
sounds like a permissions thing. Try running that command with sudo I front of it. then log out of the terminal.

---

