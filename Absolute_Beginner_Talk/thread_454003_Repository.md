---
title: "Repository"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by jeff09 on 2007-05-25
wHEN I AM CLICKING MY CHECK FOR UPDATES FOR MY UBUNTU I AM GETTING THIS ERROR

E: Type 'wget' is not known on line 22 in source list /etc/apt/source.list
E: Unable to lock the list directory

What should I do i am just beginning to learn ubuntu..pls help..tanx

---

### Post by irish_flu on 2007-05-25
Hmmm you're the second person I've seen in as many days with an error like that who wasn't sure where it came from.  Did you, by chance, try to install Automatix or Beryl (or something else you couldn't get from the "stock" repositories) before this started happening?

In any case, you want to remove the line in your sources.list file that starts with "wget".

in the terminal, type:
```

sudo gedit /etc/apt/sources.list

```

When the file opens up, find the line that starts with "wget" and either remove the line or put the # symbol in front of it (that's called "commenting it out", and in effect tells the file to ignore that line).

I'm not sure if it'll just work then, or if you'll have to restart.  Either way, you should be fine then.

---

### Post by STREETURCHINE on 2007-05-25
when opening graphical displays you should always use" gksudo"

  ```
gksudo gedit /etc/apt/sources.list
```

---

### Post by irish_flu on 2007-05-25
of course streeturchine is correct, I've been awake for many many hours.  :KS

---

### Post by jeff09 on 2007-05-25
Yes before this happen i try to install automatrix, then the updates just start to get blank and i am receiving this error.. to those who reply in my post thanx a lot

---

### Post by STREETURCHINE on 2007-05-25
copy and paste the output from 

```
cat /etc/apt/sources.list
```

and we will help sort it out

---

### Post by beatbros on 2007-05-25
> **STREETURCHINE said:**
> when opening graphical displays you should always use" gksudo"

  ```
gksudo gedit /etc/atp/sources.list
```

Just to who wants to cut & paste (atp#apt)

gksudo gedit /etc/apt/sources.list

---

### Post by quinnten83 on 2007-05-25
I also get this error.
And i have both Beryl and Automatix installed (was Automatix not a good idea, cause in the Dutch forum everybody was against it?)
What is the difference between gksudo and sudo? typing both still got me my sources.list opened.
Also I didn't find the wget entry. 

Plus I remember getting this error once while I was playing around with the live CD and tried to install beryl using add/ remove programs, but this could be unrelated.

---

### Post by hyper_ch on 2007-05-25
Generally it's not recommended to use Automatix... if during the automatix install something happens your sources.list can become corrupt and with regards to later upgrades Automatix can cause troubles then...

Well, just post the content of your sources.list.

---

### Post by STREETURCHINE on 2007-05-25
> **beatbros said:**
> Just to who wants to cut & paste (atp#apt)

gksudo gedit /etc/apt/sources.list

oops typo on my behalf..fixed it

---

### Post by STREETURCHINE on 2007-05-25
> **quinnten83 said:**
> I also get this error.
And i have both Beryl and Automatix installed (was Automatix not a good idea, cause in the Dutch forum everybody was against it?)
What is the difference between gksudo and sudo? typing both still got me my sources.list opened.
Also I didn't find the wget entry. 

Plus I remember getting this error once while I was playing around with the live CD and tried to install beryl using add/ remove programs, but this could be unrelated.

it is just that some people have a bee in there bonnett with automatix i have used it since  ubuntu breezy 5.10 and it has been no problem for me .
any problem with the sources.list is easily fixed:p

---

### Post by quinnten83 on 2007-05-25
Should I de-install Automatix then? I really don't need trouble later on (or at anytime for that matter).
So what IS the difference between gksudo and regular plain sudo?

Content of my sources.list:
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://nl.archive.ubuntu.com/ubuntu/](http://nl.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) feisty main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) feisty-security main restricted universe multiverse
#AUTOMATIX REPOS END

---

### Post by STREETURCHINE on 2007-05-25
well i dont actually see a problem with your source list.

i dont want to turn this into a automatix debate(i would keep it ,well i do have it  on three computers)
if you have concerns instead of just listening to what they say here go to the automatix forum and get the other side of the story.dont convicted without knowing the facts.there is a link to the automatix forums in my signature below

as to gksudo it is for all your graphical uses like gksudo gedit,or gksudo nautilus,
if you dont use it you can run into permission problems later on.

sudo gives you temporary super user privlages so you can install uninstall and stuff.

---

