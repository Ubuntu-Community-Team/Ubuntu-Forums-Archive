---
title: "Add/Remove Applications trouble"
date: 2006-12-29
forum: Absolute Beginner Talk
---

### Post by Foolishgrunt on 2006-12-29
Let me start by warning you that I´m a helpless Windows slave, and that I´m still in my first few days of running Ubuntu. I´m also quickly finding out how truly clueless I am when it comes to Linux. Pleas take that into consideration and pardon my idiocy. :)

Here´s my problem. When I try to start the Add/Remove Applications program, I get an error message that goes something like this:

[I]**Failed to check for installed and available applications**
This is a major failure of your software management system. Check the file permissions and correctness of the file ´/etc/apt/sources.list´ and reload the software information: ´sudo apt-get update´.[/I]

That kinda scared me. So I opened a terminal and investigated the sources.list file. But of course, I have no idea what any of the stuff means or what I need to look for.

So then I decided to type ´sudo apt-get update´ and see what happens. When I did, I got another error message:

*Type '“deb' is not known on line 35 in source list /etc/apt/sources.list*

And that brings me back to the same problem: my sources.list file is apparently screwed up. So my question is... what the heck is wrong with it?

---

### Post by Tasu on 2006-12-29
Would you please post here your 35th line in that file (or the complete file)? So we can have a glance at it and find  if the line if messed up.

---

### Post by Foolishgrunt on 2006-12-29
Sorry, forgot that part. Here´s the complete file:
__________________________________________________

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted universe multiverse
deb [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/) edgy free non-free
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) edgy-security main restricted
#deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
&#8220;deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main&#8221;
## Automatix repo
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
deb [http://easyubuntu.cafuego.net](http://easyubuntu.cafuego.net) main easyubuntu

---

### Post by Tasu on 2006-12-29
ahaha! Heavily modified! ^_^ However, the problem are those double quotes, the line must read:

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

instead of:

“deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main”

Note the quotes... both trailing and the first character.

Bye and tell us if this has resolved your problem (I bet yes! ;-)

---

### Post by Foolishgrunt on 2006-12-29
Well, that worked. Thanks for your help, Tasu!

But now now I feel really stupid. Quote marks, huh? Maybe next time I´ll have a slightly less feather-brained question. :rolleyes:

---

