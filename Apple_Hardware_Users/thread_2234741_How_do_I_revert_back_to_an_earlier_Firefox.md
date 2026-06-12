---
title: "How do I revert back to an earlier Firefox"
date: 2014-07-16
forum: Apple Hardware Users
---

### Post by jacatone on 2014-07-16
I did an update on FF v12.04 on my Powerbook G4 and found the newer v30 is terrible. It's slow and doesn't show bookmarks. Version 11 was much better. How do I revert back?

---

### Post by ian-weisser on 2014-07-16
1) Remove the current version of Firefox (WARNING: Older browser versions maybe vulerable!)
```
sudo apt-get remove firefox
```

2) Look in /var/cache/archives/apt for the exact filename you want to install.
```
sudo dpkg --install /var/cache/apt/archives/<exact filename>
```

3) Pin the older version so your system doesn't promptly upgrade you to the version you don't want.
See [https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto) for an excellent step-by-step.

---

### Post by jacatone on 2014-07-17
Thanks, I've been giving that Midori browser a try since FF 30 was unusable. It's actually pretty good except you can't create bookmark folders for same subject sites which makes for kind of a jumble. Also no way to alphabetize bookmarks.

---

### Post by rsavage on 2014-07-17
I can't say I've experienced this.  Maybe Firefox can be a little slow if you load an old session?  Other than that, FF30 is fine with me.

