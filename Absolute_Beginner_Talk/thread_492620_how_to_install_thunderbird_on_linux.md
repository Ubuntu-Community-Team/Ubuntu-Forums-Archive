---
title: "how to install thunderbird on linux"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Ehaic on 2007-07-04
hello, I just now got linux installed (YAY ME!)  and I want to install a few apps my friends suggested, but I havent got the hang of installing things manually yet :( can anyone give me a hand?  I also eed to know how to make a shortut for the app lol.

---

### Post by Vajra Vrtti on 2007-07-04
The first place to look for a desired application is **Add/Remove...** in the application menu.
You will find Thunderbird there, in the *Internet* folder. Just mark it and it will be installed.

---

### Post by steveneddy on 2007-07-05
How about

```
sudo apt-get install mozilla-thunderbird
```

EDIT - THANKS - MISSED THAT ONE.

---

### Post by alienexplorers on 2007-07-05
What version of Thunderbird did you download.

---

### Post by Vajra Vrtti on 2007-07-05
Since Ehaic is new to Linux, I was trying to show him not just how to install Thunderbird but also where to *look for* new ones when he needs. 

Anyway, the name of the package is **mozilla-thunderbird**.

---

### Post by davidjmayo on 2007-07-05
> The first place to look for a desired application is Add/Remove... in the application menu.
You will find Thunderbird there, in the Internet folder. Just mark it and it will be installed.


Also you need to click apply 

The icon will be created in applications==>Internet

---

### Post by mjwhitfield on 2007-07-05
I'm only seeing Thunderbird 1.5, where's the shiny new 2.0 version hidden?

---

### Post by moredhel on 2007-07-05
It won't be in the official repos until october, with the new release. However, you can get a .deb for it probably on the web. Infact, I remember finding a script on these very forums that got 2 for you. Try googling thunderbird for ubuntu in google or something ;)

Though I would personally recommend tying evolution. I used to use thunderbird on windows, and so used it in linux, but after trying evolution, I preferred its far tighter intergration with ubuntu (or more correctly, with gnome). It has all the features from thunderbird that the majority of people need anyway.

---

### Post by mjwhitfield on 2007-07-05
Why the wait till October? I thought the repo's were updated continuously? sorry if i'm asking stupid questions!

---

### Post by moredhel on 2007-07-05
I ask the same questions ;)

I don't know why, I think there is an ubuntu policy of no upgrade except security ones. So they are staying at 1.5 but updating to 1.5.12. It's a good principle I guess, but perhaps having a team to do an extra repository with all the latest would be good :) In the mean time you have to either wait or just look for .debs online, which is what I do :)

---

### Post by mjwhitfield on 2007-07-05
oki dokie.  It doesn't bother me that much I guess.

---

### Post by Vajra Vrtti on 2007-07-05
You can find new versions of applications in the **backports** **repositories.**

> **Ubuntu backports project**
The Ubuntu backports project provides packages from the development version, built for the latest stable release. This way you can mix stability with being on the bleeding edge. This repository is an official one, but should be used with care and only if you know what you are doing.

To enable the backports repositories edit */etc/apt/sources.list* and uncomment them in the proper lines:

> ## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

---

### Post by mjwhitfield on 2007-07-05
You're a legend, thanks mate.

---

### Post by stchman on 2007-07-05
> **steveneddy said:**
> How about

```
sudo apt-get install thunderbird
```

Really, does not get any easier than that.  Windows you would have to go get the installer from Mozilla first.

---

### Post by kittyhawk63 on 2007-07-05
I have found that installing Automatix2 off the Internet for my Linux Ubuntu version gave me the most recent Thunderbird. It is Thunderbird 2.0.0.4
I don't think there is a newer version.
kh

---

### Post by davidjmayo on 2007-07-06
See 3.1 Installation

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird)

This will install Thunderbird 2.0.0.4

---

### Post by kittyhawk63 on 2007-07-06
> **davidjmayo said:**
> See 3.1 Installation

[http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird](http://pykeylogger.sourceforge.net/wiki/index.php/Ubuntuzilla#Update_Official_Mozilla_Build_of_Thunderbird)

This will install Thunderbird 2.0.0.4

Thanks for this link. I will follow it next time.
kh

---

### Post by macogw on 2007-07-06
> **moredhel said:**
> I ask the same questions ;)

I don't know why, I think there is an ubuntu policy of no upgrade except security ones. So they are staying at 1.5 but updating to 1.5.12. It's a good principle I guess, but perhaps having a team to do an extra repository with all the latest would be good :) In the mean time you have to either wait or just look for .debs online, which is what I do :)

It's for stability. When you add new programs and new features, you are adding more bugs (since no software is without bugs).  Bugs make things crash or insecure, so this way you don't get that problem.  6 months isn't too bad. Debian only marks their distro as stable when it is *really* stable (less than 200 bugs or some number like that), which means it's usually a year or two between releases.

---

