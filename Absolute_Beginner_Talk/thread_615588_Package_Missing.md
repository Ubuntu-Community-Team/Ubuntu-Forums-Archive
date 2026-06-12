---
title: "Package Missing"
date: 2007-11-17
forum: Absolute Beginner Talk
---

### Post by bern1939 on 2007-11-17
Hello again...

Just got Ubuntu 7.10 up & running.
Wanted to use it in the main to run Latex.

All the tex files available are loaded i.e.
tex-common
texlive-base
texlive-base-bin
texlive-common
texlive-doc-base
texlive-fonts-recommended

However when I latex a .tex file I get the following:
The program 'latex' is currently not installed.  You can install it by typing:
sudo apt-get install texlive-latex-base
bash: latex: command not found

So I do as instructed and get:


Reading package lists... Done

Building dependency tree       

Reading state information... Done

Package texlive-latex-base is not available, but is referred to by another package.

This may mean that the package is missing, has been obsoleted, or

is only available from another source

E: Package texlive-latex-base has no installation candidate


Q. [B]Where do I get the texlive-latex-base package from please?
[/B]
Thanks

Bern

---

### Post by wooster on 2007-11-17
The package appears to be in gutsy ([http://packages.ubuntu.com/gutsy/tex/texlive-latex-base](http://packages.ubuntu.com/gutsy/tex/texlive-latex-base))

I'm not sure why you aren't getting it. I ran sudo apt-get install texlive-latex-base and it worked perfectly fine.  You can try running sudo apt-get update then rerunning the command to install texlive-latex-base. if that doesn't work try showing us what is in the file /etc/apt/sources.list and we check out why it's not showing up. 

run this command to view the file and paste what it says.
sudo gedit /etc/apt/sources.list

---

### Post by bern1939 on 2007-11-17
Thanks.

[B]Yes when I installed the distro earlier I did get the following msg:
[/B]
“The security updates on security.ubuntu.com couldn't be accessed so those updates will not be available to you at this time. You should investigate later.
Commented out entries for security.ubuntu.com have been added to the etc/apt/source.list file”

[B]So I then did as you suggest and this is the result:
[/B]
“deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to

# newer versions of the distribution.



# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy main restricted



## Major bug fix updates produced after the final release of the

## distribution.

# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu

## team, and may not be under a free licence. Please satisfy yourself as to

## your rights to use the software. Also, please note that software in

## universe WILL NOT receive any review or updates from the Ubuntu security

## team.

# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy universe

# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates universe



## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 

## team, and may not be under a free licence. Please satisfy yourself as to 

## your rights to use the software. Also, please note that software in 

## multiverse WILL NOT receive any review or updates from the Ubuntu

## security team.

# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy multiverse

# Line commented out by installer because it failed to verify:

#deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

# Line commented out by installer because it failed to verify:

#deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse



## Uncomment the following two lines to add software from the 'backports'

## repository.

## N.B. software from this repository may not have been tested as

## extensively as that contained in the main release, although it includes

## newer versions of some applications which may provide useful features.

## Also, please note that software in backports WILL NOT receive any review

## or updates from the Ubuntu security team.

# deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

# deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse



## Uncomment the following two lines to add software from Canonical's

## 'partner' repository. This software is not part of Ubuntu, but is

## offered by Canonical and the respective vendors as a service to Ubuntu

## users.

# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
”

[B]Obviously there is a connection here.
What do you suggest I do now please.

Many thanks for your assistance.

Bern[/B]

---

### Post by 1337455 10534 on 2007-11-17
Every line in this list is commented out, or unable to be read by the Update Manager.
Or anything else for that matter.

Remove "deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted" and remove the "#"s from the begining of **all entries beginning with deb**.

Then, do a sudo apt-get update.
Then install the package from wherever. I suggest the website though, it's always more reliable then depending on apt's fetching skillz.

---

### Post by bern1939 on 2007-11-17
Thanks for that....I see that the file **_sources.list.save _**is the one I need to change as suggested.
However I need to change the permissions to do that and can't figure how to do that...
Right-clicking on the file and going to Properties & Permissions shows all possible boxes _greyed out_.

Presume there must be a command to change the permissions to owner.
Would you advise me please.
Many thanks

Bern

---

### Post by bern1939 on 2007-11-17
Sorry about previous posting.... I figured it out via the Terminal.
Am now proceeding to next stage.


Thanks


Bern

---

### Post by 1337455 10534 on 2007-11-18
Rite, so:
```

gksudo gedit /etc/apt/sources.list.save

```

---

### Post by bern1939 on 2007-11-18
Thanks worked very well. Thanks again


Bern

---

