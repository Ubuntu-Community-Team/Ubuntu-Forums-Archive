---
title: "apt-get keeps wanting to upgrade libc6"
date: 2011-07-04
forum: Any Other OS
---

### Post by studout on 2011-07-04
When I try to use apt-get to install wine or eagle, apt-get demands to **"**upgrade**"** libc6 in the process.  On a previous install of Intrepid/8.10, I made the mistake (ONCE!) of allowing it to do this; it rendered my system unusable, and I was forced to reinstall.  I am running Linux Mint 10, but as I mentioned, this bug has existed at least since Intrepid/8.10.

After I first install the machine, apt-get is willing to install big packages like wine, but after the machine has been installed for a while, apt-get decides that libc6 and several other packages need to be upgraded also.  I am not sure if this is a function of the install getting old on the computer, or the install getting old relative to the repositories.

It has been brought to my attention that with 300+ "not upgraded" packages, my system is "out of date".  I am not going to let apt-get **"**upgrade**"** working packages so that I get all the latest regression bugs and end up with things getting broken.  That's another mistake I will only make ONCE!

Is there a workaround for this apt-get bug?

```
user@comp ~/Desktop $ sudo apt-get install eagle
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  eagle-data ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5
  lib32stdc++6 lib32v4l-0 lib32z1 libasound2 libc-bin libc-dev-bin libc6
  libc6-dev libc6-i386
Suggested packages:
  lib32asound2-plugins glibc-doc
The following NEW packages will be installed:
  eagle eagle-data ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5
  lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386
The following packages will be upgraded:
  libasound2 libc-bin libc-dev-bin libc6 libc6-dev
5 upgraded, 11 newly installed, 0 to remove and 331 not upgraded.
Need to get 82.6MB of archives.
After this operation, 248MB of additional disk space will be used.
Do you want to continue [Y/n]? ^C
user@comp ~/Desktop $
.
.
.
.
.lines added to separate the two invocations of apt-get
.
.
.
.
user@comp ~/Desktop $ sudo apt-get install wine
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  gnome-exe-thumbnailer ia32-libs icoutils lib32asound2 lib32bz2-1.0 lib32gcc1
  lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32v4l-0 lib32z1 libasound2
  libc-bin libc-dev-bin libc6 libc6-dev libc6-i386 libwbclient0 samba
  samba-common smbclient ttf-mscorefonts-installer ttf-symbol-replacement
  ttf-umefont ttf-unfonts-core winbind wine1.2 wine1.2-gecko
Suggested packages:
  libterm-readline-gnu-perl libterm-readline-perl-perl lib32asound2-plugins
  glibc-doc openbsd-inetd inet-superserver smbldap-tools ldb-tools cifs-utils
Recommended packages:
  winetricks wisotool
The following NEW packages will be installed:
  gnome-exe-thumbnailer ia32-libs icoutils lib32asound2 lib32bz2-1.0 lib32gcc1
  lib32ncurses5 lib32nss-mdns lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386
  ttf-mscorefonts-installer ttf-symbol-replacement ttf-umefont
  ttf-unfonts-core winbind wine wine1.2 wine1.2-gecko
The following packages will be upgraded:
  libasound2 libc-bin libc-dev-bin libc6 libc6-dev libwbclient0 samba
  samba-common smbclient
9 upgraded, 20 newly installed, 0 to remove and 327 not upgraded.
Need to get 154MB of archives.
After this operation, 383MB of additional disk space will be used.
Do you want to continue [Y/n]? ^C
user@comp ~/Desktop $
```

---

### Post by mörgæs on 2011-07-04
Just because libc6 made trouble two years ago you should not expect it to happen again. You are risking more (including security and privacy) by runnig a system which is not updated.

My advice is doing a full update. After this we can focus on installing Wine.

---

### Post by studout on 2011-07-04
I am not going to "upgrade" packages that are not broken.  Period.  Are there any possible solutions that fix apt-get so that it will do the INSTALL I commanded it to do, rather than going off into the weeds and trying to do uncommanded "upgrades"?

---

### Post by studout on 2011-07-04
Found it.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

---

### Post by dFlyer on 2011-07-04
If your not willing to update than your running an out of date system and could be at risk. If your not willing to update, why ask the question? Updates fix bugs and security holes and are highly recommended.

---

### Post by studout on 2011-07-04
[ugh, sigh]

The part of my question pertaining to upgrading was how to get apt-get to do an INSTALL without demanding to "UPGRADE" other packages.

