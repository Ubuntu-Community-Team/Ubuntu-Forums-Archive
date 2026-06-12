---
title: "[SOLVED] problems upgrading to 7.10"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by iamthemicrowave on 2007-10-13
I upgraded to 7.10RC about 2 days ago, but there were some errors in the process.  My machine is currently workable, but the update manager tells me I have 30 updates to install.  When I try to do that , I get the following error message:

E: tzdata: subprocess post-installation script returned error exit status 10
E: util-linux: dependency problems - leaving unconfigured

Then a new window opens and says not all updates were installed.  The terminal below has this output:
```

Preconfiguring packages ...
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 tzdata
 util-linux
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up tzdata (2007f-3ubuntu1) ...
dpkg: error processing tzdata (--configure):
 subprocess post-installation script returned error exit status 10
dpkg: dependency problems prevent configuration of locales:
 locales depends on tzdata; however:
  Package tzdata is not configured yet.
dpkg: error processing locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en-base:
 language-pack-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux:
 util-linux depends on tzdata (>= 2006c-2); however:
  Package tzdata is not configured yet.
dpkg: error processing util-linux (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-minimal:
 ubuntu-minimal depends on locales; however:
  Package locales is not configured yet.
 ubuntu-minimal depends on tzdata; however:
  Package tzdata is not configured yet.
 ubuntu-minimal depends on util-linux; however:
  Package util-linux is not configured yet.
dpkg: error processing ubuntu-minimal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-en:
 language-pack-en depends on language-pack-en-base; however:
  Package language-pack-en-base is not configured yet.
dpkg: error processing language-pack-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en-base:
 language-pack-gnome-en-base depends on locales (>= 2.3.6); however:
  Package locales is not configured yet.
dpkg: error processing language-pack-gnome-en-base (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jre:
 sun-java6-jre depends on locales; however:
  Package locales is not configured yet.
dpkg: error processing sun-java6-jre (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of util-linux-locales:
 util-linux-locales depends on util-linux (>= 2.13-0); however:
  Package util-linux is not configured yet.
 util-linux-locales depends on util-linux (<< 2.13.0-0); however:
  Package util-linux is not configured yet.
dpkg: error processing util-linux-locales (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of language-pack-gnome-en:
 language-pack-gnome-en depends on language-pack-gnome-en-base; however:
  Package language-pack-gnome-en-base is not configured yet.
dpkg: error processing language-pack-gnome-en (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-jdk:
 sun-java6-jdk depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-jdk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-bin:
 sun-java6-bin depends on sun-java6-jre (= 6-03-0ubuntu2); however:
  Package sun-java6-jre is not configured yet.
dpkg: error processing sun-java6-bin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on sun-java6-bin (= 6-03-0ubuntu2); however:
  Package sun-java6-bin is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured

```
Please help.

---

### Post by kronk on 2007-10-13
Just to clarify Microwave how did you "upgrade" via cd / dvd ? or Dist Upgrade ?

---

### Post by iamthemicrowave on 2007-10-13
I did a dist upgrade
```
$update-manager -d 
```

---

### Post by kronk on 2007-10-13
Ok so do you get any kind of errors when running the command 
> 
sudo apt-get update

?

---

### Post by sailor2001 on 2007-10-13
there are some progs that will cause the upgrade to malfunction if upgrading directly. Go to synaptics.search "getdeb" "version" and if any progs come up that are installed, remove them. Democracy player is one that I know of.

---

### Post by iamthemicrowave on 2007-10-13
I tried updating several times, and it finally worked, but I don't know why!  Thanks for all of the help.

---

### Post by kronk on 2007-10-13
No problems :)

---

