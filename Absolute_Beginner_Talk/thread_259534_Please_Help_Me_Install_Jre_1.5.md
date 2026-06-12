---
title: "Please Help Me Install Jre 1.5"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by sociallyteamed on 2006-09-17
i tried everyting online every little guide and i cant install it please help me, plese try to go setp by step thanks, need to install frostwire.

---

### Post by bulldog on 2006-09-17
Go to Administration-->synaptic

Then search for jre and see what happens.

---

### Post by jd65pl on 2006-09-17
If you want frostwire why don't you download the "ubuntu" .deb file off their home page[URL="http://www.frostwire.com/"]
http://www.frostwire.com/[/URL]

Maybe I've got your question wrong.

J

---

### Post by bulldog on 2006-09-17
If you want frostwire,java and more stuff take a look at Automatix.

[http://ubuntuforums.org/showthread.php?t=80295](http://ubuntuforums.org/showthread.php?t=80295)

You have to read a little but get a load of software.
Try it.

---

### Post by blx_286 on 2006-09-17
> **sociallyteamed said:**
> i tried everyting online every little guide and i cant install it please help me, plese try to go setp by step thanks, need to install frostwire.

I wrested with JRE for a while, then installed it with Automatix.

---

### Post by ckonrad on 2006-10-13
> **bulldog said:**
> Go to Administration-->synaptic

Then search for jre and see what happens.

nothing happens i tried that to and i have all ther repositories selected like universe etc. Pretty strange. There is no JRE in synaptic, there is an open source one but it doesnt seem to recognize web content, i dont know why that is.

---

### Post by Perfect Storm on 2006-10-13
Please post output of this:
```
cat /etc/apt/sources.list
```

---

### Post by David Corrales on 2006-10-13
You'll need to enable the extra repositories.

---

### Post by coolboarderguy on 2006-10-14
Hi All,

I'm rather new to Ubuntu. I've used Fedora and Centos before that. I am also wanting to install JRE. I am in Synaptic, and I get a number of hits when searchig for jre, but nothing titled jre. If I manually search for it, I get the following,

javacc
java-common
java-gcj-*

etc, but nothing for jre. Surely installing jre shouldn't be so cryptinc, no? Anyone willing to tell me where I'm going wrong here? Cheers.

---

### Post by Perfect Storm on 2006-10-15
Post your sourcelist.

---

### Post by coolboarderguy on 2006-10-15
Hi All,

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


BTW, I've since then tried installing following this tut,

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

with no luck, even after rebooting the PC. At a loss. Just want jre installed.

---

### Post by coolboarderguy on 2006-10-15
Hi All,

below are the details for the soft links created in the mozilla/firefox plugins directories.

mark@marklaptop:/usr/lib/mozilla-firefox/plugins$ ls -al libjavaplugin_oji.so
lrwxrwxrwx 1 root root 58 2006-10-15 13:54 libjavaplugin_oji.so -> /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so
mark@marklaptop:/usr/lib/mozilla-firefox/plugins$ cd /usr/lib/firefox/plugins/
mark@marklaptop:/usr/lib/firefox/plugins$ ls -al libjavaplugin_oji.so
lrwxrwxrwx 1 root root 58 2006-10-15 13:54 libjavaplugin_oji.so -> /usr/java/jre1.5.0_08/plugin/i386/ns7/libjavaplugin_oji.so

They look okay to me. Please advise if you think something is not right or need more info.

---

### Post by Perfect Storm on 2006-10-15
> **coolboarderguy said:**
> Hi All,

deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe


BTW, I've since then tried installing following this tut,

[http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_J2SE_Runtime_Environment_.28JRE.29_with_Plug-in_for_Mozilla_Firefox)

with no luck, even after rebooting the PC. At a loss. Just want jre installed.

add
```

# Ubuntu community supported packages (packages, GPG key: 437D05B5)
deb http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb http://security.ubuntu.com/ubuntu dapper-security universe multiverse

# Ubuntu community supported packages (sources, GPG key: 437D05B5)
deb-src http://archive.ubuntu.com/ubuntu dapper universe multiverse
deb-src http://archive.ubuntu.com/ubuntu dapper-updates universe multiverse
deb-src http://security.ubuntu.com/ubuntu dapper-security universe multiverse
```

---

### Post by NeoLithium on 2006-10-15
Darn, someone beat me to the add-ons for your source list ;)  

Oh well. Another good idea, for any future installs of ubuntu; would be to use automatix. It works very well for plugins, codecs, java, and extra package installs.

There are detailed installation instructions [available on their website]("http://www.getautomatix.com"); and many people around here swear by it's efficiency :)

---

### Post by coolboarderguy on 2006-10-15
Hi All,

great stuff. Thank you.

---

### Post by fluffnik on 2006-10-15
You can use make-jpkg (from java-package) to turn the .bin file from Sun into .debs

---

