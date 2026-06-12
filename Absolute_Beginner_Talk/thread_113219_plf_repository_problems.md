---
title: "plf repository problems"
date: 2006-01-05
forum: Absolute Beginner Talk
---

### Post by iand675@gmail.com on 2006-01-05
i fixed the user problem, and now i'm trying to install the plf ubuntu repositories, but it always fails on the primary and mirror sites. What is it that I'm doing wrong?

---

### Post by thk on 2006-01-05
Err... perhaps what you are doing wrong is not posting your config file (/etc/apt/source.list) so someone can help?

---

### Post by iand675@gmail.com on 2006-01-05
```
#deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


## Uncomment the following two lines to fetch updated software from the network
# deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu breezy universe main restricted multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
 deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
 deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

deb http://security.ubuntu.com/ubuntu breezy-security universe main restricted multiverse
# deb-src http://security.ubuntu.com/ubuntu breezy-security universe
## FTP mirror from http://free.fr (french ISP)
deb ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free
deb-src ftp://ftp.free.fr/pub/Distributions_Linux/plf/ubuntu/plf/ breezy free non-free

```

---

### Post by Mustard on 2006-01-05
When you say fail, what error message are you receiving?

---

### Post by iand675@gmail.com on 2006-01-05
it doesn't give an error persay- but when you view the prgress of individual files when reloading the repositroy it says "failed" on the little download bars for those ones. And the packages don't show up.

---

### Post by Mustard on 2006-01-05
Are you using a proxy?
Do the errors only relate to gpg errors or do all the plf links fail?  (From what I am reading I am assuming they are all failing)

---

### Post by iand675@gmail.com on 2006-01-05
no proxy, no firewall yet, dhcp internet connection going through a linksys wireless router

---

### Post by Perfect Storm on 2006-01-05
Have you tried one of their mirrors?

---

### Post by iand675@gmail.com on 2006-01-05
yeah, i tried the main server and the mirror.

---

### Post by Mustard on 2006-01-05
Ok...I'm looking for more clues :)

Close synaptic and in terminal do this command...

```
sudo apt-get update
```

Copy and paste the output from that command into this thread.

Hopefully that will provide the clue we need to solve this.

---

### Post by iand675@gmail.com on 2006-01-05
```
Get:1 http://us.archive.ubuntu.com breezy-updates Release.gpg [189B]
Get:2 http://us.archive.ubuntu.com breezy Release.gpg [189B]
Get:3 http://us.archive.ubuntu.com breezy-backports Release.gpg [189B]
Get:4 http://security.ubuntu.com breezy-security Release.gpg [189B]
Hit http://us.archive.ubuntu.com breezy-updates Release
Hit http://us.archive.ubuntu.com breezy Release
Get:5 http://security.ubuntu.com breezy-security Release [19.6kB]
Hit http://us.archive.ubuntu.com breezy-backports Release
Hit http://us.archive.ubuntu.com breezy-updates/main Packages
Hit http://us.archive.ubuntu.com breezy-updates/restricted Packages
Get:6 ftp://ftp.free.fr breezy Release.gpg
Hit http://us.archive.ubuntu.com breezy-updates/universe Packages
Hit http://security.ubuntu.com breezy-security/universe Packages
Hit http://us.archive.ubuntu.com breezy-updates/multiverse Packages
Hit http://security.ubuntu.com breezy-security/main Packages
Hit http://security.ubuntu.com breezy-security/restricted Packages
Hit http://security.ubuntu.com breezy-security/multiverse Packages
Hit http://us.archive.ubuntu.com breezy/universe Packages
Hit http://us.archive.ubuntu.com breezy/main Packages
Ign ftp://ftp.free.fr breezy Release.gpg
Hit http://us.archive.ubuntu.com breezy/restricted Packages
Hit http://us.archive.ubuntu.com breezy/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-backports/main Packages
Get:7 ftp://ftp.free.fr breezy Release
Hit http://us.archive.ubuntu.com breezy-backports/restricted Packages
Hit http://us.archive.ubuntu.com breezy-backports/universe Packages
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com breezy-backports/main Sources
Ign ftp://ftp.free.fr breezy Release
Hit http://us.archive.ubuntu.com breezy-backports/restricted Sources
Hit http://us.archive.ubuntu.com breezy-backports/universe Sources
Hit http://us.archive.ubuntu.com breezy-backports/multiverse Sources
Get:8 ftp://ftp.free.fr breezy/free Packages
Ign ftp://ftp.free.fr breezy/free Packages
Get:9 ftp://ftp.free.fr breezy/non-free Packages
Ign ftp://ftp.free.fr breezy/non-free Packages
Get:10 ftp://ftp.free.fr breezy/free Sources
Ign ftp://ftp.free.fr breezy/free Sources
Get:11 ftp://ftp.free.fr breezy/non-free Sources
Ign ftp://ftp.free.fr breezy/non-free Sources
Hit ftp://ftp.free.fr breezy/free Packages
Hit ftp://ftp.free.fr breezy/non-free Packages
Hit ftp://ftp.free.fr breezy/free Sources
Hit ftp://ftp.free.fr breezy/non-free Sources
Fetched 19.8kB in 6s (3005B/s)
```

---

### Post by Mustard on 2006-01-05
I'm stumped. Can you put the PLF URL into your browser and browse to the site that way?

I'm wondering whether there is an issue with connecting with the repo that is outside your system.

---

### Post by iand675@gmail.com on 2006-01-05
im going to sleep now. If you have any ideas, post them, and i will get back on this post tomorrow after school

---

### Post by iand675@gmail.com on 2006-01-06
yeah i can browse it.

---

### Post by Mustard on 2006-01-06
Roger.  I've got to go shopping now myself. :)

---

### Post by iand675@gmail.com on 2006-01-06
okay, i'm just bumping this since i'm back home now

---

### Post by iand675@gmail.com on 2006-01-06
well i think I have it working possibly, but i can't find the waste program anywhere. I figured it would be in world wide web or networking maybe, but it is nowhere to be found. That would be good proof that it is operational, so if anyone has any idea about that, it might be useful to know.
edit: I is there some sort of other file that tells it to ignore custom repositories or something, because that would kind of explain this strangeness. It still isn't working

---

### Post by invisibastard on 2006-01-07
I am having the same problem. This is what I get from synaptic:

Could not download all repository indexes

[http://public.planetmirror.com/plf/ubuntu/plf/dists/breezy/Release.gpg](http://public.planetmirror.com/plf/ubuntu/plf/dists/breezy/Release.gpg)


then this:

[HTML]W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_free_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://public.planetmirror.com](http://public.planetmirror.com) breezy/non-free Packages (/var/lib/apt/lists/public.planetmirror.com_pub_plf_ubuntu_plf_dists_breezy_non-free_binary-i386_Packages) - stat (2 No such file or directory)[/HTML]


I can't access the site, either. I haven't had time to punch in the original, non-mirror site, but it sounds like it has the same problem too. I haven't had time to look for other mirrors, do they exist?

Thanks,
Rich

---

### Post by invisibastard on 2006-01-07
Okay, now that I have had a few seconds, found this:

[http://wiki.ubuntu-fr.org/doc/plf](http://wiki.ubuntu-fr.org/doc/plf)

The primary mirror is back online. I switched to it and everything is fine.

---

