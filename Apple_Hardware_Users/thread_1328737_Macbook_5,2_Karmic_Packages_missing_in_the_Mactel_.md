---
title: "Macbook 5,2 Karmic: Packages missing in the Mactel PPA repository for i386"
date: 2009-11-16
forum: Apple Hardware Users
---

### Post by alissa.huskey on 2009-11-16
When following the instructions for Macbook 5,2: Karmic Koala, I ran into trouble under the Keyboard section.  Namely, I added the Mactel repo, imported the GPG key, but the packages were not found.

```

 ~$ sudo grep mactel /etc/apt/sources.list
deb http://ppa.launchpad.net/mactel-support/ubuntu karmic main
deb-src http://ppa.launchpad.net/mactel-support/ubuntu karmic main
 ~$ sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --recv-keys --keyserver keyserver.ubuntu.com 7A6BC20C4FE04DADD10837608DB7F87A2B97B7B8
gpg: requesting key 2B97B7B8 from hkp server keyserver.ubuntu.com
gpg: key 2B97B7B8: "Launchpad PPA for Mactel Support" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1
 ~$ sudo apt-get update
Hit http://ppa.launchpad.net karmic Release.gpg
Ign http://ppa.launchpad.net karmic/main Translation-en_US          
Hit http://us.archive.ubuntu.com karmic Release.gpg                 
Ign http://us.archive.ubuntu.com karmic/main Translation-en_US       
Hit http://security.ubuntu.com karmic-security Release.gpg           
Ign http://security.ubuntu.com karmic-security/main Translation-en_US
Hit http://ppa.launchpad.net karmic Release                          
Ign http://us.archive.ubuntu.com karmic/restricted Translation-en_US 
Ign http://us.archive.ubuntu.com karmic/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic-updates Release.gpg
Ign http://us.archive.ubuntu.com karmic-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/universe Translation-en_US
Ign http://us.archive.ubuntu.com karmic-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com karmic Release
Ign http://security.ubuntu.com karmic-security/restricted Translation-en_US               
Ign http://security.ubuntu.com karmic-security/universe Translation-en_US
Ign http://security.ubuntu.com karmic-security/multiverse Translation-en_US
Hit http://security.ubuntu.com karmic-security Release               
Hit http://us.archive.ubuntu.com karmic-updates Release              
Hit http://ppa.launchpad.net karmic/main Packages                                         
Hit http://security.ubuntu.com karmic-security/main Packages         
Hit http://us.archive.ubuntu.com karmic/main Packages
Hit http://us.archive.ubuntu.com karmic/restricted Packages
Hit http://us.archive.ubuntu.com karmic/main Sources                 
Hit http://us.archive.ubuntu.com karmic/restricted Sources           
Hit http://us.archive.ubuntu.com karmic/universe Packages            
Hit http://ppa.launchpad.net karmic/main Sources                     
Hit http://security.ubuntu.com karmic-security/restricted Packages   
Hit http://security.ubuntu.com karmic-security/main Sources
Hit http://security.ubuntu.com karmic-security/restricted Sources
Hit http://security.ubuntu.com karmic-security/universe Packages
Hit http://us.archive.ubuntu.com karmic/universe Sources
Hit http://us.archive.ubuntu.com karmic/multiverse Packages
Hit http://us.archive.ubuntu.com karmic/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/main Packages
Hit http://us.archive.ubuntu.com karmic-updates/restricted Packages
Hit http://us.archive.ubuntu.com karmic-updates/main Sources
Hit http://us.archive.ubuntu.com karmic-updates/restricted Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Packages
Hit http://security.ubuntu.com karmic-security/universe Sources
Hit http://security.ubuntu.com karmic-security/multiverse Packages
Hit http://security.ubuntu.com karmic-security/multiverse Sources
Hit http://us.archive.ubuntu.com karmic-updates/universe Sources
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Packages
Hit http://us.archive.ubuntu.com karmic-updates/multiverse Sources
Reading package lists... Done
 ~$ apt-cache search applesmc-dkms
 ~$ 

```

So I went poking around the repo itself, and sure enough, the package does not appear to be there:

[http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/binary-i386/Packages](http://ppa.launchpad.net/mactel-support/ubuntu/dists/karmic/main/binary-i386/Packages)

Compare to:

[http://ppa.launchpad.net/mactel-support/ubuntu/dists/jaunty/main/binary-i386/Packages](http://ppa.launchpad.net/mactel-support/ubuntu/dists/jaunty/main/binary-i386/Packages)


Ideas anyone?


(Apologies if this is not the correct place for this thread.)

---

### Post by thinktyler on 2009-12-07
I had the same problems, you can manually install. These are the links i used.

[https://launchpad.net/~mactel-support/+archive/ppa/+build/1167378/+files/gnome-power-manager_2.27.5-0ubuntu2~mactel1_amd64.deb](https://launchpad.net/~mactel-support/+archive/ppa/+build/1167378/+files/gnome-power-manager_2.27.5-0ubuntu2~mactel1_amd64.deb)

[https://launchpad.net/~mactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.23~karmic_all.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/mbp-nvidia-bl-dkms_0.23~karmic_all.deb)


[https://launchpad.net/~mactel-support/+archive/ppa/+files/gpomme_1.30-mactel2_amd64.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/gpomme_1.30-mactel2_amd64.deb)


[https://launchpad.net/~mactel-support/+archive/ppa/+files/xserver-xorg-input-synaptics_1.1.2-1ubuntu7-mactel1_amd64.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/xserver-xorg-input-synaptics_1.1.2-1ubuntu7-mactel1_amd64.deb)

[https://launchpad.net/~mactel-support/+archive/ppa/+files/xserver-xorg-video-intel-dbg_2.8.0-0ubuntu2~mactel1_amd64.deb](https://launchpad.net/~mactel-support/+archive/ppa/+files/xserver-xorg-video-intel-dbg_2.8.0-0ubuntu2~mactel1_amd64.deb)

---

