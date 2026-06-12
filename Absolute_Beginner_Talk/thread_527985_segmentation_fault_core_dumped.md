---
title: "segmentation fault core dumped"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-08-17
[FONT="Comic Sans MS"]Hi. Just read something about Aptitude so tried having a look about. Got the message above. Tried aptitude update - ditto.
Tried apt-get update and get this;> Failed to fetch [http://security.ubuntu.com/ubuntu/dists/feisty-security/Release](http://security.ubuntu.com/ubuntu/dists/feisty-security/Release)  Unable to find expected entry  multiversedeb/source/Sources in Meta-index file (malformed Release file?)
Reading package lists... Done
E: Some index files failed to download, they have been ignored, or old ones used instead.
Synaptic basically gives the same message, of course.
Checked my /etc/apt/sources.list and got this;
> # See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://hk.archive.ubuntu.com/ubuntu/](http://hk.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiversedeb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
That last line looked dodgy so I tried moving the second part down to its own line but it made no difference. So I put it back.[/FONT]
[FONT="Comic Sans MS"]Recent changes? Sure, heaps, always.
Haven't had any trouble with update manager. I'm sure there's a simple fix, but I don't know what it is[/FONT]

---

### Post by EndPerform on 2007-08-17
The problem looks to be your last line:

```
deb-src http://security.ubuntu.com/ubuntu feisty-security multiversedeb http://packages.medibuntu.org/ feisty free non-free
```

Change it to:

```
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
deb http://packages.medibuntu.org/ feisty free non-free

```

Let me know if that works.

---

### Post by carloslosgrande on 2007-08-17
[FONT="Comic Sans MS"]Hi Endperform, I actually tried that before, but I've just done it again without any benefit.[/FONT]

---

### Post by RomeReactor on 2007-08-17
Hi. So did you keep the last line as it was before? As EndPerform said, it really should be two lines, not one. Split them up again and run aptitude update.

---

### Post by Boreras on 2007-08-17
*EDIT: I think you do have the sources.list wrong. When the lines are combined as in your case, I get the same error.

If I changed your last line to > 
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free

I got no error at all.

You probably copy-pasted pasted the last line in gedit, but you forgot to give the new repo a new line.

---

### Post by carloslosgrande on 2007-08-17
[FONT="Comic Sans MS"]Hi guys, I tried again as you've suggested but no luck.
Looking at the lines I tried something that looked sensible, I changed the last line so it looked like the others by adding in>  [COLOR="#ff0000"]-src[/COLOR] and it now looks like this;
> deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
deb[COLOR="Red"]-src[/COLOR] [http://packages.medibuntu.org/](http://packages.medibuntu.org/) feisty free non-free
this has fixed the apt-get error.
Thanks for your help.
However, aptitude is still telling me >  segmentation fault core dumped
Is there some command to give aptitude a kick?[/FONT]

---

### Post by carloslosgrande on 2007-08-17
[FONT="Comic Sans MS"]Well I've restarted this morning and there's absolutely no improvement with aptitude.:(
 I've searched thru the threads for 'segmentation fault' and they all deal with specific apps causing this error, but I'm just trying to update/check it out.
Is there some way to reset or restart aptitude  -   to give it a kick in the guts as it were?[/FONT]:confused:

---

### Post by carloslosgrande on 2007-08-24
[FONT="Comic Sans MS"]Ok, current status is; I've done a total reinstall.

Everything is working fine, except aptitude.

I'm still getting the same error.

apt-get works fine.

What can be wrong with my aptitude, I haven't seen any other recent threads re this.[/FONT]

---

### Post by RomeReactor on 2007-08-24
Have you searched for **aptitude** in Synaptic? maybe it's marked as a broken package, though I don't know why this keeps happening since you did a total reinstall. You cold try searching [Launchpad]("https://bugs.launchpad.net/") for a bug in Aptitude; if your particular case doesn't show up, you could try filing one yourself, in which case make sure you include as much detail as possible (what version of Ubuntu you have, for what architecture--32 or 64 bit--and if you added additional repositories or installed other packages prior to this error showing up

---

### Post by carloslosgrande on 2007-08-25
[FONT="Comic Sans MS"]Hi. I went to synaptic and checked. Aptitude wasn't listed as broken. I decided to reinstall it anyway, as well as the manual doc that goes with it (aptitude-doc-en). Thought maybe I might get some more detail in the error messages.

Well now something REALLY weird has happened.
When I try to enter my password in the terminal it doesn't recognise it. Yes, numerous attempts!

So I went to >system>administration>software sources, which I knew would ask for my password, entered and, hey presto, no problem.
I did make a change in the terminal setup via 'visudo' which gives comments for incorrect passwords. It seems this was a mistake.
Can't get into visudo to fix it!!!
Bugger![/FONT]

---

### Post by SuperMike on 2007-09-02
I just encountered this problem on my Feisty Fawn PC. I didn't have a bug in my /etc/apt/sources.list, so I found that I could fix it by doing:

```
sudo su
dselect
[choose update]
[choose install]
[choose configure]
[choose remove]
[choose quit]
exit
apt-get update
```

And at that point I could do apt-get install <my desired package>. All was well again.

---

