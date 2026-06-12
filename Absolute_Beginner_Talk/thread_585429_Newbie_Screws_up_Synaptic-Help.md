---
title: "Newbie Screws up Synaptic-Help"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by johnwillyums on 2007-10-21
Hi all, after many attempts I've finally got Ubuntu 7.10 64x to dual boot with Vista 64x.

Problem is I'm a complete newbie all round-windows and linux.

I've been trying to configure stuff and I was looking for other repositories to get compizconfig-settings manager and I seem to have broken synaptic.

It won't open now and I get-

E: Malformed line 56 in source list/etc/apt/source.list (dist parse)
E; The list of sources could not be read
Go to repository dialog to correct problem
E:cache-> open() failed, please report

I tried to find repository dialog using the search facility box from the top bar(right) squiggly icon but get-

Error: keyword not valid or missing.

Could somebody help me out here?

Thanks, John Williams

ps. I just noticed an orange icon on my top bar which tells me that installed items have unmet dependencies.

When I open that I get the same "malformed line" message and the update package manager won't open.

---

### Post by Maestro23 on 2007-10-21
There is an error on line 56 of your sources.list file.  In a terminal run the following command, and post the output.

> cat /etc/apt/sources.list

If you see the error yourself, just edit the file using gedit.  Make the changes and save.

> gksudo gedit /etc/apt/sources.list

---

### Post by johnwillyums on 2007-10-21
Ok, thanks.

I tried that- typed the command after the squiggle and dollar sign and got-

bash:cat/etc/apt/source.list: no such file or directory.

John

---

### Post by Maestro23 on 2007-10-21
> **johnwillyums said:**
> Ok, thanks.

I tried that- typed the command after the squiggle and dollar sign and got-

bash:cat/etc/apt/source.list: no such file or directory.

John

Need a space in between cat and /etc....

---

### Post by vgrisham on 2007-10-21
> **johnwillyums said:**
> Ok, thanks.

I tried that- typed the command after the squiggle and dollar sign and got-

bash:cat/etc/apt/source.list: no such file or directory.

John

That should be sources.list (note the plural). That's the problem.

Added: John, it took me a while to catch onto, but if you copy and paste the commands, it makes terminal work easier and less prone to typos.

---

### Post by mikeize on 2007-10-21
-edited for redundancy-

---

### Post by johnwillyums on 2007-10-21
Ok. I've now got a lengthy box of text about"deb" and unsupported packages plus "uncomment the following two lines" and stuff about backport

I tried to copy and paste it into this reply but cannot find a way of doing it.
John

---

### Post by aktiwers on 2007-10-21
Just rightclick and pick Copy.

Or open it like this:
```
gksudo gedit /etc/apt/sources.list
```And copy/paste it here for us to see

---

### Post by johnwillyums on 2007-10-21
Ok. I tried that new command and got this
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports

That seems to be the last two lines of the previous lengthy message.

John

in fact that's what I got when I tried to copy and paste the entire long message-just the last two lines

---

### Post by aktiwers on 2007-10-21
Didnt it open up a text editor with lots of info in it?
You need to copy/paste all the info from that text file.. so I can see whats wrong in line 56 :)

---

### Post by johnwillyums on 2007-10-21
Yes. I've got a lengthy text, a couple of pages in a small window but I don't seem to be able to copy and paste the whole thing 
If I go to Edit the drop down box has copy greyed out and if I try paste I get this-

## newer versions of some applications which may provide useful features.
## Also, please note that software in backports

Which, as i said is the last two lines of the long text. If I try to drag my pointer over the entire text it goes black and this is what happens if I paste it into this message box.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

That seems to be the first paragraph after the command. 
Should I try to copy and paste it a paragraph at a time?
John

---

### Post by vgrisham on 2007-10-21
Are you using gedit? If so, with your sources.list file in front of you, key ctrl-a, then ctrl-c. Then paste it with ctrl-v in a thread response window.

---

### Post by vgrisham on 2007-10-21
...also, if you're sources.list file is messed up, you can always rebuild it using this handy web tool: [http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/), though you should probably study up a bit at [https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)

---

### Post by aktiwers on 2007-10-21
CTRL+C and then CTRL+V dont work either?
Thats strange!

So I guess you are on Gutsy?

This is how mine looks:
> deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Beta i386 (20070925.2)]/ gutsy main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main restricted #Added by software-properties
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://dk.archive.ubuntu.com/ubuntu/](http://dk.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) gutsy-backports main restricted universe multiverse
#AUTOMATIX REPOS END

You could simply replace your own with mine and save it. That would fix it, but then you will get connected to the danish servers (the one with dk).

But you should be able to copy/paste it in here, just like I did, so I can find your mistake, and tell you how to fix it..

---

### Post by johnwillyums on 2007-10-21
gksudo gedit /etc/apt/sources.listgksudo gedit /etc/apt/sources.listdeb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy universe
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates universe
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
deb [http://archive.ubuntu.com/ubuntu/gutsy](http://archive.ubuntu.com/ubuntu/gutsy) main


Nice one ,got it and here it is. Any use?
John

---

### Post by aktiwers on 2007-10-21
Now try replace it with this one:

> 
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://im.archive.ubuntu.com/ubuntu/](http://im.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverseAnd save.

Then run this command from Terminal:
```
sudo apt-get update
```Everything should be fine now :)

EDIT:
Fixed something in the quote.

---

### Post by johnwillyums on 2007-10-21
Ok.
I deleted the source list and pasted your one in and saved.
I then opened terminal and typed sudo apt-get update.
This got me a request for password but would not let me type.
However synaptic is now opening so hopefully that's sorted.

I'm very grateful for your help. I have to sleep now as I have work early in the morning. 
No doubt I'll be back on tomorrow as I try to learn more about this amazing system.

Many thanks, John Williams

---

### Post by aktiwers on 2007-10-21
No problem :)
Remember it lets you type, it just doesn't show you what you are typing :)
So just type in the password and hit enter.

In Synaptic you can hit the "Reload" button as well.. it  will do the same thing as that command.

---

