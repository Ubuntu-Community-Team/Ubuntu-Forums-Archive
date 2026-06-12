---
title: "Updating list of applications"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by fiik on 2007-12-16
Cannot load list of applications.  Downloads are enabled under Add/Remove/Preferences.   Sources are ticked.  Window showing Downloading 6 of 36 files.  All files fail.
Under Synaptic Package Manager it shows 10 of 40 files and still fails.

---

### Post by philinux on 2007-12-16
You'll need to post the errors messages.

---

### Post by Pumalite on 2007-12-16
Post:
sudo dpkg --configure -a (Enter)
sudo apt-get update (Enter)
sudo apt-get upgrade (Enter)

---

### Post by fiik on 2007-12-16
My brain hurts.  I'm only just installed, so all of the commands I got will take me days to figure out.  
Right now it's nearly 1.00 am in Oz and like I said my brain hurts.  I'll save all that printout and try and figure it out after some sleep.  Thanks for your help so far.
FIIK

---

### Post by fiik on 2007-12-17
Hello again.
In response to Pumalite-

bruce@bruce-desktop:~$ sudo dpkg --configure -a
[sudo] password for bruce:
bruce@bruce-desktop:~$ sudo dpkg --configure
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
bruce@bruce-desktop:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg                            
  Could not connect to packages.medibuntu.org:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_AU               
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU                  
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_AU                 
  Could not connect to packages.medibuntu.org:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU            
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err 

I had to close the terminal to get the next command in.

bruce@bruce-desktop:~$ sudo apt-get upgrade
[sudo] password for bruce:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bruce@bruce-desktop:~$ 


Hoping that someone can pick this up and help me.

---

### Post by Anicka on 2007-12-17
Maybe you can try this: [http://ubuntuforums.org/showthread.php?t=587225&page=2](http://ubuntuforums.org/showthread.php?t=587225&page=2)

---

### Post by Pumalite on 2007-12-17
> **fiik said:**
> Hello again.
In response to Pumalite-

bruce@bruce-desktop:~$ sudo dpkg --configure -a
[sudo] password for bruce:
bruce@bruce-desktop:~$ sudo dpkg --configure
dpkg: --configure needs at least one package name argument

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --license for copyright license and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
bruce@bruce-desktop:~$ sudo apt-get update
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg                             
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy Release.gpg                             
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg                            
  Could not connect to packages.medibuntu.org:80 (1.0.0.0), connection timed out
Err [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_AU               
  Could not connect to archive.canonical.com:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/main Translation-en_AU                  
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_AU                 
  Could not connect to packages.medibuntu.org:80 (1.0.0.0), connection timed out
Err [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) gutsy/restricted Translation-en_AU            
  Could not connect to au.archive.ubuntu.com:80 (1.0.0.0), connection timed out
Err 

I had to close the terminal to get the next command in.

bruce@bruce-desktop:~$ sudo apt-get upgrade
[sudo] password for bruce:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bruce@bruce-desktop:~$ 


Hoping that someone can pick this up and help me.

You missed the 'a' in:
sudo dpkg --configure -a

---

### Post by fiik on 2007-12-17
Tried changing the ISP addresses - was on Primary DNS so changed it to IP address.
Still could not download indexes and it knocked me off the web as well.  Changed it back and got back online.

---

### Post by hyper_ch on 2007-12-17
does your internet connection work at all?

It seems you can't reach the servers.

---

### Post by fiik on 2007-12-17
I'm on wired broadband and using the same computer for the forum.  The IP and DNS addresses are straight of the Connection Information function.

---

### Post by hyper_ch on 2007-12-17
what do you get when you ping?

```

ping archive.canoncial.com

```

---

### Post by fiik on 2007-12-17
bruce@bruce-desktop:~$ ping archive.canoncial.com
PING archive.canoncial.com (66.45.254.245) 56(84) bytes of data.
64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=1 ttl=49 time=290 ms
64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=2 ttl=49 time=290 ms

64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=3 ttl=49 time=289 ms
64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=4 ttl=49 time=291 ms
64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=5 ttl=49 time=290 ms
64 bytes from archive.canoncial.com (66.45.254.245): icmp_seq=6 ttl=49 time=291 ms

---

### Post by hyper_ch on 2007-12-17
strange...

---

### Post by fiik on 2007-12-17
Things are starting to happen here!
Add/Remove/Preferences/Download From. Choices given were MainServer, Australian Server, Other
I chose other, tested for best, chose that mirror and Downloading of the Repositories started.
Many of the 'Translations' are failing but Sources and packages are getting thru.
Right now it seems to have hung on file 58 of 68, but running it again should do it.

---

### Post by fiik on 2008-01-02
Firstly, the problem is solved but thank you all for trying to help me.

I am running Mint - but I had the same problem on Ubuntu 7.10.
B/band direct connection.
Had the question posted on Ubuntu Forum and Launchpad Ubuntu.
The successful thread is- [https://answers.launchpad.net/ubuntu/+question/21143](https://answers.launchpad.net/ubuntu/+question/21143)
Apparently a known bug.
The final question I have is should I add the Mint Repoitory source to my Ubunatu Indexes?

Both the features of Mint/Ubuntu are awesome, but the support provided by all is fantastic.

I am now a full convert. Windows sucks.

---

