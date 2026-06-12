---
title: "how can i update kubuntu ?"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by DO55 on 2008-01-29
in ubuntu there is "update manager "  but i cant find it i kubuntu 
help

---

### Post by (((X))) on 2008-01-29
Alt + F2 
then type: Adept
Adept

---

### Post by shadyedsan on 2008-01-29
KMenu -> System -> Adept Manager (Manage Packages)

---

### Post by DO55 on 2008-01-29
> **(((X))) said:**
> Alt + F2 
then type: Adept
Adept

Could not run the specified command.

---

### Post by DO55 on 2008-01-29
> **shadyedsan said:**
> KMenu -> System -> Adept Manager (Manage Packages)

ok  i open it  

what can i do next ?

---

### Post by smurphy_it on 2008-01-29
I believe update-manager is a gnome application.  Wouldn't be installed by default in a Kde environment.  It's been a long time since I've used kubuntu so I can't remember if you had an application like update-manager, if you had to force it to auto-run, or if it is already there by default.

Don't have Kubuntu here, so I can't check it ---> on a M$ pos machine at the moment.

---

### Post by (((X))) on 2008-01-29
OR, run root terminal, type:
# apt-get install synaptic

---

### Post by shadyedsan on 2008-01-29
i can't remember the specifics, so bear with me.

try this : in a konsole type adept-updater

that should update your system

---

### Post by shadyedsan on 2008-01-29
> **shadyedsan said:**
> i can't remember the specifics, so bear with me.

try this : in a konsole type adept-updater

that should update your system

adept isn't a good program anyway, better off with synaptic

sudo apt-get install synaptic :)

---

### Post by (((X))) on 2008-01-29
> **DO55 said:**
> Could not run the specified command.

it´s adept-updater, sorry

---

### Post by shadyedsan on 2008-01-29
> **smurphy_it said:**
> I believe update-manager is a gnome application.  Wouldn't be installed by default in a Kde environment.  It's been a long time since I've used kubuntu so I can't remember if you had an application like update-manager, if you had to force it to auto-run, or if it is already there by default.

Don't have Kubuntu here, so I can't check it ---> on a M$ pos machine at the moment.

sorry, i use ubuntu studio with gnome, should have remembered hehe :)

---

### Post by DO55 on 2008-01-29
i used this

sudo apt-get install synaptic

its give me long lines 


now what can i do ?

---

### Post by shadyedsan on 2008-01-29
what kind of long lines? please post an example

---

### Post by DO55 on 2008-01-29
eading package lists... Done
Building dependency tree
Reading state information... Done
The following extra packages will be installed:
  docbook-xml liblaunchpad-integration0 libscrollkeeper0 libvte-common libvte9
  scrollkeeper sgml-data
Suggested packages:
  docbook docbook-doc docbook-dsssl docbook-xsl perlsgml doc-html-w3 opensp
  libxml2-utils dwww
Recommended packages:
  gksu deborphan libgnome2-perl
The following NEW packages will be installed:

---

### Post by DO55 on 2008-01-29
docbook-xml liblaunchpad-integration0 libscrollkeeper0 libvte-common libvte9
  scrollkeeper sgml-data synaptic
0 upgraded, 8 newly installed, 0 to remove and 0 not upgraded.
Need to get 2937kB of archives.
After unpacking 18.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main sgml-data 2.0.3 [279kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main docbook-xml 4.5-4 [344kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main liblaunchpad-integration0 0.1.15 [17.3kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libscrollkeeper0 0.3.14-13ubuntu3 [51.4kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libvte-common 1:0.16.9-0ubuntu3 [128kB]

---

### Post by shadyedsan on 2008-01-29
that looks about right, some updates to your system. not to worry, when you use apt-get to install something it finds and installs the dependencies as well i.e. the packages the installed item needs to function

---

### Post by shadyedsan on 2008-01-29
to use synaptic, simply find it in Kmenu and enter a password if asked and hey presto :)

---

### Post by DO55 on 2008-01-30
shadyedsan

thanks :)

---

