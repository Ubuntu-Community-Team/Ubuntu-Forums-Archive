---
title: "ubuntusetup.sh"
date: 2005-06-16
forum: Absolute Beginner Talk
---

### Post by Scheltes on 2005-06-16
Hello,

After downloading "ubuntusetup.sh" and using the command "sudo sh ubuntusetup.sh" the installation using this script ends with an error. Although the output is in Dutch the last sentence is in English. The error reads as follows:

ERROR # 100 : There was an error in apt-get update.

Is anyone familiar with that and if so what is the solution to overcome this error?

Thanks in advance.

---

### Post by davahmet on 2005-06-16
I am assuming this is a fresh installation.  Check /etc/apt/sources.list and verify that the installation CD is not identified as your primary repository.  Usually a failure for apt-get update is because apt was unable to access the expected update repository.

My aploogies that I cannot remember the exact line your sources file should have.  I am at work at the moment with no access to my Ubuntu system.

Hope this helps.

---

### Post by Scheltes on 2005-06-16
Thanks for your reply. This is indeed a fresh installation. As I don't quite understand what you mean you will find the content of the sources list below. Maybe you can advise me what lines has to be changed:

"deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted universe multiverse

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) stable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) unstable main
deb [ftp://ftp.nerim.net/debian-marillat/](ftp://ftp.nerim.net/debian-marillat/) testing main

#Primary Mirror (5/17/2005) overloaded :)
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-backports main universe multiverse restricted
#deb [http://backports.ubuntuforums.org/backports](http://backports.ubuntuforums.org/backports) hoary-extras main universe multiverse restricted

#backup Mirror - FAST
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted"

I'm looking forward to your next reply and thank in advance.

---

### Post by davahmet on 2005-06-16
Hmmm...actually, your sources.list looks fine.  Can you give more detail on the error you get?  I don't know the solution yet, but we will get this working.  :-k

---

### Post by Scheltes on 2005-06-17
I entered another topic in this same forum regarding an error-message I used to get when starting Synaptic Package Manager. Although I received a reply I decided to try to solve this problem myself. The website of the Unofficial 5.04 Starter Guide ([http://www.ubuntuguide.org/](http://www.ubuntuguide.org/)) gave me the idea to change the contents of the sources.list. So I used the topic "How to add extra repositories?" and copied the complete contents of the sources.list shown to the sources.list on my computer after having removed the original contents and that solved my problem I nmentioned in the other topic. But I haven't tried yet whether this new sources.list would solve my problem mentioned in this topic. Below you will find the contents of my new sources.list:

"## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse"

What do you think of that? Is that good and would this be the trick? Do you think it is good enough to give it a try?

I hope to hear from you soon.

---

### Post by Scheltes on 2005-06-17
I owe you yet more detail on the error I get. After "Geraakt [ftp://ftp2.caliu.info](ftp://ftp2.caliu.info) hoary-extras/restricted Packages" the following output I got:

74,1kB opgehaald in 5s (13,4kB/s)
Ophalen van [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz) MD5Sum komt niet overeen is mislukt
Ophalen van [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz) MD5Sum komt niet overeen is mislukt
Pakketlijsten worden ingelezen... Klaar
W: Kon de status van de bronpakketlijst [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: Kon de status van de bronpakketlijst [ftp://ftp.nerim.net](ftp://ftp.nerim.net) testing/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_testing_main_binary-i386_Packages) niet opvragen - stat (2 Onbekend bestand of map)
W: U kunt misschien 'apt-get update' uitvoeren om deze problemen te verhelpen
E: Ophalen van sommige indexbestanden is mislukt, deze zijn of genegeerd, of er zijn oudere versies van gebruikt.
ERROR # 100 : There was an error in apt-get update.
jan@ubuntu:~/Desktop$"

Unfortunately the output is more or less in the Dutch language but maybe you can figure out what some of it means. Anyway I shall try to translate:
The first 2 sentences say that on collecting binary packages MD5Sum does not correspond so failed.
Packagelist is being read .....ready
W: could not claim or asks for the status of the sourcepackagelist.......- staty (2 unknown file or folder)
W: Perhaps you might try to perform 'apt-get update' to solve these problems
E: collecting some of the indexfiles failed, these may have been ignored or older version has been used.
ERROR # 100 : There was an error in apt-get update.

I hope this is clear to you. What can you make of it?

---

### Post by davahmet on 2005-06-17
That sources.list looks pretty good and should work.  

It looks like the Dutch ftp source in your original sources.list had some MD5 problems indication the signatures did not match the database for available packages.  A failure at this point is the correct behavior for apt-get since MD5 signature is how we verify package integrity.

You should be able to upgrade yiour packages with the new sources.list.  Although you may have to run the commands:

sudo apt-get update
sudo apt-get -f install 

to fix any broken packages on your system.


Hope this helps.

---

