---
title: "How do I install ubuntu-restricted-extras without an internet connection?"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by saurabhgupta on 2008-03-24
hi when i try to install ubuntu restricted extra thru terminal ,i face the following
problem:
[COLOR="Red"]saurabh@saurabh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for saurabh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras[/COLOR]

what shall i do now :(

---

### Post by DaV|d on 2008-03-24
Check that you have the multiverse repository enabled.
In **Synaptic** go to **Settings > Repositories ** and tick "Software restricted by copyright or legal issues (multiverse)" click Close and reload.

---

### Post by AndyCooll on 2008-03-24
> **DaV|d said:**
> Check that you have the multiverse repository enabled.
In **Synaptic** go to **Settings > Repositories ** and tick "Software restricted by copyright or legal issues (multiverse)" click Close and reload.

Or go to System > Administration > Software Sources
and place a tick against all the "Downloadable from the Internet" sources on the Ubuntu Software tab.

:cool:

---

### Post by saurabhgupta on 2008-04-14
Hi Guys,
i am extremely amateur to ubuntu. i have dual boot ie. XP and Ubuntu 7.10.
I have internet on XP but not on Ubuntu. In order to install net on ubuntu i have to take care of the .exe (setup) file which doesn't work on ubuntu.
And your above mentioned reply (Settings->Repositories) and then reloading requires the Internet which i dont have on ubuntu :(
Please tell me how do i rectify this problem?
Thanx a lot in advance.

---

### Post by saurabhgupta on 2008-04-14
ERROR

saurabh@saurabh-laptop:~$ sudo apt-get install ubuntu-restricted-extras
[sudo] password for saurabh:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package ubuntu-restricted-extras


I have a dual boot ie: XP and Ubuntu. I have the internet on XP but not ubuntu.
this is bcoz i can't install the setup file (.exe) :(
some solution would be highly appreciated.
thanx in advance...

---

### Post by hyper_ch on 2008-04-14
(1) are you using ubuntu or kubuntu or xubuntu?

(2) did you enable the additional repositories (universe/multiverse)?

(3) and if you did (2), did you then update the packages?

---

### Post by Tatty on 2008-04-14
You need to have an internet connection to install things from the repositories, so we need to fix that first.

.exe files will not run in linux.  Wine can run *some* windows apps, but it will not allow you to use windows drivers in linux.

How are you connecting to the internet, is this a wireless connection?  Have a look in System->Administration->Restricted Extras to see if there are any drivers available for your card

---

### Post by kesman on 2008-04-14
He said there's no internet connection in ubuntu.

For OP, do you have a router that is supposed to give your machine an IP-address, or did you manually enter them in windows? If so, you could check the settings in windows and copy them to ubuntu. No setup -files are required to get internet connection to work...

---

### Post by DaV|d on 2008-04-14
> **saurabhgupta said:**
> In order to install net on ubuntu i have to take care of the .exe (setup) file which doesn't work on ubuntu.

I didn't understand what you mean by that :( AFAIK no setup files are needed to connect..

Setting up an internet connection depends on how you are connected. Do you have a dial-up connection, an ADSL connection, cable internet, or what?

---

### Post by saurabhgupta on 2008-04-14
well, i have an  external data modem and for that i have to install 
the set up (exe file) which i did in case of XP.
My question is how do i go about from here to install the setup  for internet in case of  Ubuntu.

---

### Post by saurabhgupta on 2008-04-14
Hello,
I have an internet connection (in XP)where i didn't added 
the ip address,it was done automatically.
You had asked to get the same settings in case of Ubuntu as it is there for XP;but 
i cldn't understand which settings u r talking about.
I am using UBUNTU 7.10 gutsy gibbon

---

### Post by Martje_001 on 2008-04-14
Does internet work on Ubuntu? Have you tried searching for ubuntu-restricted-extras in Synaptic (System --> Administration --> Synaptic)? Are you sure you didn't made a typo?

---

### Post by DaV|d on 2008-04-14
Could you be more specific please? What make is the modem (usually printed on the modem itself)? Also if you have any other relevant information, post it (ex. a link to the manufacturer's site)

---

### Post by zvacet on 2008-04-14
@ **saurabhgupta**

[this#6]Here #6](http://ubuntuforums.org/showthread.php?t=704585&highlight=pppoe) I hope it will help you.

---

### Post by zvacet on 2008-04-14
@ **saurabhgupta**
[here #6](http://ubuntuforums.org/showthread.php?t=704585&highlight=pppoe)I hope it will help you.

---

