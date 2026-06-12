---
title: "how to upgrade from sqeeze to  wheezy?"
date: 2012-07-19
forum: Any Other OS
---

### Post by vykuntamsrinivas on 2012-07-19
hi,friends.
  i am using sqeeze now and i want to move to wheezy.I  have googled it and find so many answers,but i added   third party repos  to my sources.list . I think that  it may give  problems  at time of   upgrade.I am pasting sources.list
```
deb cdrom:[Debian GNU/Linux 6.0.5 _Squeeze_ - Official i386 CD Binary-1 20120512-13:45]/ squeeze main

#security repos
deb http://security.debian.org/ squeeze/updates main
deb-src http://security.debian.org/ squeeze/updates main
deb http://security.debian.org/ squeeze/updates main contrib non-free
deb http://mozilla.debian.net/ squeeze-backports iceweasel-release

#backports
deb http://backports.debian.org/debian-backports squeeze-backports main
deb http://backports.debian.org/debian-backports squeeze-backports main contrib non-free

#mirror
deb http://ftp.us.debian.org/debian squeeze main contrib non-free

#multimedia
deb ftp://ftp.deb-multimedia.org squeeze main non-free

```can any one please give a   brief on the upgrade process?

---

### Post by cortman on 2012-07-19
Debian has a [great forums of their own]("http://forums.debian.net/")- why not ask there?

The mailing lists are also very active.

---

### Post by vykuntamsrinivas on 2012-07-19
> **cortman said:**
> Debian has a [great forums of their own]("http://forums.debian.net/")- why not ask there?

The mailing lists are also very active.

hi,cortman.
                   i  have made a post in both the forums to get a quick reply.This forum has name other OS/DISTRO talk,so i think this is the right place to get help.Is nt it?

---

### Post by cortman on 2012-07-19
> **vykuntamsrinivas said:**
> hi,cortman.
                   i  have made a post in both the forums to get a quick reply.This forum has name other OS/DISTRO talk,so i think this is the right place to get help.Is nt it?

Yes, you got the right place- just saying you'll have better luck in a forum dedicated to Debian. I see you've done so.

I'm a novice when it comes to Debian but would you be able to simply change all references of "squeeze" to "wheezy"?

---

### Post by vykuntamsrinivas on 2012-07-19
i   am not sure about it,but i have seen that repos  have the string "testing " and "wheezy"  both in most of  web pages i refered.So many posted in internet that  "change repos of sqeeze to wheezy, and then  update and upgrade it".But i have some non free/contrib softwares installed in my sqeeze,i think they may get distrub while upgrading(if i dont do upgrade as per my sources.list).

---

### Post by wheeze on 2012-07-19
Your sources are actually pretty standard, you can just change references of squeeze to wheezy. However, there are some repos that are not yet in effect for wheezy so you could simply comment those out. I also see some duplication that could be removed to clean things up.

According to mozilla.debian.net you have to add the Debian experimental repo to get updated Iceweasel, but that can lead to other problems so I don't list it here. You can get instruction on mozilla.debian.net if you wish to do so.

Any particular reason for the src repo in Security? Just curious.

I would backup your original sources.list, call it sources.list.squeeze for example, then modify sources.list to look like this:

```
#security repos
deb http://security.debian.org/ wheezy/updates main contrib non-free
deb-src http://security.debian.org/ wheezy/updates main contrib non-free

#mirror
deb http://ftp.us.debian.org/debian wheezy main contrib non-free

#multimedia
deb ftp://ftp.deb-multimedia.org wheezy main non-free
```

---

### Post by wheeze on 2012-07-19
> **vykuntamsrinivas said:**
> i   am not sure about it,but i have seen that repos  have the string "testing " and "wheezy"  both in most of  web pages i refered.So many posted in internet that  "change repos of sqeeze to wheezy, and then  update and upgrade it".But i have some non free/contrib softwares installed in my sqeeze,i think they may get distrub while upgrading(if i dont do upgrade as per my sources.list).

testing and wheezy are currently the same distribution. wheezy is an alias for testing. When it gets released it will re-aliased to stable. The contrib/non-free repos are maintained by Debian so your added software will be upgraded to the Debian-approved version for your distribution.

Yours looks to be a fairly standard upgrade.

---

### Post by vykuntamsrinivas on 2012-07-19
thanks for reply  friends!
         What you are telling is right,i justed replaced the word  squeeze by testing/wheezy.Its workiing  but small update,its asking  public key for multimedia repo for that i just did:#apt-get install debian-multimedia-keyring.contents of my sources.list are
```
############################
# Testing US mirror:
deb http://ftp.us.debian.org/debian/ testing main contrib non-free
#deb-src http://ftp.us.debian.org/debian/ testing main contrib non-free

# Testing Security Updates
deb http://security.debian.org/ testing/updates main contrib non-free

#Testing Proposed Updates
deb http://ftp.debian.org/debian/ testing-proposed-updates main contrib non-free


## Multimedia ##
# Marillat For info visit http://www.debian-multimedia.org
deb http://www.debian-multimedia.org testing main non-free############################

```
this  may help others : 
[http://ubuntuforums.org/showthread.php?t=1818476](http://ubuntuforums.org/showthread.php?t=1818476)
any way i am doing upgrade now.I may be back if i have any errors later.....

---

