---
title: "how to use c programming in 7.04"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by kartik2104 on 2007-07-07
hi!
i am a begginer to the world of linux and just yesterday i have installed ubuntu 7.04 now i would like to know how to use c programming in ubuntu and also about other programming languages that are supported by ubuntu 7.04(fiesty fawn)/

---

### Post by steve.horsley on 2007-07-07
Install it by installing the package build-essential: 
**sudo aptitude install build-essential**
After installing this, the command cc will launch the compiler, e.g.
**cc HelloWorld.c -o HelloWorld**

For an editor, gedit is a reasonable start, but many programmers have other favourites. You will need good C tutorial and reference documents. If noone gives you some references here, ask in the Programming forum: [http://ubuntuforums.org/forumdisplay.php?f=39](http://ubuntuforums.org/forumdisplay.php?f=39)

---

### Post by kartik2104 on 2007-07-11
i dont really understand what this "sudo aptitude install build-essential"
means and how it works so please someone tell me about that.

---

### Post by Golyadkin on 2007-07-11
What you do is you open a terminal (click Applications > Accessories > Terminal)  and type that command. Then it will ask for your password. You enter it, and the build-essential package will be installed.

Please make sure you[ read this]("http://monkeyblog.org/ubuntu/installing/") since you are new to Ubuntu.

---

### Post by Nussbaum on 2007-07-11
> **kartik2104 said:**
> i dont really understand what this "sudo aptitude install build-essential"
means and how it works so please someone tell me about that.

Im new to Ubuntu too so at the risk of being wrong, that command will install things like libararies, compilers etc, stuf you need to compile your source. Also I dont much about programming but maybe Anjuta is worth looking into(its available IIRC in the Add/Remove section under Applications)

[http://en.wikipedia.org/wiki/Anjuta](http://en.wikipedia.org/wiki/Anjuta)

---

### Post by Nuverde on 2007-07-11
IDEs (Integrated Development Environments) like Anjuta, Eclipse, etc. are nice for managing complex projects.  But I would suggest using a simple text editor like gedit or kate (in kubuntu) while you are initially trying to learn the basics of programming in a new language.  This way you can focus on learning the language itself and not get frustrated by dealing with projects and makefiles and whatnot.   Once you have more experience with a given language, you can choose an IDE that fits your style and needs.

---

### Post by LaRoza on 2007-07-11
In Ubuntu these languages are very useful:

* C/C++
* Python
* Perl

I suggest you learn them, my wiki, has all you need. (Python and Perl will already be installed on Ubuntu, although certain modules will be missing) The link to my wiki is in my sig.

Compiling through the command line is the same as compiling through the command line in Windows.

My wiki has free resources for learning how to program on it. (actually, links to them)

---

### Post by stigala on 2007-07-11
I've installed ubuntu 7.04 today and tried the mentioned installation command: **sudo aptitude install build-essential**, but got troubles midway through the installation process:

[I][COLOR="Green"]stig@stig-laptop:~$ sudo aptitude install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk 
  capplets-data evolution-data-server evolution-data-server-common file 
  firefox firefox-gnome-support gimp gimp-data gimp-python gnome-app-install 
  gnome-control-center gnome-panel gnome-panel-data hwdb-client-common 
  hwdb-client-gnome language-pack-en language-pack-gnome-en libcamel1.2-10 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libfreetype6 libgimp2.0 
  libgnome-window-settings1 libkrb53 libmagic1 libmagick9 libmetacity0 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libslab0 libsmbclient 
  linux-generic linux-headers-generic metacity metacity-common openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python python-apport 
  python-gdbm python-minimal python-problem-report python-uno python2.5 
  python2.5-minimal rdesktop samba-common smbclient ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core vim-common vim-tiny 
  xscreensaver-data xscreensaver-gl 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 86 not upgraded.
Need to get 667kB/7906kB of archives. After unpacking 33.0MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  linux-libc-dev 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": y
Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.29
  504 Proxy Timeout ( The connection timed out. For more information about this event, see ISA Server Help.  ) [IP: 91.189.88.31 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:) 504 Proxy Timeout ( The connection timed out. For more information about this event, see ISA Server Help.  ) [IP: 91.189.88.31 80]
[/COLOR][/I]

It seems to me it can't get the linux-libc-dev_2.6.20-16.29_i386.deb file from the server. I'm writing this post, so I'm obviously online. **Could I have done something wrong or is it the server which is the problem?**

I downloaded a build-essential file (build-essential_11.3_i386.deb) from [http://packages.debian.org/unstable/devel/build-essential](http://packages.debian.org/unstable/devel/build-essential), but it's not the same file as the one the aptitude-command tried to fetch. I tried to install it, but I didn't specify any destination so it complained about that. 

[I][COLOR="Green"]stig@stig-laptop:~/Packages$ sudo install build-essential_11.3_i386.deb 
Password:
install: missing destination file operand after `build-essential_11.3_i386.deb'
Try `install --help' for more information.
[/COLOR][/I]
**Should I install it, and if so, what should the destination be? **

Regards, 

Stig

---

### Post by stigala on 2007-07-12
I tried again this morning to install the build-essential package (sudo aptitude install build-essential) and this time it worked. Didn't change a thing (didn't reboot either), so I guess the problem had something to do with the server or my network connection. 

So I'm back on track!

Stig

---

### Post by dfreer on 2007-07-12
> **stigala said:**
> I've installed ubuntu 7.04 today and tried the mentioned installation command: **sudo aptitude install build-essential**, but got troubles midway through the installation process:

[I][COLOR="Green"]stig@stig-laptop:~$ sudo aptitude install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages have been automatically kept back:
  linux-image-generic linux-restricted-modules-common 
  linux-restricted-modules-generic 
The following NEW packages will be automatically installed:
  g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
The following packages have been kept back:
  app-install-data app-install-data-commercial apport apport-gtk 
  capplets-data evolution-data-server evolution-data-server-common file 
  firefox firefox-gnome-support gimp gimp-data gimp-python gnome-app-install 
  gnome-control-center gnome-panel gnome-panel-data hwdb-client-common 
  hwdb-client-gnome language-pack-en language-pack-gnome-en libcamel1.2-10 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-9 libedataserverui1.2-8 libegroupwise1.2-13 
  libexchange-storage1.2-3 libexif12 libfreetype6 libgimp2.0 
  libgnome-window-settings1 libkrb53 libmagic1 libmagick9 libmetacity0 
  libnspr4 libnss3 libpanel-applet2-0 libpng12-0 libslab0 libsmbclient 
  linux-generic linux-headers-generic metacity metacity-common openoffice.org 
  openoffice.org-base openoffice.org-calc openoffice.org-common 
  openoffice.org-core openoffice.org-draw openoffice.org-evolution 
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-java-common openoffice.org-math 
  openoffice.org-style-human openoffice.org-writer python python-apport 
  python-gdbm python-minimal python-problem-report python-uno python2.5 
  python2.5-minimal rdesktop samba-common smbclient ttf-opensymbol tzdata 
  unattended-upgrades update-manager update-manager-core vim-common vim-tiny 
  xscreensaver-data xscreensaver-gl 
The following NEW packages will be installed:
  build-essential g++ g++-4.1 libc6-dev libstdc++6-4.1-dev linux-libc-dev 
0 packages upgraded, 6 newly installed, 0 to remove and 86 not upgraded.
Need to get 667kB/7906kB of archives. After unpacking 33.0MB will be used.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  linux-libc-dev 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": y
Unrecognized input.  Enter either "Yes" or "No".
Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
Writing extended state information... Done
Err [http://security.ubuntu.com](http://security.ubuntu.com) feisty-security/main linux-libc-dev 2.6.20-16.29
  504 Proxy Timeout ( The connection timed out. For more information about this event, see ISA Server Help.  ) [IP: 91.189.88.31 80]
E: Failed to fetch [http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:](http://security.ubuntu.com/ubuntu/pool/main/l/linux-source-2.6.20/linux-libc-dev_2.6.20-16.29_i386.deb:) 504 Proxy Timeout ( The connection timed out. For more information about this event, see ISA Server Help.  ) [IP: 91.189.88.31 80]
[/COLOR][/I]

It seems to me it can't get the linux-libc-dev_2.6.20-16.29_i386.deb file from the server. I'm writing this post, so I'm obviously online. **Could I have done something wrong or is it the server which is the problem?**

I downloaded a build-essential file (build-essential_11.3_i386.deb) from [http://packages.debian.org/unstable/devel/build-essential](http://packages.debian.org/unstable/devel/build-essential), but it's not the same file as the one the aptitude-command tried to fetch. I tried to install it, but I didn't specify any destination so it complained about that. 

[I][COLOR="Green"]stig@stig-laptop:~/Packages$ sudo install build-essential_11.3_i386.deb 
Password:
install: missing destination file operand after `build-essential_11.3_i386.deb'
Try `install --help' for more information.
[/COLOR][/I]
**Should I install it, and if so, what should the destination be? **

Regards, 

Stig

First off, the command to install a .deb from the command line is not 
```
sudo install *.deb
```
It would be:
```
sudo dpkg -i *.deb
```
In most cases, it will complain about dependencies, in which case you will need to run this command:
```
sudo apt-get -f install
```


Secondly, If you are going to download .deb files for ubuntu, it is probably best to check [http://packages.ubuntu.com](http://packages.ubuntu.com) before you check [http://packages.debian.com](http://packages.debian.com) even though you can install a debian package on ubuntu, it's probably best to download the package made specifically for ubuntu.

Then, about your original error: it sounds like you added some extra repositories in you /etc/apt/sources.list, one of which is from a non-trusted repository. I would either go through the file and put comments (#) in front of the non-official repositories, or post the file here, and we can show you which ones to comment out. From there, do the following commands:
```
sudo aptitude update
sudo aptitude upgrade
sudo aptitude dist-upgrade
sudo aptitude install build-essential
```
Then you'll prolly need to reboot, as there is a new kernel being installed in your updates.

---

