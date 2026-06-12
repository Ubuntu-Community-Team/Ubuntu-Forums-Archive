---
title: "OK I am a bit confused"
date: 2005-09-12
forum: Absolute Beginner Talk
---

### Post by bootlinux on 2005-09-12
OK I am a bit confused,,, well a whole lot confused. This may sound like a dumb question but I need conformation. Keep in mind that I'm from the old school of DOS. 
I'v read quite a bit about Linux and have tried many distros in the past year. I'v heard the comment more then once that if you keep your Linux OS current by updating then you don't have to install a new version when it comes out.  You already have have it. So I have Hoary installed and wouldn't need to install Breeze? New releases would only make sense for a new install. Installing Breeze over a Hoary partition wouldn't get me anything new. Did I just answer my own question?

---

### Post by bsussman on 2005-09-12
No - you will still need to upgrade.  And it will involve repointing your repositories.

But you will not need to reinstall from scratch.

---

### Post by aysiu on 2005-09-12
Think of Breezy to Hoary as Windows 2000 to WIndows ME or Mac OS X Tiger to Mac OS X Panther.

Breezy's a new version of Ubuntu. The difference is that with Windows and Mac, you need a separate disk to even upgrade, or you mean not be able to upgrade and might have to reinstall completely.

With most Linux distributions you can upgrade by simply changing your repository sources and typing in these two commands
```

sudo apt-get update
sudo apt-get dist-upgrade
``` Some people are hesitant to do this, as it can hose your system if it doesn't go well. Others have reported it works fine. In my experience with Breezy beta (i.e., not the final release because it hasn't been officially released yet), doing a dist-upgrade is fine as long as I'm in text-only mode. If I do it with the graphical user interface up, it screws up my X.

---

### Post by bootlinux on 2005-09-12
Ok I think I got it. Each version has it's own repository. If I boot a Breeze cd then I can upgrade Hoary which will change apt-get to the Breeze repositories?

---

### Post by bootlinux on 2005-09-12
[QUOTE=aysiu]Think of Breezy to Hoary as Windows 2000 to WIndows ME or Mac OS X Tiger to Mac OS X Panther.

Breezy's a new version of Ubuntu. The difference is that with Windows and Mac, you need a separate disk to even upgrade, or you mean not be able to upgrade and might have to reinstall completely.

With most Linux distributions you can upgrade by simply changing your repository sources and typing in these two commands
```

sudo apt-get update
sudo apt-get dist-upgrade
``` Some people are hesitant to do this, as it can hose your system if it doesn't go well. Others have reported it works fine. In my experience with Breezy beta (i.e., not the final release because it hasn't been officially released yet), doing a dist-upgrade is fine as long as I'm in text-only mode. If I do it with the graphical user interface up, it screws up my X.[/QUOTE]
 
Code:

sudo apt-get update
 sudo apt-get dist-upgrade

Ok I don't need a Breeze cd with this code. Actually I'v seen that code before. It just didn't click at the time I guess. Thanks for clearing my confusion.

---

### Post by aysiu on 2005-09-12
[QUOTE=bootlinux]Ok I think I got it. Each version has it's own repository. If I boot a Breeze cd then I can upgrade Hoary which will change apt-get to the Breeze repositories?[/QUOTE] Not exactly. You have two options:

1. Install Breezy over your Hoary installation using the Breezy CD. Of course, you'd back up your data and settings. This is why a lot of people have separate /home partitions, so they can reinstall the OS or install an upgrade of the OS without affecting their settings and preferences (which live in the /home folder).

2. Change the sources in /etc/apt/sources.list from Hoary to Breezy, then type in the commands I just gave you. That will download the upgrade from the internet.

---

### Post by nitricacid on 2005-09-12
[QUOTE=aysiu]Not exactly. You have two options:

2. Change the sources in /etc/apt/sources.list from Hoary to Breezy, then type in the commands I just gave you. That will download the upgrade from the internet.[/QUOTE]


Sorry if this is a Noobie qusetion but I am more or less a noob to linux even though I have messed around with Mandrake for a few months.

Back to my question:
How do I get the rites to change the /etc/apt/sources.list ?
I found the document i need to chnage but it says i don't have the rite to change it because it's in the root directory and when i try to login as a ROOT user i am denied access by a window that says something about root is not eccessable.
Also what editor should i use to edit the document, it KATE alright?

How can I chage any root files if i can not even login as a root?

Thanks

---

### Post by wvslkr on 2005-09-12
Preface the command with sudo.  There is no root account in Ubuntu it uses sudo.

Example > sudo gedit /etc/apt/sources.list.  You will be asked for passwd use regular user passwd.

---

### Post by nitricacid on 2005-09-12
[QUOTE=wvslkr]Preface the command with sudo.  There is no root account in Ubuntu it uses sudo.

Example > sudo gedit /etc/apt/sources.list.  You will be asked for passwd use regular user passwd.[/QUOTE]

Next question:
Do i edit all the words that say hoary with the word breezy?

Thanks for setting me straight with the sudo gedit

N\M, I THINK I GOT IT SET. EVERTHING IS INSTALLING NOW.
thanks agian.

---

