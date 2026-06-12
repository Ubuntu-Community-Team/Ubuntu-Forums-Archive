---
title: "Make, Perl, GCC etc"
date: 2006-10-03
forum: Absolute Beginner Talk
---

### Post by Digital221 on 2006-10-03
Hi, I've installed Ubuntu Server and I need basic utils to get going but i dont how to install them :( can anyone help. I need Perl, Make, GCC, and maybe more. Is there some command i can type in to get all these?  I thought they came as standard with the install. Thanks

---

### Post by Chickencha on 2006-10-03
You should be able to get all of the mentioned things by simply entering

```

sudo apt-get install build-essential

```

If there are other packages you need that you didn't mention above, I can't guarantee this will get you everything you want.  It will get you perl, make, and gcc (among other things), though.

---

### Post by Digital221 on 2006-10-03
thanks for your help, but i keep getting the below errors. Any advice?

gov@server:~$ sudo apt-get install build-essential
Reading package lists... Done
Building dependency tree... Done
build-essential is already the newest version.
You might want to run âapt-get -f installâ to correct these:
The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not going to be installedor
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but it is not going to be installed
                   Depends: g++ (>= 4:4.1.1) but it is not going to be installed
                   Depends: make but it is not going to be installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not going to be installed
  perl-modules: Depends: perl (>= 5.8.8-1) but 5.8.7-10ubuntu1 is to be installed
  webmin: Depends: libnet-ssleay-perl but it is not going to be installed
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not going to be installed
E: Unmet dependencies. Try âapt-get -f installâ with no packages (or specify a solution).
gov@server:~$

ok, i fixed it YAY: i just deleted apt.conf and it worked a treat :) SWEET :p

---

### Post by Leeghoofd on 2006-10-03
" build-essential is already the newest version. " 

This should indicate that build utilities are already installed an running at the latest version.

Try getting info on how to run each programm...

---

### Post by Medieval_Creations on 2006-10-03
I would try it again, but this time try 

sudo apt-get update
   then
sudo apt-get install build-essential

I've over looked that step in the past too and gotten similar errors sometimes.
You could also try: sudo apt-get upgrade

---

### Post by Digital221 on 2006-10-04
I tried to update it but im getting the below error, i definetly have internet access on the machine as I tried using wget.

root@server:~#  sudo apt-get update
Errhttp://gb.archive.ubuntu.com dapper Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper-updates Release.gpg
  Connection failed [IP: 195.248.90.54 80]
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates Release
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper/restricted Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Packages
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/main Sources
Ign [http://gb.archive.ubuntu.com](http://gb.archive.ubuntu.com) dapper-updates/restricted Sources
Errhttp://gb.archive.ubuntu.com dapper/main Packages
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper/main Sources
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Packages
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Packages
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/main Sources
  Connection failed [IP: 195.248.90.54 80]
Errhttp://gb.archive.ubuntu.com dapper-updates/restricted Sources
  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/Release.gpg)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/binary-i386/Packages.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/main/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Failed to fetch [http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz](http://gb.archive.ubuntu.com/ubuntu/dists/dapper-updates/restricted/source/Sources.gz)  Connection failed [IP: 195.248.90.54 80]
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

and get this when i try sudo apt-get upgrade

root@server:~# sudo apt-get upgrade
Reading package lists... Done
Building dependency tree... Done
You might want to run âapt-get -f installâ to correct these.
The following packages have unmet dependencies.
  build-essential: Depends: libc6-dev but it is not installedor
                            libc-dev
                   Depends: gcc (>= 4:4.1.1) but it is not installed
                   Depends: g++ (>= 4:4.1.1) but it is not installed
                   Depends: make but it is not installed
                   Depends: dpkg-dev (>= 1.13.5) but it is not installed
  perl-modules: Depends: perl (>= 5.8.8-1) but 5.8.7-10ubuntu1 is installed
  webmin: Depends: libnet-ssleay-perl but it is not installed
          Depends: libauthen-pam-perl but it is not installable
          Depends: libio-pty-perl but it is not installed
E: Unmet dependencies. Try using -f.

---

### Post by Leeghoofd on 2006-10-04
Have you tried getting perl and python through synaptic? thats how i got them..

---

### Post by davmac on 2006-10-04
Digital221,

That looks like a net access problem to me. I'm guessing this because of the "Connection failed [IP: 195.248.90.54 80]" messages.

If you type "ping www.google.com" what do you get?

There looks to be a separate problem with package dependencies when you do the apt-get upgrade. I had, and solved, this exact problem a few months ago but, for the life of me can't remember how. I'll carry on digging and respond if I can find the answer.

Dave Mac

---

### Post by davmac on 2006-10-04
There's a thread here ([http://ubuntuforums.org/archive/index.php/t-75596.html](http://ubuntuforums.org/archive/index.php/t-75596.html)) that also refers to the build-essential dependency problem. The solution suggested is to run "sudo apt-get -f install". No response about whether it worked or not, but got to be worth a try once you sort out the net access issue.

Hope this helps,

Dave Mac

---

### Post by Medieval_Creations on 2006-10-04
Digital221,

Have there been any changes made to your /etc/apt/sources.list?

Mine consists of the following Lines:
```

deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe main restricted multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#Givre's repository (ntfs-3g & fuse 2.5.3)
deb [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main
deb-src [http://givre.cabspace.com/ubuntu/](http://givre.cabspace.com/ubuntu/) dapper main

#Wine for Ubunto Dapper (6.06)
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
```

---

### Post by Digital221 on 2006-10-04
thanks for all the help guys, the sudo apt-get -f install followed by sudo apt-get install build-essential. Worked a treat :P thanks for all your help. Now i get cracking :P

---

### Post by Digital221 on 2006-10-04
I still have one problem :( I follwed your sources.list to the letter but it still fails when trying to connect to them. I can ping google and I can even ping ip's its failing on, ie: 146.137.96.15

I cant figure it out, why does it fail connecting but i can ping it?

---

