---
title: "So hey wine problem here"
date: 2007-11-12
forum: Absolute Beginner Talk
---

### Post by Heaf on 2007-11-12
E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list


So this comes up in terminal when i try to do something. I cant even update  this. :mad:

---

### Post by Maestro23 on 2007-11-12
> **Heaf said:**
> E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list


So this comes up in terminal when i try to do something. I cant even update  this. :mad:

Post your /etc/apt/sources.list

> cat /etc/apt/sources.list

Edit: Thanks twice. Read it wrong.

---

### Post by twiceasworn on 2007-11-12
Actually post your winehq.list, since that is the file with the issue.  Did you edit this at any point?

---

### Post by Heaf on 2007-11-12
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"

i think this is the problem  cos im using gusty ?

---

### Post by Maestro23 on 2007-11-12
> **Heaf said:**
> deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"
deb-src [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) feisty main #WineHQ - Ubuntu 7.04 "Feisty Fawn"

i think this is the problem  cos im using gusty ?

Comment out those two lines with #'s in front of deb and deb-src.  Then:

> sudo apt-get update && sudo apt-get upgrade

*To edit the file:

> gksudo gedit /etc/apt/sources.list

*Then you can always go and add the Gutsy Repository for Wine: [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
or do as the other 2 have suggested, as I have never used wine.  Just trying to help you with your sources.lsit.

---

### Post by g2g591 on 2007-11-12
I'd recommend not putting #s infront of those lines (if you want the new versions of wine), post "cat /etc/apt/sources.list.d/winehq.list"

---

### Post by Heaf on 2007-11-12
what the hell  ](*,) 
  i dont get this

---

### Post by Maestro23 on 2007-11-12
> **Heaf said:**
> what the hell  ](*,) 
  i dont get this

Where are you having problems?

---

### Post by Heaf on 2007-11-12
so i installed wine and then i just installed steam it worked fine. now wine dont work i cant uninstall it and i cant even use update manager, synaptic manager etc.

---

### Post by Maestro23 on 2007-11-12
> **Heaf said:**
> so i installed wine and then i just installed steam it worked fine. now wine dont work i cant uninstall it and i cant even use update manager, synaptic manager etc.

What errors are you getting when trying Synaptic, update manager?

---

### Post by Heaf on 2007-11-12
at update manager comes red mark and close window and synaptic 

E: Type &#8216;<!DOCTYPE&#8217; is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

that wine hq is ghosting allover

---

### Post by FuturePilot on 2007-11-12
Have you tried ```
gksudo gedit /etc/apt/sources.list.d/winehq.list
```
Just put a # in front of the two lines for now.
Then run
```
sudo apt-get update
```

---

### Post by Heaf on 2007-11-12
> <!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 3.2 Final//EN">
<html>
 <head>
  <title>Index of /apt/sources.list.d</title>
 </head>
 <body>
<h1>Index of /apt/sources.list.d</h1>
<pre><img src="/icons/blank.gif" alt="Icon "> <a href="?C=N;O=D">Name</a>                    <a href="?C=M;O=A">Last modified</a>      <a href="?C=S;O=A">Size</a>  <a href="?C=D;O=A">Description</a><hr><img src="/icons/back.gif" alt="[DIR]"> <a href="/apt/">Parent Directory</a>                             -   
<img src="/icons/unknown.gif" alt="[   ]"> <a href="dapper.list">dapper.list</a>             18-Jan-2007 22:17  151   
<img src="/icons/unknown.gif" alt="[   ]"> <a href="edgy.list">edgy.list</a>               18-Jan-2007 22:17  139   
<img src="/icons/unknown.gif" alt="[   ]"> <a href="etch.list">etch.list</a>               26-May-2007 21:49  160   
<img src="/icons/unknown.gif" alt="[   ]"> <a href="feisty.list">feisty.list</a>             26-May-2007 21:47  181   
<img src="/icons/unknown.gif" alt="[   ]"> <a href="gutsy.list">gutsy.list</a>              17-Oct-2007 00:21  181   
<hr></pre>
<address>Apache/2.0.55 (Ubuntu) Server at wine.budgetdedicated.com Port 80</address>
</body></html>

this looks strange =D html code

---

### Post by FuturePilot on 2007-11-12
I'm taking it that that is your winehq.list. If that's the case it looks like it's borked.
So try deleting everything in that file and then add these lines
```
deb http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
deb-src http://wine.budgetdedicated.com/apt gutsy main #WineHQ - Ubuntu 7.10 "Gutsy Gibbon"
```
Then run ```
sudo apt-get update
```

---

### Post by Heaf on 2007-11-12
> W: GPG error: [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 58403026387EE263
W: You may want to run apt-get update to correct these problems


bloody hell

---

### Post by icechen1 on 2007-11-12
> **Heaf said:**
> bloody hell

1st,remove that html code
second go to system>admin.>software source and remove  [http://wine.budgetdedicated.com](http://wine.budgetdedicated.com) gutsy Release **in Security**

---

### Post by FuturePilot on 2007-11-12
> **Heaf said:**
> bloody hell
Just do
```
wget -q http://wine.budgetdedicated.com/apt/387EE263.gpg -O- | sudo apt-key add -
```
Then
```
sudo apt-get update
```
:)

---

### Post by Heaf on 2007-11-12
wooow now updatemagager works
 thanks for that  now im going to check  other thing in need to solve 
 can u say what was corrupted my system ?

---

### Post by FuturePilot on 2007-11-12
> **Heaf said:**
> wooow now updatemagager works
 thanks for that  now im going to check  other thing in need to solve 
 can u say what was corrupted my system ?

Yeah, something was wrong with your winehq.list. I'm not sure what happened there, but it was because of all the html stuff that was in there. Apt couldn't understand it. Glad you got it working.:)

---

### Post by Heaf on 2007-11-12
first I will uninstall that wine hell out of my computer and install it again and do it in right way 

 maby i can ask the best way to do it  from you ? :popcorn:

---

### Post by FuturePilot on 2007-11-12
Sure. you could probably just do 
```
sudo apt-get remove --purge wine
sudo apt-get install wine
```
:)

---

### Post by stchman on 2007-11-12
> **Heaf said:**
> E: Type ‘<!DOCTYPE’ is not known on line 1 in source list /etc/apt/sources.list.d/winehq.list


So this comes up in terminal when i try to do something. I cant even update  this. :mad:

Follow my tutorial on installing WINE and IE6 (optional) on Ubuntu.  It covers Gutsy as well.

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

WINE is now in the Gutsy repos, but you can add WINE to the repos as well.

---

### Post by Heaf on 2007-11-13
so hey guys thanks for help :mrgreen: maby i can e-mail to you or post here if i get again something wierd

---

