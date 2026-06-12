---
title: "Just installed gusty and it says it is up to date when its not."
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by spacesearcher on 2008-03-25
Ok so I just installed ubuntu really late last night and waited till today to get my wireless network running (im using it now). when I go to system > administration > update manager, click check, and enter password,  it says my system is up to date. I don't know how it could have done that without being connected to the internet so I think its not working, How do i fix it?

---

### Post by indytim on 2008-03-25
I'm on Kubuntu so we have a slightly different interface.  Isn't there a button like check for updates of something similar after you've entered your password?

IndyTim

---

### Post by LaRoza on 2008-03-25
> **spacesearcher said:**
> Ok so I just installed ubuntu really late last night and waited till today to get my wireless network running (im using it now). when I go to system > administration > update manager, click check, and enter password,  it says my system is up to date. I don't know how it could have done that without being connected to the internet so I think its not working, How do i fix it?

Try using the update manager to search for updates.

---

### Post by glennric on 2008-03-25
Try typing
```
sudo apt-get update
sudo apt-get upgrade
```
in a terminal and see what output you get.  If everything works as it should then your system may be up to date.  If you get errors post them here and we can help you diagnose them.  You may also need to check to see that your software sources are all activated.

---

### Post by Belliinator on 2008-03-25
I think it says that until it accesses the internet for the first time anyway.
If your connected now go to synaptic and press 'reload' button.

---

### Post by joshrobinson on 2008-03-25
> **spacesearcher said:**
> Ok so I just installed ubuntu really late last night and waited till today to get my wireless network running (im using it now). when I go to system > administration > update manager, click check, and enter password,  it says my system is up to date. I don't know how it could have done that without being connected to the internet so I think its not working, How do i fix it?

click system > administration > synaptic package manager
click settings, then repositories

click the check marks next to main, restricted, multiverse, and universe (so they are checked)
in the cd rom section at the bottom, uncheck that
on the second tab third party, check the first one, close the window, and click the reload button, then mark all upgrades, and apply

---

### Post by spacesearcher on 2008-03-25
update manager is exactly what im trying to use but it doesn't recognize any it downloads like six files or something every time i hit check but then it always says it is up to date

---

### Post by spacesearcher on 2008-03-25
> **joshrobinson said:**
> click system > administration > synaptic package manager
click settings, then repositories

click the check marks next to main, restricted, multiverse, and universe (so they are checked)
in the cd rom section at the bottom, uncheck that
on the second tab third party, check the first one, close the window, and click the reload button, then mark all upgrades, and apply

when I click mark all upgrades it acts like its doing something then does nothing and apply still is just gray. does that button just check all of the packages underneath?

---

### Post by joshrobinson on 2008-03-25
so main, restricted, multiverse, and universe all are checked?

as for your question, no mark all upgrades doesnt install everything below, they are other optional packages

try closing synaptic, and running these commands in a terminal
```
sudo apt-get update
```
```
sudo apt-get upgrade
```

and see what it does

---

### Post by spacesearcher on 2008-03-25
ok something made it just click because when I was about to put in my password while running those commands it told me there were 205 updates so I guess its working now. but its strange that the update manager wasn't working earlier. 

oh well thanks for your help any ways

---

### Post by joshrobinson on 2008-03-25
it probably just didnt know where to look for the updates, when i had you check those boxes in the repositories menu, that told ubuntu where to look for updates, good to see you got it working, and that update manager is working now

---

### Post by spacesearcher on 2008-03-31
Ok its doing it again. I had to reinstall ubuntu doing sudo apt-get update then sudo apt-get upgrade gives this:
joe@joe-laptop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release    
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 2B in 0s (2B/s)  
Reading package lists... Done
joe@joe-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe-laptop:~$ 


the repository settings in synaptic are
under Ubuntu software tab only main universe restricted and multiverse are selected.
under the third party software the first one is checked 
and under updates only check for updates and "only notify about available updates" is checked. (should other things in here be checked?)

it still does not update it acts like its doing something but then never has any to download. this is like this in terminal synaptic and update manager.

Does anyone have a solution?

---

### Post by wirelessmonkey on 2008-03-31
Based on the output, it looks like your ubuntu is now up to date.  I see nothing to indicate a problem.

---

