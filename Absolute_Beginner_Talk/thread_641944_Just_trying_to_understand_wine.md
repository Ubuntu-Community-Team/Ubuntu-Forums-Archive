---
title: "Just trying to understand wine"
date: 2007-12-16
forum: Absolute Beginner Talk
---

### Post by TriadDraykin on 2007-12-16
I'm not quite looking to get any specific program to work through Wine, just get it working... As I understand it, Wine is a way to get most .exe files working... Beyond this site, a lot of sites are, understandably, too complex for me to currently understand. I'm GREAT with Windows, but I know that doesn't really mean jack when it comes to linux. 
Something I'd really love is a person or database where i can find out what i'm doing when i blindly enter commands in the terminal... I hate doing what i'm told and not knowing what i'm doing. :)
Anyways, i got this message when following the instructions at [http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages

/\/\/\/\/\/\/\/\/\/\/\
So, it would appear that Wine didn't install properly... Then i realized i have real knowlege of even how to test such a thing... Any help would be greatly appreciated, and thank you so much for volunteering the information if you do. I hope to become good enough at this that one day I can return the favor to the Linux community.

---

### Post by Bothered on 2007-12-16
Which version of ubuntu are you using? Dapper/Edgy/Feisty/Gutsy?

Could you type the following in a terminal and post the results:

```
cat /etc/apt/sources.list
```

It will display the software repositories used by your package manager.

---

### Post by TriadDraykin on 2007-12-16
```
triad@triad-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
triad@triad-laptop:~$ 
```

I believe I'm working on Gutsy. I used the latest download.

---

### Post by LCDR_Kahuna on 2007-12-16
I am in the same boat! I said F windows last night and now I am kinda stuck with the basic linux programs so far. I have been spoiled by easy 1 click installs! 

I dont know why I like linux more then windows, I dont know how to do jack but yet I still like it more. Strange...

Ubuntu-Gutsy

---

### Post by TriadDraykin on 2007-12-16
> **LCDR_Kahuna said:**
> I am in the same boat! I said F windows last night and now I am kinda stuck with the basic linux programs so far. I have been spoiled by easy 1 click installs! 

I dont know why I like linux more then windows, I dont know how to do jack but yet I still like it more. Strange...

Ubuntu-Gutsy

It's because it hold promise for something better. :) But if there's a next time, i'd suggest a dual-boot.

---

### Post by LCDR_Kahuna on 2007-12-16
I duel boot on my pc(but never use linux), linux is full on my laptop, I have an xfi sound card on desktop so I cant use linux on that.

dont use laptop for gaming, so no huge thing. I am using what ubuntu came with and am happy. (pidgin, firefox) all i had to do was get the flash plugin!

I just need to get filezilla set up and i am golden! 

and yeah, I dont pay for anything software wise anyway, so y not go legit and use an open source OS? with open source programs?

w/e, off to bed:grin:

---

### Post by popch on 2007-12-16
For Ubuntu users I would suggest that they use the menu Applications -> Add/Remove to install Wine. That may not fetch the most recent version but it should install it in a way that will work in Ubuntu Linux.

Once it is installed, you do not run an application called 'Wine'. Wine just sits in your Linux environment and makes it possible to run applications designed for Windows. 

Most Windows applications require that you install them before you can run them. This is true in Windows. It is also true in Linux with Wine.

---

### Post by PmDematagoda on 2007-12-16
You sources.list file is not correct. Go to Software Sources in System>Administration>Software Sources and enable all the repositories in the Software tab, and all except the pre-released updates in the Updates tab. Reload the sources list as said. After that is done your problem should be solved.

---

### Post by TriadDraykin on 2007-12-16
> **PmDematagoda said:**
> You sources.list file is not correct. Go to Software Sources in System>Administration>Software Sources and enable all the repositories in the Software tab, and all except the pre-released updates in the Updates tab. Reload the sources list as said. After that is done your problem should be solved.

You're right, it took care of it just fine! i also got Wine running, I can't believe i didn't think of just installing it from the Add/remove... Still a newb, after all... But the program i used to test it out doesn't seem to work, an installation program for an IRC client... I'm trying to connect to a text-based IRC channel called muck.furry.com, and the only client i know of, BeipMU, runs exclusively in windows... Any suggestions? I'll do research on my own, of course, but I figure i'll also drop a question here in case ya'll know where one might be already.

---

### Post by PmDematagoda on 2007-12-16
Give XChat a try, it can be installed using:-

```
sudo apt-get install xchat
```

and can also be found in Add/Remove.

---

### Post by popch on 2007-12-16
Not to question your decision, but have you tested yet the IRC clients supplied  or installable with Ubuntu Linux? I am not interested in IRC, but I think I have seen several of those clients in the installation menus.

---

### Post by Bothered on 2007-12-16
Pidgin can be used for IRC (part of the standard Ubuntu install).

---

### Post by candtalan on 2007-12-16
> **TriadDraykin said:**
>  I can't believe i didn't think of just installing it from the Add/remove...   Maybe you had heard that Linux was going to be 'trouble' or 'inconvenient'? Maybe you can help spread the word that installing programs can be unbelievably easy. The Repositories have countless programs and packages, and they can all be installed with a mouse click or so.
:-)

---

### Post by LCDR_Kahuna on 2007-12-16
wow, something so simple as install.

linux owns all

---

