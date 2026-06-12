---
title: "new to bsd ,need advise which variant to choose"
date: 2008-11-22
forum: BSD
---

### Post by cmay on 2008-11-22
hi.
i have tried a pair of bsd variants in the past but not for so long. i have more than one old computer which i use to betatest distributions on so i uninstall and install often. i however would like to have a permanent bsd install on one of them. i have tried pc-bsd 7.0 but i did not find that very easy to relate to. i have had desktop bsd installed a couple of times (version 1.6) which i like. i have tried freebsd once but it was not easy to install so i almost regret i deleted that in favor for a linux beta distro. i have a openbsd boxset i must admit i simply cant figure out how to install. 
what i would like to ask from given experience level what distribution of bsd would you recommend. i use computers for simple things as a casual user. and i also learn unix programming from books as a hobby so this is my primary use for it. 
thanks for reading this and thanks in advance.

---

### Post by cardinals_fan on 2008-11-22
I have a few suggestions:

**DesktopBSD**: It's just FreeBSD with a GUI, which provides the same power of a FreeBSD system without *whimpers* *sysinstall*.  The best system to start out with.

**NetBSD**: My personal favorite.  Extremely minimal, leaving all configuration and customization up to the user.  Superb installer that leaves things alone for you to tweak.  Very clean base system with well-audited code.

Regular **FreeBSD** is okay, but I hate the installer and would recommend DesktopBSD instead (you can download a snapshot image with FreeBSD 7).  I like **OpenBSD**'s emphasis on binary packages over source-based software installation, but the system never worked well for me.  **DragonFlyBSD** is an extremely interesting system that is rapidly maturing.  They recently released a live DVD that is definitely worth a shot.

---

### Post by cmay on 2008-11-22
thanks. i have as said openbsd boxset i cant figure out to install. i have also the desktop bsd cd still so i am going to start with that. i have been reading about dragonfly bsd and orded a cd from a internet shop that deals with nice burned cd so i am maybe going to try that very soon. i did not know that the difference between installers was so great when i first got the boxset. but maybe i can get used to desktop bsd first. it is the 1.6 release of desktop bsd that is the latest right.
anyway thanks alot.

---

### Post by LateNiteTV on 2008-11-24
what do u mean when u say you cant figure out how to install it? did you look at the openbsd website for instructions?

---

### Post by chachawpi on 2008-11-24
OpenBSD has got to be the fastest installation of OS out there.  Hit enter a bunch of times, with the exception of changing a few of the default answers from NO to YES (Of course I want to continue the install, I put the damn disc in didn't I?)

Then you hit "a" a few times in combination with some other early letters in the alphabet.  Then a "q."  And finally some more enters.  I think there might be one more NO you have to change to a YES here as well.

Bam.

---

### Post by cmay on 2008-11-24
i read the install intructions and tried to do this right but still no luck.the trouble is to get the partion done. maybe i am too used to debian installers to see the logic. of course when i have the box set i paid for it then  i will want it installed some day. i am just not so great at bsd installs yet.i know how to install debian minix and freedos but this open bsd i have trouble with for some reason. i had free bsd installed which is a bit harder than debian in my experience or lack of.it is the label editor and the part about the partion i cant seem to figure out how to do. it blacks out on me when i go trough this part. 

thanks for the replies. i will post when i have found the bsd of choice. i like these systems once they are installed and running.

---

### Post by Sorivenul on 2008-11-24
I personally suggest FreeBSD, however, I do like OpenBSD, and if you have the set try it one more time.  [**This**]("http://www.openbsd101.com/installation.html") is the best guide I've found on OpenBSD installation.

---

### Post by chucky chuckaluck on 2009-01-24
> **chachawpi said:**
> OpenBSD has got to be the fastest installation of OS out there.  Hit enter a bunch of times, with the exception of changing a few of the default answers from NO to YES (Of course I want to continue the install, I put the damn disc in didn't I?)

Then you hit "a" a few times in combination with some other early letters in the alphabet.  Then a "q."  And finally some more enters.  I think there might be one more NO you have to change to a YES here as well.

Bam.

is it really that simple? (i'm guessing openbsd has some "if you don't feel like standing on your head" autoconfig options, yes?)

---

### Post by Sorivenul on 2009-01-24
> **chucky chuckaluck said:**
> is it really that simple? (i'm guessing openbsd has some "if you don't feel like standing on your head" autoconfig options, yes?)
Pretty much, yes. The few times I've tested OpenBSD I've had it setup in about 15 minutes from boot to hard disk login.

---

### Post by perlluver on 2009-01-24
One slight problem with FreeBSD, if you like flash, then you will need to run Firefox through wine.  Flash doesn't work, in FreeBSD yet.

---

### Post by JMJ_coder on 2009-01-24
> **chucky chuckaluck said:**
> is it really that simple? (i'm guessing openbsd has some "if you don't feel like standing on your head" autoconfig options, yes?)

When I do a NetBSD install, I spend about 5 minutes setting the configuration, about 5-10 minutes waiting for it to actually install and about 1 more minute doing the post install (set timezone, root password, etc.).

---

### Post by mips on 2009-01-25
For those wanting a bootable install cd of OpenBSD I wrote a guide a while back for 4.1, just adapt it for 4.4.

[http://ubuntuforums.org/showthread.php?t=554486&highlight=OpenBSD](http://ubuntuforums.org/showthread.php?t=554486&highlight=OpenBSD)

.

---

### Post by cardinals_fan on 2009-01-25
> **jmj_coder said:**
> when i do a netbsd install, i spend about 5 minutes setting the configuration, about 5-10 minutes waiting for it to actually install and about 1 more minute doing the post install (set timezone, root password, etc.).
+1

---

### Post by chucky chuckaluck on 2009-01-25
> **perlluver said:**
> One slight problem with FreeBSD, if you like flash, then you will need to run Firefox through wine.  Flash doesn't work, in FreeBSD yet.

ah, the end. thanks.

---

### Post by cmay on 2009-01-25
> **perlluver said:**
> One slight problem with FreeBSD, if you like flash, then you will need to run Firefox through wine.  Flash doesn't work, in FreeBSD yet.
i had never installed flash in debian before a couple of days ago for the fun of it. i like to avoid the restricted stuff as much as i can. so it wont hardly be a problem. by the way , i have played around a bit with desktop bsd in the meantime. i am going to use bsd some more some other time as i have decided upon and installed  jaunty jackaope on this computer i had free to play with other distros and systems right now.

---

### Post by cammin on 2009-01-25
linux-flashplugin works fine for me in FBSD

---

### Post by chucky chuckaluck on 2009-01-26
> **cammin said:**
> linux-flashplugin works fine for me in FBSD

works for youtube?

---

### Post by cardinals_fan on 2009-01-26
> **chucky chuckaluck said:**
> works for youtube?
Flash 7 works flawlessly, 9 works with some tweaking/swearing/luck.

---

### Post by Sorivenul on 2009-01-26
> **cardinals_fan said:**
> Flash 7 works flawlessly, 9 works with some tweaking/swearing/luck.
+1. I've preferred Flash 7 since I started using the BSDs. It won't play some "newer" things, but I haven't had many issues at all with YouTube.

---

### Post by chucky chuckaluck on 2009-01-26
> **cardinals_fan said:**
> Flash 7 works flawlessly, 9 works with some tweaking/swearing/luck.

the swearing and luck i've got covered. it's the tweaking that gets me.

---

