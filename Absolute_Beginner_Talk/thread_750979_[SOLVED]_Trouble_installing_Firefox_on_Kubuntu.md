---
title: "[SOLVED] Trouble installing Firefox on Kubuntu"
date: 2008-04-10
forum: Absolute Beginner Talk
---

### Post by Oliver Closov on 2008-04-10
[I] Originally Posted by sidhusummer 
I am having trouble installing firefox as well. On running this command: apt-get install mozilla-firefox , I get the following:

"Reading package lists... Done
Building dependency tree... Done
Package mozilla-firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package mozilla-firefox has no installation candidate
"[/I]


I am having this exact same problem, however updating has not helped so far. Exact same problem when I tried to install Thunderbird. I have tried typing both sudo apt-get install mozilla-firefox AND sudo apt-get install firefox, just in case different distros have different protocols (which I imagine they do).
I am using Kubuntu 7.
I am a complete beginner who has previously relied on the "convenience" of the MS GUI world.
I went to the Mozilla webpage and found the Ubuntu install instructions which say to click on applications->add/remove programs->type in firefox->then click box, but it doesn't want to let me click in the box.

UPDATE:
Based on something I found on the suggested link, I tried adding repositories to the source list - Of the very few choices (and not even really understanding what the purpose was) I chose [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) (which seemed harmless enough) and now it won't even let me open the add/remove apps gui (saying "The APT Database could not be opened! This may be caused by incorrect APT configuration or some similar problem. try running apt-setup (which when i tried said "command not found") and apt-set update (which said "E: Type 'http://archive.canonical.com/ubuntu' is not known on line 78 in source list /etc/apt/sources.list") to see if it helps resolve the problem (which it clearly did not)). PLUS when I tried to sudo apt-get install firefox the message i was getting changed to...
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the admistration directory (/var/lib/dpkg/), is another process using it?
I closed the add/remove gui i had open and tried sudo apt-get install firefox again and the message changed to ...
E: Type 'http://archive.canonical.com/ubuntu' is not known on line 78 in source list /etc/apt/sources.list
E: The list of sources could not be read.
I tried to open the file listed and delete the line, but it did not give me permission.

Will somebody please hold my hand?

Thanks,

Oliver
_____

---

### Post by paydaydaddy on 2008-04-10
make sure all instances of adept, apt-get, synaptic, or whatever are shut down, then open a terminal and type in or cut and paste
```
kdesu apt-get -f install
```
Then run the command
```
kdesu dpkg --configure -a
```
then open the adept package manager, click on "adept" and choose "manage repositories". Tick the boxes for main, universe, restricted, and multiverse. Close. Now search for firefox. Request installation then click apply. Cross your fingers for luck.

---

### Post by warbread on 2008-04-10
First, make sure you're only running apt-get once.  You cannot, for instance, have Add/Remove programs open and then try to run apt-get in terminal.  If you're going to use the terminal, make sure Synaptic (found in System>Administration) and Add/Remove are closed.

Second, try doing a search in Synaptic for Firefox.  

Third, why isn't Firefox already installed?  It comes default on all *buntu installations, n'est pas?

Lastly, never, ever delete lines from config files.  Always comment them out (put a pound sign '#' at the very left of the line you want to comment out).  This will prevent that line from being read, but allow you to more easily undo your action if it causes further problems, as it will here.  If you're paranoid like me, you'll even put another comment below that line with the date and reason for commenting it out.  

Type into the terminal "sudo apt-get update" and see what that says.

---

### Post by Trail on 2008-04-10
Firefox is not installed by default on kubuntu... KDE uses Konqueror, which in my opinion is better but slower.

Try firefox3-b5 in any case?

---

### Post by Oliver Closov on 2008-04-10
> **paydaydaddy said:**
> make sure all instances of adept, apt-get, synaptic, or whatever are shut down, then open a terminal and type in or cut and paste
```
kdesu apt-get -f install
```
Then run the command
```
kdesu dpkg --configure -a
```
then open the adept package manager, click on "adept" and choose "manage repositories". Tick the boxes for main, universe, restricted, and multiverse. Close. Now search for firefox. Request installation then click apply. Cross your fingers for luck.

When I tried the first command it says:
kdesu: Unknown option '-f'.

And like Trail commented, it is not installed on Kubuntu. My main reason for wanting Firefox is familiarity and convenience.
I had already tried sudo apt-get update before my original post and that did not solve the problem.

Thanks,
Oliver

---

### Post by paydaydaddy on 2008-04-10
Sorry, that should be
```
sudo apt-get -f install
```
and
```
sudo dpkg --configure -a
```

These commands are to get your package manager working, which I guess is part of your trouble. Once you get adept working and enable the repositories you should have several options of firefox available in the package list.

---

### Post by Oliver Closov on 2008-04-10
> **paydaydaddy said:**
> Sorry, that should be
```
sudo apt-get -f install
```
and
```
sudo dpkg --configure -a
```

These commands are to get your package manager working, which I guess is part of your trouble. Once you get adept working and enable the repositories you should have several options of firefox available in the package list.

Thank you for your quick replies.
However, i get the same response as I mentioned above...
E: Type 'http://archive.canonical.com/ubuntu' is not known on line 78 in source list /etc/apt/sources.list
E: The list of sources could not be read.

I assume this all stems from an attempt to follow instructions on how to add sources to the repository. Ever since then I can't even open add/remove programs gui. It won't let me change things there, cuz I am not in root, but I am not sure how to correct the problem from the command line.

---

### Post by smartboyathome on 2008-04-10
post the output of this: cat /etc/apt/sources.list

---

### Post by Oliver Closov on 2008-04-11
> **smartboyathome said:**
> post the output of this: cat /etc/apt/sources.list


deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed universe main
[http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

Is that what you meant?

---

### Post by eternicode on 2008-04-11
Yup, that's it.  Add "deb " before that last line (following the form of the previous lines).  "kdesu kate /etc/apt/sources.list" to edit with root privileges.

Also, up in the first three sections, uncomment (remove the #) the lines like so:
```

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

```

Then use:

```
sudo apt-get update
```

Assuming you have a network connection on this particular computer.  If not, using apt-get will do you no good (unless you're using the cdrom repo...)

---

### Post by Oliver Closov on 2008-04-11
Dude, it finally worked. Thank you so much. I never would have know to erase all of those "#"s How could it have gotten so screwed up on a first Linux install? I had just hooked up the internet the day before. I can't imagine I did anything that caused that.
I'm new here, is there any kind of recommendation or thank you form for me to fill out? hehe

- Oliver

---

### Post by Oliver Closov on 2008-04-11
Dude, it finally worked. Thank you so much. I never would have know to erase all of those "#"s How could it have gotten so screwed up on a first Linux install? I had just hooked up the internet the day before. I can't imagine I did anything that caused that.
I'm new here, is there any kind of recommendation or thank you form for me to fill out? hehe

- Oliver

---

### Post by Oliver Closov on 2008-04-11
Dude, it finally worked. Thank you so much. I never would have know to erase all of those "#"s How could it have gotten so screwed up on a first Linux install? I had just hooked up the internet the day before. I can't imagine I did anything that caused that.
I'm new here, is there any kind of recommendation or thank you form for me to fill out? hehe

---

### Post by eternicode on 2008-04-11
Hehe, no "Thank you" form, to the best of my knowledge.  Just the little star next to the "quote" button in each post.

---

