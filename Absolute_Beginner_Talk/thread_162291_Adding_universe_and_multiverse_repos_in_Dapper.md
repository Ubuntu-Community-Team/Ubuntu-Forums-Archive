---
title: "Adding universe and multiverse repos in Dapper"
date: 2006-04-18
forum: Absolute Beginner Talk
---

### Post by dreamsINdigital on 2006-04-18
I'm trying to follow [this guide]("https://wiki.ubuntu.com/AddingRepositoriesHowto?action=show&redirect=HowToEnableTheMultiverseRepositoryInUbuntu#head-45edcdb233b5b386b0760db59e62dd44dc40aeda") to add the universe and multiverse repositories.  It says to click "Repositories" in the "Settings" menu.  Then it says to click the "Settings" button.  The thing is, I don't see a "Settings" button.  So what am I supposed to do to add the universe and multiverse repositories in Dapper Drake Flight 6?

Thanks.

---

### Post by macdo on 2006-04-18
Well, if you're not afraid of directly editing the file, the easy way to do this is to shut down synaptic, open a terminal, backup the file by typing ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.old
```
then type ```
gksudo gedit /etc/apt/sources.list
```You'll need your password.
In the file that opens, erase the hash # that starts lines with universe and multiverse in them:
```
 deb http://archive.ubuntu.com/ubuntu dapper universe
 deb-src http://archive.ubuntu.com/ubuntu dapper universe

 deb http://archive.ubuntu.com/ubuntu dapper multiverse
 deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
```

Save the file, close it, and reopen synaptic. Use the Update button to apply your changes - and you're sorted!

I know this probably wasn't the answer that you expected, but I can't duplicate your problem - and any correct answer is better than none, right?

---

### Post by angkor on 2006-04-18
For the record, In the gui it is:

System -> Administration -> Synaptic (enter password for Synaptic)

In Synaptic:

Settings -> Repositories

(Un)check the desired repositories.

Click 'Reload' to update your repositories list.

---

### Post by dreamsINdigital on 2006-04-18
Can someone post the original unmodified sources.list from Dapper Drake 6.06 Flight 6 please?

**macdo**:  Thanks.  I've tried doing that before, but along with other stuff so I think my sources.list is a little messy.  I guess you can't reproduce my problem because you're not using Dapper?  I know back when I had Breezy I followed the guide and it worked fine.  Or am I just the only person who doesn't have a "Settings" button in Dapper?

**angkor**:  For the record :roll: , you wanna explain why the guide doesn't put it that way?  It also says to enable multiverse, *"To enable the Multiverse repository, for each of the Community Maintained (Universe) entries click on the entry, click Edit, then change the entry for Sections from 'universe' to 'universe multiverse'."* Do I not have to worry about that with your method?

---

### Post by macdo on 2006-04-18
Too true - Breezy for me until I'm 99% sure that Dapper ain't going to break anything. The PC's too important at the mo :-)

Here's a sample dapper sources.list, if you're in the US: 
```

deb http://us.archive.ubuntu.com/ubuntu dapper main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu dapper-updates main restricted

## Uncomment the following two lines to add software from the ‘universe’
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu dapper universe
deb-src http://us.archive.ubuntu.com/ubuntu dapper universe

## Uncomment the following two lines to add software from the ‘backports’
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu dapper-security main restricted
deb-src http://security.ubuntu.com/ubuntu dapper-security main restricted

deb http://security.ubuntu.com/ubuntu dapper-security universe
deb-src http://security.ubuntu.com/ubuntu dapper-security universe
 
deb http://archive.ubuntu.com/ubuntu dapper multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper multiverse
 
## Backports
deb http://archive.ubuntu.com/ubuntu dapper-backports main restricted universe multiverse
```

Go [here]("http://www.ubuntulinux.nl/source-o-matic") and it'll make you your very own sources.list....

-

---

### Post by dreamsINdigital on 2006-04-18
Thanks a lot macdo! =D>

---

### Post by angkor on 2006-04-19
[QUOTE=dreamsINdigital]
**angkor**:  For the record :roll: , you wanna explain why the guide doesn't put it that way? [/quote]

I think the wiki page still needs to be edited a little for Dapper. Probably cause dapper is still new and unfinished. In dapper you don't need to tick Show disabled software sources anymore.

You could edit the page yourself if you want to.

[QUOTE=dreamsINdigital]
It also says to enable multiverse, *"To enable the Multiverse repository, for each of the Community Maintained (Universe) entries click on the entry, click Edit, then change the entry for Sections from 'universe' to 'universe multiverse'."* Do I not have to worry about that with your method?[/QUOTE]

In dapper there's no need to edit the sections. In synaptic the universe entries already include the multiverse repos by default.

It will put an entry in your sources.list like this:

```
deb http://nl.archive.ubuntu.com/ubuntu/ dapper universe multiverse
deb-src http://nl.archive.ubuntu.com/ubuntu/ dapper universe multiverse
```

---

