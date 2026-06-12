---
title: "Alien-cannot access file on cd during installation"
date: 2007-10-22
forum: Absolute Beginner Talk
---

### Post by switchover on 2007-10-22
Hello,
OK so i open up the terminal and type in:
sudo apt-get install alien

after typing in my password i get the following:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  debhelper dpkg-dev patch
Suggested packages:
  lsb-rpm lintian dh-make debian-keyring diff-doc
The following NEW packages will be installed
  alien debhelper dpkg-dev patch
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/888kB of archives.
After unpacking 2494kB of additional disk space will be used.
Do you want to continue [Y/n]? 

So i then press Y and i get the following with my Ubuntu 7.10 cd inserted in my cd drive:
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/p/patch/patch_2.5.9-4_i386.deb  Hash Sum mismatch
Failed to fetch cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/pool/main/d/dpkg/dpkg-dev_1.14.5ubuntu16_all.deb  Hash Sum mismatch
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

Don't have a clue what that means, but i'm assuming its trying to read a file of the ubuntu cd to which i have naviagted to but cannot open.
Any help greatly appreciated.
THanks

---

### Post by LanDan on 2007-10-22
i guess you have an internet connection, in that case it is save to remove the cd from your sources list and enable the online repositories..

i assume you use synaptic, simply look for repositorys and disable the cdrom and enable the on-line options

reload the sources and then try again

---

### Post by SOULRiDER on 2007-10-22
Also, remember its not a good idea (its a bad one actually) to install RPMs, even with alien. Try to get a deb package or compile from source. Only use an RPM package as a last resort.

---

### Post by switchover on 2007-10-22
thanks thats installed and i want to install adobe reader and when i type in:
sudo alien -i /home/myusername/Desktop/AdobeReader_enu-8.1.1-1.i486.rpm

i get the following:
Warning: Skipping conversion of scripts in package AdobeReader_enu: postinst postrm prerm
Warning: Use the --scripts parameter to include the scripts.

what do i do now?

---

### Post by LanDan on 2007-10-22
sure that acroread is not in the ubuntu repo's?

---

### Post by LanDan on 2007-10-22
is it possible that acroread is no langer in the multiverse????
otherwise you can use this link. it will give you the proper package, no alien needed
[http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb](http://ardownload.adobe.com/pub/adobe/reader/unix/8.x/8.1.1/enu/AdobeReader_enu-8.1.1-1.i386.deb)

---

### Post by switchover on 2007-10-22
strange, it says a later version of adobe reader is installed when i launched the package downloaded in the link provided by landan, but i can't find it on the applications menu anywhere.

"is it possible that acroread is no langer in the multiverse????"
"sure that acroread is not in the ubuntu repo's?"
what does that mean?

---

### Post by LanDan on 2007-10-22
> **switchover said:**
> strange, it says a later version of adobe reader is installed when i launched the package downloaded in the link provided by landan, but i can't find it on the applications menu anywhere.

"is it possible that acroread is no langer in the multiverse????"
"sure that acroread is not in the ubuntu repo's?"
what does that mean?

think there is still something to learn about how to install programms.
do have you the program synaptic?
just have a look over there, you can search install and de-install any program you like over there,

---

### Post by Maestro23 on 2007-10-22
> **switchover said:**
> strange, it says a later version of adobe reader is installed when i launched the package downloaded in the link provided by landan, but i can't find it on the applications menu anywhere.

"is it possible that acroread is no langer in the multiverse????"
"sure that acroread is not in the ubuntu repo's?"
what does that mean?

Just installed it from the repos myself.

In a terminal type: (to see if its installed)

> which acroread

*Should give a path to the file. Should be able to type acroread and run from terminal.  It's in my Main menu under Apps>> Office

Future Reference:

Installing Software: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by switchover on 2007-10-22
all sorted. thank you.

---

### Post by Maestro23 on 2007-10-22
> **switchover said:**
> all sorted. thank you.

Good deal.  Pease mark this thread SOLVED using the Thread Tools.

---

### Post by LanDan on 2007-10-22
> **Maestro23 said:**
> Just installed it from the repos myself.

weird, it isn't in mine

---

