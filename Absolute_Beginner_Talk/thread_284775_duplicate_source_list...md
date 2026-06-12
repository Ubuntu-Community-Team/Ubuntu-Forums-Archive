---
title: "duplicate source list.."
date: 2006-10-26
forum: Absolute Beginner Talk
---

### Post by STREETURCHINE on 2006-10-26
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)
W: Duplicate sources.list entry [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages)
 could anybody tell me how to fix this,thank you](*,)

---

### Post by Kateikyoushi on 2006-10-26
Copy this to the terminal.

```
gksudo gedit /etc/apt/sources.list
```

Then post the content of the file here.

---

### Post by Titus A Duxass on 2006-10-26
Open up your sources.list file, identify the duplicated entries.
You can either delete the lines or hash (#) them out.

Do sudo nano /etc/apt/sources.list (note: you can replace nano with your preferred editor).

---

### Post by STREETURCHINE on 2006-10-26
deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
##N.B. software from this repository may not have been tested as
##extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

 that is my source list now i just need to know which lines to comment
 thanks:)

---

### Post by Titus A Duxass on 2006-10-26
Here's one:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Third one down under #AUTOMATIX REPOS START and is repeated on the bottom line.

It looks like you have used Easyubuntu and Automatix, that is not going to give you a tidy sources.list unless you tell one or the other to overwrite the sources.list. I know Automatix does this (or did) but am not familiar with Easyubuntu.

---

### Post by STREETURCHINE on 2006-10-26
> **Titus A Duxass said:**
> Here's one:

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

Third one down under #AUTOMATIX REPOS START and is repeated on the bottom line.

It looks like you have used Easyubuntu and Automatix, that is not going to give you a tidy sources.list unless you tell one or the other to overwrite the sources.list. I know Automatix does this (or did) but am not familiar with Easyubuntu.
thanks commented that one ,they are quite hard to find

---

### Post by STREETURCHINE on 2006-10-26
i loaded easyubuntu first but could not resolve the missing key problem,so i loaded automatix and i am trying to get rid of easy ubuntu once i work out how.

---

### Post by Esben Kramer on 2006-10-26
You could do a fast fix, by simply deleting ALL the Automatix repositories. When you then run Automatix, just make it go back to your old sources.list file everytime you exit it. That way you don't have the problem.

The best would be to just delete the dublicates though, so that your update-manager will also find updates to the programs installed by automatix. I hope this makes sense to you? If not, just ask.

---

### Post by STREETURCHINE on 2006-10-26
> **Esben Kramer said:**
> You could do a fast fix, by simply deleting ALL the Automatix repositories. When you then run Automatix, just make it go back to your old sources.list file everytime you exit it. That way you don't have the problem.

The best would be to just delete the dublicates though, so that your update-manager will also find updates to the programs installed by automatix. I hope this makes sense to you? If not, just ask.

i have deleted one duplicate but i just cant see the outhers to delete them,being a newbie they all look differant but i just dont know,but thanks i will keep looking and hopefully i can find them:D

---

### Post by TitusDalwards on 2006-10-26
i confused it, is it necessary to delete duplicate repos because these are only warnings not errors.

---

### Post by STREETURCHINE on 2006-10-26
:) i dont think they are dangerous i just dont like annoying little popup windows telling me i have a problem.so i will keep digging till i get it fixed:D

---

### Post by arnieboy on 2006-10-26
> **STREETURCHINE said:**
> deb [http://packages.freecontrib.org/plf/](http://packages.freecontrib.org/plf/) dapper free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

deb [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://download.videolan.org/pub/videolan/debian](http://download.videolan.org/pub/videolan/debian) sarge main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
## Uncomment the following two lines to add software from the 'backports'
##N.B. software from this repository may not have been tested as
##extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
#AUTOMATIX REPOS END
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

 that is my source list now i just need to know which lines to comment
 thanks:)

The duplication of sources.list happened because of a bug in version 1.1-1.1 of AX2 which was trying out a totally new procedure in handling sources.list, in which AX2 would scan for existing repositories and directories, retain the user's repos and add only the necessary (official) ones to make it complete. This bug has been fixed in both dapper and edgy i386 in version 1.1.1-2.

---

### Post by STREETURCHINE on 2006-10-26
can i update automatix ,or do i uninstall and reinstall the new version :-k

---

### Post by arnieboy on 2006-10-26
> **STREETURCHINE said:**
> can i update automatix ,or do i uninstall and reinstall the new version :-k

```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by STREETURCHINE on 2006-10-26
thanks heaps for the help ,it is much appreciated :-D

---

