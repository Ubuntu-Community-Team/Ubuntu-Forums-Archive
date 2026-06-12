---
title: "/etc/apt/sources.list broken?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by Sardjen on 2007-02-05
So, I was trying to install VLC, and I added a repository, and the next time I booted the Add/Remove Programs manager I got this:

Failed to check for installed and available applications

This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

So, this is what my sources.list looks like, after the bit of text at the beginning:

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
#AUTOMATIX REPOS END
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper-plf

Synaptic says that line 50 is "malformed", but I'm still learning the shell and everything, so I don't really know what I need to do. Could you guys give me a hand, please?

---

### Post by Spr0k3t on 2007-02-05
Not sure what line 50 is referring to as I don't see 50 lines there.

You might want to open a terminal and try this

$ sudo apt-get check

Personally speaking, I've not had any luck with Automatix and reinstalled from scratch (laptop only).  Since then I've only used the terminal or the Synaptic Package Manager after adding the universe multiverse to my sources list as explained on ubuntuguide.org.

---

### Post by jvc26 on 2007-02-05
I can't see there being 50 lines in there either... Can you post up the entire thing?
Il

---

### Post by dannyboy79 on 2007-02-05
you can use nano to go directly to line 50 and then paste it here and we'll tell you whats wrong with it. first do sudo nano /etc/apt/sources.list, then I think it's ctrl & underscore (_). and hte way you do that is by holding ctrl and shift, then hit the dash which is to the right of the number 0 (zero). then simply hit 50 and enter and the cursor will go to line 50. i have really learned to use nano well due to me ssh'ing into my box from work and playing around in the command line. installing tripwire, checking my /var/log/auth.log files, etc etc. post line 50, or fix it yourself. good luck.

---

### Post by Sardjen on 2007-02-05
Sorry for the wait, just got back from university. Here's the whole thing:


deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

#AUTOMATIX REPOS START

deb [http://wine.lowvoice.nl/apt](http://wine.lowvoice.nl/apt) dapper main

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) dapper main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper universe multiverse main restricted
#AUTOMATIX REPOS END
deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) dapper main
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) dapper-plf

---

### Post by Hendrixski on 2007-02-05
If synaptic tells you that line 50 of your sources.list file is malformed then try commenting out the 50'th line and do another update.  Take your pic of text editors, many of them should have the option of showing which line number you're on, or displaying the numbers to the left of your text.  To comment out the line just put a # in front of it.  You should be able to update apt from synaptic, if not just type in "sudo apt-get update" into your terminal.

If I may point out, you mentioned that this is a failure of our package management system.  I would like to welcome you to the open source community, where you too are a partial owner.  If you don't like it you can download the source code and change the way that it works.  Just like Wikipedia.  So now that you feel at home don't be affraid to comment about the functionality of "our" (as in includes you too) package management system.

If you don't like apt then you can try out other package managers.  Red-hat based distributions come with yum package manage, OpenSuse and others come with YaST package manager, and Linspire comes with Click'nRun (which also carries commercial applications that you can purchase).  There are a few others I can't think of, but those are the major ones.  Microsoft doesn't have one.  I don't know about Mac, but I assume you can install any of the above on it because it is a UNIX-based system.

---

### Post by Sardjen on 2007-02-05
I'll have to try a few different package managers, then.

TBH, I'm still getting the hang of things. I migrated over from Windows after using it my whole life, so in a while I'll be able to make a fair assessment of which system I prefer.

Synaptic's been good to me for the most part, though. I'm rather curious as to exactly why the error showed up in the first place, though. I'll have to avoid doing that again, whatever it was...:)

EDIT: I commented out the last two lines acting as root, and the problem seems to have resolved itself. Everything works fine now.

Thanks for all the help, guys. I feel a lot more confident with the terminal and stuff now.

---

