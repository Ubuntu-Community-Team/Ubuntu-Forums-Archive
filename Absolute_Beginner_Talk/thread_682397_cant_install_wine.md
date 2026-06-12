---
title: "cant install wine"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by Jmejme on 2008-01-30
ok heres my problem. i tried
```
sudo apt-get install wine
```

and this is what i got

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package wine

```



I looked in synaptic and add/remove programs and nothing there... Any ideas???

---

### Post by jaytek13 on 2008-01-30
Wine has it's own source that is not by default in the synaptic sources list. To add this, in a terminal:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

sudo apt-get install wine


Then you should be set.

This information is available at [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

---

### Post by RomeReactor on 2008-01-30
Hi. Have you installed other packages before? If you haven't been able to install other programs, you might need to enable the software sources. Please open a terminal (Applications->Accessories->Terminal) and write or paste:
```
cat /etc/apt/sources.list
```
Press ENTER, and post the output.

---

### Post by JoshuaRL on 2008-01-30
That's the best way in my book.  The one in the repos is out of date, and with an ongoing app like Wine you're always better with the newest version.  But it should be in the repos.

Could you post the output of:

```

gedit /etc/apt/sources.list

```

I think your sources might be broken.

---

### Post by Jmejme on 2008-01-30
> **jaytek13 said:**
> Wine has it's own source that is not by default in the synaptic sources list. To add this, in a terminal:

wget -q [http://wine.budgetdedicated.com/apt/387EE263.gpg](http://wine.budgetdedicated.com/apt/387EE263.gpg) -O- | sudo apt-key add -

sudo wget [http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list](http://wine.budgetdedicated.com/apt/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/winehq.list

sudo apt-get update

sudo apt-get install wine


Then you should be set.

This information is available at [http://winehq.org/site/download-deb](http://winehq.org/site/download-deb)

This is what i got...?
 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
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

```

---

### Post by Jmejme on 2008-01-30
put this

```
gedit /etc/apt/sources.list
```

got this

```
(gedit:15180): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

```

---

### Post by RomeReactor on 2008-01-30
> (gedit:15180): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

That's a common warning when launching Gedit from the terminal; please post the rest of the output, or run this:
```
cat /etc/apt/sources.list
```
and post the output.

---

### Post by Jmejme on 2008-01-30
Its alot but you asked lol hope this helps Please and Thankyou

```
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

```

---

### Post by Jmejme on 2008-01-30
should i assume this as awkward silence. lol jk just makin sure no one forgot about me lol

---

### Post by JoshuaRL on 2008-01-30
Nope, this is not that big of a problem.  See every line that says something like

> 
#deb [http://aplaceontheinternetwherepackagesare.org](http://aplaceontheinternetwherepackagesare.org)


Those are your sources for updates and upgrades.  

First, close that and run:
```

gksu gedit /etc/apt/sources.list

```
It'll look the same but it'll allow you to edit that file from gedit.  You want to do that.  Take the # out from the beginning of every line that starts with "deb".  Then update your system and try the steps lined out in post #2.  Your sources.list should look something like this:

> 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
 deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


Sorry for the wait, had to go home from work and get on my computer.  :)

---

### Post by Jmejme on 2008-01-30
so once i take it out of the sources file...do i just save it run it in terminal...or what thank you btw for helping

---

### Post by JoshuaRL on 2008-01-30
Not a problem.

Yes.  You would want to save it, and when it asks you if you want to overwrite the file, you would chose yes.  Then run update manager!  After you install over 100 updates, (Just a guess, that's what it was for me) then try those steps to get Wine.

---

### Post by Jmejme on 2008-01-30
lmao yeah 78 updates or somethin and 186 packets... WOW Thank you verry much ill post if wine works as soon as the 186 packets are done dl

---

### Post by JoshuaRL on 2008-01-30
Cool dude.  Yeah, after that gets done the instructions to install Wine should work.

---

### Post by RomeReactor on 2008-01-30
Just as a side note: it's not necessary to edit the sources.list file by hand; you can enable the sources by going to 'System->Administration->Software Sources' and on the first tab (Ubuntu Software) check the boxes for the first four repositories, except 'Source'. You'll be prompted to reload the package information, so press the 'Reload' button. Or you can enable the sources directly from Synaptic, the package manager; open Synaptic (System->Administration->Synaptic), go to 'Edit->Preferences', and on the same first tab check the same boxes. Close that window and, still in Synaptic, press the blue 'Reload' button. Afterwards the software sources are enabled.

Your software sources were disabled most likely due to performing the installation without access to the internet.

---

### Post by JoshuaRL on 2008-01-30
You're right.  I should start telling people that.  

It's just easier when you're helping people to use the terminal.

---

### Post by RomeReactor on 2008-01-30
> **JoshuaRL said:**
> You're right.  I should start telling people that.  

It's just easier when you're helping people to use the terminal.

It *is* faster and easier for people who are used to the terminal or editing configuration files--like you or I might be--but others might prefer a graphical interface for that. In any case, either way will yield the same result.

---

### Post by Xabora on 2008-01-31
> **JoshuaRL said:**
> Nope, this is not that big of a problem.  See every line that says something like



Those are your sources for updates and upgrades.  

First, close that and run:
```

gksu gedit /etc/apt/sources.list

```
It'll look the same but it'll allow you to edit that file from gedit.  You want to do that.  Take the # out from the beginning of every line that starts with "deb".  Then update your system and try the steps lined out in post #2.  Your sources.list should look something like this:



Sorry for the wait, had to go home from work and get on my computer.  :)

Kinda popped in to see if I had a similar issue and it was the EXACT same issue.
Installed via a RT61 Network card and had all sorts of issues.

---

### Post by Jmejme on 2008-02-01
btw it worked perfectly thanks!!!

---

### Post by JoshuaRL on 2008-02-01
Cool!  You might think about going to the top of the thread and the menu Thread Tools.  From there you can mark this as solved.

---

