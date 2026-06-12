---
title: "[SOLVED] Will Dist-Upgrade force me OUT of Dapper?"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by ubromtoo on 2007-07-09
when I open update-manager, there is the following message :

    "Cannot install all available updates

The following updates will be skipped:

dpkg-dev
libc6
libc6-dev
libc6-i68  "


      I've read in various threads that the solution might be to :

   sudo apt-get update && sudo apt-get dist-upgrade


       but does the " dist-upgrade" mean that I'd be changing to Edgy ?

   don't want Edgy , but on the other hand I don't want to miss any updates, 

if they are important.  Help a dumb ol' newbie ):P:-k

---

### Post by zero244 on 2007-07-09
You will still have Dapper, it might update your kernel or some system files etc.
To do a full upgrade to the latest or next version you have to click on the Upgrade Button at the top.
Which may or may not work well.

---

### Post by into_311 on 2007-07-09
Correct me if I'm wrong somebody, but I believe you would first have to change around all your /etc/apt/sources.lst entries to say Edgy instead of dapper in order to upgrade the distro to a newer release.

Therefore 
```

sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```

should:
1) update your list of packages to the most recent updates
2) upgrade should upgrade any packages that have newer releases due to bugfixes, security reasons, etc.
3) should upgrade to any  most system /kernel release available

That is my understanding of this..

---

### Post by ubromtoo on 2007-07-10
When I ran " sudo apt-get dist-upgrade " in the terminal, here's what happened :


               2 upgraded, 1 newly installed, 19 to remove and 1 not upgraded.
Need to get 0B/7435kB of archives.
After unpacking 35.0MB disk space will be freed.
Do you want to continue [Y/n]? y
Media Change: Please insert the disc labelled
 ‘Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)’
in the drive ‘/cdrom/’ and press enter


            so I just closed the terminal.  Don't want no Edgy !!  :(

  Next I'll check to see if anything has changed ; if so, will post .

---

### Post by bobplano on 2007-07-10
check you software sources. it sounds like somehow the edgy cd software source got added. just remove that and then do those commands again.

---

### Post by ubromtoo on 2007-07-10
Bobplano :

    How do I do what you've suggested ?

              Thank you ! :)

---

### Post by 3rdalbum on 2007-07-11
> **ubromtoo said:**
> Bobplano :

    How do I do what you've suggested ?

              Thank you ! :)

System > Administration > Software Properties

In the first tab, you will have "CD disk with Ubuntu 6.10" or something similar in the list box. Uncheck it, click Close, and then the Reload button when asked if you want to reload the package list.

---

### Post by ubromtoo on 2007-07-11
bobplano & 3rdalbum :

     When I did as you suggested and then clicked on "reload" , got this :

The following problems were found on your system:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/
universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_
universe_binary-i386_Packages)


    ....and when I checked, sure enough two of the "channels" were identical, so deleted 
one of them, and again hit "reload".

     After that, ran the command " sudo apt-get dist-upgrade " and the upgrade seems to

have gone very smoothly ! 

      My sincere thanks to all for the help !!   :guitar:

---

### Post by southernman on 2007-07-12
> **ubromtoo said:**
> bobplano & 3rdalbum :

     When I did as you suggested and then clicked on "reload" , got this :

The following problems were found on your system:

W: Duplicate sources.list entry [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/
universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_dapper-security_
universe_binary-i386_Packages)


    ....and when I checked, sure enough two of the "channels" were identical, so deleted 
one of them, and again hit "reload".

     After that, ran the command " sudo apt-get dist-upgrade " and the upgrade seems to

have gone very smoothly ! 

      My sincere thanks to all for the help !!   :guitar:Congrats... would you mind updating your original post so it reflects as being solved. Helps others who may have this problem find a solution, and keeps potential volunteer help(ers) from wasting time to read through your thread *cough*.

Thanks.

---

### Post by ubromtoo on 2007-07-12
Southernman :

         Please accept my apologies  :oops:   -didn't know about that ; now I'll fix 

one or two other threads to show they've been solved too.  My bad ...

---

### Post by southernman on 2007-07-12
> **ubromtoo said:**
> Southernman :

         Please accept my apologies  :oops:   -didn't know about that ; now I'll fix 

one or two other threads to show they've been solved too.  My bad ...It's ok ubromtoo! Thanks for helping out.

:)

---

