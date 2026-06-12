---
title: "How do I update Ubuntu ?"
date: 2005-07-06
forum: Absolute Beginner Talk
---

### Post by weasel fierce on 2005-07-06
Are there any easy ways, through synaptic or apt-get, to upgrade the basic ubuntu files and such ?

Or will it prompt me automatically when new things are available or fixed ?

---

### Post by Bl0wn2b1ts on 2005-07-06
Hi,

If you go into System/Administration/Ubuntu Update Manager

then click preferences and select the repository and click settings

I think everything you need is in there!

hope this helps

Bl0wn2b1ts

---

### Post by codejunkie on 2005-07-06
it should automaticly remind you when updates are avaliable thru the update manager you can easily update all the packages on your system at any time by opening a terminal and type 
```

sudo apt-get update
```
then 
```

sudo apt-get dist-upgrade

```
or by opening synaptic click Reload then Mark All Upgrades then click Smart Upgrade and then apply.

---

### Post by doc_holiday on 2005-07-06
Looking for apt-get dist-upgrade ?
Then you also need to change your sources.list

---

### Post by XDevHald on 2005-07-06
[QUOTE=doc_holiday]Looking for apt-get dist-upgrade ?
Then you also need to change your sources.list[/QUOTE]

Since you're wanting to just UPDATE your desktop, then do apt-get -f update, if you're wanting to UPGRADE then do the following listed below.

Open a Terminal Window and Type:
 > **gedit /etc/apt/sources.list**

Then remove either hoary or warty, whichever one you're using and rename it to breezy. Now if you're upgrading from warty to hoary then you will type hoary where warty is sitting at in the sources.list

Example:
 > deb [http://us.archive.ubuntu.com/ubuntu]("http://us.archive.ubuntu.com/ubuntu") **hoary**-updates main restricted
change the dist that you're using to the newer upgrade that you wish to use.

---

### Post by ozzie123 on 2005-07-06
[QUOTE=BB]Since you're wanting to just UPDATE your desktop, then do apt-get -f update, if you're wanting to UPGRADE then do the following listed below.

Open a Terminal Window and Type:
 

Then remove either hoary or warty, whichever one you're using and rename it to breezy. Now if you're upgrading from warty to hoary then you will type hoary where warty is sitting at in the sources.list

Example:
 
change the dist that you're using to the newer upgrade that you wish to use.[/QUOTE]
 I prefer using Synaptic because its ease of use rather than a command line of apt-get.

---

### Post by XDevHald on 2005-07-06
[QUOTE=ozzie123]I prefer using Synaptic because its ease of use rather than a command line of apt-get.[/QUOTE]
 Hmm, well if you think that not being able to force the package to install is great then yes, but if you find yourself wanting to just update and get errors, then feel free with Synaptic, but either way you look at it, the packages are going to need a -f to make it happen ;)

---

### Post by Kvark on 2005-07-06
I think what weasel fierce wants is the notification icon that appears in the panel when there is a newer version of any of your programs. Just click the icon when you notice it has appeared, look at the list of updates for a secound, and click ok.

Don't upgrade to breezy yet (unless you are very curious and can accept some problems), wait until it is stable.

---

### Post by served on 2005-07-07
i cant upgrade pcs i dunno why console speaks for it selve
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Packages
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Packages [91.4kB]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/main Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [102B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) warty/restricted Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Packages
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [108B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Sources [20.3kB]
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/main Release [104B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Sources
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) warty-security/restricted Release [110B]
Err [ftp://ubuntujava.yimports.com](ftp://ubuntujava.yimports.com) binary/ Packages
  PASS failed, server said: Login incorrect.
Err [ftp://ubuntujava.yimports.com](ftp://ubuntujava.yimports.com) binary/ Release
  PASS failed, server said: Login incorrect.
Err [ftp://ubuntujava.yimports.com](ftp://ubuntujava.yimports.com) source/ Sources
  PASS failed, server said: Login incorrect.
Err [ftp://ubuntujava.yimports.com](ftp://ubuntujava.yimports.com) source/ Release
  PASS failed, server said: Login incorrect.
Fetched 112kB in 6s (18.2kB/s)
Failed to fetch [ftp://ubuntujava.yimports.com/binary/Packages.gz](ftp://ubuntujava.yimports.com/binary/Packages.gz)  PASS failed, server said: Login incorrect.
Failed to fetch [ftp://ubuntujava.yimports.com/binary/Release](ftp://ubuntujava.yimports.com/binary/Release)  PASS failed, server said: Login incorrect.
Failed to fetch [ftp://ubuntujava.yimports.com/source/Sources.gz](ftp://ubuntujava.yimports.com/source/Sources.gz)  PASS failed, server said: Login incorrect.
Failed to fetch [ftp://ubuntujava.yimports.com/source/Release](ftp://ubuntujava.yimports.com/source/Release)  PASS failed, server said: Login incorrect.
Reading Package Lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by poofyhairguy on 2005-07-07
Please do this:

> gedit /etc/apt/sources.list

and then post its content here and I'll edit it to be correct.

---

