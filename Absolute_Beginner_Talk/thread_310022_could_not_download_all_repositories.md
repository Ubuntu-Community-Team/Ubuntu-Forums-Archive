---
title: "could not download all repositories"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by pulldogg on 2006-11-30
[http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


this is the message i get when i try to add universe n multiverse repos,ne1 know wat to do?

---

### Post by pulldogg on 2006-12-01
some1 pls help??

---

### Post by ciscosurfer on 2006-12-01
Please post the output of the following command (entered in a terminal)```
cat /etc/apt/sources.list
```And your second post was 12 minutes apart from your first post.  Sometimes it takes a little longer for people to respond.  Please be patient next time. :D

---

### Post by Scorpuk on 2006-12-01
just tried a ping and got this:

> Pinging 213.251.190.135 with 32 bytes of data:

Request timed out.
Request timed out.
Request timed out.
Request timed out.

Ping statistics for 213.251.190.135:
    Packets: Sent = 4, Received = 0, Lost = 4 (100% loss),

Not conclusive as my works network may block ping commands or even the host at the other end may block pings, but might indicate that the mirror is down...

---

### Post by ciscosurfer on 2006-12-01
> **Scorpuk said:**
> just tried a ping and got this:



Not conclusive as my works network may block ping commands or even the host at the other end may block pings, but might indicate that the mirror is down...The links do appear to be down on my end as well, and I'm not behind a proxy.  So, to answer the original posters question, the site is down or the site, as listed, is invalid or needs to be amended to point to the correct domain/site.

---

### Post by ciscosurfer on 2006-12-01
> **pulldogg said:**
> [http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/plf/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)
[http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/dists/breezy/Release.gpg:) Could not connect to antesis.freecontrib.org:80 (213.251.190.135). - connect (111 Connection refused)


this is the message i get when i try to add universe n multiverse repos,ne1 know wat to do?I would recommend looking at this page as the links to freecontrib have been updated: [http://packages.freecontrib.org/ubuntu/plf/](http://packages.freecontrib.org/ubuntu/plf/)

And your universe and multiverse repos may be timing out because the freecontrib link is timing the whole process out.  So, in other words, adding universe and multiverse to your normal repo lines is not causing this timeout; it's the freecontrib.org line itself that is timing out.  Have a look at the link I just mentioned in web browser and amend your repo lines to reflect the change.  The change would look something like this:

deb [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/free)
deb [http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free](http://packages.freecontrib.org/ubuntu/plf/dists/breezy/non-free)

If that doesn't work, it's because Apt sees the site links differently.  Try modifying the two deb lines and make them look like other repo lines in your sources.list file

Of couse, you can always just download the packages you want directly from the site via web browser and not use Apt to download them.

---

### Post by pulldogg on 2006-12-03
# The above lines were generated automatically by EasyUbuntu 3.02 Release
# The rest of your sources.list follows

# #deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted
## Major bug fix updates produced after the final release of the
## distribution.
## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy universe
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy multiverse
## Uncomment the following two lines to add software from the 'backports'
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security multiverse
## PLF repositories, contains litigious packages, see [http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)
deb [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/plf/](http://antesis.freecontrib.org/mirrors/ubuntu/plf/) breezy free non-free
## Freecontrib, funny packages by the Ubuntu PLF Team
deb [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiversedeb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/](http://antesis.freecontrib.org/mirrors/ubuntu/freecontrib/) breezy free non-free

---

### Post by ciscosurfer on 2006-12-03
Your PLF links are outdated.  Use the ones I posted above.

---

