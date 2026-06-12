---
title: "iMac G4 - Need advice"
date: 2012-07-03
forum: Apple Hardware Users
---

### Post by BakaOsaka on 2012-07-03
Hi everyone, I have an iMac G4 20" and need some advice.

The disk drive doesn't work - Can I boot from USB easily? If not, is there another method?
Can I dual-boot Ubuntu and OS X without losing my data?
Finally, if I install Ubuntu completely over the HDD can I reinstall OS X?

Thanks a lot!

---

### Post by llamabr on 2012-07-03
The disk drive doesn't work - Can I boot from USB easily? If not, is there another method?

Yes, it's pretty easy:
[https://help.ubuntu.com/community/Installation/FromUSBStick/](https://help.ubuntu.com/community/Installation/FromUSBStick/)


Can I dual-boot Ubuntu and OS X without losing my data?

You always risk losing data.  But if you do a backup first, you minimize this risk.

Finally, if I install Ubuntu completely over the HDD can I reinstall OS X?

Yes, if you still have your osx disks.

BTW, ubuntu no longer supports your machine.  You may prefer running debian on an older ppc machine like that.

---

### Post by rsavage on 2012-07-04
> **llamabr said:**
> 
BTW, ubuntu no longer supports your machine. You may prefer running debian on an older ppc machine like that.
 
PowerPC is community supported - just like Lubuntu, Xubuntu (and now Kubuntu?).  Do you tell the users of these to go use Debian too?
 
USB instructions for PowerPC are here [https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F](https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_boot_from_a_USB_drive.3F) .
 
The PowerPC instruction for Debian are here ..... oh sorry. That's right, they don't have any.

---

### Post by llamabr on 2012-07-04
> **rsavage said:**
> PowerPC is community supported - just like Lubuntu, Xubuntu (and now Kubuntu?).  Do you tell the users of these to go use Debian too?

Community supported is hardly the same thing.  Your machine is no longer officially supported by ubuntu, and hasn't been since 2007.

[https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html](https://lists.ubuntu.com/archives/ubuntu-announce/2007-February/000098.html)

Yes, I advise those considering lubuntu, xubunt, and kubuntu to consider debian, which still supports the architecture that runs their machines.

---

### Post by rsavage on 2012-07-04
You don't know what you are talking about.

Lubuntu and Xubuntu (for any architecture) are community supported.

PowerPC is community supported.

The PowerPC kernel is maintained by the Ubuntu kernel team just like any other architecture.

So PowerPC Lubuntu/Xubuntu has exactly the same level of support as any other architecture.

PowerPC Ubuntu/Lubuntu/Kubuntu goes through exactly the same testing procedure as any other architecture.  ISOs will only be released if they pass.

Ubuntu PowerPC specific bugs are still solved by Ubuntu and the wider community, but they will not delay a release.  For 12.04 there were no outstanding PowerPC bugs that were known about at the time of release.

---

### Post by llamabr on 2012-08-18
> **rsavage said:**
> You don't know what you are talking about.


Yes I do.

---

### Post by 2blue on 2012-08-19
I like lubuntu thought, and I know there are a lot of consumer powerpcs still around. Is latest debian any more likely to work with the issues that are common for powerpc; Gnash, gnome mplayer - gecko mediaplayer set up in browser? The rest seems to be working fine.

---

### Post by llamabr on 2012-08-19
It's been years since I've tried gnash.  I remember it was horrible when it first started loading with ubuntu.  I'll give it a try again.

My machine is so old that I don't use it for flash videos like youtube, but now with html5, maybe that will change, as well.  However, my mplayer still works fine.  You have trouble with mplayer on ubuntu?

---

### Post by 2blue on 2012-08-19
Mplayer and it`s forks works fine on its` own (default in lubuntu is gnome mplayer, with mplayer2 and gecko mediaplayer browser setup). Problem is all browser plugin packages are broken for powerpc; gecko package and gnash browser plugin package for firefox and related browsers do not work. They really should. Exception is Midori, where gnash streams fairly well (not mozilla related I suppose). Html5 might get better in the future, but as the situation is now it plays, halts, starts, stops (sound is fairly smooth running), at least in youtube.  

I have checked with others using debianppc and mintppc, situation is no better. Last night someone told be to try Fedora, the build team there appearantly has a few ppc users.

---

### Post by llamabr on 2012-08-19
Right.  I wouldn't know, since I don't run ubuntu on my ibook, and wouldn't, since the hardware inside is no longer supported by ubuntu.  Instead, I run debian, because it is.  Also, I'm rather sick of the ubuntu team telling me what is the "default" on my machine.

I don't run gnash, since last time I tried (years ago, to be fair), it was the suck.  I don't play youtube -- the machine is too old, and flash is wobbly, and gnash doesn't work.  But otherwise, I experience none of the issues you describe.

---

### Post by rsavage on 2012-08-20
Please stop saying powerpc is nonlonger supported in ubuntu without an explanation of what that actually means.  If you don't know, then you should start by reading this [https://wiki.ubuntu.com/PowerPCFAQ#Is_Ubuntu_supported_on_PowerPC.3F](https://wiki.ubuntu.com/PowerPCFAQ#Is_Ubuntu_supported_on_PowerPC.3F) 
 
In summary, package releases will not be delayed due to powerpc specific problems.
 
Like I said before, at the time of the 12.04 release there were no known powerpc specific problems with applcation/desktop packages.  Since Ubuntu only performs security and bug fix updates it is likely that this will remain the same throughout the life of 12.04.
 
The only(?) package that gets major updates is Firefox.  This did cause a problem for PowerPC in June (because it would not compile) and a release was missed in PowerPC (the problem is now solved).   Every distribution had this problem because a fix for PowerPC had not been worked out at the time, but it was handled differently by each distrubition because of how they 'support' the architecture.
 
In Ubuntu, firefox continued to be released except on PowerPC (this allowed the 'supported' architecutes to get the latest version).  In debian, they held back firefox/iceweasel to the version that would compile on every architecture and applied security updates to that version.  In debian squeeze I think I am right in saying the current version of iceweasel is 3.5 with version 10 available in backports.  In *Ubuntu 10.04-12.04 the version is now 14 (including powerpc).
 
The situation I describe above is rare and the only case that I know about.
 
I hope that clarifies the 'support' of PowerPC.

---

### Post by 2blue on 2012-08-20
Thanks rsavage. It would be nice if the issue with gnome mplayer, gecko and flash video replacer packages would be treated as a bug.  Embedded play on powerpc should be possible, and 12.04 is the longterm supported issue. Anhow, I have updated to gnome and gecko 1.0.6, built packages locally, and are trying to figure out where things are going wrong. If backport issue of player works it would be a good fix. I think the issue is getting the right information to devs and package builders, they seem very open to deal with the right kind of info.

---

### Post by jibawakee on 2012-08-20
Use Universal linux usb installer to make a bootable usb ;)

---

### Post by rsavage on 2012-08-21
> **2blue said:**
> Thanks rsavage. It would be nice if the issue with gnome mplayer, gecko and flash video replacer packages would be treated as a bug. Embedded play on powerpc should be possible, and 12.04 is the longterm supported issue. Anhow, I have updated to gnome and gecko 1.0.6, built packages locally, and are trying to figure out where things are going wrong. If backport issue of player works it would be a good fix. I think the issue is getting the right information to devs and package builders, they seem very open to deal with the right kind of info.
 
There are indeed problems with gecko-mediaplayer and gnash, but nobody reported them as bugs (before you did) so they were not 'known' at release time.  Bugs don't get fixed if they don't get reported (this still seems to surprise people).
 
I actually think the problem is going to be with firefox.  Somewhere around version 5 it went wrong.  If you want to track the problem down then I would start by installing old versions of firefox. You can find them here [https://launchpad.net/ubuntu/natty/powerpc/firefox](https://launchpad.net/ubuntu/natty/powerpc/firefox) .  This should help devs.
 
You may want to contact the lubuntu-mailing list about gecko-mediaplayer.  There is already a discussion about gnome-mediaplayer [https://lists.ubuntu.com/archives/lubuntu-users/2012-August/002243.html](https://lists.ubuntu.com/archives/lubuntu-users/2012-August/002243.html)
 
Both the totem and vlc browser plugins work in PowerPC by the way, so it really isn't the end of the world about gecko-mediaplayer.
 
Also, Lubuntu is not technically a LTS release as far as I am aware (unless thing have changed).  Xubuntu is an LTS release.  It runs really well if you optimise your graphics.
 
Don't know what the future of flash-video-replacer is.  It was withdrawn last time I checked.

---

### Post by 2blue on 2012-08-22
Thanks again rsavage. This is tricky stuff for an amateur. I have puppy linux 528 installed on a regular HP computer, it runs with firefox 14.01 with the same gnome-mplayer/gecko setup and it works fine with everyting it should. I wonder why powerpc is that different? 

Is Firefox 4 or 5 available and possible to install alongside 14.01? 

I keep getting remarks like "we need feed back from ppc users", "please make a bug report", "devs need the feedbak" and then some "there is no point in using powerpc", "you cannot expect any fixes for powerpc", "devs don`t care about obsolete hardware".....

---

### Post by rsavage on 2012-08-22
I checked this for you with gnash.  It works using the last version of firefox 4.  It doesn't work using the first version of firefox 5.  Presumably one of the changes listed here [https://launchpad.net/ubuntu/natty/+source/firefox/+changelog](https://launchpad.net/ubuntu/natty/+source/firefox/+changelog) is responsible:

> 
firefox (5.0~b5+build1+nobinonly-0ubuntu0.11.04.1) natty-security; urgency=low

  * New upstream release from the beta channel (FIREFOX_5_0b5_BUILD1)

  * Update globalmenu-extension to 1.0.6
  * Switch to mozilla-beta
    - update debian/mozclient/firefox.conf
  * Drop the ability to build with an external xulrunner, and all the packaging
    complexity which went with it
    - update debian/apport/firefox.in
    - update debian/firefox.install.in
    - update debian/firefox.lintian-overrides.in
    - update debian/firefox.sh.in
    - update debian/mozconfig.in
    - update debian/rules
  * Build language packs directly from the firefox source
    + Fixes LP: #294187 - Firefox Locales should install locale specific
      search plugins
    + Rip out the bits to create a en-US.xpi
      - update debian/rules
      - remove debian/translation-support/install.rdf.in
    + Include compare-locales FIREFOX_5_0b1_BUILD1 from
      [http://hg.mozilla.org/build/compare-locales](http://hg.mozilla.org/build/compare-locales). It's needed for merging
      en-US strings with incomplete locales
    + Pull l10n data in to tarball from bzr
      - update debian/mozclient/firefox.conf
    + Configure build for creating language packs by configuring with
      "--with-l10n-base="
      - update debian/mozconfig.in
    + Store the list of locales to ship, and provide a way of automatically
      generating that list and the control file entries from the upstream
      source. Also provide a way to blacklist languages. We map languages
      to package names using langpack-o-matic (and also get descriptions
      from there too)
      - update debian/rules
      - add debian/locales-supported
      - add debian/control.langpacks
      - update debian/control
      - add debian/locale-blacklist
      - add debian/refresh-supported-locales.pl
    + Add common-build-indep hook to build the translation xpi's
      - update debian/rules
    + Add common-binary-post-install-indep to install the xpi's and
      searchplugins in to the correct debian packages
      - update debian/rules
      - add debian/get-xpi-id.py
    + When rebuilding debian/control in the clean target, fail the build
      if the control file was out-of-date. This ensures that we don't
      accidentally drop language packs, and forces me to maintain an
      up-to-date control file in bzr
      - update debian/rules
    + Apply vendor patches to localized searchplugins too
      - update debian/patches/ubuntu-codes-amazon.patch
      - add debian/patches/ubuntu-codes-baidu.patch
      - update debian/patches/ubuntu-codes-google.patch
  * Ditch all the version-number based branding selection. Do this all
    purely on the channel name now
    - remove debian/firefox-beta.desktop.in
    - remove debian/firefox-nightly.desktop.in
    - remove debian/firefox-unofficial.desktop.in
    - rename debian/firefox-final.desktop.in => debian/firefox.desktop.in
    - update debian/firefox.desktop.in
    - update debian/rules
    - update debian/firefox.sh.in
  * Drop the DEB_ENABLE_IPC option, now that IPC is mandatory
    - update debian/rules
    - update debian/apport/firefox.in
    - update debian/firefox.install.in
    - update debian/mozconfig.in
  * Add some missing options to the manpage
    - update debian/firefox.1.in
  * Ensure we set LD_LIBRARY_PATH before running "firefox -h"
    - update debian/firefox.sh.in
  * Drop patches merged upstream:
    - 64-bit-be-fix.patch
  * Refresh patches:
    - mozilla-kde.patch
  * Ship channel-prefs.js. We used to ship this in Firefox 3.6, and it's
    required by Test Pilot now
    - update debian/firefox.install.in
  * Backport patch from mozilla-central to fix powerpc build failure
    - add debian/patches/powerpc-build-fix.patch
    - update debian/patches/series
  * Support storing language descriptions in locales.unavailable. This
    will be useful for translations which disappear temporarily
    - update debian/rules
    - update debian/refresh-supported-locales.pl
  * Add languages that are currently dropped in FF5 (compared with FF4) to
    locales.unavailable. Having transitional packages now will make
    transitioning easier later on if they come back
    - update debian/locales.unavailable
  * Refresh debian/control to pick up transitional packages
  * Don't bundle our vendor preferences in the omni.jar. This needs a distro
    patch and it turns out that Firefox does still read prefs from
    $LIBDIR/defaults/pref, so just install it there instead
    - update debian/rules
    - update debian/firefox.install.in
    - remove debian/patches/install-vendor-prefs.patch
    - update debian/patches/series
  * Add a global pref file again (/etc/firefox/syspref.js) and add the
    necessary preinst/postinst magic to move the old file there if it
    was previously customized
    - add debian/syspref.js
    - update debian/firefox.install.in
    - update debian/firefox.links.in
    - update debian/firefox.postinst.in
    - update debian/firefox.preinst.in
  * Ensure "Depends: ${misc:Depends}" is added to all transitional
    language packs
    - update debian/control.langpacks.unavail
    - refresh debian/control
  * Ship testpilot on aurora too
    - update debian/firefox.install.in
  * Set the right Vcs-Bzr URL
    - update debian/control.in
    - refresh debian/control
  * Update list of language packs to include new ones added upstream
    - refresh debian/locales.shipped and debian/locals.unavailable
    - refresh debian/control
 -- Chris Coulson <email address hidden>   Thu, 09 Jun 2011 13:21:00 +0100


If you want to try with gecko-mediaplayer, then I just downloaded the binary and installed using

```

sudo dpkg -i firefox_4*.deb

```When you have finished playing then install 14 again using
```

sudo apt-get install firefox

```

---

### Post by 2blue on 2012-08-23
Thanks again rsavage. I sort of put the Gnash issue with Firefox to the side, and forgot about it when I installed Midori and it wroked quite well there. It`s not ideal at all, but the 1.42GHz cpu can handle it fairly well it seams, or maybe its the graphics card. Problem is mostly html5 overrides Gnash at times which is a bit annoying. 

I am searching for info on Xubuntu and Parole, and wonder if there are any plugins for browser embedded video streams there? Parole is all new to me.

---

