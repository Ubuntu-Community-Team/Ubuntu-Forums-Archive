---
title: "Problem with Openoffice"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by vaaa on 2007-09-20
Hello everyone,

Although I have some experience with linux I classify myself as a complete newbie.
I've downloaded openoffice from the official site and tried to install it without previously uninstalling the ubuntu-openoffice.

Now it seems that there is something wrong and I cannot either uninstall the ubuntu-openoffice or install the new one.

Moreover I cannot install some other services like Unix Networks Support....

I keep getting the error msg : 

[I]dpkg: parse error, in file `/var/lib/dpkg/available' near line 16857 package `openoffice.org-help-2.0.3':
 missing version[/I]

What should I do? Any help would be very appreciated....

Thanks 

V

---

### Post by skyjacker on 2007-09-20
why did you not use the OO in add/remove programs??

Try this to remove OO. 
Code:
sudo apt-get remove --purge program_name
program_name = exact name of your Avg

---

### Post by vaaa on 2007-09-20
This is what the outcome was after running the command :
[I]
sudo apt-get remove --purge openoffice*[/I]

(...a lot of notes like: 
*Note, selecting openoffice.org2-dev for regex 'openoffice.org*'*)

.
.
.

[I]0 upgraded, 0 newly installed, 34 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 265MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 16857 package `openoffice.org-help-2.0.3':
 missing version
E: Sub-process /usr/bin/dpkg returned an error code (2)[/I]


Now what? :'(

---

### Post by p_quarles on 2007-09-20
It sounds like there's a broken package somewhere. Try running:
```
sudo dpkg --configure -a
```
I looked at the new OOo release yesterday, and from what I could tell it was only available as an .rpm (which means it won't work with apt or dpkg). If you have a pressing need for some feature in the new version, you could try using an application called "alien" to convert the .rpm into a .deb package.

---

### Post by vaaa on 2007-09-20
Again the same output :

[I] sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/available' near line 16857 package `openoffice.org-help-2.0.3':
 missing version[/I]

I dont want any new features. As a matter of fact I tried to install OO as soon as I installed ubuntu because I had no idea that it was pre installed.

I just want to be able to install other services like Unix Network Support to map a network folder to my pc....

---

### Post by p_quarles on 2007-09-20
Okay, so just to clarify: the problem is that you can't install any new software now?

Here are a couple things to try. Update the cache:
```
sudo apt-get update
```
attempt to fix broken packages:
```
sudo apt-get check -f
```
Run those, and see if you get the same error. 
Anyway, I'm not sure exactly what you mean by Unix Network Support. There are many ways of mapping a networked share into the file manager. Are the server and desktop both running Linux? What is the specific name of the package you're trying to install?

---

### Post by Bothered on 2007-09-20
It sounds like you've installed openoffice outside of a package manager. If you can, I recommend you uninstall the latest version of openoffice (I don't know how to do this - how did you install it) then reinstall the broken packages on your system.

EDIT: You can install the latest version once you've done this - I'm just recommending this to try to get you system back into a working state.

---

### Post by funrider on 2007-09-20
go to synaptic manager, search for openoffice.....complete removal and then install it again

---

### Post by vaaa on 2007-09-20
Yes the truth is that I tried to install outside package manager by running the setup file of the downloaded OO.

After running
```

sudo apt-get check -f 
sudo apt-get update
```

I tried to share a folder. A pop-up window came up that said that additional services should be installed to be able to share the folder. (Install Unix Networks Support (NFS) and Windows Networks Support (SMB)   )

After pressing install the output message was:

