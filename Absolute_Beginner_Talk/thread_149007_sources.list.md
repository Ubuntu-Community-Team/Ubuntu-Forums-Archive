---
title: "sources.list"
date: 2006-03-23
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-23
I think that my sources.list may be corrupted, or I may have messed it up, because i get the following errors when loading synaptics:

W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/main Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/restricted Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/universe Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports/multiverse Packages (/var/lib/apt/lists/gb.archive.ubuntu.com_ubuntu_dists_breezy-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_universe_binary-i386_Packages) - stat (2 No such file or directory)



What is all of that about?? Anyone know what I can do?

---

### Post by localzuk on 2006-03-23
Hi, could you post your sources.list file here?

---

### Post by tommy1987 on 2006-03-23
# deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
 deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

 deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
 deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main

---

### Post by Perfect Storm on 2006-03-23
Have you tried:

```
sudo apt-get update
```
(remember to exit synaptic first)

---

### Post by tommy1987 on 2006-03-23
thats the problem, I cant access the internet in terminal so I get loads of errors like the following when trying that (due to proxy which i cant configure for terminal to access only browsers because of the .pac configuration url):

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Err [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy-backports Release.gpg
  Could not connect to gb.archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection refused) [IP: 82.211.81.151 80]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Packages
Ign [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/universe Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) breezy Release
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)

---

### Post by Perfect Storm on 2006-03-23
So the same also happen if you hit the reload button in synaptic?

---

### Post by tommy1987 on 2006-03-23
yeah its really getting to me now, because I cant seem to get anything other than browsers to see the internet connection, i have a .pac file which i have posted as another thread, you could take a look at and see if you can deduce anything from because I cant..  If I could just find some way of getting terminal to see the internet then everything would be okay!

---

### Post by anirban.sam on 2006-03-23
add [export_http=//:[www.yourproxy.com:port]](www.yourproxy.com:port]) string into your bash_profile file. then run it by . .bash_profile and try $sudo apt-get update again

---

### Post by tommy1987 on 2006-03-23
can you please give me some more detailed instructions on how to do this please?
Im new to all of this? sounds like your onto something.. ;-)

---

### Post by cotcot on 2006-03-23
It happens that synaptic gives this error by me too. I then go to terminal and do "apt-get update" (the same as the "reload" button in synaptic) without problems.

---

### Post by jkeyes0 on 2006-03-24
You said you were behind a proxy, correct? Have you tried going to System -> Preferences -> Network Proxy and entering a Manual (or Automatic) proxy configuration there?

---

### Post by arnieboy on 2006-03-24
use the instructions outlined in the following post for configuring apt-get and wget when behind a proxy:
[http://ubuntuforums.org/showpost.php?p=541276&postcount=1006](http://ubuntuforums.org/showpost.php?p=541276&postcount=1006)

---

### Post by anirban.sam on 2006-03-28
Try this from a console;
user@computername:~$ vi ~/.bash_profile (a text file will open, type [export_http=//:[www.yourproxyname:portnumber]](www.yourproxyname:portnumber]) at the bottom of the file without the brackets. hit Esc key once, type [:wq] without brackets and press enter. 

Now issue this command at the command prompt;
user@computername:~$. . bash_profile, if asked for passwd, give it.

Finally try by typing [sudo apt-get update] from command prompt again

---

