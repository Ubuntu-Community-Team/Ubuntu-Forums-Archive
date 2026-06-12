---
title: "Updated Programs"
date: 2006-11-13
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-13
I have a pretty general question.  When a new version of a program comes out(lets say firefox) is this updated by the new updates to download or do I have to uninstall what I have and reinstall never version.

---

### Post by earobinson on 2006-11-13
The update icon that auto appears will let you update firfox :)

---

### Post by joshsherman on 2006-11-13
It updates it

-j

---

### Post by joshsherman on 2006-11-13
> **earobinson said:**
> The update icon that auto appears will let you update firfox :)

Pardon my redundant post... you beat me to it ;)

-j

---

### Post by earobinson on 2006-11-13
> **joshsherman said:**
> Pardon my redundant post... you beat me to it ;)

-j
np I know when I post a Q its always nice to have more than one answer that way you can be more certain you have the correct one

---

### Post by gentlemanmasher on 2006-11-13
Thanks I appreciate both responses.  I too like more that one answer.

---

### Post by Craftycorner on 2006-11-13
I don't mean to be 'duh', but this apply to Amule as well?  To all the programs?  Cuz I know that in some cases, if your not up to the minute, your butt is to the wind so to speak...lol

---

### Post by earobinson on 2006-11-13
This will apply to any programs you installed using the repositories (synaptic or apt-get)

---

### Post by keithweddell on 2006-11-13
Sorry to be picky but ...
You will get all security updates for programs downloaded from the repoistories.  But I don't think you will get new versions, features etc. until you upgrade to a new release of Ubuntu (eg Dapper -> Edgy).  Please correct me if I'm wrong.

Keith

---

### Post by earobinson on 2006-11-13
depends, if the new version is added to to the repos you will get it. also it depends on your sources.list

---

### Post by Craftycorner on 2006-11-13
I installed Amule using Symantic and I think I've got Edgy, how do I make sure I got Edgy?

---

### Post by earobinson on 2006-11-13
one of the easyest ways is to "cat /etc/sources.list" look for the word "edgy"

---

### Post by Craftycorner on 2006-11-13
I don't have edgy, how do i get it

---

### Post by earobinson on 2006-11-13
googled: ubuntu upgrade to edgy found: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades). Just to make sure I assume you have dapper?

---

### Post by Craftycorner on 2006-11-13
add remove programs...yes.  presuming that's dapper.

---

### Post by Craftycorner on 2006-11-13
I wish you'd open your MSN, I have that, it would be faster.

---

### Post by earobinson on 2006-11-13
> **Craftycorner said:**
> add remove programs...yes.  presuming that's dapper.
Im not sure I understand that

---

### Post by Craftycorner on 2006-11-13
My MSN is [email]craftycorner201@hotmail.com[/email].  My Adapt Installer is open.  What do I do now?  What do I search for?

---

### Post by earobinson on 2006-11-13
no msn, Im not sure I understand why couldn't you use that tutorial I linked to upgrade to edgy?

---

### Post by Craftycorner on 2006-11-13
URL please...

---

### Post by Craftycorner on 2006-11-13
I see it now

---

### Post by earobinson on 2006-11-13
> **earobinson said:**
> googled: ubuntu upgrade to edgy found: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades). Just to make sure I assume you have dapper?
^^^

---

### Post by Craftycorner on 2006-11-13
run command does not recognize 
gksu "update-manager -c" 
or - update-manager -c

---

### Post by earobinson on 2006-11-13
can you copy and paste the output?

---

### Post by Craftycorner on 2006-11-13
update-manager -c
Could not run the specified command.

gksu update-manager -c 
Could not run the specified command.

---

### Post by earobinson on 2006-11-13
try gksudo "update-manager -c"

---

### Post by Craftycorner on 2006-11-13
same reply from the puter

---

### Post by Craftycorner on 2006-11-13
I've got Kubuntu, not Ubuntu btw

---

### Post by earobinson on 2006-11-13
ok so lets check if its gksudo or update-manager missing can you paste the output of ```
which gksudo
``` and ```
which update-manager
```

---

### Post by earobinson on 2006-11-13
> **Craftycorner said:**
> I've got Kubuntu, not Ubuntu btw
lol in that case its a kdesu (I think) or you could use sudo

---

### Post by Craftycorner on 2006-11-13
I don't understand

---

### Post by earobinson on 2006-11-13
instead of gksudo use kdesu (I think) or sudo

---

### Post by Craftycorner on 2006-11-13
with sudo, 

cntrl + f2 update-manager -c just disapeared

---

### Post by earobinson on 2006-11-13
> **Craftycorner said:**
> with sudo, 

cntrl + f2 update-manager -c just disapeared
Sorry I dont understand this post

---

### Post by Craftycorner on 2006-11-13
I entered the text 

sudo update-manager -c 

in the run command window.  I didn't get an error message this time.  I didn't get anything.  the run command window dissapeared as if I had closed it but I did not close it.

---

### Post by earobinson on 2006-11-13
did it prompt for a password? Try: ```
sudo -s
update-manager -c 
```

---

### Post by Craftycorner on 2006-11-13
same thing