The link I posted gives instructions on how to accomplish that, but it does not cure the problem of apt-get wanting to needlessly change packages.  I am still feeling uneasy about letting apt-get run on my system when it is clearly has a bug, or is at the very least misconfigured.

Was any of what I said, in any of my posts; unclear?  If I am speaking unclearly, I would like to know so that I might speak more clearly in the future.  I ask because I post a question about how to get apt-get to work properly, and why I don't want it to do an upgrade of anything (or so I think that is what I said), and then people come along and rather than answering my question about apt-get; tell me to upgrade, how it won't hurt anything, and how it's so important.

---

### Post by dFlyer on 2011-07-04
> **studout said:**
> [ugh, sigh]

The part of my question pertaining to upgrading was how to get apt-get to do an INSTALL without demanding to "UPGRADE" other packages.

The link I posted gives instructions on how to accomplish that, but it does not cure the problem of apt-get wanting to needlessly change packages.  I am still feeling uneasy about letting apt-get run on my system when it is clearly has a bug, or is at the very least misconfigured.

Was any of what I said, in any of my posts; unclear?  If I am speaking unclearly, I would like to know so that I might speak more clearly in the future.  I ask because I post a question about how to get apt-get to work properly, and why I don't want it to do an upgrade of anything (or so I think that is what I said), and then people come along and rather than answering my question about apt-get; tell me to upgrade, how it won't hurt anything, and how it's so important.

I guess, whats miss configured? Your system? Why are you so worried? Are you running a mixed distro system? If you update a program that needs a more updated lib it will install that lib, otherwise the program may not run.

Things may have gone wrong in the past, that doesn't mean they will now. If you haven't run apt-get autoclean you older version should still be in archives /var/cache/apt/archives which gives you the ability to reinstall the old version.

If you pin a version, and you try to install a program that requires a newer version of a lib to run it will not run until you install the new lib. So what your trying to do may not be possible.

I still say update all your program and lib. If your worried about it get clonezilla and clone your system first.

---

### Post by studout on 2011-07-04
Like I said in the OP, I am running Linux Mint 10, but this is the same problem I have had as far back as Ubuntu 8.10.

