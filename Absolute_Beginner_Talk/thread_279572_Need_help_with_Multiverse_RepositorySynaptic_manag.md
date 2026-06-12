---
title: "Need help with Multiverse Repository/Synaptic manager"
date: 2006-10-18
forum: Absolute Beginner Talk
---

### Post by IronArjen on 2006-10-18
I have been trying to install some software from the multiverse repository.
First I changed the settings of my listed repositories via de System->Administration->Software properties. I checked the required boxes, followed the procdure (Load or reload), went to Synaptic. The software does not appear. HItting th reload button results in the download of 33 packages, software still not listed, hit reload: download 33 packages.

I think I have a problem with my Synpatic or with the real install routine (Synaptic being the GUI to help me).

What to do?

---

### Post by bluefrog on 2006-10-18
if memory serves, multiverse is not in the repo, only universe.

if this is the case for you edit the universe line, add a space and write multiverse. save, reload.

James

---

### Post by IronArjen on 2006-10-18
I do not fully understand what you mean with "memory serves".

Belowe you find my source.list. What I am not sure about is whether "dapper-backports main restricted universe multiverse" is the real "multiverse", I tried to look for the address but have not been able to find it anywhere. I believe that is the problem.

Source.list:


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Google Picasa for Linux repository
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

---

### Post by bluefrog on 2006-10-18
if memory serves = if I remember well (e.g. was not sure...)
with your source list I am sure now.

backports is something special, won't get into that now.

change one line in your list as follows and it will be alright

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe multiverse

(you can put a separate line if you wish so you can enable/disable them independently...)

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper multiverse

James

---

### Post by Kateikyoushi on 2006-10-18
Try to add multiverse to the end of the first line, like this

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

---

### Post by klytu on 2006-10-18
> **IronArjen said:**
> I do not fully understand what you mean with "memory serves".

Belowe you find my source.list. What I am not sure about is whether "dapper-backports main restricted universe multiverse" is the real "multiverse", I tried to look for the address but have not been able to find it anywhere. I believe that is the problem.

Source.list:


deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

## Google Picasa for Linux repository
# deb [http://dl.google.com/linux/deb/](http://dl.google.com/linux/deb/) stable non-free

My sources.list also contains the following lines for the multiverse repositiories:

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates multiverse

It looks like yours only has the multiverse backports repositories. Read [here]("http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories") for instructions to updating your sources.list for your location.

---

### Post by IronArjen on 2006-10-18
I added the 

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

as well as

deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper multiverse

and now it works. 
The strange thing to this is: Just half a year ago I started with Ubuntu (Breezy) and the mutliverse line was present in source.list (with # to delete if you wish to use is) With Dapper it is not standardly included and on the help pages it does not state what the correct address is.

I will try to change the strange "universe multiverse" comment back on it and put a nice source.list for other scientists and mutliverse users available in a "howto".

Thanks for these simple and very helpful comments!

Arjen

---

### Post by Bachstelze on 2006-10-18
[Here](http://paste.ubuntu-nl.org/6666/)'s a nice default sources.list for Dapper :)

---

