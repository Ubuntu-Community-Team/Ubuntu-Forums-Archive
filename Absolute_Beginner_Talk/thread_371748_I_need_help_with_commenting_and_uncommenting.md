---
title: "I need help with commenting and uncommenting"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by devious1 on 2007-02-27
How do you uncomment?

I am following instruction on the perfect setup. this is where I'm stuck
6 Edit /etc/apt/sources.list And Update Your Linux Installation

Edit /etc/apt/sources.list. Comment out the CD and enable some of the other repositories. It should look like this:

vi /etc/apt/sources.list

#
# deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted


#deb cdrom:[Ubuntu-Server 6.10 _Edgy Eft_ - Release i386 (20061025.1)]/ edgy main restricted

deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://de.archive.ubuntu.com/ubuntu/](http://de.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse\


also once done editing how do you exit.

---

### Post by charles.g.moore on 2007-02-27
If you want to uncomment something you place an # at the beginning of the line

---

### Post by Patrick K on 2007-02-27
it's the other way around. To comment something put a hash in front of it. This make the command interpretor ignore anything after the hash. It becomes a comment.To uncomment it remove the hash. Now it will be acted on by the interpretor.

---

### Post by charles.g.moore on 2007-02-27
> **Patrick K said:**
> it's the other way around. To comment something put a hash in front of it. This make the command interpretor ignore anything after the hash. It becomes a comment.To uncomment it remove the hash. Now it will be acted on by the interpretor.

Thank you Patrick, I guess I should be sure to read the posts thoroughly before replying.

---

### Post by devious1 on 2007-02-27
thanx for the help. I'll be back........I'm sure of it:guitar:

---

