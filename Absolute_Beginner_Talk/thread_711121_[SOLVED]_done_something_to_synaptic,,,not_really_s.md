---
title: "[SOLVED] done something to synaptic,,,not really sure what"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by satanic-yobbo on 2008-02-29
can some-one please help me fix this "little" problem i seem to have caused for myself 

An error occured

The following details are provided:

E: Malformed line 5 in source list /etc/apt/sources.list (URI parse)
E: The list of sources could not be read.
Go to the repository dialogue to correct the problem.
E: _cache->open() failed, please report.

---

### Post by neurostu on 2008-02-29
Where you editing your **sources.list** file? It looks like something is wrong with line 5.

If you backed it up before you started editing, I would make a copy of the edited file and then restore you sources.list from the original backup.  Try synaptic again and see if it works.  If it does then it is a problem with your edited sources.list.

Also if you want, you can paste your **edited** sources.list below and we'll take a look at it...

---

### Post by kellemes on 2008-02-29
Please post the contents of /etc/apt/sources.list
There seems to be a syntax error.

---

### Post by satanic-yobbo on 2008-02-29
where do i find  /etc/apt/sources.list? as i cannot open synaptic at all it gives me that msg and closes on me again

---

### Post by neurostu on 2008-02-29
to access your sources.list to pate it simply type
```

sudo gedit /etc/apt/sources.list

```

This will bring it up in gedit, simply copy the entire thing. Paste it below!

ps

btw sources.list is saved at /etc/apt/

---

### Post by satanic-yobbo on 2008-02-29
ok put the code into terminal and this is what it gave me 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb Australia gutsy restricted main
deb-src Australia gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb Australia gutsy-updates main restricted
deb-src Australia gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb Australia gutsy universe
deb Australia gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb Australia gutsy multiverse
deb Australia gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb Australia gutsy-security main restricted
deb-src Australia gutsy-security restricted main multiverse universe #Added by software-properties
deb Australia gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb Australia gutsy-security multiverse


hope this is what you need

---

### Post by philinux on 2008-02-29
Use sudo gedit again to get the file up.

Where you see a line with

deb

it should have deb http...... after it as this is the web address.

any line that has deb but no http following it add a # to the beginning then save the file.
Like these should have a # infront
deb Australia gutsy-security main restricted
deb-src Australia gutsy-security restricted main multiverse universe #Added by software-properties
deb Australia gutsy-security universe

Then in the terminal do

sudo apt-get update 
then

sudo apt-get upgrade

---

### Post by neurostu on 2008-02-29
Now did you edit your sources.list before you got that error? What did you do before you got that error?

---

### Post by satanic-yobbo on 2008-02-29
yes i think i was editing the source list before i got the error i will do what you said and see what happens 

thanks for the help

---

### Post by neurostu on 2008-02-29
Wow, you have a few edits you need to make....
```

deb Australia gutsy restricted main
deb-src Australia gutsy restricted main multiverse universe #Added by software-properties

# deb http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://au.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```

Notice how the 2nd set of lines has ```

http://au.archive.ubuntu.com/ubuntu

```

you need to add a line like this to all of the lines that have deb which are ** NOT ** followed by a http:// tag of some sort...



Now you can comment out those lines as the previous poster said, but those are some pretty important repos.  

Try fixing it to look like:
----------------------------------------------------------
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy restricted main
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy multiverse
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-security main restricted
deb-src Australia gutsy-security restricted main multiverse universe #Added by software-properties
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) Australia gutsy-security multiverse

---

### Post by satanic-yobbo on 2008-02-29
ok this is what it looks like now and i can use synaptic again 

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

#deb Australia gutsy restricted main
#deb-src Australia gutsy restricted main multiverse universe #Added by software-properties

## Major bug fix updates produced after the final release of the
## distribution.
#deb Australia gutsy-updates main restricted
#deb-src Australia gutsy-updates restricted main multiverse universe #Added by software-properties

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
#deb Australia gutsy universe
#deb Australia gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
#deb Australia gutsy multiverse
#deb Australia gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

#deb Australia gutsy-security main restricted
#deb-src Australia gutsy-security restricted main multiverse universe #Added by software-properties
#deb Australia gutsy-security universe
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted main
#deb Australia gutsy-security multiverse

 i hope this is right and if it is i will not be touching the sources list again (for a while anyway lol ) and thanks to all who helped me get out of this mess i made

---

### Post by kellemes on 2008-02-29
Doesn't he need to remove "Australia"?
So basically replace Australia with  [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/)

Also, The first line points to a cdrom.. You normally won't use that anymore.

Edit: Well, great it worked.. By the way, don't forget to create a backup so you can safely screw it up without headache.

---

### Post by philinux on 2008-02-29
I'd delete what you got and then copy and paste stu's list.

---

