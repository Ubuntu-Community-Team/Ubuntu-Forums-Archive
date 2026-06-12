---
title: "Updating to 6.10"
date: 2007-03-09
forum: Absolute Beginner Talk
---

### Post by mdknaebel on 2007-03-09
I installed Ubuntu 5.10 on my Powerbook G3 Wallstreet (Old world) using this site as a guide: [http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/]("http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/")

Its hard to just put in the 6.10 CD and install, which I have tried, and I would kind of like to upgrade to Ubuntu 6.10.  One time, I was offered a an update that downloaded and began to install 6.10, but i had to stop it.  I have never gotten this message, is there any way to upgrade from ubuntu itself?

---

### Post by halitech on 2007-03-09
open a terminal and do

```

gksu "update-manager -c -d"

```

---

### Post by mikewhatever on 2007-03-09
> **mdknaebel said:**
> I installed Ubuntu 5.10 on my Powerbook G3 Wallstreet (Old world) using this site as a guide: [http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/]("http://http://gonz.wordpress.com/2006/03/22/installing-ubuntu-510-breezy-badger-on-an-old-world-powerbook-g3-wallstreet/")

Its hard to just put in the 6.10 CD and install, which I have tried, and I would kind of like to upgrade to Ubuntu 6.10.  One time, I was offered a an update that downloaded and began to install 6.10, but i had to stop it.  I have never gotten this message, is there any way to upgrade from ubuntu itself?

Why is it hard to 'put in the 6.10 CD and install'?. Aren't you saying you've tried? Same about the online update. What do you mean by upgrading from Ubuntu itself? Can you upgrade Ubuntu from another OS? Sorry, I am lost here.

---

### Post by mdknaebel on 2007-03-09
Sorry mike, 

Because im on an old world mac, you cannot just put the cd in and install. you have to configure bootX, transfer files from installation cd, and then start the alternate installer...

Ive tried to use the instructions I posted to do 6.10, however it did not work like 5.10 did.  I want to upgrade Ubuntu while using Ubuntu, and I dont get the OS upgrader from the software updater

---

### Post by mikewhatever on 2007-03-09
Right, but I do not think you can upgrade from 5.10 straight to 6.10 because that skips a release (6.06)

---

### Post by mdknaebel on 2007-03-09
> **halitech said:**
> open a terminal and do

```

gksu "update-manager -c -d"

```
thanks for your reply

after typing that code into terminal, i get a window that says enter the root password... what is it? My password does not work...

---

### Post by mdknaebel on 2007-03-09
> **mikewhatever said:**
> Right, but I do not think you can upgrade from 5.10 straight to 6.10 because that skips a release (6.06)
can I upgrade to 6.06 then, do you know?

---

### Post by picpak on 2007-03-09
In that case, to change your password try:

```
passwd your-username
```

Obviously, change your-username to your user name.

---

### Post by halitech on 2007-03-09
> **mdknaebel said:**
> thanks for your reply

after typing that code into terminal, i get a window that says enter the root password... what is it? My password does not work...

does the password work to log you into the computer?

---

### Post by mdknaebel on 2007-03-09
> **halitech said:**
> does the password work to log you into the computer?
yeah, i know my password and it does work... it says to enter the root password, is that different?  It gave some keychain thing the first time, but i dont remember what it said. I just typed my password into it...

---

### Post by halitech on 2007-03-09
~slaps my forehead~

forgot Ubuntu doesn't use su, change it to gksudo

sorry

---

### Post by mdknaebel on 2007-03-09
OK... that worked, however that just brings me to the software updater, which says up-to-date.  It also gives me a message about 'A new release of Ubuntu is availiable' and tells me to go to a website for more info.  Once, I was able to download and install the new version directly, while running Ubuntu, but I have since re-installed Ubuntu 5.10 and I want to do it again...

Any Ideas?

---

### Post by halitech on 2007-03-09
when you run the command, do you not get a button that say upgrade in the upper right?

---

### Post by mdknaebel on 2007-03-09
Hmmm.... no, currently I do not have that message. The only thing that shows is a pop-up window that says
"There is a new release of Ubuntu availiable!"
"A new release with the codename 'edgy' is availiable. Please see [http://www.ubuntulinux.org/](http://www.ubuntulinux.org/) for update instructions"

That is strange, the upgrade thing might have been what I clicked on before when I did it...

---

### Post by mdknaebel on 2007-03-09
Is there a way to do it with a CD, while running Ubuntu?

---

### Post by halitech on 2007-03-09
I would almost hazzard a guess that you can't jump versions and you would have to go from 5.10 to 6.06 then to 6.10.

if you edit your sources.list file and replace all of the refs from breezy to dapper, you might be able to upgrade that way, then you can stay there or upgrade to edgy

---

### Post by mdknaebel on 2007-03-09
Ok, thanks... how do i edit the sources.list?

---

### Post by halitech on 2007-03-09
try this

```

gksudo gedit /etc/apt/sources.list

```

---

### Post by mdknaebel on 2007-03-09
hmmm well that is empty... maybe different for 5.10?

Its ok, though, thanks for all your help

I think ill figure this out another day :)

---

### Post by Amenemhet on 2007-03-09
> **halitech said:**
> I would almost hazzard a guess that you can't jump versions and you would have to go from 5.10 to 6.06 then to 6.10.

if you edit your sources.list file and replace all of the refs from breezy to dapper, you might be able to upgrade that way, then you can stay there or upgrade to edgy


You are quite correct. To upgrade from dapper to edgy >
edit the  /etc/apt/sources.list
Change 'dapper' to 'edgy' ... then
#apt-get update
#apt-get dist-upgrade
#apt-get upgrade
#reboot

This shoud do it. To upgrade from earlier versions, replace the version name in /etc/apt/sources.list to the next version and do not skip versions. ie: 5.10 > 6.06 > 6.10

luck

---

### Post by halitech on 2007-03-09
should be the same for all versions, least from what I can find...

---

### Post by mdknaebel on 2007-03-09
When I type that in, nothing comes up in gedit... what do i do???

---

### Post by halitech on 2007-03-09
> **Amenemhet said:**
> You are quite correct. To upgrade from dapper to edgy >
edit the  /etc/apt/sources.list
Change 'dapper' to 'edgy' ... then
#apt-get update
#apt-get dist-upgrade
#apt-get upgrade
#reboot

This shoud do it. To upgrade from earlier versions, replace the version name in /etc/apt/sources.list to the next version and do not skip versions. ie: 5.10 > 6.06 > 6.10

luck

that looks like what I did to go from breezy to dapper so I didn't have to wait to download the cd but been awhile :)

---

### Post by halitech on 2007-03-09
check here

[http://www.psychocats.net/ubuntu/sources]("http://www.psychocats.net/ubuntu/sources")

---

### Post by mdknaebel on 2007-03-09
This is what it says in terminal afer typing that in:

mike@ubuntu:~$ gksudo gedit /etc/apt/sources.list

(gedit:6840): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.


Any Ideas?

---

### Post by halitech on 2007-03-09
I get the same thing but my sources list still opens correctly so no clue on why

---

