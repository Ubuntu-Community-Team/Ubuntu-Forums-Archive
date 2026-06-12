---
title: "Fresh Install 7.10 from 6.06"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by danbrownlow on 2008-02-20
Hey all, I've tried everything to upgrade that people have suggested for upgrading from 6.06 to a new version and I realise if I upgrade I'll have to step through the releases so I'm wanting to perform a clean install.

I want to give kubuntu a try this time and so I have burned the .ISO to a disc and I thought when I put the CD into the computer, it would automatically start and update itself. The only problem is nothing seems to happen when I load the CD.

What do I have to do to perfrom a clean install?

Many thanks, Dan.

---

### Post by jan quark on 2008-02-20
good starting point is this site

[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

do you want to completely remove your old ubuntu system?

 it would be the easiest way:
do a backup of you important data and install the newest version of ubuntu 
as explained in the site linked above

---

### Post by jan de beuker on 2008-02-20
Your computer has to boot from cd
This option has to be set in the BIOS of your computer.

---

### Post by oedha on 2008-02-20
have you set your BIOS to boot from CD first ?
how did you burn the iso ?
low speed burning will be better......

---

### Post by danbrownlow on 2008-02-20
Hey, yea' I've done all that now =] Now the problem seems to be once I select the option to install Kubuntu, it's stuck saying, "Loading, please wait.." for a suspiciously long amount of time. Does this normally happen? Or am I supposed to write something in the terminal? Lol. Thanks.

---

### Post by danbrownlow on 2008-02-20
Right, it wouldn't load again so I've burned again, really slow at like 8x and still no luck. I guess I'm going to have to go through the steps of upgrading as without a CD-R.. That's about the only thing I can do.

What I've done is use update manager and installed the updates I need, although, when I used the update manager, it told me that it was going to skip some things and that I should use Synpatic to Include all updates which I did and then let install. At no point was I prompted to update to a newer version of Ubuntu. How do I get it to prompt me to update?

Dan.

---

### Post by oedha on 2008-02-20
open terminal
sudo apt-get update
sudo apt-get upgrade

---

### Post by oedha on 2008-02-20
mmm.......what if....(wondering)
you boot from the cd again...the edit the boot line by adding all_generic_ide

---

### Post by danbrownlow on 2008-02-20
Well, I really think my drive has had it. It's not loading anything and when I checked the disc, it was fine. I guess I'm just going to have to go through terminal and update via that. I've also tried using the xubuntu disc and I've had no luck with that, I get upto the stage where it declares it's defaulted to rubbish graphics drivers then I get up to the Running local boot scripts (etc/rc.local) and then nothing happens. Any ideas or is it because my CD-R drive is dead =]

---

### Post by danbrownlow on 2008-02-20
I just tried the sudo apt-get update and upgrade and it's done nothing. I keep getting errors constantly. I have no idea what to do now. :( Lol.

---

