---
title: "Upgrading to 5.04"
date: 2005-04-08
forum: Apple PPC Users
---

### Post by Castaa on 2005-04-08
Is there currently a way to upgrade from v4 to v5.04 without reinstalling the OS?

Thanks. :-)

---

### Post by kuleali on 2005-04-08
sudo sed -e 's/warty/hoary/' -i /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade

---

### Post by Bizcocho on 2005-04-08
[QUOTE=kuleali]sudo sed -e 's/warty/hoary/' -i /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]

Will this apply to the upgrade from hoary RC to the 5.04 release to?

---

### Post by lao_V on 2005-04-08
apt-get dist-upgrade will always get you the latest release

---

### Post by ivan.virtuale on 2005-04-08
Sorry, I get a big problem when I try to upgrade from ubuntu 4.10 to hoary.
I change the source.list in this way:

eb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe

deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted
deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) hoary-security main restricted

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hoary-security universe

I download the list of the new packets and when i try to do 'apt-get dist-upgrade
' i receive this message :

The following packages have been kept back:
  firestarter gnome-cpufreq-applet gstreamer0.8-swfdec gtk2-engines-crux
  gtk2-engines-lighthouseblue gtkhtml3.2 libgal2.2-common libgcrypt7
  libgnutls10 libgtkhtml3.2-11 lufs-cryptofs mc python-hip python2.3-examples
  python2.3-gdbm python2.3-librdf python2.3-mpz python2.3-osd python2.3-pycurl
  python2.3-pymacs python2.3-pyorbit python2.3-reportlab python2.3-sqlite
  xfree86-common xserver-xfree86

Why?
How can I force to upgrade from xfree86 to xorg?
Ivan

---

### Post by Castaa on 2005-04-08
[QUOTE=kuleali]sudo sed -e 's/warty/hoary/' -i /etc/apt/sources.list

sudo apt-get update
sudo apt-get dist-upgrade[/QUOTE]
 Ok.  Thanks.   I'll give it a try. :D

---

### Post by muzza on 2005-04-09
How big would that d/l be?  I only have dialup.

---

### Post by lao_V on 2005-04-09
[QUOTE=muzza]How big would that d/l be?  I only have dialup.[/QUOTE]

depends on how old your system is :-)

---

### Post by muzza on 2005-04-11
I just installed Warty a few days ago.  I think it was a fairly recent release.

---

