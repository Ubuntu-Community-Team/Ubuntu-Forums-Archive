---
title: "Nothing will download."
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by wtfitsRICK on 2007-12-12
Yeah.  To me, this is a pretty major problem.  I have the Compaq Presario C700 with the Broadcom wireless card that seems to have so many problems.  I installed Gutsy on a partition.  I can use the internet if I connect directly with ethernet.  I downloaded a patch or something that said should enable my wireless card, but it didn't work.

My main problem right now is basically nothing will download.  Firefox plugins won't download.  If I go to  Add/Remove Applications, and I try to install any program it all, it tells me that the list needs to refresh.  I click refresh, and it says it's doing something (it had the number six involved, but it goes too fast), and then it just takes me back to where I was.  If I try to install the program, it tells me to do it all over again.  I'm pretty sure this isn't just me being new and not understanding much about Ubuntu.  From what I understand, the add/remove applications thing is supposed to be one of the user-friendly, easy features.  :-/  Thanks for any help you can give.  Even if it's just "downgrade to Feisty."  Anyone know if this would at least be fixed by getting Feisty?  I hope there're some fixes to Gutsy soon.  Overall, it seems a lot of people are disappointed.

---

### Post by PurposeOfReason on 2007-12-12
First, try ```
ping -c 3 www.google.com
``` and see if you are able to do that. Looks like below if it worked. If so, post your /etc/apt/sources.list.

```

shawn@reasons:~$ ping -c 3 www.google.com
PING www.l.google.com (72.14.253.147) 56(84) bytes of data.
64 bytes from po-in-f147.google.com (72.14.253.147): icmp_seq=1 ttl=243 time=51.6 ms
64 bytes from po-in-f147.google.com (72.14.253.147): icmp_seq=2 ttl=243 time=51.3 ms
64 bytes from po-in-f147.google.com (72.14.253.147): icmp_seq=3 ttl=243 time=51.4 ms

--- www.l.google.com ping statistics ---
3 packets transmitted, 3 received, 0% packet loss, time 1998ms
rtt min/avg/max/mdev = 51.379/51.498/51.627/0.280 ms

```

---

### Post by wtfitsRICK on 2007-12-28
I got this:
rick@rick-laptop:~$ ping -c 3 [www.google.com](www.google.com)
PING [www.l.google.com](www.l.google.com) (64.233.167.104) 56(84) bytes of data.
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=1 ttl=246 time=26.5 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=2 ttl=246 time=27.4 ms
64 bytes from py-in-f104.google.com (64.233.167.104): icmp_seq=3 ttl=246 time=27.6 ms

---

### Post by PurposeOfReason on 2007-12-28
So you're connected. What does ```
cat /etc/apt/sources.list
``` say?

---

### Post by wtfitsRICK on 2007-12-28
```
rick@rick-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Mind you, this is on a wired connection.

---

### Post by PurposeOfReason on 2007-12-28
There's your problem. All of your sources are commented out and not being used. Remove the # in front of anything that starts with a #deb-src or just #deb. Then run sudo apt-get update and sudo apt-get upgrade.

---

### Post by wtfitsRICK on 2007-12-28
I'm pretty sure I have no idea what you just said.  I understand the taking # out, I guess.  But what's sudo apt-get update and all that?

---

### Post by PurposeOfReason on 2007-12-28
Okay, the # in front of those lines means "ignore me" so when ubuntu installed, it didn't have a connection and commented (#) them out. By removing the comment in front of the sources (the deb and deb-src ones) it's letting you use them. The sudo apt-get update means re-read the file and the sudp apt-get upgrade means upgrade the system with the new sources.

---

### Post by wtfitsRICK on 2007-12-28
So, where do I take those #s out?  And, how do I do the sudo get stuff?
I'm sorry for my incompetence.  I haven't much experience with Ubuntu, especially when it comes to the terminal.  thanks for your help so far.

---

### Post by PurposeOfReason on 2007-12-28
I'll do it for you, just as long as you look at it and see what I did.
```
rick@rick-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
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
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
```

Copy paste that over what you already had. So open up a terminal (don't be afraid) and type```
sudo gedit /etc/apt/sources.list
```. That means to open that file with a text editor called gedit. Delete the entire file and then past what I just did above into it. Save and close. Then run the two commands (update and upgrade) into the terminal.

---

### Post by wtfitsRICK on 2007-12-28
I feel extremely stupid.  I'm trying really hard to understand what's going on.  I see what you did to the first code.  So I get the removing #.  After that, I'm not sure what to do.  Am I supposed to copy the big code and paste that over what it originally was?  If not, can I just delete the #s like you said?
After that, what am I to do with the sudo code and text editor?

---

### Post by PurposeOfReason on 2007-12-28
Okay, once you have the file open (where you can edit it), you can either paste what I did over it, or delete it yourself. After that, open up a terminal and type in the codes

sudo apt-get update
sudo apt-get upgrade

---

### Post by wtfitsRICK on 2007-12-28
Am I supposed to save the edited file somewhere?

---

### Post by PurposeOfReason on 2007-12-28
What do you mean? You're just going to open up the original file, take out the comments, and then save it.

---

### Post by wtfitsRICK on 2007-12-28
Okay, so I took out the comments, saved it in my folder, pasted the codes in the terminal, and now what do I do?  I tried downloading something again, and it didn't work.

---

### Post by ugm6hr on 2007-12-28
This explains how to enable all the repositories for Ubuntu.

Most people find it easier to follow a point-and-click solution....

In **Applications->Add/Remove...** (presumably where you were having the problems before):
Click **Preferences**
A new window **Software Sources** will open
Select the **Ubuntu Software** tab
Make sure the top 4 boxes are ticked (as screenshot) & Click** Close**

Then try to install an application again.  Hopefully it will now work (if not - you might have to click on reload in Synaptic)

Please note - this will only work with functioning internet.

---

### Post by wtfitsRICK on 2007-12-28
Oh, wow.  Thanks.  None of those boxes were checked.  So far, this seems to be working.  It's actually installing a game currently.  I'll check in a minute if it will install my restricted driver as well.
Thanks to both of you.

EDIT:
Okay, this worked to an extent.  I installed a game, and it works.  I installed a driver, and I'm not sure if it works.  However, that just may be my Broadcom wireless card.  I can also install Firefox plugins.  Thing is, I installed a flash plugin, and it makes things CRAZY.  It seems to activate a bunch of clickable things rapidly.  For example: [www.purevolume.com/thecolorfred](www.purevolume.com/thecolorfred)  It switches back and forth between the playlist and albums and all that.
That's no fun.

---

