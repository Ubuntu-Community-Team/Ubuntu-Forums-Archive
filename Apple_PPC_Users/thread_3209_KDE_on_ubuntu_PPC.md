---
title: "KDE on ubuntu PPC"
date: 2004-11-04
forum: Apple PPC Users
---

### Post by sgiunchi on 2004-11-04
This is my /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

I did apt-get update, then

root@iMac01:/etc/apt # apt-get install kde
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: quanta but it is not installable
E: Broken packages


Has anybody installed KDE successfully?

Stefano Giunchi

---

### Post by TekMate on 2004-11-04
[QUOTE=sgiunchi]This is my /etc/apt/sources.list

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) warty main restricted universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) warty-security main restricted

I did apt-get update, then

root@iMac01:/etc/apt # apt-get install kde
Reading Package Lists... Done
Building Dependency Tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  kde: Depends: kde-core but it is not going to be installed
       Depends: kde-amusements but it is not going to be installed
       Depends: kdeaddons but it is not going to be installed
       Depends: kdeadmin but it is not going to be installed
       Depends: kdeartwork but it is not going to be installed
       Depends: kdegraphics but it is not going to be installed
       Depends: kdemultimedia but it is not going to be installed
       Depends: kdenetwork but it is not going to be installed
       Depends: kdepim but it is not going to be installed
       Depends: kdeutils but it is not going to be installed
       Depends: quanta but it is not installable
E: Broken packages


Has anybody installed KDE successfully?

Stefano Giunchi[/QUOTE]
 I'm getting the same thing I can't instll any KDE apps.

---

### Post by Down8ve on 2004-11-04
We are all in the same place.  I dare not go for YDL 4.0 just for KDE after the lukewarm reception it is receiving, but I miss some of my favorite apps.

Perhaps the KDE packages will be fixed in an upcoming Hoary release.

DSM

---

### Post by moly82 on 2004-11-09
i was able to install kde on ubuntu, just inserting the debian sid repositories inside /eta/apt/sources.list

then apt-get install kdebase

it works fine here, then you can also remove the above-mentioned repositories if you like  

ciao!

---

### Post by malmjako on 2004-11-16
I have KDE 3.3.0 installed and it's working fine. I'm not sure which repositories it was fetched from, but I had Debian main, unstable, testing and contrib selected, I think. (Not in Ubuntu just now...)

--
Jakob Malm

---

### Post by Viro on 2004-11-17
[QUOTE=moly82]i was able to install kde on ubuntu, just inserting the debian sid repositories inside /eta/apt/sources.list

then apt-get install kdebase

it works fine here, then you can also remove the above-mentioned repositories if you like  

ciao![/QUOTE]
 Where are the sid repositories?

---

### Post by malmjako on 2004-11-17
The following is my /etc/apt/sources.list file. I think testing is the same as SID.

```
deb http://archive.ubuntu.com/ubuntu/ warty main restricted 
deb-src http://archive.ubuntu.com/ubuntu/ warty main restricted 

deb http://archive.ubuntu.com/ubuntu/ warty universe 
deb-src http://archive.ubuntu.com/ubuntu/ warty universe 
# deb http://ftp.tux.org/pub/java/debian/ woody non-free  
deb http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb-src http://security.ubuntu.com/ubuntu/ warty-security main restricted 
deb http://archive.ubuntu.com/ubuntu/ warty multiverse 
deb http://security.ubuntu.com/ubuntu/ warty multiverse 

deb http://http.us.debian.org/debian/ stable main contrib non-free 
deb http://non-us.debian.org/debian-non-US/ stable/non-US main contrib non-free  

deb http://http.us.debian.org/debian/ unstable main contrib non-free  
deb http://non-us.debian.org/debian-non-US/ unstable/non-US main contrib non-free  

deb http://http.us.debian.org/debian/ testing main contrib non-free   
deb http://non-us.debian.org/debian-non-US/ testing/non-US main contrib non-free
```

---

### Post by trash on 2004-11-18
[QUOTE=Down8ve]We are all in the same place.  I dare not go for YDL 4.0 just for KDE after the lukewarm reception it is receiving, but I miss some of my favorite apps.

Perhaps the KDE packages will be fixed in an upcoming Hoary release.

DSM[/QUOTE]

I still run YDL on two machines, but since I have seen what Ubuntu has done on a one cd install, i'm not really sure YDL is the right choice for a simple desktop.  Ubuntu install finished and i was up and runniing with usb printer and usb webcam working, whereas in YDL3.01 i never managed to get either of them working. I still find KDE to slow and bloated for my taste, but I'm curious about what apps you guys miss?

---

### Post by sumanjay on 2004-11-18
I'm just praying that Terrasoft condescend to releasing YDL 4.0 iso's for download soon. I've been a bit of a distro-hopper, but YDL has been my first love and will remain so. I guess what I'm really salivating over is Xorg's composite extensions in YDL 4.0. Hoary's supposed to have Xorg, but it isn't coming out till April, while YDL came out a coupla months ago.

---

### Post by trash on 2004-11-18
I thought I read in the Ubuntu announcment forum that Xorg is available?? I don't pay much attention to anything screen related cuz my g4 is using a really old mac monitor with one resolution 832x624

---

### Post by sumanjay on 2004-11-19
Xorg is available if you add the Hoary repositories to your source.list file. And since that's still testing, I'd rather stay with Warty stable. Xorg runs beautifully on Gentoo, so we really ought to have it as an option. But I suppose more testing won't hurt.  :-)

---

### Post by paulproteus on 2004-11-21
[QUOTE=malmjako]The following is my /etc/apt/sources.list file. I think testing is the same as SID.[/QUOTE]

Testing is actually Sarge.  [http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/) has the straightforward explanation of the release.

---

### Post by malmjako on 2004-11-22
> Testing is actually Sarge. [http://www.debian.org/releases/testing/](http://www.debian.org/releases/testing/) has the straightforward explanation of the release.

Ok. I was a bit confused... Then unstable would be Sid, right?

---

### Post by M4VE on 2005-12-26
I know this thread is as old as dirt, but just to clear up, Sarge is not Testing...  Sarge is Stable, Etch is testing, and Sid is Unstable(Still In Developement)  Just editing the thread so that people that come across it know the difference before they continue googling.

---

