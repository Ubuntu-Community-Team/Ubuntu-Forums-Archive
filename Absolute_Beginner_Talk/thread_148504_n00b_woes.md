---
title: "n00b woes"
date: 2006-03-22
forum: Absolute Beginner Talk
---

### Post by tommy1987 on 2006-03-22
When typing the following:

sudo apt-get update

I get the following, im guessing this isnt normal, can someone please explain what this command does and what is going wrong with mine.

Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release .gpg
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy Release
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
Ign cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Pa ckages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restric ted Packages
  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update can not be used to add new CD-ROMs
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Con nection refused) [IP: 82.211.81.151 80]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages
  Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Con nection refused) [IP: 82.211.81.151 80]
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could  not connect to archive.ubuntu.com:80 (82.211.81.151). - connect (111 Connection  refused) [IP: 82.211.81.151 80]
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/di sts/breezy/main/binary-i386/Packages.gz  Please use apt-cdrom to make this CD-RO M recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/di sts/breezy/restricted/binary-i386/Packages.gz  Please use apt-cdrom to make this  CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/P](http://archive.ubuntu.com/ubuntu/dists/breezy/main/binary-i386/P) ackages.gz  Could not connect to archive.ubuntu.com:80 (82.211.81.151). - connec t (111 Connection refused) [IP: 82.211.81.151 80]
Reading package lists... Done
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Relea se i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fB reezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i38 6_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Relea se i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10% 20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricte d_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packa ges (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_ Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used  instead.


Thanks,,

---

### Post by markr on 2006-03-22
It looks like either you are not connected to the internet or the repositories are down.  I suspect it is a connection issue.

---

### Post by localzuk on 2006-03-22
Could you post your /etc/apt/sources.list file?

---

### Post by tommy1987 on 2006-03-22
sure its here:

deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu](http://gb.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy main




im also gettin this error when starting synaptic:

W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/main Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list cdrom://Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012) breezy/restricted Packages (/var/lib/apt/lists/Ubuntu%205.10%20%5fBreezy%20Badger%5f%20-%20Release%20i386%20(20051012)_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)



I didnt used to, what has happened?

---

### Post by xmastree on 2006-03-22
Open that file in an editor (use **sudo gedit /etc/apt/sources.list**) and remove all the # from the beginnings of the lines which have only one #. That will enable the extra repositories.
Then, insert a # at the beginning of the first line, to block the CD from the list.

save the file, and try sudo apt-get update again.

---

### Post by localzuk on 2006-03-22
Also, put a # in front of the line at the bottom deb [http://archive](http://archive)...

---

### Post by tommy1987 on 2006-03-22
ok now i get lots of errors such as this:

Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138). - connect (111 Connection refused)

does that mean that it is a connection problem, because i connect through an annoying proxy, if this is the case how do i configure terminal to see my internet connection, because browsers can see it once i type the HTTP proxy auto configuaration url in, is there something similar for terminal?

Thanks ,,

---

### Post by LKRaider on 2006-03-22
Try this:
Go to _Synaptic -> Settings -> Preferences -> Network_ and configure your proxy there, click OK and then click the Reload button to update.

---

### Post by tommy1987 on 2006-03-22
The settings were set already but it is still not seeing the connection, Its so annoying because until this is sorted apt-get commands to install software wont work! I really dont understand it though?? I HATE PROXIES!

---

### Post by LKRaider on 2006-03-22
Post your current proxy settings here.
Try removing the proxy and do an update. What happens then?

---

### Post by tommy1987 on 2006-03-22
Getting this error when starting synaptic:

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

Starting to annoy me now, I wish I just had a normal internet connection through a network and not a damn proxy!!

---

### Post by localzuk on 2006-03-22
You may find some information that could help you on the wiki here: [https://wiki.ubuntu.com/AptProxyHowTo](https://wiki.ubuntu.com/AptProxyHowTo)

EDIT: Nothing to see here. Ignore the above. I misread the title :)

EDIT2: However, you could try typing
```

export http_proxy="http://proxyserver:port"
export ftp_proxy="http://proxyserver:port"

```

before running
```

sudo apt-get update

```

This should set the proxy on the console...

---

### Post by tommy1987 on 2006-03-22
I may just have to make do with not installing anything for a while, because I am connected to the internet through the a university proxy which makes life difficult because I have little control over it obviously, may just have to wait, there is lots of connection issues on my computer, such as GAIM doesnt see the internet, the only thing that does work is the browser, im guessing these are all connection issues, and if so they will be sorted when i get a direct connection in a few months...

---

### Post by localzuk on 2006-03-22
It will all come down to configuring the proxy settings correctly - at the Uni where I work we have students with the exact same issues. Random bits not working due to not having the proxy set up correctly.

My advise would be to speak to someone at your computer support desk about it - they may be able to provide some insight.

---

### Post by tommy1987 on 2006-03-22
Thanks, sounds like a plan, I will pay them a visit, ;-)

---

