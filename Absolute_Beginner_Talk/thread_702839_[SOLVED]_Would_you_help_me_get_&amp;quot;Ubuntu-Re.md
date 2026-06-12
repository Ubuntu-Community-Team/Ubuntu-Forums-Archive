---
title: "[SOLVED] Would you help me get &amp;quot;Ubuntu-Resticted-Extras&amp;quot; (terminal couldn't find pack"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-20
[COLOR="Green"]Would any of you please tell me what should I do to get that package that I'm required to install on my computer to get the ubuntu-restricted-extras?

Here's a relevant screenshot of the message I got when I typed *sudo apt-get install ubuntu-restricted-extras* in my terminal:[/COLOR]
[IMG]http://img229.imageshack.us/img229/5209/screenshoterrormessageal9.png[/IMG]

---

### Post by Zimmer on 2008-02-20
What you may be looking for is a way to add the repositories that the 'Restricted Extras ' reside in.
I take it you followed this :
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

You may need to edit your etc/apt/sources.list   and  un-comment a couple of lines to enable the relevant repositories.

---

### Post by stoneybroke on 2008-02-20
Hi just go to SYSTEM>ADMINISTRATION then click on the RESTRICTED PACKAGES MANAGER you should get ether a downloadable files or a message that says you do not need them.

---

### Post by spiderbatdad on 2008-02-20
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

---

### Post by Zimmer on 2008-02-20
Thanks, Spiderbatdad, I posted a quick reply based on Dapper, but as I was looking for a better bit of documentation I discovered that Gutsy has the ability to do it differently, I refreshed the page and , Voila! the answer...from you...

---

### Post by ahuman on 2008-02-20
***This message is In reference to the link of that forum-topic inserted earlier, here:***
[http://ubuntuforums.org/showthread.php?t=693309](http://ubuntuforums.org/showthread.php?t=693309)

> **Crashmaxx said:**
> There is an easier way to do this. Just go to System>Administration>Synaptic Package Manager and select Settings>Repositories.

Under the "Ubuntu Software" tab, just check the sources you want. In this case, make sure Universe and Multiverse are selected. Then click "Close" and "Reload", that's it.

Now all the apps will show up in Synaptic Package Manager, Add/Remove, and when you use apt-get.
[B][COLOR="Purple"]Would any of you tell me what you believe Crashmaxx meant by "reload"? Does it mean "Apply" or  "Restart computer"?

Also: Please tell me if this screenshot would indicate that Ubuntu-Restricted-Extras have been successfully/perfectly installed:[/COLOR][/B]

[img]http://img54.imageshack.us/img54/2811/screenshotsynapticpackazs7.png[/img]

---

### Post by Zimmer on 2008-02-20
From the screenshot it seems the restricted extras are loaded..   the little box on the left of it is green.

And if you look at the tools there is a 'Reload ' button. This action refreshes the repository software lists available.
Hover the mouse over the button for a help hint...

EDIT:  When installing new packages you mark them fist, then click 'Apply' to download and install the marked packages.

---

### Post by oedha on 2008-02-20
for me : reload means...you reload the database list of the pointing server.....in order to make enable to install it.......doesnt mean to be restart....

---

### Post by oldos2er on 2008-02-20
> **ahuman said:**
> [COLOR=Green]Would any of you please tell me what should I do to get that package that I'm required to install on my computer to get the ubuntu-restricted-extras?

Here's a relevant screenshot of the message I got when I typed *sudo apt-get install ubuntu-restricted-extras* in my terminal:[/COLOR]
[IMG]http://img229.imageshack.us/img229/5209/screenshoterrormessageal9.png[/IMG]

 If you're still having a problem, could you please post the output of "cat /etc/apt/sources.list"?

---

### Post by ahuman on 2008-02-20
> **oldos2er said:**
> If you're still having a problem, could you please post the output of "cat /etc/apt/sources.list"?
[COLOR="Navy"]Yes, I posted that output (below this paragraph). Would you or someone else please tell me what's the best way to test the ubuntu-restricted-extras to see if they actually work? Should I try to play a DVD or something like that (is that a decent way of testing those "extras"?) ? [/COLOR]
```
truthseeker@4XLDLD1:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted
deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

```

---

### Post by aysiu on 2008-02-20
Here's a step-by-step tutorial with screenshots:
[http://psychocats.net/ubuntu/nonfree](http://psychocats.net/ubuntu/nonfree)

---

### Post by oldos2er on 2008-02-20
Your sources.list looks ok; but there's one more step if you want to play commercial DVDs. Run this command in a terminal: 

sudo wget [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list) -O /etc/apt/sources.list.d/medibuntu.list

 Then run:  wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

 And one more: sudo aptitude install libdvdcss2

 You should be good to go now.

---

### Post by jcitguy78 on 2008-02-20
not sure if this is a good way but find a website that runs Java, that might help

---

### Post by ubuntu27 on 2008-02-21
So it seems that you installed Ubuntu when you had no internet connection. Your source.list works. 
I did a little clean-up. Try this:

```
gksudo gedit /etc/apt/sources.list
```

Now remove everything in there, and copy and paste the following:

```
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.


deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse

deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted

deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe

deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://archive.ubuntu.com/ubuntu/ gutsy main universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates universe main restricted

deb http://security.ubuntu.com/ubuntu/ gutsy-security universe main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Save, and exit.

Now reload (update the software list)

```
sudo apt-get update
```

Now you should have no problem. :)


From the screenshots that you posted earlier, it seems that you were successful at installing the restricted-extras packages. 
Go to a website that contains Flash, and see if it works. Also try to play some multiemdia (e.g. listen to music)

---

