---
title: "E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the p"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by twbdan on 2007-10-18
what does this mean? and what do I do about it

---

### Post by nikef on 2007-10-18
Hi
i am getting the same error,lets hope some1 can help us  :confused:

---

### Post by bodhi.zazen on 2007-10-18
What are you playing with ???

```
sudo dpkg --configure -a
```

---

### Post by twbdan on 2007-10-18
The screen saver kicked on and frooze the computer

---

### Post by Butthead on 2007-10-18
Most likely one of the package managers borked. :rolleyes:

Run that as root if you ever want to gain access to it again.

---

### Post by Butthead on 2007-10-18
Oops, my mistake! :oops:

Sorry 'bout that!

---

### Post by suliman on 2007-10-18
Hello,

I received the same message today.  This was a result of trying to update 7.04 to 7.10, after many hours of downloading files the installation began which resulted in multiple "Could not install"  libpam0g,etc...

The update manager eventually disappeared (without reaching the "Cleaning Up" state).  Then running the update manager again produced the message in Title.

I blindly executed the command in a terminal - not sure whether this was a wise move because I really don't know what effect it has had.

Any ideas as to what damage is done by executing the message in Title of thread ?

---

### Post by bodhi.zazen on 2007-10-19
Hopefully that command repairs any damage.

If not you likely have serious problem and will need to post more information ...

---

### Post by Bitbucket on 2007-10-19
This happens when something or someone has interrupted the install/upgrade. Just run the command   as root. You will most likely have to restart the install/upgrade. Just run this command as root(aka sudo)after the aforementioned command;
 ```
sudo apt-get dist-upgrade
```

---

### Post by suliman on 2007-10-19
Thanks for both of your replies.

I executed the command

 sudo apt-get dist-upgrade

and got the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It would seem that all is well (at least that's what I'd like to believe...)

Is there another way of checking whether the update 7.04 --> 7.10 went OK?

---

### Post by Frak on 2007-10-19
> **suliman said:**
> Thanks for both of your replies.

I executed the command

 sudo apt-get dist-upgrade

and got the following

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

It would seem that all is well (at least that's what I'd like to believe...)

Is there another way of checking whether the update 7.04 --> 7.10 went OK?
```
sudo lsb_release -a
```
> 
frak@main:~$ sudo lsb_release -a
[sudo] password for frak:
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
frak@main:~$ 

---

### Post by suliman on 2007-10-19
Well, I obtained the same output after issuing:    sudo lsb_release -a

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy

Thanks Frak.

---

### Post by bodhi.zazen on 2007-10-19
> **Frak said:**
> ```
sudo lsb_release -a
```

Cool command Frak, but, FYI, you do not need sudo (I may be paranoid but why run as root with you do not need to ?)

> bodhi@VirtualUbuntu:~$ lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.10
Release:        7.10
Codename:       gutsy
bodhi@VirtualUbuntu:~$ 

---

### Post by Frak on 2007-10-19
> **bodhi.zazen said:**
> Cool command Frak, but, FYI, you do not need sudo (I may be paranoid but why run as root with you do not need to ?)
Bad habbit ;)

---

### Post by dmgthe2nd on 2007-10-22
What happens if I get this:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

The installation from 7.04 to 7.10 never completed.  The clean up froze too.
What do I do?? Im receiving the title of thread message for many crucial programs installations.
Im a noob so please be specific.
Thanks, D.

---

### Post by bodhi.zazen on 2007-10-23
> **dmgthe2nd said:**
> What happens if I get this:

No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 7.04
Release:        7.04
Codename:       feisty

The installation from 7.04 to 7.10 never completed.  The clean up froze too.
What do I do?? Im receiving the title of thread message for many crucial programs installations.
Im a noob so please be specific.
Thanks, D.

sudo dpkg --configure -a

Then update , I advise you use update manager ...

[https://help.ubuntu.com/community/GutsyUpgrades](https://help.ubuntu.com/community/GutsyUpgrades)

---