Telling apt-get to be verbose gives me this
```
snip
wine1.2 (1.2.2-0ubuntu2~maverick2)
snip
libc6 (2.12.1-0ubuntu6 => 2.12.1-0ubuntu10.2)
snip
```
Looking at the page for the version of wine to be installed
[http://packages.ubuntu.com/maverick/wine1.2](http://packages.ubuntu.com/maverick/wine1.2) we see that it wants libc6 >= 2.11
I have libc6 2.12.1  There is apparently a newer version of libc6, but the version I have is also clearly meeting the version spec required for the version of wine to be installed... so why apt-get is wanting to upgrade to a newer version is unclear to me.

I read a long time ago that messing with the runtime C library, the library that things like bash and ls dynamically link against, is a very bad idea.  I really needed to get something installed, so I let apt-get upgrade libc6 and it destroyed my system, I tried to fix it, but eventually just ended reinstalling.  Even to this day, that system does not work as well as it did on the first install.  That incident with apt-get really left a bad taste in my mouth.  I hope you can imagine why there is no way on Earth I will let it touch libc6 again.

---

### Post by bdentremont on 2011-07-04
> **studout said:**
> [ugh, sigh]

The part of my question pertaining to upgrading was how to get apt-get to do an INSTALL without demanding to "UPGRADE" other packages. ...

Apt-get is not doing a general upgrade nor is this a bug.  It is attempting to furfill your request to install "eagle".  The package "eagle" depends upon "libc6-i386", so apt-get proposes installing the current version from the repository.  The newly downloaded "libc6-i386" requires a matching version (i.e. current) of "libc6", so it needs to be upgraded to current to satisfy your initial request.

If you had a really good reason to avoid a particular version, such as a known conflict with something else, you could investigate the version dependencies thoroughly, find and install specific versions to your liking. However, you are FAR more likely to run into serious problems that way than if you let apt-get do its job.

---

### Post by studout on 2011-07-04
Thank you, that makes a lot of sence why it would be wanting to adjust libc6.
I agree that pinning/holding is risky.. which is why I have not done anything.

What irks me is why at one point, apt-get is willing to install wine very simply without installing/upgrading all kinds of other packages, and at another point, now, it demands to upgrade libc6.

As I have mentioned before, I have had a really bad experience allowing apt-get to mess with libc6... that is not a risk I will take again.  PERIOD.
Also, as I have said before, I have had bad experiences upgrading without a strong reason to.  That is another thing I will not do again.  PERIOD.

Perhaps apt-get's willingness to install wine without a huge fuss on one occasion, and not others (now) is due to the requirements of the particular version of wine proposed to be installed.  The answer would then seem to be to find a list of wine versions and try increasingly old versions until one is found that will install.

I am going to repeatedly repeat myself but as I have said before; apt-get is sometimes willing to install wine without a huge fuss, and other times not.  I need to find my way to one of the "without a huge fuss" times.

Anyone know where there is a comprehensive list of versions of wine that I could tell apt-get to install?

---

### Post by bdentremont on 2011-07-05
> **studout said:**
> ...  Anyone know where there is a comprehensive list of versions of wine that I could tell apt-get to install?

The Synaptic Package Manager on my computer lists the dependency of Wine 1.2.2 (current) as lib6c-i386 >= 2.6-1, which is quite old.  What you need is not an older version of wine, but to install the version of lib6c-i386 which corresponds to your existing lib6c.  If an acceptable version of lib6c-i386 is already installed, apt-get will not try to grab a new copy and will have no need to upgrade lib6c.

You might be able to download the deb file at [http://packages.ubuntu.com](http://packages.ubuntu.com) or point your package manager at your installation CD.  I can't provide any more help there, since I keep my system up-to-date.

I've never had a system crash as a result of an update, but have noticed a lot of stuff get fixed.  I'm sorry you had a problem in the past, but I do agree with the others that updating, while it has the potential for problems, is on the whole a good thing.

In any case, good luck with this.

---

### Post by Perfect Storm on 2011-07-05
Moved to Other OS/Distro Talk.

---

### Post by el_koraco on 2011-07-05
Try

```
sudo apt-get install --no-install-recommends <package>

```
run it with the simulate switch, in order to test


```
sudo apt-get install --no-install-recommends <package> --simulate

```

---

### Post by studout on 2011-07-05
bdentremont; Thank you, I like that idea.
Maybe I will be able to manually install the version of each of the depends that will smoothly install, and then after that, be able to get wine/eagle to smoothly install.

el_koraco; Thank you.
Here is the output.
```
user@comp ~/Desktop $ sudo apt-get install --no-install-recommends eagle --simulate
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  eagle-data ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libasound2 libc-bin libc-dev-bin
  libc6 libc6-dev libc6-i386
Suggested packages:
  lib32asound2-plugins glibc-doc
The following NEW packages will be installed:
  eagle eagle-data ia32-libs lib32asound2 lib32bz2-1.0 lib32gcc1 lib32ncurses5 lib32stdc++6 lib32v4l-0 lib32z1 libc6-i386
The following packages will be upgraded:
  libasound2 libc-bin libc-dev-bin libc6 libc6-dev
<SNIP>
```

---

### Post by studout on 2011-07-05
Solved!  YEA! :D

I did a bit of web searching and found that "aptitude -v show libc6-i386" would show me all of the possible versions to install.  The last one shown was the version compatible with my currently installed version of libc6.  I ran "sudo apt-get install libc6-i386=2.12.1-0ubuntu6" and apt-get smoothly and cleanly installed exactly that package.  I manually installed all of the other packages that apt-get wanted to upgrade to install wine.  All but lib32asound2 installed cleanly.  I had to repeat the "aptitude -v show" version finding process to get apt-get to install lib32asound2 cleanly without trying to upgrade other things.  After that, I again told apt-get to install wine, and all apt-get wanted to upgrade were four things of or relating to samba.  Looking back at my logs, I found that on a previous successful install of wine, samba was upgraded also.  I allowed apt-get to run, it upgraded samba and installed wine.  As of now, wine appears to be running smoothly.

**bdentremont**; Thank you so much for the hint about needing a compatible version of libc6-i386.  Additionally, I was not comfortable with putting a hold on the packages I did not want it to upgrade.  I didn't know what bad would happen; but I am glad to know that my discomfort was founded, and what would have happened.  Thank you again.

---

### Post by studout on 2011-07-05
Ugh well.. Wine appears to be working, but as a part of installing wine, apt-get did a lot of things relating to the system fonts.  The fonts displayed in Firefox, at least on some of the pages I regularly visit, are noticeably, albeit not annoyingly; different.

---

