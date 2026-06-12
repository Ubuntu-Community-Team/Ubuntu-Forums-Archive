---
title: "Idiot Makes Programming Mistake (Film at eleven)"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by Xaviar on 2006-03-01
Hello all.  I am 3 days into running Ubuntu and I should point out that the last time I used any kind of computer code was on an Apple IIe at high school (gives away my age doesn't it?).  I would also like to thank everyone at this site for the help I received in another thread and for the cut & paste approach to making it easier for dolts like me to ease into the Command Line experience.  Like so many here I am very new to this so please bear with me.  Here's where I came undone.

I installed Ubuntu (Hoary Hedgehog) as the sole OS on my previously Windows computer (I'm done with Windows) from an old Live CD that came free with a magazine (APC magazine I think) and found that the Thunderbird & Firefox packages were out of date.  Some helpful folks here assisted me with getting sound on my Totem media player and sent me in the direction of the Unofficial Ubuntu 5.04 Starter Guide so I could make the approriate changes to allow me to update to a later version of Thunderbird & Firefox and to update from Hoary to Breezy.  I took the advice of the section called "How to add extra repositories" which was as follows.  I've added the bold text to differentiate between the directions and the exact code (I'm not shouting).

**Go to Applications > System Tools > Terminal and click. Then type the following**

sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list

[B]Then press return.
I did this and the text editor opened with some text in it. The advice went on to say I should find the following section of text[/B]

## Uncomment the following two lines to fetch updated software from the network
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

[B]and replace it with the following
[/B]
## Uncomment the following two lines to fetch updated software from the network
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) hoary universe

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) hoary multiverse

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

**Then save the file. ** I did all this and now the Synaptic Package Manager says it can't find things and that I should check the address.  Now I do remember that before I foolishly pasted over the original text it seemed to contain a **www** address with an **au** prefix while the text I pasted over it contains an **us** prefix.  As I am in Australia I assume that **au **address was required and I cannot remember what it was.  Does anybody here know what text Australians should paste to add extra repositories?  Can I fix this?  Sorry to be a bother but the only other computers I've used were IBMs running Windows (I never used DOS or MS-DOS) and an Atari STe before that (which used a GEM Desktop) so typing code is entirely new to me.  I'd also like to thank everyone here once again for holding my hand while I blunder through these teething problems.  Any help would be appreciated.  The text of the warning I receive when I open the Synaptic Package Manager is as follows

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

---

### Post by tmahmood on 2006-03-01
Hi
I think u just need to replace

deb [http://**us](http://**us)**.archive.ubuntu.com/ubuntu hoary universe
deb-src http://[COLOR="black"]**us**[/COLOR].archive.ubuntu.com/ubuntu hoary universe

with
deb [http://**au](http://**au)**.archive.ubuntu.com/ubuntu hoary universe
deb-src [http://**au](http://**au)**.archive.ubuntu.com/ubuntu hoary universe

so on...


and the warning you are getting is not because of this...

---

### Post by Xaviar on 2006-03-01
Okay, thanks.  I'll try that.  Any idea what the warning is about?

---

### Post by Gustav on 2006-03-01
instead of the line:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted

use the line:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary-backports main universe multiverse restricted

---

### Post by Madpilot on 2006-03-01
Ubuntu's **us.** archives have been having various trouble, you might have run into that...

So have the **ca.** archives - I've had to use the main archives for a couple of weeks now... :p

---

