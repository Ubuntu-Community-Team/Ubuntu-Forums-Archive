---
title: "Upgrading help, 5.10"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by Goemon4 on 2007-08-02
Hello, i just had to re-install ubuntu from a disc today, but the newest disc i had was for 5.10. So i just said, ill upgrade it to the latest, but when i went to i got tons of errors, like 

> W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)


so i went nad edited my repo's to remove the CD upgrade, and just have the Updates, Security Updates, and Breezy BAdger repos. And i get this error 

> [http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/universe/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/main/binary-i386/Packages.gz:) 404 Not Found
[http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:](http://security.ubuntu.com/ubuntu/dists/breezy-security/restricted/binary-i386/Packages.gz:) 404 Not Found
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]
[http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:](http://us.archive.ubuntu.com/ubuntu/dists/breezy/restricted/binary-i386/Packages.gz:) 404 Not Found [IP: 91.189.89.8 80]


and then this one
> 
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)

Im pretty positive its because over time the url's for the updates have changed, or something. Im stumped on what to do, but i need to upgrade, and would appreciate some help. I tried searching and didnt find anything to helpful btw.

My system is an x86 Intell machine, with 5.10 of course

Thanks for any help
-goemon4

---

### Post by Billy_McBong on 2007-08-02
[COLOR="Blue"]i would just do a fresh install of feisty because you would have to like 3 upgrades to get to feisty(cant skip versions have to do breezy>dapper>edgy>feisty)[/COLOR]

---

### Post by Goemon4 on 2007-08-02
yeah, i know, but i dont have any blank discs :(  ill go search for some then, if that would be the easiest solution

---

### Post by Seisen on 2007-08-02
Here are the links to upgrade
Upgrading from Breezy to Dapper
[http://daniel.holba.ch/blog/?p=14]("http://daniel.holba.ch/blog/?p=14")
Dapper to Edgy
[http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html]("http://www.debianadmin.com/upgrade-ubuntu-dapper-to-ubuntu-edgy-eft.html")
Edgy to Feisty
[http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/](http://www.howtogeek.com/howto/ubuntu/upgrade-ubuntu-edgy-to-feisty/)

Just make sure after upgrading to each distribution you reboot and make sure everything is up to date  and working before installing the next distribution.

---

### Post by Goemon4 on 2007-08-02
thanks, ill keep those links bookmarked,  but every time i try to update i get an error. I wont even dl the packages needed. It happens when i try the update manager, or in the terminal. I think my sources.list may be out of date tho, the more i look at things. any ideas?

btw, yeah i have no blank cd's, so i cant just go straight to Feisty :(

---

### Post by Raineer on 2007-08-02
The issue definitely lies in your sources.list, i would look over those links or try to find more current ones with repos (mind you, those respositories are old by now).

Personally I would just reinstall if you can find the discs, as you'll be waiting quite a while.  The upgrade path *will* work though, just need to find the right sources.

---

### Post by wpshooter on 2007-08-02
Download, burn & install the latest released version of Ubuntu (Feisty) from here & forget about upgrading.  You are wasting too much of your valuable time.

[http://www.ubuntu.com/getubuntu](http://www.ubuntu.com/getubuntu)

---

### Post by qpieus on 2007-08-02
As you already found out, the various standard ways to upgrade from 5.10 will not work. This is because 5.10 is no longer supported by canonical. That's why you keep getting the "404 not found" errors - the files are no longer present on the canonical servers. 

I had the same issue about a month ago. I googled "breezy repository" and came up with this:

[http://bea.cabarel.com/modules/PunBB/viewtopic.php?pid=1734](http://bea.cabarel.com/modules/PunBB/viewtopic.php?pid=1734)

The link discusses mirrors of the old canonical breezy repos. I tried to use these to upgrade a breezy server. I replaced all ubuntu http references with one of the mirror addresses from that link. The upgrade looked OK for a bit, but then crapped out because of some dependency problem. I ended up doing a fresh install.

So, it didn't work for me, but it's worth a shot - maybe it'll work for you. If this doesn't work, then your only choice is a fresh install.

---

### Post by Goemon4 on 2007-08-02
@ Raineer - if thats it, then would it be ok to just get a 6.06 sources list and then use synaptic to upgrade ererything? 

@ wpshooter - if i could get a blank cd, that would be the first thing i would of done (if only i could find one :(  )


@ qpieus - ill give that a shot to, if what ima about to try dosnt work, ty for the help everyone!

---

### Post by Goemon4 on 2007-08-02
ok, got it, i just went here

[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

made a sources.list for 6.06 and went to synaptic and upgraded things ,im now on 6.06! thanks for all the help guys

---

