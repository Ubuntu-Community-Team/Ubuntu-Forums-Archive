---
title: "DSL modem configure??? (article)"
date: 2006-07-09
forum: Absolute Beginner Talk
---

### Post by candtalan on 2006-07-09
I would like to know if this article is realistic about its comments about (ubuntu) 'configuring a DSL modem' - I often talk to newbie users, and have not done this particular action myself yet.

====================================
[http://www.playfuls.com/news_03359_Linux_Makes_Things_Easier_For_New_Users.html](http://www.playfuls.com/news_03359_Linux_Makes_Things_Easier_For_New_Users.html)

Three new versions of Linux called Ubuntu, Fedora and Suse Linux are now offering automatic hardware recognition, the Hanover-based c't magazine reported. 

During installation, users can set up the free system with just a few mouse clicks. On top of that, all three systems come with an expansive collection of software.

As the graphic interface is similar to Windows, the first steps into the Linux world are easier for beginners or people switching systems.

However, there are hurdles. Tests showed problems such as configuring a DSL modem with the new system. Ubuntu, for example, requires users to enter text commands with conservative prompts, which might be challenging for beginners.
====================================
tia

---

### Post by not_yet on 2006-07-09
well I can tell you that during the install of dapper, my dsl was set up perfectly

it was auto-magical :D , no tweaking required

cheers

---

### Post by RaZer0r on 2006-07-09
it shouldn't be as hard to configure as in windows... most of the time it configures correctly from the first time

---

### Post by Jucato on 2006-07-09
I think you have to take into consideration that DSL/ADSL connections are either using DHCP or PPPoE. DHCP is easily detected by any Linux installation, since you don't have to supply any username and password. However, there are some DSL/ADSL connections that use or are starting to use PPPoE. This is the one that requires configuration using a command line, specifically pppoeconf. This has been one of my issues/complaints, as I am affected by it.

AFAIK, only SUSE, Fedora and PCLinuxOS have graphical interfaces for setting up any type of internet connection, including PPPoE DSL. It seems that none of the Debian-based distros have something similar installed by default (I'm not sure abut Linspire, though). Probably just a coincidence. MEPIS and KNOPPIX do try to have a GUI for that, but it's just pppoeconf started from the terminal.

---

