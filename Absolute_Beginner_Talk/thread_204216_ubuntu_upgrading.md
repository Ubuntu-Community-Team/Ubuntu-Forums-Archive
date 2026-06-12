---
title: "ubuntu upgrading"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by compgump on 2006-06-26
I installed ubuntu 6.06  finally stumbled on how to get it to connect pppoe...now the update manager or update icon that appears states their are 93 updates available.  I click on it, and it use my password, and get a message stating that only 1 software management tool is allowed to run at the same time.  Please close the other application eg aptitude, or synaptic....  where are these open? how do i close them?  and why if i am only in the main area are all these open?

also was browsing websites, needed to install flashplayer...I was trying to uncompres it to the /file system, and it was saying i dont have authorization.   I uncompressed it to the desktop, read the readme, saying it needed to be installed in command line...i used terminal and tried the command it said to use, and was told file not found...is this because 1 its not uncompressed in the right area, or 2 terminal isn't command?  or both....

---

### Post by shoot2kill on 2006-06-26
first make sure you have not got any other programs open, and try again.. if this doesnot work i would end current session and logg back in.. there might be code to use in teminal but i am still new to all of this, so i dont know it...

---

### Post by Jagot on 2006-06-26
[QUOTE=compgump]also was browsing websites, needed to install flashplayer...I was trying to uncompres it to the /file system, and it was saying i dont have authorization.   I uncompressed it to the desktop, read the readme, saying it needed to be installed in command line...i used terminal and tried the command it said to use, and was told file not found...is this because 1 its not uncompressed in the right area, or 2 terminal isn't command?  or both....[/QUOTE]

[https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b](https://help.ubuntu.com/community/RestrictedFormats#head-f375cba46014e861cd5ec7643bd7c4ef05acff2b)

---

### Post by DCM36 on 2006-06-26
Have you checked on all of the virtual desktops don't have synaptic or the add/remove programs running? 

I think that you are using the command in the wrong folder. Here are few steps to help you get to the right place. Type these at the command line / terminal (they are the same thing).

```
cd Desktop
cd "Name of the folder it is extracted in"
sudo ./"install command"
```

---

### Post by catlett on 2006-06-26
Upgrade from the terminal and you shouldn't have a problem. Use these commands in the terminal```
 sudo aptitude update
``````
sudo aptitude upgrade
``` Directions from tar files may not take into account sudo. Most distros do not use it so following a guide that was written for someone who's distro uses su won't work for you. You have to compensate for the fact that a root terminal in ubuntu means preface the command with sudo.
Here is the official explanation [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
This guide will give you the rundown on installing in ubuntu. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

You should always search synaptic package manager before you try to compile an application. If it is in synaptic it will install and run on your system easily. Compiling doesn't always work.

---

### Post by compgump on 2006-06-26
ok, the error with the update icon is directly at startup...   I went into the terminal, and typed cd desktop, says bash: cd: desktop no such file or directiory...i tried cd install_flash_player_7_linux same error   

 while trying sudo update, and sudo upgrade i am getting E: dpkg was interrupted, you must manually run 'dpkg - - configure -a' to correct the problem  i did that, and got a lot of dpkg this that....now i try and run sudo update, or sudo upgrade, says command not found  also while using synaptic, it says the following errors were found on your system....E:dpkg...etc

---

### Post by catlett on 2006-06-26
I'm assuming you ran it but run it again just to make sure```
sudo dpkg --configure -a
``` Then run an upgrade with aptitude. It uses the same repositories etc as apt-get but it is better at handling dependency issues.
Actually since you are having so many issues, run a dist-upgrade
```
sudo aptitude update 
``````
sudo aptitude dist-upgrade
``` See what happens after that. Aptitude should clear everything up.

---

### Post by compgump on 2006-06-27
Ok, thank you, updates/upgrades went well, things are working now.

As far as not finding Desktop....not desktop...i now know linux is case sensitive, which is a good thing.....

Everything seems to be in good order now, cept OHS..operator head space...which i dont think can be helped much her in the forums...

---

