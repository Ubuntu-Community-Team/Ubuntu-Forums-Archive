---
title: "Where can I find an older version of Firefox"
date: 2014-10-30
forum: Apple Hardware Users
---

### Post by jacatone on 2014-10-30
I'm looking for Firefox 11 or 12 .deb for PPC? It doesn't seem to be in my archives and I don't like v33 from a recent update.

---

### Post by coldraven on 2014-10-31
For security reasons I would not use old versions of Firefox. Have you tried using the Classic Theme Restorer add-on?
[https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/](https://addons.mozilla.org/en-US/firefox/addon/classicthemerestorer/)

---

### Post by jacatone on 2014-10-31
Don't know if this will work. I damaged the bookmarks feature in FF v33 trying to get it to work. When I try removing and reinstalling, it doesn't fix itl.

---

### Post by CharlesA on 2014-10-31
> **jacatone said:**
> Don't know if this will work. I damaged the bookmarks feature in FF v33 trying to get it to work. When I try removing and reinstalling, it doesn't fix itl.

Did you try creating a new profile in Firefox? Purging firefox doesn't remove your profile. It should be in your home directory in .mozilla iirc.

---

### Post by dae2 on 2014-11-08
> **jacatone said:**
> I'm looking for Firefox 11 or 12 .deb for PPC? It doesn't seem to be in my archives and I don't like v33 from a recent update.

```

sudo -i
<password>
dpkg --configure -a
apt-get purge -y firefox && apt-get purge -y firefox-locale-fr && apt-get purge -y firefox-locale-en
wget -q http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_28.0+build2-0ubuntu2_i386.deb -o ~/firefox_28.0+build2-0ubuntu2_i386.deb
wget -q http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fr_28.0+build2-0ubuntu2_i386.deb -o ~/firefox-locale-fr_28.0+build2-0ubuntu2_i386.deb

## For x64
#wget -q http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox_28.0+build2-0ubuntu2_amd64.deb -o ~/firefox_28.0+build2-0ubuntu2_amd64.deb
#wget -q http://security.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-locale-fr_28.0+build2-0ubuntu2_amd64.deb -o ~/firefox-locale-fr_28.0+build2-0ubuntu2_amd64.deb

apt-mark hold firefox && apt-mark hold firefox-locale-fr && add-apt-repository -r ppa:mozillateam/firefox-next -O- | sudo apt-key add -

```

best version ever

+ adblock edge
+S3 google
+Stylish
+Web2PDF
+video and flash download
+fasterfox
+flashblock
+email this
+fastest notifier gmail

---

### Post by pqwoerituytrueiwoq on 2014-11-08
old version are advisable here
[https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/](https://ftp.mozilla.org/pub/mozilla.org/firefox/releases/)

there is not a deb file, extract hte archive and run ./firefox  from the archive
@[**[COLOR=#000000]coldraven[/COLOR]**]("http://ubuntuforums.org/member.php?u=993657") +1

---

### Post by dae2 on 2014-11-13
isn't easy and fun to go on your link 
[http://security.ubuntu.com/ubuntu/pool/main/f/firefox/](http://security.ubuntu.com/ubuntu/pool/main/f/firefox/)
here you have all .deb (easy use with ubuntu)

---

### Post by jacatone on 2014-12-05
I'm looking for the powerpc.deb file for firefox 11 or 12? the links above are for i386 machines.

---

### Post by Dennis N on 2014-12-05
> **jacatone said:**
> I'm looking for the powerpc.deb file for firefox 11 or 12? the links above are for i386 machines.

FF 11 .deb file (Mar 2012) for your computer is probably this:

[http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_11.0+build1-0ubuntu0.10.10.2_powerpc.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_11.0+build1-0ubuntu0.10.10.2_powerpc.deb)

Realize that plug-ins and extensions may no longer be available, and this version is now considered insecure.

Good Luck.

---

