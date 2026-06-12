---
title: "Please Help! Can't install anything!"
date: 2007-10-06
forum: Absolute Beginner Talk
---

### Post by TaiQui on 2007-10-06
When I first got ubuntu, I installed Limewire but it froze write in the middle so I force quitted it. I have rebooted many times sinnce this happenned, but whenever I try to install something it just says "Please close the other install manager like update manager or Synaptics" or something similar.:confused:


Please Help!

TaiQui

EDIT: Heres an image.

[http://i23.tinypic.com/25p34i1.jpg](http://i23.tinypic.com/25p34i1.jpg)

---

### Post by bapoumba on 2007-10-06
Please open a terminal (> Accessories > Terminal) and paste the complete error message to:
```
sudo aptitude update
```

---

### Post by Pumalite on 2007-10-06
When you use apt-get, Synaptic has to be closed.

---

### Post by TaiQui on 2007-10-06
> **bapoumba said:**
> Please open a terminal (> Accessories > Terminal) and paste the complete error message to:
```
sudo aptitude update
```

and then what does it do? I just asted it and its not like loading anything I just retried it and it still says the same thing

and I'm not sure what synaaptic is. if its the update manager when I right click  it I can't close it.:confused:

---

### Post by bapoumba on 2007-10-06
> **TaiQui said:**
> and then what does it do? I just asted it and its not like loading anything I just retried it and it still says the same thing

Enter the line in terminal. Then, there will be a blank line, enter your password (it will not appear on the screen, it is normal) and hit <enter>. Paste the whole output in a reply here.

---

### Post by TaiQui on 2007-10-06
Sorry for it being so long, but I did it, and got this.

```
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/main Translation-en_US
Ign cdrom://Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415) feisty/restricted Translation-en_US
Get:1 http://us.archive.ubuntu.com feisty Release.gpg [191B]  
Ign http://us.archive.ubuntu.com feisty/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty/multiverse Translation-en_US
Get:2 http://us.archive.ubuntu.com feisty-updates Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-updates/restricted Translation-en_US
Get:3 http://us.archive.ubuntu.com feisty-security Release.gpg [191B]
Ign http://us.archive.ubuntu.com feisty-security/main Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/restricted Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/universe Translation-en_US
Ign http://us.archive.ubuntu.com feisty-security/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com feisty Release
Hit http://us.archive.ubuntu.com feisty-updates Release
Hit http://us.archive.ubuntu.com feisty-security Release
Hit http://us.archive.ubuntu.com feisty/main Packages
Hit http://us.archive.ubuntu.com feisty/restricted Packages
Hit http://us.archive.ubuntu.com feisty/main Sources
Hit http://us.archive.ubuntu.com feisty/restricted Sources
Hit http://us.archive.ubuntu.com feisty/universe Packages
Hit http://us.archive.ubuntu.com feisty/universe Sources
Hit http://us.archive.ubuntu.com feisty/multiverse Packages
Hit http://us.archive.ubuntu.com feisty/multiverse Sources
Hit http://us.archive.ubuntu.com feisty-updates/main Packages
Hit http://us.archive.ubuntu.com feisty-updates/restricted Packages
Hit http://us.archive.ubuntu.com feisty-updates/main Sources
Hit http://us.archive.ubuntu.com feisty-updates/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/main Packages
Hit http://us.archive.ubuntu.com feisty-security/restricted Packages
Hit http://us.archive.ubuntu.com feisty-security/main Sources
Hit http://us.archive.ubuntu.com feisty-security/restricted Sources
Hit http://us.archive.ubuntu.com feisty-security/universe Packages
Hit http://us.archive.ubuntu.com feisty-security/universe Sources
Hit http://us.archive.ubuntu.com feisty-security/multiverse Packages
Hit http://us.archive.ubuntu.com feisty-security/multiverse Sources
Fetched 3B in 1s (3B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: Couldn't rebuild package cache
```
and I still can't install stuff

---

### Post by bapoumba on 2007-10-06
Please go bak to the terminal and run:
```
sudo dpkg --configure -a
```

Paste back in here any error you get.

---

### Post by TaiQui on 2007-10-06
it says its finished installing, but then the status says:

Error: Failed to satisfy all dependicies (broken cache)

---

### Post by bapoumba on 2007-10-06
Was there any package name associated to the error message?

Try:
```
sudo apt-get -f install
```
You can cancel the process if it wants to do things you do not understand. Once again paste the WHOLE output, even if it is long (use the code bbcode  ;)).

---

### Post by TaiQui on 2007-10-06
I just did the sudo apt get and I got this.

```
Package configuration                                                           
                                                                                
 &#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9508; Configuring sun-java5-jre &#9500;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;  
 &#9474;                                                                           &#9474;  
 &#9474; Operating System Distributor License for Java v1.1 (DLJ)                  &#8593;  
 &#9474;                                                                           &#9646;  
 &#9474; Operating System Distributor License for Java version 1.1 (DLJ)           &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; SUN MICROSYSTEMS, INC. ("SUN") IS WILLING TO LICENSE THE JAVA PLATFORM    &#9618;  
 &#9474; STANDARD EDITION DEVELOPER KIT ("JDK" - THE "SOFTWARE") TO YOU ONLY UPON  &#9618;  
 &#9474; THE CONDITION THAT YOU ACCEPT ALL OF THE TERMS CONTAINED IN THIS LICENSE  &#9618;  
 &#9474; AGREEMENT (THE "AGREEMENT").  PLEASE READ THE AGREEMENT CAREFULLY.  BY    &#9618;  
 &#9474; INSTALLING, USING, OR DISTRIBUTING THIS SOFTWARE, YOU ACCEPT ALL OF THE   &#9618;  
 &#9474; TERMS OF THE AGREEMENT.                                                   &#9618;  
 &#9474;                                                                           &#9618;  
 &#9474; 1.  DEFINITIONS. "Software" means the code identified above in binary     &#9618;  
 &#9474;     form, any other machine readable materials including, but not         &#9618;  
 &#9474;     limited to, libraries, source files, header files, and data files),   &#8595;  
 &#9474;                                                                              
 &#9474;                                  <Ok>                                        
 &#9474;                                                                           &#9474;  
 &#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9496;  
      
```

How do I continue?
EDIT: I scrolled all the way down too. So how do I do this now?

---

### Post by bapoumba on 2007-10-06
<Tab> will get you to the ok button. Accept the java licence ;)

---

### Post by GavinZac on 2007-10-06
yes, you need to hit OK to make it install java.

its actually easier to do that bit if you do it in terminal with apt-get

---

