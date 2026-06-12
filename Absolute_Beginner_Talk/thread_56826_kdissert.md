---
title: "kdissert"
date: 2005-08-14
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2005-08-14
Sorry to ask again,

Perhaps there is someone around now who can tell me if KDissert works in Gnome or not. It appears to be a KDE application. 

thank you,

--
sophtpaw

---

### Post by Ampersand on 2005-08-14
It should do. You'll have to install the kde libraries (which will be done automatically by synaptic/apt) and it'll use the kde theme instead of the gnome one, but I don't see why it shouldn't run,
Richard

---

### Post by nic2 on 2005-08-14
I installed it using the Synapatic Package Manager and it appears to be working fine.

---

### Post by sophtpaw on 2005-08-14
[QUOTE=nic2]I installed it using the Synapatic Package Manager and it appears to be working fine.[/QUOTE]

Great!

can you talk me through the steps, please?

1. [http://freehackers.org/~tnagy/kdissert/](http://freehackers.org/~tnagy/kdissert/)
2.Download

The latest stable version is v1.0.4 you can download it here.

The compilation requires a working KDE installation (version > 3.3) and python-xml. An update is available for kde 3.2 users here

Suse RPMs can be found usually at this location

Debian packages can be found there

3. I click on Debian packages and i see that it does not have the latest version. It has stable ( 0.3.8-1) testing ( 0.9.0-1 ) and unstable ( also 0.9.0-1 ??)

Which one did you choose, if, indeed this is how you went about it. If there is an easier option please do tell me.

Thank you,

--
sophtpaw

---

### Post by Ampersand on 2005-08-14
It's probably easiest to get the KDE libraries by installing 'kdebase' from synaptic or apt. You should then be able to install the testing or unstable deb (I think they're both the same) using dpkg -i. If there are any libraries missing it should tell you, and you can get them from apt.

If you want the latest version, it's probably easiest to get the tar.gz .

---

### Post by nic2 on 2005-08-14
I used the Synaptic Package Manager to get Kdissert - [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto) .  

Please note that you have to add the extra repositories to be able to do this - [www.ubuntuguide.org/#extrarepositories](www.ubuntuguide.org/#extrarepositories) .

---

### Post by Ampersand on 2005-08-14
I didn't see kdissert in there when I looked, but that makes it a bit easier. (: Do you happen to which repository it's in?

---

### Post by sophtpaw on 2005-08-14
[QUOTE=nic2]I used the Synaptic Package Manager to get Kdissert - [https://wiki.ubuntu.com/SynapticHowto](https://wiki.ubuntu.com/SynapticHowto) .  

Please note that you have to add the extra repositories to be able to do this - [www.ubuntuguide.org/#extrarepositories](www.ubuntuguide.org/#extrarepositories) .[/QUOTE]


Well, that certainly would be the easy and preferably way to do it, as far as i'm concerned. But i don't have it in Synaptic. I did upgrade repositories through Synaptic/ Settings/ Repositories which has taken me to a total of 16,314 package available

I've downloaded kbase as Ampersand suggested, and i seem to have all the dependencies sorted, so gonna try and install that tarbal and see if i can sudo dpkg -i the thing.

Please tell me any further suggestions, though

thx,

--
sophtpaw

---

### Post by SGC on 2005-08-14
[QUOTE=Ampersand]I didn't see kdissert in there when I looked, but that makes it a bit easier. (: Do you happen to which repository it's in?[/QUOTE]
 Its in the backports repository

---

### Post by sophtpaw on 2005-08-14
[QUOTE=sophtpaw]Well, that certainly would be the easy and preferably way to do it, as far as i'm concerned. But i don't have it in Synaptic. I did upgrade repositories through Synaptic/ Settings/ Repositories which has taken me to a total of 16,314 package available

I've downloaded kbase as Ampersand suggested, and i seem to have all the dependencies sorted, so gonna try and install that tarbal and see if i can sudo dpkg -i the thing.

Please tell me any further suggestions, though

thx,

--
sophtpaw[/QUOTE]

conrad@x1-6-00-0b-6a-16-78-f0kernel:/tmp/kdissert-1.0.4$ ls
AUTHORS  config.bks  doc       INSTALL  README   runme.sh    src
bksys    COPYING     Doxyfile  po       ROADMAP  SConstruct  VERSION

i want to be able to read Install and README files. 

thx



it didn't like sudo dpkg -i kdissert-1.0.4
came back:

conrad@x1-6-00-0b-6a-16-78-f0kernel:/tmp/kdissert-1.0.4$ sudo dpkg -i kdissert-1.0.4
dpkg: error processing kdissert-1.0.4 (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 kdissert-1.0.4

I tried ./configure 
came back:
bash: ./configure: No such file or directory

So, i'm at a slight loss. 

Can someone tell me how to open the README and INSTALL files in kdissert?

--
sophtpaw

---

### Post by nic2 on 2005-08-14
[QUOTE=SGC]Its in the backports repository[/QUOTE]

[https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)

---

### Post by sophtpaw on 2005-08-14
[QUOTE=nic2][https://wiki.ubuntu.com/UbuntuBackports](https://wiki.ubuntu.com/UbuntuBackports)[/QUOTE]

Thx,

i thought i had everything to the max. This has got my total list up to, 16,340 but still doesn't include kdissert  ](*,)   imao

any further suggestions?

---

### Post by SGC on 2005-08-14
[QUOTE=sophtpaw]Thx,

i thought i had everything to the max. This has got my total list up to, 16,340 but still doesn't include kdissert  ](*,)   imao

any further suggestions?[/QUOTE]
 Direct link to the .deb package of kdissert from the backports:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb)

Install it with:
dpkg -i kdissert_0.9.0-1build1~5.04ubp1_i386.deb

---

### Post by sophtpaw on 2005-08-14
[QUOTE=SGC]Direct link to the .deb package of kdissert from the backports:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/kdissert_0.9.0-1build1~5.04ubp1_i386.deb)

Install it with:
dpkg -i kdissert_0.9.0-1build1~5.04ubp1_i386.deb[/QUOTE]

So, nearly a breakthrough:

However, dependency issue arose. I have libgcc1 which the program wants. But my version is 1:4.0-Opre6untu7 when it wants instead version 1:4.0.0-7. Like, common! and Synaptic doesn't have that version.

Didn't think it could be so hard to install one piece of software,

But the mirror site was perfect otherwise - thx!

--
sophtpaw

---

### Post by SGC on 2005-08-14
[QUOTE=sophtpaw]So, nearly a breakthrough:

However, dependency issue arose. I have libgcc1 which the program wants. But my version is 1:4.0-Opre6untu7 when it wants instead version 1:4.0.0-7. Like, common! and Synaptic doesn't have that version.

Didn't think it could be so hard to install one piece of software,

But the mirror site was perfect otherwise - thx!

--
sophtpaw[/QUOTE]
 Libgcc1 1:4.0.0-7
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb)

To browse the backports repository:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/)

---

### Post by sophtpaw on 2005-08-14
[QUOTE=SGC]Libgcc1 1:4.0.0-7
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/libgcc1_4.0.0-7ubuntu6~5.04ubp1_i386.deb)

To browse the backports repository:
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/)[/QUOTE]

at last a breakthrough. I have installed Kdissert. For anyone elses benefit i should like to add that cons at [www.scons.org](www.scons.org) also needs to be installed (apparently) and Synaptic did that for me. By the way it also installed Kdissert for me, as it did for Nic2. Shame i never managed to compile and install manually from command line.

Still, now all i have to do is figure out the application. It doesn't look as straightforward as it has been made out to be.

--
sophtpaw

---

