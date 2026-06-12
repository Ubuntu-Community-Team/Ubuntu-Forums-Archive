---
title: "Cant download repository Error"
date: 2014-08-31
forum: Any Other OS
---

### Post by firas2 on 2014-08-31
Please look here 

[http://u.cubeupload.com/elfc/201408312212441920x1.png](http://u.cubeupload.com/elfc/201408312212441920x1.png)

this is not the first time ,, why do i keep geting this ??

thank u

BTW  i am at this site   trying to download Terminology    look here  all the way down

[http://www.webupd8.org/2013/04/terminology-more-than-terminal-emulator.html](http://www.webupd8.org/2013/04/terminology-more-than-terminal-emulator.html)

---

### Post by Bashing-om on 2014-08-31
firas2; Hello !

What distribution and release are you running ?
We often see these errors due to 3rd party PPAs enabled in the sources and the authors of said software have not caught up to 14.04 . This then causes a failure to communicate with the requested server.
There are a number of ways to trouble shoot this situation. Perhaps the easier for the casual user is to disable ALL 3rd party sources in ubuntu Software Center;
See what results then when the system is updated/upgraded, then ->
a) investigate the PPA and see if 14.04 has support;
b) one at a time turn a PPA back on, update/upgrade and see what results.

Heed the advisory for these 3rd party softwares
user be ware -> installing untrusted software.

[INDENT][INDENT]not a big deal, just
[INDENT][INDENT][INDENT][INDENT]something that has gotta be done
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by coffeecat on 2014-08-31
*Thread moved to **Other Operating Systems and Projects**.*

@firas2, will you please stop posting Linux Mint questions in the Ubuntu sections. Which bit of this is not clear?

> Ubuntu Official Flavours Support
Choose the most appropriate category for your questions regarding Ubuntu, Kubuntu, Xubuntu, Edubuntu, Lubuntu, UbuntuGnome, Ubuntu Studio, and Mythbuntu.

---

### Post by firas2 on 2014-09-01
> **firas2 said:**
> Please look here 

[http://u.cubeupload.com/elfc/201408312212441920x1.png](http://u.cubeupload.com/elfc/201408312212441920x1.png)

this is not the first time ,, why do i keep geting this ??

thank u

BTW  i am at this site   trying to download Terminology    look here  all the way down

[http://www.webupd8.org/2013/04/terminology-more-than-terminal-emulator.html](http://www.webupd8.org/2013/04/terminology-more-than-terminal-emulator.html)

> **Bashing-om said:**
> firas2; Hello !

What distribution and release are you running ?
We often see these errors due to 3rd party PPAs enabled in the sources and the authors of said software have not caught up to 14.04 . This then causes a failure to communicate with the requested server.
There are a number of ways to trouble shoot this situation. Perhaps the easier for the casual user is to disable ALL 3rd party sources in ubuntu Software Center;
See what results then when the system is updated/upgraded, then ->
a) investigate the PPA and see if 14.04 has support;
b) one at a time turn a PPA back on, update/upgrade and see what results.

Heed the advisory for these 3rd party softwares
user be ware -> installing untrusted software.[INDENT][INDENT]not a big deal, just[INDENT][INDENT][INDENT][INDENT]something that has gotta be done
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]
[/INDENT]


Yes I did Disable all and it worked , So now I will go back and enable them one by one and see witch one .
But this is always the case when installing new 3d party  , it looks Like it wont except  any third party PPA 

> **coffeecat said:**
> *Thread moved to **Other Operating Systems and Projects**.*

@firas2, will you please stop posting Linux Mint questions in the Ubuntu sections. Which bit of this is not clear?

Sorry  I dont know where is the Linux topics here in Ubuntu forums ??  I did try to post in other places  But I think U also Moved them 

can u please tell me witch is the right Place ??  would it be this  

Ubuntu,Linux and os chat ??  or this  where U have moved it   to  ***Other Operating Systems and Projects**. ???*

Thank u

---

### Post by ThatBum on 2014-09-01
Linux mint has [its own forum]("http://forums.linuxmint.com/").

---

### Post by Bashing-om on 2014-09-01
firas2; Well, 

In this case:
> **firas2 said:**
> Yes I did Disable all and it worked , So now I will go back and enable them one by one and see witch one .
But this is always the case when installing new 3d party  , it looks Like it wont except  any third party PPA 

Make sure universe, multiverse and as well 'partners' repositories are enabled.
3rd party software is sort of a grey area as ubuntu has no direct control over others' coding. Maybe the authors of the software have not caught up the point that there is support in the release you are running ??? Do not mix release software repositories ! -> leads to Dependency Hell !
All you can do is check and see what support is available from the author(s) of the subject software, before you are able to update/install.

[INDENT][INDENT][INDENT]hope this helps
[/INDENT][/INDENT][/INDENT]

---

### Post by firas2 on 2014-09-01
> **ThatBum said:**
> Linux mint has [its own forum]("http://forums.linuxmint.com/").



Yes I know this   But I also want to be  Part of the  community  

POOF =  used to convey the suddenness with which someone or something disappears.    lol  

):P

---

### Post by QIII on 2014-09-01
> **firas2 said:**
> 

can u please tell me witch is the right Place ??  would it be this  

Ubuntu,Linux and os chat ??  or this  where U have moved it   to  ***Other Operating Systems and Projects**. ???*

Thank u


I think it was very clear:

> *Thread moved to **Other Operating Systems and Projects**.*We are happy to have users of other distros ask questions here, but this is the sub forum where those questions belong.

Cheers!

---

### Post by vasa1 on 2014-09-01
> **ThatBum said:**
> Linux mint has [its own forum]("http://forums.linuxmint.com/").
OP is aware of that and has posted there as well about some conky stuff (at least).

All people are asking is that Linux Mint questions be asked in the appropriate subforum and tagged accordingly.

---

### Post by firas2 on 2014-09-01
@ Qlll  and Vasa1

Will do  Please for give a newbi 

To be more clear   I would Love to ask this Question   Because i would like to know   Is Linux part of UBUNTU  or UBUNTU is a Part of Linux ???  

Or what is  going on here LOL ???

many thanks

---

### Post by ThatBum on 2014-09-01
Ubuntu is a distribution of Linux. This means it's an OS built around the Linux kernel, the core of the OS. There are many, many distributions, and they all are designed to fit a particular purpose or preference for the user. Linux Mint is a derivative of Ubuntu, which in itself is a derivative of Debian.

Anyway, those errors seem to all be 404. Maybe they're having issues on their end, or your Internet connection is acting up? Try again later.

As previously stated, be aware of what you're adding to your repo list and make sure it's from a reputable source. Also, don't cross-pollinate repos from different distributions in an attempt to get more or newer software, it leads to Bad Things.

---

