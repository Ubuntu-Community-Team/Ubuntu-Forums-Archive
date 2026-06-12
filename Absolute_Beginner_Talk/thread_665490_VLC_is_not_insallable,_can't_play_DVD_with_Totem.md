---
title: "VLC is not insallable, can't play DVD with Totem"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by HP_Boehler on 2008-01-12
Hi,

searching the forms now for some day's - installing lot's of packages but nothing helps. 
Running 7.10 64 bits on a Lenovo R61, anything is fine so far except DVD movies. 

Trying to install VLC gives errors in the add-remove window.
Trying to install VLC over the synaptic gives the following error message:
[INDENT]
"not all necessary packages could be selected:
vlc:
 Hängt ab: libsdl-image1.2 (>=1.2.5) but it is not installable[/INDENT]

And now? Why not istallable......

It's a frustration on this side

Please help!

---

### Post by limac on 2008-01-12
where do you live is the first question?
if in the us, you amy not be able to without the license i guess, but there are hacks, which are illegal though. so don't even think about the hacks! and if you live outide of US, its just a few DVD plugins that you need

---

### Post by PmDematagoda on 2008-01-12
Please post the output of:-
```
cat /etc/apt/sources.list
```

---

### Post by ayenack on 2008-01-12
Take a look at this

[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_To_Add_DVD_Playback_Capability)

Or you could try this in terminal.

**sudo apt-get install ubuntu-restricted-extras**

For all those lovely add ons. If you need to enable more apt sources you should be able to do this using Add/Remove from Application>Add/Remove once open top right corner and from the drop down menu select "All available applications" if I remember right this will add all the needed repo's.

---

### Post by HP_Boehler on 2008-01-12
Hi together,

these fast responses are encouraging. Thanks.

Living in Europe / Suisse
 The output of cat /etc/apt/sources.list is

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


and the ubuntu-restricted-extras added by the add/remove window did not change the situation.

Curious to what next. 

regards HP

---

### Post by philinux on 2008-01-12
click the medibuntu link and follow the procedure there.

---

### Post by nikoPSK on 2008-01-12
here you go:

add the medibuntu repos:

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list

```that'll add the repos to your sources.list file, now:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```Install all your requirements:

```
sudo apt-get install libdvdread3 libdvdcss2 libxine1-ffmpeg totem-xine
```It'll change totem gstreamer to totem xine to enable dvd menus. (if in gutsy replace the section of the top code 'fiesty" to "gutsy".

Best Regards,
nikoPSK

---

### Post by limac on 2008-01-12
nikoPSK: is that legal in Canada? If yes, you are soooooo lucky! It's illegal in the USA, if i want to play a DVD in Kubunut or Ubuntu, i have to purchase a license! :( :)

---

### Post by nikoPSK on 2008-01-12
oh darn, I hope I didn't break any rules... :(

but yes, it's legal here. should I censure my post?

---

### Post by ayenack on 2008-01-12
Could just use the wiki.

[http://ubuntuguide.org/wiki/Ubuntu:G...ack_Capability](http://ubuntuguide.org/wiki/Ubuntu:G...ack_Capability)


nikoPSK
I say leave the post as is. Personal choice if you ask me. BTW. How did ReactOS work for you?

EDIT: Just noticed that HP_boehler's /etc/apt/sources.list has neally all of the repo's commented out which is strange. Other than these three.

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse

So probably an idea to uncomment most of them if you ask me.

---

### Post by oldos2er on 2008-01-12
> **HP_Boehler said:**
> Hi together,

these fast responses are encouraging. Thanks.

Living in Europe / Suisse
 The output of cat /etc/apt/sources.list is

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071017)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ch.archive.ubuntu.com/ubuntu/](http://ch.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

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
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy universe multiverse
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security universe main restricted multiverse
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse


and the ubuntu-restricted-extras added by the add/remove window did not change the situation.

Curious to what next. 

regards HP

 Remove the comment mark "#" from each line that begins with either deb or deb-src. Then run "sudo aptitude update && sudo aptitude upgrade". You should be able to install VLC then.

---

### Post by HP_Boehler on 2008-01-12
Hi togther,

Nothing changed. I can't bring up VLC to be installed and totem makes funny things (one type DVD an error "can't read" and another one sound only......

I run all the lines nikoPSK suggested. Last command gave an error:
[INDENT]
Paket totem-xine ist nicht verfügbar, wird aber von einem anderen 
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet 
ist oder nur aus einer anderen Quelle verfügbar ist. 
Doch die folgenden Pakete ersetzen es: 
  libtotem-plparser7 libtotem-plparser-dev 
E: Paket totem-xine hat keinen Installationskandidaten  [/INDENT]

a rough translation is that the package totem-ixine is not available. another package would replace it called "libtotem-plparser7 libtotem-plparser-dev" 

How should the command line look like to solve this?

Regards

---

### Post by nikoPSK on 2008-01-12
> **HP_Boehler said:**
> Hi togther,

Nothing changed. I can't bring up VLC to be installed and totem makes funny things (one type DVD an error "can't read" and another one sound only......

I run all the lines nikoPSK suggested. Last command gave an error:[INDENT]
Paket totem-xine ist nicht verfügbar, wird aber von einem anderen 
Paket referenziert. Das kann heißen, dass das Paket fehlt, dass es veraltet 
ist oder nur aus einer anderen Quelle verfügbar ist. 
Doch die folgenden Pakete ersetzen es: 
  libtotem-plparser7 libtotem-plparser-dev 
E: Paket totem-xine hat keinen Installationskandidaten  [/INDENT]a rough translation is that the package totem-ixine is not available. another package would replace it called "libtotem-plparser7 libtotem-plparser-dev" 

How should the command line look like to solve this?

Regards

apparently the server is down atm. It won't get me updates either. Wait a day or two. It should be fixed.

---

### Post by HP_Boehler on 2008-01-12
Hey thanks:) to oldos2er

VLC is up and for some DVD's working. 
I assume to understand the error of the ubuntu-restricted stuff now and will try this once more to see if this will resove the remaining non playables.

regards HP

---

### Post by oldos2er on 2008-01-12
Glad you got it going. You may also need to enable the Medibuntu repository (if you don't already have it), and install libdvdcss2. "sudo aptitude install libdvdcss2" in a terminal.

---

### Post by nikoPSK on 2008-01-12
> **oldos2er said:**
> Glad you got it going. You may also need to enable the Medibuntu repository (if you don't already have it), and install libdvdcss2. "sudo aptitude install libdvdcss2" in a terminal.

like in my post on the first page.

---

### Post by HP_Boehler on 2008-01-13
Oh hola,

this solved the last bit of non playing DVD's out of the cllection. Thank you very much!:):):)

---

### Post by nikoPSK on 2008-01-13
> **HP_Boehler said:**
> Oh hola,

this solved the last bit of non playing DVD's out of the cllection. Thank you very much!:):):)

No problem, I only figured this out a month ago. :p

Regards,
nikoPSK

---

