---
title: "Mac PowerPC Ubuntu 12.04 LTS Updates"
date: 2014-03-24
forum: Apple Hardware Users
---

### Post by forumqa on 2014-03-24
Having installed Ubuntu 12.04 LTS for an old Mac PowerPC laptop, I am having problems updating software from the Update Manager.  I have to install latest updates listed by the Update Manager.  The problems happens after I act to Install Updates and Authenticate, Update Manager says:  

[I][B]¨Failed to download package files

Check your Internet connection.

Details

Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb) 404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb) 404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/u/udisks/udisks_1.0.4-5ubuntu2.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/u/udisks/udisks_1.0.4-5ubuntu2.1_powerpc.deb) 404  Not Found¨[/B][/I]


There is Internet connection, so the above is eFUD.

---

### Post by claracc on 2014-03-24
Cetainly, the requested package: firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb is not in the server addressed, so it is normal update manger cannot find it.

For the addresses given this is firefox answer: [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb)

You will have to look fot this package in other server.

---

### Post by frank18 on 2014-03-24
> **forumqa said:**
> Having installed Ubuntu 12.04 LTS for an old Mac PowerPC laptop, I am having problems updating software from the Update Manager.  I have to install latest updates listed by the Update Manager.  The problems happens after I act to Install Updates and Authenticate, Update Manager says:  

[I][B]¨Failed to download package files

Check your Internet connection.

Details

Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb) 404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb) 404  Not Found
Failed to fetch [http://ports.ubuntu.com/ubuntu-ports/pool/main/u/udisks/udisks_1.0.4-5ubuntu2.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/u/udisks/udisks_1.0.4-5ubuntu2.1_powerpc.deb) 404  Not Found¨[/B][/I]


There is Internet connection, so the above is eFUD.


What PPC you have is this Intel or G5?

---

### Post by forumqa on 2014-03-24
> **frank18 said:**
> What PPC you have is this Intel or G5?

I am in England ):P and it is a G3 ):P which were IBM ):P not Intel.

---

### Post by forumqa on 2014-03-27
> **claracc said:**
> Cetainly, the requested package: firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb is not in the server addressed, so it is normal update manger cannot find it.

