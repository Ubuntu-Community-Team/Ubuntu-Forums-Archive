---
title: "Ign problems?"
date: 2005-07-28
forum: Bug Reports / Support
---

### Post by Farina on 2005-07-28
First of all, I have searched the forum, but have no found no advice to fix my problem.  After following the instructions on the backports page as well as looking at some sources.list recipes on this forum, I have been unable to make my apt grok the backports repository.

I offer a transcription of both a log of the update and my sources.list file:
sources.list:
```
#############Ubuntu Hoary##############
deb http://archive.ubuntu.com/ubuntu/ hoary main
deb http://archive.ubuntu.com/ubuntu/ hoary universe
deb http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb http://archive.ubuntu.com/ubuntu/ hoary restricted

deb-src http://archive.ubuntu.com/ubuntu/ hoary main
deb-src http://archive.ubuntu.com/ubuntu/ hoary universe
deb-src http://archive.ubuntu.com/ubuntu/ hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu/ hoary restricted


##############Ubuntu Security##############
deb http://security.ubuntu.com/ubuntu/ hoary-security main
deb http://security.ubuntu.com/ubuntu/ hoary-security restricted
deb http://security.ubuntu.com/ubuntu/ hoary-security universe
deb http://security.ubuntu.com/ubuntu/ hoary-security multiverse

deb-src http://security.ubuntu.com/ubuntu/ hoary-security main
deb-src http://security.ubuntu.com/ubuntu/ hoary-security restricted
deb-src http://security.ubuntu.com/ubuntu/ hoary-security universe
deb-src http://security.ubuntu.com/ubuntu/ hoary-security multiverse


##############Backports ##############
deb http://ubuntu-backports.mirrormax.net/ hoary-backports main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-backports-staging main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras main universe multiverse restricted
deb http://ubuntu-backports.mirrormax.net/ hoary-extras-staging main universe multiverse restricted
```

the log of apt-get update:
```
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging Release.gpg
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Hit http://security.ubuntu.com hoary-security Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging Release
Hit http://archive.ubuntu.com hoary Release
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://archive.ubuntu.com hoary/main Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://security.ubuntu.com hoary-security/multiverse Sources
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
Fetched 2B in 1s (1B/s)
Reading package lists...

```

I don't think I'm the only one with this issue; perhaps the backports page needs additional clarification?

---

### Post by jdong on 2005-07-28
Everything looks good. Does **apt-get dist-upgrade** not pull the latest backport?

What does **apt-cache policy firefox** say? Do you have an /etc/apt/preferences file with pinning set?

---

### Post by ShaneAu on 2005-07-29
I think it's related to this:

[http://ubuntuforums.org/showthread.php?t=50353](http://ubuntuforums.org/showthread.php?t=50353)

---

### Post by jdong on 2005-07-29
I dont think bz2's are necessary or beneficial in this case. APT tries .gz, .bz2, and uncompressed, which is where all the Ign's (and 404's on Shane's end) come from.

If I create BZ2's, they take 5x longer to compress/regenerate than gz's, which would mean less frequent syncs if I want the server to be responsive to developers.

---

### Post by Farina on 2005-07-29
[QUOTE=jdong]Everything looks good. Does **apt-get dist-upgrade** not pull the latest backport?

What does **apt-cache policy firefox** say? Do you have an /etc/apt/preferences file with pinning set?[/QUOTE]

I do have a file named this with some stuff in it.
```
Package: *
Pin: release o=Unofficial Multimedia Packages
Pin-Priority: 1

```

but as I recall, this should be the default.

checking on the mozilla firefox caching policy:
```
apt-cache policy mozilla-firefox
mozilla-firefox:
  Installed: 1.0.6-0ubuntu0.1
  Candidate: 1.0.6-0ubuntu0.1
  Version table:
 *** 1.0.6-0ubuntu0.1 0
        500 http://security.ubuntu.com hoary-security/main Packages
        100 /var/lib/dpkg/status
     1.0.2-0ubuntu5 0
        500 http://archive.ubuntu.com hoary/main Packages

```

---

### Post by jdong on 2005-07-29
Retry an apt-get update now... The repository should be back in working order...

---

### Post by ShaneAu on 2005-07-29
[QUOTE=jdong]I dont think bz2's are necessary or beneficial in this case. APT tries .gz, .bz2, and uncompressed, which is where all the Ign's (and 404's on Shane's end) come from.

If I create BZ2's, they take 5x longer to compress/regenerate than gz's, which would mean less frequent syncs if I want the server to be responsive to developers.[/QUOTE]
 Yeah, I don't log to error logs or access logs anymore anyway. :). It's nothing important, it just causes people to think there's something wrong, but everything still works.

---

### Post by Farina on 2005-08-01
[QUOTE=jdong]Retry an apt-get update now... The repository should be back in working order...[/QUOTE]


I have just attempted an update:
```
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release.gpg
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release.gpg
Get:1 http://security.ubuntu.com hoary-security Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging Release.gpg
Get:2 http://archive.ubuntu.com hoary Release.gpg [189B]
Ign http://ubuntu-backports.mirrormax.net hoary-backports Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras Release
Hit http://security.ubuntu.com hoary-security Release
Hit http://archive.ubuntu.com hoary Release
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging Release
Ign http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages
Hit http://archive.ubuntu.com hoary/main Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
Ign http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/universe Packages
Hit http://security.ubuntu.com hoary-security/restricted Packages
Hit http://security.ubuntu.com hoary-security/universe Packages
Hit http://security.ubuntu.com hoary-security/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/multiverse Packages
Hit http://archive.ubuntu.com hoary/universe Packages
Hit http://archive.ubuntu.com hoary/multiverse Packages
Hit http://archive.ubuntu.com hoary/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-backports-staging/restricted Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras/restricted Packages
Hit http://security.ubuntu.com hoary-security/main Sources
Hit http://security.ubuntu.com hoary-security/restricted Sources
Hit http://security.ubuntu.com hoary-security/universe Sources
Hit http://security.ubuntu.com hoary-security/multiverse Sources
Hit http://archive.ubuntu.com hoary/main Sources
Hit http://archive.ubuntu.com hoary/universe Sources
Hit http://archive.ubuntu.com hoary/multiverse Sources
Hit http://archive.ubuntu.com hoary/restricted Sources
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/main Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/universe Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/multiverse Packages
Hit http://ubuntu-backports.mirrormax.net hoary-extras-staging/restricted Packages
Fetched 2B in 1s (1B/s)
Reading package lists...

```

No apparent improvement?

I should mention that this is an attempt off a virtually fresh install of Ubuntu, x86-64  release, so nothing has been altered from default...

---