[I]debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 16857 package `openoffice.org-help-2.0.3':
 missing version

Not all changes and updates succeeded. For further details of the the failure, please expand the 'terminal' panel below.
[/I]

Thanks for the support so far guys!!!

---

### Post by Lord Illidan on 2007-09-20
Can you clarify how you tried to install Open Office?

EDIT : Ok, I was a bit slow on that one.

EDIT again : For clarification, did you download this : OOo_2.3.0_LinuxIntel_install_wJRE_en-US.tar.gz ?

I am going to try and repeat the steps you took, so perhaps I can find a way to uninstall it.

---

### Post by p_quarles on 2007-09-20
Hmm. Maybe it will help to have a look at the line it says is causing the problem. Open up the file /var/lib/dpkg/available in a text editor and post the package listing for openoffice.org-help-2.0.3. 

Most text editors will have a feature that allows you skip ahead to line 16,857. That will be easier than scrolling. :)

---

### Post by Lord Illidan on 2007-09-20
Did you use this site for instructions?
[http://www.openoffice.org/dev_docs/instructions.html](http://www.openoffice.org/dev_docs/instructions.html)

---

### Post by vaaa on 2007-09-20
Yes I downloaded that version of open-office

I unzipped it on Desktop and then double clicked on setup file... :)

I'm a newbie what can I say ? :)

As for that line in the file it was

package=openoffice.org-help-2.0.3

---

### Post by p_quarles on 2007-09-20
Could you post the surrounding package information as well?

---

### Post by Bothered on 2007-09-20
> **vaaa said:**
> I'm a newbie what can I say ? :)

Don't worry about it. I've used linux for a year and I still count myself a beginner on many things.

Is there anything called "uninstall" in the archive you downloaded? Or perhaps the "setup" file can be passed an argument to uninstall it.

---

### Post by Lord Illidan on 2007-09-20
How did you get it to work without rpm? Or did you install alien?

---

### Post by vaaa on 2007-09-20
I would like to clarify that I believe the "official" OO did not install itself at all as all I did was to doubleclick the setup file. And the ubuntu-OO also works without any problem.

What Im trying to say is that when I try and share a folder a popup window comes up and asks if I want to install some services.
I click to install both services and the following message comes up:
[I]
debconf: unable to initialize frontend: Dialog
debconf: (Dialog frontend will not work on a dumb terminal, an emacs shell buffer, or without a controlling terminal.)
debconf: falling back to frontend: Readline
Preconfiguring packages ...
dpkg: parse error, in file `/var/lib/dpkg/available' near line 16857 package `openoffice.org-help-2.0.3':
 missing version

Not all changes and updates succeeded. For further details of the the failure, please expand the 'terminal' panel below.[/I]

and because the error has a line about OO I thought that this might be causing the problem....

waiting for ur help :)

---

### Post by Bothered on 2007-09-20
> **vaaa said:**
> I would like to clarify that I believe the "official" OO did not install itself at all as all I did was to doubleclick the setup file. And the ubuntu-OO also works without any problem.

In that case, so long as you didn't run it as root it shouldn't cause a problem.

---

### Post by vaaa on 2007-09-20
So why don't the network services get installed?

---

### Post by Lord Illidan on 2007-09-20
So you didn't see any setup windows of Open Office installing itself? You just clicked the setup and nothing happened, is that correct?

---

### Post by vaaa on 2007-09-20
I think that a script ran but Im not sure...

---

### Post by Lord Illidan on 2007-09-20
Just as a check, can we see your /etc/apt/sources.list ?

---

### Post by vaaa on 2007-09-20
Yes I can

---

### Post by Lord Illidan on 2007-09-20
Er, post it here, please?

---

### Post by vaaa on 2007-09-20
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://cy.archive.ubuntu.com/ubuntu/](http://cy.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

---

### Post by HereInOz on 2007-09-20
Just a thought - you say that you installed Open Office just after you installed Ubuntu.  If that is the case, and you have not done much configuration with Ubuntu, apart from all the above, why not put the CD in the drive again and re-install, with a format of the appropriate partitions.

We all go through this phase with any new OS.  Put it down as a learning experience and start again.

---

### Post by vaaa on 2007-09-20
sorry missed smth


```
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://cy.archive.ubuntu.com/ubuntu/ feisty main restricted
deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://cy.archive.ubuntu.com/ubuntu/ feisty-updates main restricted
deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://cy.archive.ubuntu.com/ubuntu/ feisty universe
deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://cy.archive.ubuntu.com/ubuntu/ feisty multiverse
deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://cy.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse
# deb-src http://cy.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu feisty-security main restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security main restricted
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb-src http://security.ubuntu.com/ubuntu feisty-security universe
deb http://security.ubuntu.com/ubuntu feisty-security multiverse
deb-src http://security.ubuntu.com/ubuntu feisty-security multiverse
```

---

### Post by Lord Illidan on 2007-09-20
> **HereInOz said:**
> Just a thought - you say that you installed Open Office just after you installed Ubuntu.  If that is the case, and you have not done much configuration with Ubuntu, apart from all the above, why not put the CD in the drive again and re-install, with a format of the appropriate partitions.

We all go through this phase with any new OS.  Put it down as a learning experience and start again.

I have to agree with this.

---

### Post by vaaa on 2007-09-20
OK finally it seems that finally I should be doing that... 


Thanks for the support. It was a matter of learning also not just for fixing my pc.

---

### Post by Lord Illidan on 2007-09-20
> **vaaa said:**
> OK finally it seems that finally I should be doing that... 


Thanks for the support. It was a matter of learning also not just for fixing my pc.

Yes...if you had some more experience, you could have fixed it yourself, probably. But sometimes it helps to clear the slate and start afresh.

---

### Post by shae on 2007-09-20
If you have not reformatted yet, I have a few ideas we could try.

---

