---
title: "dist-upgrade questions"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by Aberrix on 2007-02-15
A quick question... I guess I didn't fully understand what I was doing here but... I did a 'sudo apt-get dis-upgrade' on my 6.06LTS box... the upgrade completed, etc, etc... so did this upgrade me to 6.10? or what exactly did/does the dist-upgrade do? thanks in advance.

---

### Post by tchoklat on 2007-02-15
it upgrades the packages you have to the newer distro, 6.06 to 6.10 etc
 
You should back up first as it will delete the packages prior to upgrading ...

---

### Post by Jussi Kukkonen on 2007-02-15
Upgrading using apt-get is possible, but not recommended. Instructions here: [https://help.ubuntu.com/community/EdgyUpgrades](https://help.ubuntu.com/community/EdgyUpgrades)

---

### Post by bapoumba on 2007-02-15
Hello,
dist-upgrade, without changing the repositories in sources.list, will not upgrade to the next Ubuntu release. It will perform an upgrade, checking dependencies better.

---

### Post by jvc26 on 2007-02-15
System -> About Ubuntu will tell you if you have updated to 6.10. I havent used the dist-upgrade option in a while as I prefer to install fresh each time I update a distro. If you dist-upgrade it upgrades the entire OS (presuming you put the edgy repos in)
Il

---

### Post by tchoklat on 2007-02-15
[[COLOR=#d40000]**Sef**[/COLOR]]("http://www.ubuntuforums.org/member.php?u=57646") [IMG]http://ubuntuforums.org/images/uf/statusicon/user_offline.gif[/IMG] vbmenu_register("postmenu_1645702", true);  
Ubuntu Master Roaster
[IMG]http://www.ubuntuforums.org/images/rank_uf_staff.png[/IMG]
 Join Date: Dec 2005
Location: Korea
Beans: 5,028
Ubuntu 6.10 Edgy User



**[B]******[/B]
**Re: problem using apt-get dist-upgrade to upgrade from 5.10 > 6.0.6** 
Did you use the two commands?

Applications > Accessories > Terminal

sudo apt-get update

sudo apt-get dist-upgrade

Also did you change your sources list?

You need to change Breezy to Dapper.

sudo gedit /etc/apt/sources.list
__________________
&#8220;Rogues are very keen in their profession, and know already much more than we can teach them.&#8221; A. C. Hobbs 

 
 
this post indicates that by amending your repositories you WILL upgrade from one version to the next, viz a viz 6.06 to 6.10.
 
Am I wrong?

---

### Post by Aberrix on 2007-02-15
> **tchoklat said:**
> 
Did you use the two commands?

sudo apt-get update

sudo apt-get dist-upgrade


This is a server that I administer via ssh, lately I've been doing 'sudo apt-get update' then 'sudo apt-get upgrade' then 'sudo apt-get dist-upgrade'.

> **tchoklat said:**
> 
Also did you change your sources list?

I have not changed/edited the sources list. I do not want to upgrade the entire distro, I want to stay at 6.06 LTS. I am just worried I accidentally upgraded the entire OS by using the dist-upgrade command, but from what you're all saying is that I'd have to update the sources.list in order to accomplish this?

I had a kernel update a couple days ago and the only way it would install was through a dist-upgrade. As I said though I want to stay at 6.06 LTS.

---

### Post by Jussi Kukkonen on 2007-02-15
> from what you're all saying is that I'd have to update the sources.list in order to accomplish this?
Correct.

---

### Post by marianlibrarian on 2007-02-15
I have an Ubuntu 6.06 CD for installing 6.06. Can I use this CD to upgrade a computer with 5.10? I have tried putting the CD in the CD player and the bios is setup to boot from the CDROM drive but now that 5.10 is on the hard drive, the CD with 6.06 is ignored. I have already used successfully the method of editing the source file and letting the upgrade happen that way but it took so long and used up so much bandwidth that this is feasible for me to do on 8 more machines. Any recommendations welcome.

---

### Post by tchoklat on 2007-02-17
you will need the 6.06 Alternative CD to upgrade. You will also have to add the CDRom to the sources list. The upgrade wil thenm take the files from the CDRom.
 
 
tony

---

