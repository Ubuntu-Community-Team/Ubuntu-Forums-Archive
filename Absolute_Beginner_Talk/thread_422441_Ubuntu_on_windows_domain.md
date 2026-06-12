---
title: "Ubuntu on windows domain"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by andneomat on 2007-04-25
Hello,

I work as Windows network administrator, but I would like to work with Linux... so i got Ubuntu 7.04.
Some things works great: work good with NTFS partion, printing with Windows workstation...but...

Problems:

1. When I share folder on Ubuntu work station, I can't access to that folder with Windows work station.

2. How to involve Ubuntu in windows domain

I started to work with Linuks yesterday... so have litle understanding and be detailed.

---

### Post by BoneKracker on 2007-04-25
You should read extensively the samba documentation. 

You can do most thing with it that NT can do (act as a PDC, participate in elections, etc.).  The authentication aspects require some study.

This is not a bad place to start (for an overview):
[http://en.wikipedia.org/wiki/Samba_software](http://en.wikipedia.org/wiki/Samba_software)

and there is 
[www.samba.org](www.samba.org)

Remember, while you're marveling at how ugly this is, that this is to some degree a historical attempt to fit into the windows network.  While this is still actively developing, things are also moving on other fronts that don't relate to smb/cifs.

---

### Post by Skrynesaver on 2007-04-25
Hi BoneKracker,
Love the sig, but how else do you explain that
sed 's/\(domain\) \(username\)/\2@\1/'
turns domain username into
username@domain

---

### Post by BoneKracker on 2007-04-25
Hey, I didn't say I _understand_ it.

I just marvel at its incomprehensibility.

If I sat down for a whole day and worked on it, I probably could not create a logically dense and correct sentence that so boggles the mind of the reader.
:confused: 

The first time I read that man page, I think I read and re-read, and the finally took out a pencil and drew a diagram to try to dissect the meaning of that sentence.

It is a work of art.

Edit: how do actually explain such?  With graphics.  But ascii-art would be bad form in a man page.  Another way would be with examples (such as the excellent one you provide).

Or you could say, "\n" expands to the nth part of the regex that's in parentheses

---

### Post by yoasif on 2007-04-25
See [Ubuntuguide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add.2Fedit.2Fdelete_network_users") for help with this -- basically, for whatever reason, the samba usernames are not added when enabling samba in ubuntu.

---

