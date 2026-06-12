---
title: "Add/remove not working properly"
date: 2007-10-07
forum: Absolute Beginner Talk
---

### Post by tarunkool on 2007-10-07
hi everyone out there. i am absolutely new to UBUNTU 7.04 linux.  so please help me out solving the following issue.
whenever i try to update any software through add/remove applications each time it fails to download anything even though my internet connection is working.
i am also attaching a screen shot with this post.

i also tried to update from terminal using the command
sudo apt-get update

but it was also of no use.
bcoz of this problem neither i am able to get updates nor am able to install any new softwares.
please help me as soon as possible.

---

### Post by PmDematagoda on 2007-10-07
Please post everything you see when you open up the sources.list file using:-
```

sudo gedit /etc/apt/sources.list
```

---

### Post by tarunkool on 2007-10-07
this what is written in sources.list


# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security main restricted
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security universe
deb [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse
deb-src [http://in.archive.ubuntu.com/ubuntu/](http://in.archive.ubuntu.com/ubuntu/) feisty-security multiverse



hope it serves your purpose

---

### Post by overdrank on 2007-10-07
Your source list looks ok, and have you tried to change servers under software source's? You can do this under system, administration, software source and change the server and see if this helps. Good luck!

---

### Post by PmDematagoda on 2007-10-07
> **overdrank said:**
> Your source list looks ok, and have you tried to change servers under software source's? You can do this under system, administration, software source and change the server and see if this helps. Good luck!

No it doesn't overdrank.

For example what is ```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```?

---

### Post by tarunkool on 2007-10-07
i tried changing the server from india server to main server and then reloading the list
again almost all the updates status was "failed"

this is the error that is shown after this updating is done(although it failed)

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

---

### Post by overdrank on 2007-10-07
> **PmDematagoda said:**
> No it doesn't overdrank.

For example what is ```
deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```?

Hi and well it is ok (from my experience to have a cd for source) and that doesn't explain the errors. But the op could comment it out ( #) and see if makes a difference. 
On a side note, when ever I install from the alternate cd I have noticed that the cd is always listed in the source list and I just always remove it. :KS

---

### Post by PmDematagoda on 2007-10-07
I just used all of your repo addresses except :-
```

deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main restricted
```

And I didn't face any problems at all. Why don't you deactivate that address by typing # infront of it and try again.

---

### Post by tarunkool on 2007-10-07
i did as u said putting # infront of that line but nothing much  happened. again everthing showed the status of failed as usual

see the attachments
look the difference in 2 and 3rd attchment

in the third attachment it is written 

This application is provided by the Ubuntu community.
7zip cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

please help me!!

---

### Post by KIAaze on 2007-10-07
Similar problem: [http://ubuntuforums.org/showthread.php?t=427]("http://ubuntuforums.org/showthread.php?t=427")
Solution 1:
[QUOTE=alvin_voo]Hey, i believe i found the answer, juz simply change the http:// tag in your sources.list into [ftp://.](ftp://.)[/QUOTE]
Solution 2:
[QUOTE=ankursethi]I used to get a similar error, but I found 2 ways to correct them :

1. Get the proper GPG keys and add them into apt. For the freecontrib packages the method to import the key is -
Quote:
wget [http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg](http://packages.freecontrib.org/ubuntu/plf/12B83718.gpg) -O- | sudo apt-key add -
sudo apt-get update
Those of you who are using the default Ubuntu repos won't find it necessary to do this step.

2. Make sure the repos are alive and working. If not, comment them out.

Well, this is from a newbie so don't consider this to be the final answer.
[/QUOTE]

---

### Post by dptxp on 2007-10-07
> **tarunkool said:**
> i tried changing the server from india server to main server and then reloading the list
again almost all the updates status was "failed"

this is the error that is shown after this updating is done(although it failed)

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

India server does not work.
Try this:
Open Add/remove. Click on 'preferences' at bottom left. Choose optimal (or best) server. Ubuntu will select the right one.

---