For the addresses given this is firefox answer: [http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb](http://ports.ubuntu.com/ubuntu-ports/pool/main/f/firefox/firefox-globalmenu_25.0.1+build1-0ubuntu0.12.04.1_powerpc.deb)

You will have to look fot this package in other server.

I would be grateful if someone could resolve my problem, I am not a techie.  Could someone from Ubuntu include the necessary on the server or else could someone please tell me specifically actions I need to perform or suggest another forum?  I don´t have much time and if I fail to get a solution, I would have to change from this operating system,

---

### Post by forumqa on 2014-03-28
[https://answers.launchpad.net/ubuntu/+question/246190](https://answers.launchpad.net/ubuntu/+question/246190)

---

### Post by forumqa on 2014-03-28
[https://bugs.launchpad.net/ubuntu/+bug/1298943](https://bugs.launchpad.net/ubuntu/+bug/1298943)

Also I went to files listed on above server and for the first one I downloaded a newer version from the list and installed it manually in guest mode, though the next two on the list - their equivalent new version from the list - produced errors.  I then went to original Ubuntu 12.04 LTS download page to download it again in case it had changed - I stopped this once I saw that the listing date was not recent.

---

### Post by gifford on 2014-03-28
You might find better support by looking in the Apple Users forum. It is in Ubuntu Specialized support in the Ubuntu Forum.
There are still quite a few Apple ppc users.

---

### Post by forumqa on 2014-03-28
> **gifford said:**
> You might find better support by looking in the Apple Users forum. It is in Ubuntu Specialized support in the Ubuntu Forum.
There are still quite a few Apple ppc users.

[FONT=arial][SIZE=2]Cheers.  The problem is not there anymore with the Update Manager now because the updates were showing 600+ outstanding became 300+ and then nil.

I don´t understand what happened.  Was it the problematic downloaded Midori browser that caused problem not to be flagged or something else?  It is quite baffling.  

The new problem is that Ubuntu Software Centre is not allowing certain software to be downloaded because the download switch is not there, for example, Wine Windows Program Loader.  Also if I manually downloaded the program [https://www.winehq.org/download/ubuntu](https://www.winehq.org/download/ubuntu) - I as a non-techie cannot understand what Application I am supposed to Choose at the Launch Application prompt? Nor is there a wine 1.6 using Alternative Command Line Instructions for Installing Wine[/SIZE][/FONT] method.  

Similarly here [https://apps.ubuntu.com/cat/applications/precise/myunity/](https://apps.ubuntu.com/cat/applications/precise/myunity/) - [FONT=arial][SIZE=2] I as a non-techie cannot understand what Application I am supposed to Choose at the Launch Application prompt?

There is no software showing which I am supposed to Choose at the Launch Application prompt to install Wine Windows Program Loader or MyUnity?
[/SIZE][/FONT]

---

### Post by gifford on 2014-03-28
I think the problems you are experiencing are related to using ppc. I do not believe there is a version of wine for Ubuntu ppc Linux. You can search in the forum for apple users and maybe they have found a solution. Unfortunately, the G3 is rather long in the tooth so you might find that many applications are not able to be installed.
As I recall, the only available browser to install was firefox for ppc Ubuntu, but that was several years ago and may have changed.
Look to the apple user forum for help as they really are the experts.

---

### Post by frank18 on 2014-03-29
> **forumqa said:**
> I am in England ):P and it is a G3 ):P which were IBM ):P not Intel.
  


Well i have a G5 and i could never install Ubuntu 12.04 as far as i could go was to the Black terminal where it asked to log in! i could never get the desktop,  i wonder how could you do it in a G3!
the only Distro i could install on it was Debian Wheezy 7.1 that runs great.

---

### Post by forumqa on 2014-03-31
> **frank18 said:**
> Well i have a G5 and i could never install Ubuntu 12.04 as far as i could go was to the Black terminal where it asked to log in! i could never get the desktop,  i wonder how could you do it in a G3!
the only Distro i could install on it was Debian Wheezy 7.1 that runs great.

I had to upgrade the RAM because Ubuntu 12.04 LTS had higher specifications.  A YouTube video showed that it was quite easy to upgrade the RAM.

---

### Post by frank18 on 2014-03-31
> **forumqa said:**
> I had to upgrade the RAM because Ubuntu 12.04 LTS had higher specifications.  A YouTube video showed that it was quite easy to upgrade the RAM.



Hi forrumga:how much ram do you have?.
I have 1Gb ram.
Please tell me which Iso did you use!. 
 Tried to use A mini ISO.  
Also when you installed Ubuntu12.04 did you get the 64bit or 32bit lso?.
Did you get a desktop right out of the box?.
Now there is an ubuntu beta2 ppc available, check link bellow.
I know on a regular Computer Ubuntu14.04beta1 works great,better then 12.04lts, now 14.04 ppc  should  be better on aple ppc then  12.04 ,if you happen to try it please report back how it went!,i would try  it but i had bad luck with 12.04 so i installed Debian wheezy 7.1 and it gave me a litle work to set up sound,wireless,and to get video working on UTUBE still not very good but that's what i could get since ppc is not supported by flash player.

Also can you please post the instructions you followed to install Ubuntu, Thanks.    



[http://cdimage.ubuntu.com/releases/14.04/beta-2/](http://cdimage.ubuntu.com/releases/14.04/beta-2/)

---

### Post by bapoumba on 2014-03-31
Moved to Apple Users.

---

### Post by forumqa on 2014-03-31
> **frank18 said:**
> Hi forrumga:how much ram do you have?.
I have 1Gb ram.
Please tell me which Iso did you use!. 
 Tried to use A mini ISO.  
Also when you installed Ubuntu12.04 did you get the 64bit or 32bit lso?.
Did you get a desktop right out of the box?.
Now there is an ubuntu beta2 ppc available, check link bellow.
I know on a regular Computer Ubuntu14.04beta1 works great,better then 12.04lts, now 14.04 ppc  should  be better on aple ppc then  12.04 ,if you happen to try it please report back how it went!,i would try  it but i had bad luck with 12.04 so i installed Debian wheezy 7.1 and it gave me a litle work to set up sound,wireless,and to get video working on UTUBE still not very good but that's what i could get since ppc is not supported by flash player.

Also can you please post the instructions you followed to install Ubuntu, Thanks.    



[http://cdimage.ubuntu.com/releases/14.04/beta-2/](http://cdimage.ubuntu.com/releases/14.04/beta-2/)

512mb RAM

I am not using Ubuntu 12.04 LTS and have gone to using Debian because there was MyUnity app problem on the ppc, Unity without MyUnity app is not user friendly for customisation.  I thought about using Lubuntu 13.10 because I was told it does not have Unity, though the problem was I could not put the image on a CD as the file size was bigger than the CD specification.  Probably I used this when I was using Ubuntu:

"Desktop CD
 The desktop cd allows you to try Ubuntu without changing your  computer at all, and at your option to install it permanently later.   You will need at least 384MiB of RAM to install from this cd.
  There is one image available:
[Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso")  For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines."

32bit

D/T

---

### Post by frank18 on 2014-03-31
> **forumqa said:**
> 512mb RAM

I am not using Ubuntu 12.04 LTS and have gone to using Debian because there was MyUnity app problem on the ppc, Unity without MyUnity app is not user friendly for customisation.  I thought about using Lubuntu 13.10 because I was told it does not have Unity, though the problem was I could not put the image on a CD as the file size was bigger than the CD specification.  Probably I used this when I was using Ubuntu:

"Desktop CD
 The desktop cd allows you to try Ubuntu without changing your  computer at all, and at your option to install it permanently later.   You will need at least 384MiB of RAM to install from this cd.
  There is one image available:
[Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso")  For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines."

32bit

D/T

Thanks But this was the Ubuntu PPC Iso  that i tried to install that failed before i went with Debian Wheezy 7.1

[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

---

### Post by frank18 on 2014-03-31
> **forumqa said:**
> 512mb RAM

I am not using Ubuntu 12.04 LTS and have gone to using Debian because there was MyUnity app problem on the ppc, Unity without MyUnity app is not user friendly for customisation.  I thought about using Lubuntu 13.10 because I was told it does not have Unity, though the problem was I could not put the image on a CD as the file size was bigger than the CD specification.  Probably I used this when I was using Ubuntu:

"Desktop CD
 The desktop cd allows you to try Ubuntu without changing your  computer at all, and at your option to install it permanently later.   You will need at least 384MiB of RAM to install from this cd.
  There is one image available:
[Mac (PowerPC) and IBM-PPC (POWER5) desktop CD]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso")  For Apple Macintosh G3, G4, and G5 computers, including iBooks and PowerBooks as well as IBM OpenPower machines."

32bit

D/T

Thanks But this was the Ubuntu PPC Iso  that i tried to install that failed before i went with Debian Wheezy 7.1

[http://cdimage.ubuntu.com/releases/12.04/release/](http://cdimage.ubuntu.com/releases/12.04/release/)

This was the only  way i could install Debian wheezy, also the same way i tried install Ubuntu 12.04,Because i couldn't install it from the Aple OPS since this Aple PPC was given to me and i had no Password to get Administer privileges and 
could not install software on it so my only solution was the Mini Iso and throught the Debian Server,as you see in the link this instructions were for a Regular PC but you can disregard the 2 first pictures and the rest is the same execpt there was an option for the desktop, and on Ubuntu 12.04PPC it was the same set of instructions expect  there was no Desktop to chose just like this in link

 [http://dev-random.net/debian-linux-server-wheezy-7-1-installation/](http://dev-random.net/debian-linux-server-wheezy-7-1-installation/)

---