Have you tried this [http://ubuntuforums.org/showthread.php?t=2205423](http://ubuntuforums.org/showthread.php?t=2205423) ?

---

### Post by jacatone on 2014-07-17
When I look in the archive file all I see is the following:


firefox_30.0+build1-0ubuntu0.12.04.3_powerpc.deb
firefox-locale-en_30.0+build1-0ubuntu0.12.04.3_powerpc.deb

There doesn't seem to be a .deb for the original v.11 that came with the fresh install. What would I do now?

---

### Post by Dennis N on 2014-07-17
> **jacatone said:**
> When I look in the archive file all I see is the following:


firefox_30.0+build1-0ubuntu0.12.04.3_powerpc.deb
firefox-locale-en_30.0+build1-0ubuntu0.12.04.3_powerpc.deb

There doesn't seem to be a .deb for the original v.11 that came with the fresh install. What would I do now?

FF 11 .deb file (Mar 2012) for your computer is probably this:

[http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_11.0+build1-0ubuntu0.10.10.2_powerpc.deb](http://old-releases.ubuntu.com/ubuntu/pool/main/f/firefox/firefox-branding_11.0+build1-0ubuntu0.10.10.2_powerpc.deb)

Realize that plug-ins and extensions may no longer be available, and this version is now considered insecure.

Good Luck.

---

### Post by OffelNice on 2014-08-18
For some reason I couldn't find this thread earlier.  I tried to ask a similar question (how to revert back to FF 24esr but received little help.)  Thank you. I found a different work around for this.

You can download Firefox-24.8.0esr from here.  [http://www.softexia.com/internet-tools/browsing/firefox-24/](http://www.softexia.com/internet-tools/browsing/firefox-24/)  Support for this version should last until October 2014 per documentation. 

 To uninstall Firefox 31 go to software center, type in "firefox" then click on remove when it appears in the list. 

You can also try purging all old files using instructions here.  I was only successful in doing this once.
   [http://baheyeldin.com/technology/how-install-firefox-esr-on-ubuntu-1204-64-bit.html](http://baheyeldin.com/technology/how-install-firefox-esr-on-ubuntu-1204-64-bit.html) 

 --To install files--  

After extracting files, 

 If using Ubuntu 12.04, Use nautilus to move files to the firefox folder in the Home/etc or System/usr/lib folder where it should be found.
Terminal: 
gksu nautilus 
[http://forums.techarena.in/operating-systems/1428799.htm](http://forums.techarena.in/operating-systems/1428799.htm) 

 Next create launcher in Unity bar.  

Follow instructions here:
 [http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/](http://www.howopensource.com/2012/10/create-application-launcher-add-icon-to-unity-ubuntu-12-10/)  

sudo gnome-desktop-item-edit /usr/share/applications/ --create-new

 "After  filling all the required fields, set icon for the application launcher.  Just click on the small box on the top left side near name field and  chose a image for it."  Image should be found in the  firefox/browser/icon folder.  

To add the Launcher to Unity Launcher

  "Go  to the Dash (Ubuntu Icon on the top left of unity launcher) and type  the Application name. From the dash result drag your application and  drop it in Unity. Right click icon and click 'lock to launcher'"  

[EDIT] You can also try downloading the fresh copy of Firefox 31 from Software center (or leave it if it is already there) and use Nautilus to overwrite the files in the File System/usr/lib  folder using the extracted files from the downloaded tarball "firefox-24.8.0esr.tar.bz2"

---

### Post by QIII on 2014-08-18
Use the instructions above with ***extreme caution.***

You risk both damage to your OS and security vulnerability.

Please see [this]("https://www.mozilla.org/security/known-vulnerabilities/firefox.html").

Also of note:  The OP is about PPC and the packages are different.

---

### Post by cariboo on 2014-08-18
We should also note, the gksu isn't installed by default in 14.04.

---

### Post by OffelNice on 2014-09-01
No caution is necessary.  Firefox 24.7.0 esr is an extended support release and security updates continue to update it.  It is fine for those of us dabbling with Ubuntu and testing it out to see if we would like to keep it.    I just wanted to add, you'll find the firefox folder and files to overwrite in nautilus in File System/usr/lib

---

### Post by vasa1 on 2014-09-01
> **OffelNice said:**
> No caution is necessary.  Firefox 25.7.0 esr is an extended support release and security updates continue to update it.  It is fine for those of us dabbling with Ubuntu and testing it out to see if we would like to keep it.  

I just wanted to add, you'll find the firefox folder and files to overwrite in nautilus in File System/usr/lib
You are really persistent in handing out advice such as "No caution is necessary". I wonder why.

BTW, what is Firefox 2**5**.7.0 esr?

---

### Post by Dennis N on 2014-09-01
> BTW, what is Firefox 25.7.0 esr? 
Mozilla does have an extended support release, but the current one seems to be Firefox ESR 31.0 as of Jul 22, 2014.
[https://www.mozilla.org/en-US/firefox/organizations/faq/](https://www.mozilla.org/en-US/firefox/organizations/faq/)
Where did the Firefox ESR 25.7.0 come from? There is no mention of any 25's on the life cycle chart at the above link.

Edit:
Checking again, the poster made an error in post #10 - it is actually 24.7 as written in post #7. That is the one now replaced by 31.0

---

### Post by OffelNice on 2014-09-06
> **vasa1 said:**
> You are really persistent in handing out advice such as "No caution is necessary". I wonder why.  BTW, what is Firefox 25.7.0 esr?  Perhaps because you all are such good teachers.   Clearly 25 was a typo.  The new release is now 24.8.0.  I've explained why (repeatedly). Here is further explanation in their change log   [https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html](https://www.mozilla.org/security/known-vulnerabilities/firefoxESR.html) (notice it contains many of the same critical updates as 31 and 32 [https://www.mozilla.org/security/known-vulnerabilities/firefox.html](https://www.mozilla.org/security/known-vulnerabilities/firefox.html))  If Mozilla (and others of slightly more wonk than you) believes their ESR is good enough then it is.

---

### Post by este.el.paz on 2014-09-10
Folks:

In terms of FF issues . . . my testing of PPC 14.04 continues in my G4 iBook . . . this AM FF (latest version, where do we find that in the new version?) crashed 4 times while trying to log into FB "messaging" . . . happened in LXDE, Openbox, and XFCE . . . so I'm assuming it has nothing to do with DE and something to do with FF?  Would I spend time to revert to an earlier version of FF?  Nah, just renders the system less use-able . . . decision will be whether to drop back to 12.04 . . . .

e.e.p.

[edit]:  Later that same day, rebooted back into OSX and was able to use Ten4Fox to get into FB messaging and, uh, message w/o it crashing . . . so fairly clear that it's an FF thing . . . .

---

