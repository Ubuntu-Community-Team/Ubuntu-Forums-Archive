---
title: "mplayer installation dependency problem (help me AYSIU!)"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by vgrisham on 2007-03-04
Well, I've got myself into a nice little pickle. I dumped dual boot (xp) this weekend, and reinstalled Dapper while I was at it. I figured a clean install would be nice. It stayed that way for about an hour.

I installed firefox 2.0.0.2 using the sweet little psychocats [script]("http://www.psychocats.net/ubuntu/firefox"). That went well. Then I tried to install mplayer (which I realize now I should've done first), and hit a wall. Synaptic returns the following error: 

[IMG]http://img225.imageshack.us/img225/2908/screenshotsynapticgq9.png[/IMG]

I then tucked my tail between my legs and ran the uninstall script to revert back to firefox 1.5, but I still couldn't install mplayer. 

Any advice would be greatly appreciated.

---

### Post by taurus on 2007-03-04
Okay, I am not aysiu but will try.

Did you enable universe and multiverse in /etc/apt/sources.list?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

And if you are looking for a multimedia player, vlc is another option.

---

### Post by vgrisham on 2007-03-04
> **taurus said:**
> Okay, I am not aysiu but will try.

Did you enable universe and multiverse in /etc/apt/sources.list?

[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

And if you are looking for a multimedia player, vlc is another option.

Thank you so much for your quick reply. Yes, but now when I try to reload the repositories, synaptic bombs out. 

[IMG]http://img297.imageshack.us/img297/330/screenshotsynapticrq1.png[/IMG]

I guess I've done more damage than I thought. Any ideas? I should mention that I have automatix2 installed.

PS Regarding, vlc, I'm just looking for something to stream video and music from the web.

---

### Post by taurus on 2007-03-04
Open a terminal and post the output of this command here.  Don't forget to shutdown synaptic first or else you will get an error message right away about another process is running when you run the following command.

Applications -> Accessories -> Terminal
```
sudo aptitude update
```

---

### Post by aysiu on 2007-03-04
Yes, it sounds as if this has something to do with either your repositories list (not sure if you followed the instructions in the link about the sources.list file) or your internet configuration (are you behind a proxy?). The problem has nothing to do with the Firefox script.

Please post what taurus asked for. Terminal output/errors will be far more helpful in diagnosing the problem than screenshots.

---

### Post by vgrisham on 2007-03-04
> **aysiu said:**
> Yes, it sounds as if this has something to do with either your repositories list (not sure if you followed the instructions in the link about the sources.list file) or your internet configuration (are you behind a proxy?). The problem has nothing to do with the Firefox script.

Please post what taurus asked for. Terminal output/errors will be far more helpful in diagnosing the problem than screenshots.

Taurus and aysiu,

Here is the output: 
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Get:5 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:6 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Get:8 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:9 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages [6894B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages [4080B]
99% [10 Packages bzip2 0] [Waiting for headers] [Waiting for headers]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
  Sub-process bzip2 returned an error code (2)
99% [11 Packages bzip2 0] [Waiting for headers] [Waiting for headers]
bzip2: Data integrity error when decompressing.
        Input file = (stdin), output file = (stdout)

It is possible that the compressed file(s) have become corrupted.
You can use the -tvv option to test integrity of such files.

You can use the `bzip2recover' program to attempt to recover
data from undamaged sections of corrupted files.

Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
  Sub-process bzip2 returned an error code (2)
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages [24.8kB]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
99% [12 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
  Sub-process gzip returned an error code (1)
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages [128kB]
99% [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
  Sub-process gzip returned an error code (1)
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages [63.9kB]
99% [14 Packages gzip 0] [Waiting for headers] [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
  Sub-process gzip returned an error code (1)
Ign [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/universe Sources
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
99% [Waiting for headers]
gzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Sources
Get:16 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages [821kB]
99% [16 Packages gzip 0]
gzip: stdin: not in gzip format
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
  Sub-process gzip returned an error code (1)
Fetched 16B in 2s (6B/s)
Reading package lists... Done

---

### Post by aysiu on 2007-03-04
That's weird.

Can you try getting a fresh sources.list by following these instructions?
[http://www.psychocats.net/ubuntu/sources](http://www.psychocats.net/ubuntu/sources)

and then trying again? ```
sudo aptitude update
sudo aptitude install mozilla-mplayer
```

---

### Post by vgrisham on 2007-03-04
Here's the output now: 

vaughn@vaughn-asus:~$ gksudo gedit /etc/apt/sources.list

(gedit:12376): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
vaughn@vaughn-asus:~$ sudo aptitude update Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release.gpg [191B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [191B]
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.canonical.com](http://archive.canonical.com) dapper-commercial/main Packages
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release [38.4kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages [51.9kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages [619kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Sources [6566B]
Get:10 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages [4571B]
Get:11 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources [255kB]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources [1478B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages [2458kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources [975kB]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources [46.6kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages [133kB]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages [14B]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources [48.5kB]
Get:19 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources [14B]
Get:20 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages [13.0kB]
Get:21 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages [14B]
Get:22 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages [44.9kB]
Get:23 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages [7071B]
Get:24 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages [121kB]
99% [24 Packages gzip 0]                                             24.0kB/s 0sgzip: stdin: not in gzip format
Err [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
  Sub-process gzip returned an error code (1)
Fetched 4703kB in 3m20s (23.4kB/s)
Reading package lists... Done

That seems to have fixed the repositories. What does that last error mean?

---

### Post by vgrisham on 2007-03-04
vaughn@vaughn-asus:~$ sudo aptitude install mozilla-mplayer
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
The following packages are BROKEN:
  mozilla-mplayer
0 packages upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 450kB of archives. After unpacking 1593kB will be used.
The following packages have unmet dependencies:
  mozilla-mplayer: Depends: mplayer (>= 1.0-pre5) which is a virtual package. or                            mplayer-nogui (>= 1.0-pre5) which is a virtual package. or
                            mplayer-powerpc (>= 1.0-pre5) which is a virtual package. or
                            mplayer-g4 (>= 1.0-pre5) which is a virtual package.Resolving dependencies...
Unable to resolve dependencies!  Giving up...
Abort.

PS No, I'm not behind a proxy. I connect wirelessly to the local university. I also tried via another wireless host with the same errors.

---

### Post by aysiu on 2007-03-04
Hm. Maybe it's still broken from last time. Can you try this? ```
sudo dpkg --configure -a
```

By the way, I don't know why you're getting this error: ```
99% [24 Packages gzip 0] 24.0kB/s 0sgzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
Sub-process gzip returned an error code (1)
``` But it could be contributing directly to the problem, since [the *mozilla-mplayer* package is in the Multiverse repositories](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mozilla-mplayer&searchon=name&subword=1&version=all&release=all).

Maybe something's wrong with the Ubuntu servers right now?

---

### Post by vgrisham on 2007-03-04
> **aysiu said:**
> Hm. Maybe it's still broken from last time. Can you try this? ```
sudo dpkg --configure -a
```By the way, I don't know why you're getting this error: ```
99% [24 Packages gzip 0] 24.0kB/s 0sgzip: stdin: not in gzip format
Err http://archive.ubuntu.com dapper/multiverse Packages
Sub-process gzip returned an error code (1)
``` But it could be contributing directly to the problem, since [the *mozilla-mplayer* package is in the Multiverse repositories]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=mozilla-mplayer&searchon=name&subword=1&version=all&release=all").

Maybe something's wrong with the Ubuntu servers right now?

I tried that command, and it seemed to take (no errors). I updated again, with the same gzip error. Same error on mplayer. 

Should I just reinstall dapper again? I have everything backed up.

---

### Post by aysiu on 2007-03-04
> **vgrisham said:**
> 
Should I just reinstall dapper again? I have everything backed up. No. I have a sneaking suspicion it has something to do with the Multiverse repository. Maybe there was a buggy upload or something.

You might want to try a local mirror for your country. This site will help you get that list.
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

---

### Post by vgrisham on 2007-03-05
> **aysiu said:**
> No. I have a sneaking suspicion it has something to do with the Multiverse repository. Maybe there was a buggy upload or something.

You might want to try a local mirror for your country. This site will help you get that list.
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Before I got this post, I reinstalled dapper. I'm keeping my repos clean from now on; no more laziness on my part via third party installers.:wink: I've learned my lesson. 

Now, back to your website to try Firefox 2 again. 

Thanks for the help.

---