---

### Post by Craftycorner on 2006-11-13
should I be doing this on a Konsol?

---

### Post by earobinson on 2006-11-13
did sudo prompt for a password? I assume ```
sudo synaptic
``` works?

---

### Post by earobinson on 2006-11-13
> **Craftycorner said:**
> should I be doing this on a Konsol?
Yes

---

### Post by Craftycorner on 2006-11-13
That's the problem!  Trying again

---

### Post by Craftycorner on 2006-11-13
craftycorner@craftycorner:~$ sudo update-manager -c
Password:
sudo: update-manager: command not found
craftycorner@craftycorner:~$ ksudo update-manager -c
bash: ksudo: command not found
craftycorner@craftycorner:~$

---

### Post by earobinson on 2006-11-13
fyi all the code should be done in a terminal (for you Konsol) lets try ```
sudo -s
apt-get install update-manager
update-manager -c
``` this will install the update-manager then let you run it (we hope)

and dont lose hope there are plenty of people smarter than me here :)

---

### Post by Craftycorner on 2006-11-13
NOW we're cooking with gas!

---

### Post by earobinson on 2006-11-13
I assume that it was successfull?

---

### Post by Craftycorner on 2006-11-13
craftycorner@craftycorner:~$ sudo -s
root@craftycorner:~# apt-get install update-manager
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  unattended-upgrades
The following NEW packages will be installed:
  unattended-upgrades update-manager
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 750kB of archives.
After unpacking 3031kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main unattended-upgrades 0.1ubuntu3 [5060B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main update-manager 0.42.2ubuntu22 [745kB]
Fetched 750kB in 1m48s (6883B/s)
Selecting previously deselected package unattended-upgrades.
(Reading database ... 103283 files and directories currently installed.)
Unpacking unattended-upgrades (from .../unattended-upgrades_0.1ubuntu3_all.deb) ...
Selecting previously deselected package update-manager.
Unpacking update-manager (from .../update-manager_0.42.2ubuntu22_all.deb) ...
Setting up unattended-upgrades (0.1ubuntu3) ...
Setting up update-manager (0.42.2ubuntu22) ...

root@craftycorner:~#

____________________________

This how it suppose to look?  I don't remember where the paste dump is...

---

### Post by earobinson on 2006-11-13
that looks good, and when you ran update-manager -c what then?

---

### Post by Craftycorner on 2006-11-13
running........

---

### Post by earobinson on 2006-11-13
looks successfully then :) I refer you back to the tutorial then :) If you have any other problems let us know and we will do our best!

---

### Post by Craftycorner on 2006-11-13
Command 'gksu /usr/bin/update-manager ' not found.

---

### Post by Craftycorner on 2006-11-13
Command 'gksu /usr/bin/update-manager ' not found.

do I need to restart my computer?

---

### Post by earobinson on 2006-11-13
you should not be using use ```
sudo -s
update-manager 
``` instead

---

### Post by Craftycorner on 2006-11-13
I'm using icons off the Kmenu...

---

### Post by Craftycorner on 2006-11-13
and cut & pasting 4 u...

---

### Post by earobinson on 2006-11-13
> **Craftycorner said:**
> I'm using icons off the Kmenu...
icons?

---

### Post by earobinson on 2006-11-13
> **earobinson said:**
> icons?
If this dont work you might be best to dl the edgy iso and do a clean install, as I google a lot of people seem to have had problems with this update :(

---

### Post by Craftycorner on 2006-11-13
I gotta restart anyway...

---

### Post by Craftycorner on 2006-11-13
I don't want my butt in the wind, I'm not at risk am I?

---

### Post by earobinson on 2006-11-13
at risk of?

---

### Post by Craftycorner on 2006-11-13
how do i get rid of this half installed program?

---

### Post by earobinson on 2006-11-13
It fully installed but you should be able to use the same command but use "remove" instead of install

---

### Post by Craftycorner on 2006-11-13
give me the command line please, synaptic isn't responding to commands, neither is amule.

---

### Post by earobinson on 2006-11-13
> **earobinson said:**
> fyi all the code should be done in a terminal (for you Konsol) lets try ```
sudo -s
apt-get install update-manager
update-manager -c
``` this will install the update-manager then let you run it (we hope)

and dont lose hope there are plenty of people smarter than me here :)
```
sudo -s
apt-get remove update-manager
``` But this to me seems like a bad idea since that program should have been there all along

---

### Post by Craftycorner on 2006-11-13
I ask, I have corporal tunnel syndrome causing typos

---

### Post by earobinson on 2006-11-13
fair

---

### Post by Craftycorner on 2006-11-13
phone, sorry 4 hold up

---

### Post by Craftycorner on 2006-11-13
craftycorner@craftycorner:~$ sudo -s
Password:
root@craftycorner:~#
root@craftycorner:~# sudo -s
root@craftycorner:~# apt-get remove update-manager
Reading package lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
  update-manager
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 2941kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 103374 files and directories currently installed.)
Removing update-manager ...
I/O warning : failed to load external entity "/var/lib/scrollkeeper/(null)/scrollkeeper_cl.xml"
root@craftycorner:~#

????????

---

