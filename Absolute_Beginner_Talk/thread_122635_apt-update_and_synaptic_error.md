---
title: "apt-update and synaptic error"
date: 2006-01-28
forum: Absolute Beginner Talk
---

### Post by ubunlilluz on 2006-01-28
hi,
i'm trying to install wine, but if i do the update:
 
lillux@lilluxsestum:~$ sudo apt-get update
Password:
Get:1 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release.gpg [189B]
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release.gpg
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy Release
Ign [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Release
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/main Packages
Ign [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/restricted Packages
Hit [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://wine.sourceforge.net](http://wine.sourceforge.net) binary/ Packages
Get:2 [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages [3028kB]
99% [2 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages
  Il sottoprocesso gzip ha ritornato un codice d'errore (1)
Scaricato 2B in 4s (0B/s)
Impossibile ottenere [http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz](http://it.archive.ubuntu.com/ubuntu/dists/breezy/universe/binary-i386/Packages.gz)  Il sottoprocesso gzip ha ritornato un codice d'errore (1)
Lettura della lista dei pacchetti in corso... Fatto
W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: È consigliabile eseguire apt-get update per correggere questi problemi
E: Impossibile scaricare alcune file di indice, essi verranno ignorati, oppure si useranno quelli precedenti.
(i'm sorry the message are in Italian, my now i've not free time to translate)

other message, by synaptic:

W: Impossibile controllare la lista dei pacchetti sorgente [http://it.archive.ubuntu.com](http://it.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/it.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)

what's happening?
thank

---

### Post by bscbrit on 2006-01-28
Not being an Italian language speaker, my best guess is that it is a problem with the format of a file provided by your repo.  If I am correct, then there is not much that you can do at your end to fix the problem other than perhaps let them know (the repo managers) so that they can fix it.

---

### Post by ubunlilluz on 2006-02-01
my sources.list is:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://it.archive.ubuntu.com/ubuntu](http://it.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

thanks

---

### Post by bscbrit on 2006-02-01
>  deb [http://it.archive.ubuntu.com/ubuntu/](http://it.archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse 

If that is the same sources list that you had when you first saw the error then the repos above was not using GPG authentication or there was a file missing from the repos.  Have you tried again recently?

---

### Post by ubunlilluz on 2006-02-01
[QUOTE=bscbrit]If that is the same sources list that you had when you first saw the error then the repos above was not using GPG authentication or there was a file missing from the repos.  Have you tried again recently?[/QUOTE]

i've updated many times, and each time it downloads files
like something were missing, and then it works. The problem
is that the dayt after, the story is the same and that error message appears again.

---

### Post by ubunlilluz on 2006-02-01
now i'm at home.
i've connected and checked the synaptic. The message appear again and i've to donload all information again. It seems that it isn't able to store information: i've to download each time i switch on the pc.
Help

---

### Post by bscbrit on 2006-02-02
I'd be very tempted to uninstall and reinstall synaptic to see if that helps.  Do NOT uninstall apt, otherwise I cannot see how you can update again. :D   However, I will be honest and say that I really cannot understand what is happening in this particular instance.  It might be a permissions thing but I'm not sure yet what needs to be checked.

---

### Post by jegerjensen on 2006-02-03
[QUOTE=ubunlilluz]
99% [2 Packages gzip 0]
gzip: stdin: not in gzip format
[/QUOTE]

I had the same error but it worked when I followed the advice at the end of this thread:
[http://www.ubuntuforums.org/showthread.php?t=114300]("http://www.ubuntuforums.org/showthread.php?t=114300")

---

### Post by carlosqueso on 2006-02-03
The individual country repos are often screwy.  I'd try taking the "it" off of each repo that has it and trying again.

---

