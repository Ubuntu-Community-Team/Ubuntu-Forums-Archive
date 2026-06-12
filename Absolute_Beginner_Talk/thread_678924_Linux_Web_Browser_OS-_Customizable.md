---
title: "Linux Web Browser OS- Customizable"
date: 2008-01-26
forum: Absolute Beginner Talk
---

### Post by Ian505 on 2008-01-26
I want to install and/or customize a flavor of linux so that it will only load the following:
GUI
Firefox/Opera (or both)
Java 6
Adobe Flash
Adobe Reader
Internet Connection Drivers

Basically I want to make/customize a OS that I can boot if all I want to do is browse the web or play the online MMORPG RuneScape, which is Java based. Is there a way that I can do this relatively easily?

Thanks,
Ian

---

### Post by mwacky on 2008-01-26
I think your aiming for compiling a custom kernal, here is the community doc on it, it's a good thing to read before you go for it:
[URL="https://help.ubuntu.com/community/Kernel/Compile"]
https://help.ubuntu.com/community/Kernel/Compile[/URL]

Or you can build a custom install:
[URL="http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys"]
http://www.howtoforge.com/ubuntu-linux-mint-livecd-with-remastersys[/URL]

As far as that being relatively easy, I don't really think it is.  The easiest way to achieve what you want would be to use the advanced options when installing Ubuntu, this is one of the last options in the graphical mode and should allow you to modify what software to include, then since Java iand Adobe are not on the install Cd, just install the Java and  Flash plugins for firefox and/or opera when the OS is installed and you're on the internet.  The standard install works to setup most internet connection out of the box, and the restricted drivers manage can handle most of the rest.

Here's a link to help with Adobe Reader:
[URL="http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html"]
http://www.ubuntugeek.com/how-to-install-adobe-pdf-reader-811-with-plug-in-for-mozilla-firefox-in-gutsy-gibbon.html[/URL]

---

### Post by Ian505 on 2008-01-26
Uggg... this is WAAY more work that I want. Is there a linux distribution that is only a web browser that I can use and just customize that? 

-Ian

---

### Post by Bionic Apple on 2008-01-26
If all you want is web applications, Google has created gOS for just that.  It may be a fairly limited Linux OS, but if that is all you want go for it.

[http://thinkgos.com/](http://thinkgos.com/)

---

### Post by aysiu on 2008-01-26
> **Bionic Apple said:**
> If all you want is web applications, Google has created gOS for just that.  It may be a fairly limited Linux OS, but if that is all you want go for it.

[http://thinkgos.com/](http://thinkgos.com/)
Small correction: gOS is not created by Google.

---

### Post by ugm6hr on 2008-01-26
> **Ian505 said:**
> I want to install and/or customize a flavor of linux so that it will only load the following:
GUI
Firefox/Opera (or both)
Java 6
Adobe Flash
Adobe Reader
Internet Connection Drivers

Basically I want to make/customize a OS that I can boot if all I want to do is browse the web or play the online MMORPG RuneScape, which is Java based. Is there a way that I can do this relatively easily?


Any Linux distro can do this - even Ubuntu Gutsy 7.10 (as long as you have ethernet connection to internet during installation):
[http://www.psychocats.net/ubuntu/minimal#barebones](http://www.psychocats.net/ubuntu/minimal#barebones)

That will give you IceWM as Window Manager, Firefox and Synaptic (this is not strictly necessary, but might make things easier for future updates etc without the commandline).

Drivers should be installed as long as the hardware is plugged in at installation.  If you need wifi - you'll have to manually configure it using the command line ([http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)) or install Network Manager with *sudo apt-get network-manager-gnome* (or choose another roaming app like Wicd - see the link in my signature for Wicd).

Then install Flash:
[http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466](http://ubuntuforums.org/attachment.php?attachmentid=53648&stc=1&d=1198033466)
Download to your /home/username then *sudo dpkg -i flashplugin-nonfree_9.0.115.0ubuntu0.7.10_i386.deb*

Java6:
*sudo apt-get sun-java6-plugin*

Acrobat Reader:
[http://www.adobe.com/products/acrobat/readstep2_allversions_nojs2.html?option=full&platform=LINUX_.deb&language=English&buttonContinue=](http://www.adobe.com/products/acrobat/readstep2_allversions_nojs2.html?option=full&platform=LINUX_.deb&language=English&buttonContinue=)
Haven't installed this myself, but doesn't look hard.  Or you could just use evince or xpdf from the repos instead.

You could then customize IceWM however you want.  Adesklets yab bar might be a good option to have Firefox, Logout etc on a desktop bar.  Or you could just have Firefox start up automatically at login.

Customizing IceWM is a whole other thread though!

---

