---
title: "Is there another linux distribution that has something like Ubuntu Restricted Extras?"
date: 2012-01-08
forum: Any Other OS
---

### Post by Learning Linux 2011 on 2012-01-08
I've played a little bit with other distributions and it seems much more  difficult to get something equivalent to "Ubuntu Restricted Extras" on  other non-Ubuntu distributions.

Does anyone know of anything similar to "restricted extras" in another linux distribution?

---

### Post by Double.J on 2012-01-08
just wondering which distro you tried? was it rpm based? they don't follow the debian model, so typically you end up adding a lot more third party repos than normal. If it was an ubntu based distro, such as mint, you would be able to install restricted extras.

I think it's partly because rpm users are so used to adding third party repos that distros like fedora are less willing for sucha package - at the end of the day mp3 is heavily licensed - so not open source, they could theoretically get in trouble Even in debian you have to add a repo - think ice weasel instead of firefox!

---

### Post by Learning Linux 2011 on 2012-01-08
> **gnu/mirow said:**
> just wondering which distro you tried? was it rpm based? they don't follow the debian model, so typically you end up adding a lot more third party repos than normal. If it was an ubntu based distro, such as mint, you would be able to install restricted extras.

I think it's partly because rpm users are so used to adding third party repos that distros like fedora are less willing for sucha package - at the end of the day mp3 is heavily licensed - so not open source, they could theoretically get in trouble Even in debian you have to add a repo - think ice weasel instead of firefox!

[FONT=Tahoma][SIZE=2]Yes, well Debian was one of them.  Does Debian have the equivalent of "restricted extras"?

And Fedora was another for example.  I don't have much experience with Red Hat/RPM, but they do it differently with Fedora?

And yeah, funny you mentioned that, what is the deal with iceweasel?  Is there a licensing issue with Firefox or something?
I know about MP3's, etc., but I thought Firefox was open source.
[/SIZE][/FONT]

---

### Post by mips on 2012-01-09
Install crunchbang or add their repo to debian.

---

### Post by TBABill on 2012-01-09
I haven't found any distros that have a single package that adds all the codecs, but there are available repos for most any distro to add whatever extras you want. That includes Debian and Fedora. There are also others that come with all those extras included, or some of them, including PCLinuxOS, Mint, PinguyOS, Ultimate Edition, Fuduntu and others.

---

### Post by sffvba[e0rt on 2012-01-09
openSUSE offers 1-click installers where things like multimedia codecs can be installed with (you guessed it) one click. 

Example - [http://opensuse-community.org/Restricted_formats/12.1](http://opensuse-community.org/Restricted_formats/12.1)



404

---

### Post by Double.J on 2012-01-09
> **not found said:**
> openSUSE offers 1-click installers where things like multimedia codecs can be installed with (you guessed it) one click. 

Example - [http://opensuse-community.org/Restricted_formats/12.1](http://opensuse-community.org/Restricted_formats/12.1)



404

Thanks 404, can't believe I didn't know about this! figure I've got too used to using the pacman repo and build service - never thought to look for it.. well that's one less thing to do next release :D

Edit: Learning Linux 2011 - if you wanted to try a distro such as SUSE you're probably going to want to add repo's (I don't know if it was a bug but after my install the only listed repo was the dvd? I don't remember this being the case on 11.2, but that was a while ago!) in SUSE, open Software Management then click on configuration>repositories if the DVD is still there, remove it, then add> community> packman.. you may also want the build service repo of your evironment.

 You should also have some open suse repos such as OSS, non OSS and update - if you don't have these (I didn't)after install go add then choose the download method you want - for exampe I use HTTP, you may want to use FTP

All the best :)

---

### Post by haqking on 2012-01-09
> **Learning Linux 2011 said:**
> [FONT=Tahoma][SIZE=2]
And yeah, funny you mentioned that, what is the deal with iceweasel?  Is there a licensing issue with Firefox or something?
I know about MP3's, etc., but I thought Firefox was open source.
[/SIZE][/FONT]

Firefox and iceweasel are essentially the same apart from branding and security patches particular to debian stable.

from [http://wiki.debian.org/Iceweasel](http://wiki.debian.org/Iceweasel)

> Iceweasel is a fork [from Firefox] with the following purpose :

backporting of security fixes to declared Debian stable version.

no inclusion of trademarked Mozilla artwork

Beyond that, they will be basically identical

---

### Post by GERGE on 2012-01-09
Almost all of them have something like it. One command you have give or something. As one package, not sure of that.

---

### Post by ubiquitin.jf on 2012-01-09
You can add the [http://debian-multimedia.org/](http://debian-multimedia.org/) repository to Debian Squeeze/Wheezy/Sid but there isn't a nice metapackage like ubuntu-resticted-extras, you just have to pick out what you want.

---

### Post by m_duck on 2012-01-09
In Debian, add 'contrib' and 'non-free' to the end of the standard repo lines enable a load more software, in addition to what ubiquitin.jf mentioned above.

Fedora has the [RPM Fusion]("http://rpmfusion.org/") repo for 'restricted' packages.

---

### Post by shuttleworthwannabe on 2012-01-09
Take vanilla Fedora 16 and install Fedora Utils--this is a utility that can convert the vanilla into something you are looking for.

---

### Post by drfox on 2012-01-16
How about this in Debian?

#### Debian Multimedia - [http://www.debian-multimedia.org/](http://www.debian-multimedia.org/)
## Run this command: apt-get update && apt-get install debian-multimedia-keyring && apt-get update
deb [http://www.debian-multimedia.org](http://www.debian-multimedia.org) sid main non-free

Larry

---

