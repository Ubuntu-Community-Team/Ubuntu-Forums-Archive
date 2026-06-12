---
title: "Where can I get &quot;firefox-1.5.0.1.deb&quot; file?"
date: 2006-02-24
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-02-24
Hello all !!!

I would like to find "firefox-1.5.0.1.deb"?

I searched on "Synaptic" but it has the older Firefox's version...

I also went to "Mozilla's" Web Site, but I only found a ".tar.gz" file & got errors...

Is there somewhere  a ".deb" file to download & install?

Thanks.

---

### Post by briguy on 2006-02-24
I run firefox using mozilla's binaries - not installed via deb.  You can find instructions on how to do this here: [https://wiki.ubuntu.com/FirefoxNewVersion]("https://wiki.ubuntu.com/FirefoxNewVersion")

---

### Post by dvarsam on 2006-02-27
I have NEVER managed to install any ".tar.gz" package !!!

And that includes "Firefox 1.5"...

I wonder, does ANYBODY ever upgrade those Repositories?

Why can't we find ".deb" files for Firefox 1.5?

Why does it HAVE to be soooo hard each time we want to make a ".tar.gz" file install?

I tried what you suggested:
[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

And then I ended up Formatting my PC...

Is there ANYWHERE a ".deb" file for Firefox 1.5?

I do NOT get this:
We ALL want to make Ubuntu become the best OS out there, but there is NO ".deb" file NOT even for such a basic program like "Firefox 1.5"?

I even downloaded the experimental version & NOTHING again...

Question:
How often are the Repositories UPGRADED?
EVERY couple of years?
Cause I hate when NOT being able to try NEWer versions...

Help guys cause I am gettings nutts here...

---

### Post by kaamos on 2006-02-27
> I wonder, does ANYBODY ever upgrade those Repositories?
FF is more than a browser package. Upgrading firefox to 1.5 breaks:

bookmarkbridge
checky
ctxextensions
devhelp
dhelp
diggler
djvulibre
dpkg-www
endeavour
epiphany-browser
epydoc
firefox
flashplugin-nonfree
galeon
gecko-sharp
gecko-sharp2
gnome-app-install
j2se1.4-amd64
j2se1.4-i586
librsvg2
liferea
livehttpheaders
meta-j2re1.4-mozilla
mozilla-bonobo
mozilla-firefox-locale-all
mozilla-firefox-locale-ar
mozilla-firefox-locale-ca
mozilla-firefox-locale-el
mozilla-firefox-locale-eu
mozilla-firefox-locale-it
mozilla-firefox-locale-ja
mozilla-firefox-locale-ko
mozilla-firefox-locale-nb
mozilla-firefox-locale-tr
mozilla-firefox-locale-uk
mozilla-mozgest
mozilla-stumbleupon
mozilla-thunderbird
mozplugger
mplayerplug-in
nip2
nukeimage
nvu
openoffice.org2
openoffice.org2-amd64
tabextensions
venkman
vlc
wysihtml
xfig
yelp

[http://ubuntuforums.org/showthread.php?t=96595](http://ubuntuforums.org/showthread.php?t=96595)

---

### Post by dvarsam on 2006-02-27
Ok, then what do you suggest:

Look what I get:

root@house:/home/dimitris/Desktop# sudo tar -C /opt -x -z -v -f firefox-1.5.0.1.tar.gz
firefox/
firefox/.autoreg
firefox/chrome/
firefox/chrome/en-US.jar
firefox/chrome/en-US.manifest
firefox/chrome/browser.jar
firefox/chrome/browser.manifest
firefox/chrome/classic.jar
firefox/chrome/classic.manifest
firefox/chrome/comm.jar
firefox/chrome/comm.manifest
firefox/chrome/toolkit.jar
firefox/chrome/toolkit.manifest
firefox/chrome/icons/
firefox/chrome/icons/default/
firefox/chrome/icons/default/default.xpm
firefox/chrome/reporter.manifest
firefox/chrome/reporter.jar
firefox/chrome/pippki.jar
firefox/chrome/pippki.manifest
firefox/defaults/
firefox/defaults/pref/
firefox/defaults/pref/firefox-l10n.js
firefox/defaults/pref/reporter.js
firefox/defaults/pref/firefox.js
firefox/defaults/pref/channel-prefs.js
firefox/defaults/profile/
firefox/defaults/profile/bookmarks.html
firefox/defaults/profile/localstore.rdf
firefox/defaults/profile/prefs.js
firefox/defaults/profile/search.rdf
firefox/defaults/profile/mimeTypes.rdf
firefox/defaults/profile/chrome/
firefox/defaults/profile/chrome/userChrome-example.css
firefox/defaults/profile/chrome/userContent-example.css
firefox/defaults/autoconfig/
firefox/defaults/autoconfig/platform.js
firefox/defaults/autoconfig/prefcalls.js
firefox/browserconfig.properties
firefox/searchplugins/
firefox/searchplugins/amazondotcom.png
firefox/searchplugins/amazondotcom.src
firefox/searchplugins/answers.png
firefox/searchplugins/answers.src
firefox/searchplugins/creativecommons.png
firefox/searchplugins/creativecommons.src
firefox/searchplugins/eBay.gif
firefox/searchplugins/eBay.src
firefox/searchplugins/google.gif
firefox/searchplugins/google.src
firefox/searchplugins/yahoo.gif
firefox/searchplugins/yahoo.src
firefox/updater.ini
firefox/libmozjs.so

gzip: stdin: unexpected end of file
tar: Unexpected EOF in archive
tar: Unexpected EOF in archive
tar: Error is not recoverable: exiting now
root@house:/home/dimitris/Desktop#

What is this "Unexpected EOF in archive"?

And "Error is not recoverable:exiting now"?

If I get Errors right from the First step, imagine what is going to happen on the next steps....

What do I do, to fix the above?

Thanks.

---

### Post by kaamos on 2006-02-27
Try downloading the file again, it is probably just a corrupted archive.

---

### Post by Coelocanth on 2006-02-27
Yeah, there's got to be something wrong with your DLed file or you made some error in following the installation guide. I installed Firefox using that wiki guide and it worked perfectly. (If it can work for me, it can work for anyone... :lol: )

---

### Post by towsonu2003 on 2006-02-27
[QUOTE=dvarsam]
gzip: stdin: unexpected end of file
[/QUOTE]
as others said, that's a corrupted file... 

In the meantime, although upgrading firefox breaks many stuff, we still need 1.5.0.1 on the *main* repositories: [https://launchpad.net/products/firefox/+bug/32083](https://launchpad.net/products/firefox/+bug/32083)

---

### Post by dvarsam on 2006-02-27
When I get to the last command of step 5, according to:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

I get this:

root@house:/opt/firefox/plugins# rm libtotem_mozilla.*
rm: cannot remove `libtotem_mozilla.*': No such file or directory
root@house:/opt/firefox/plugins#

What is wrong in the above?

---

### Post by kaamos on 2006-02-27
That's ok. It only deals with removing a video plugin that does not work with firefox 1.5. You apparently don't have it installed so it can't be removed.

---

### Post by John.Michael.Kane on 2006-02-28
dvarsam use this method only if you feel you know what your doing as this is from debian repos. and could break your install..
[http://www.ubuntuforums.org/showthread.php?t=114292&highlight=firefox+deb](http://www.ubuntuforums.org/showthread.php?t=114292&highlight=firefox+deb)

---

### Post by Griff on 2006-02-28
You *could* install via arnieboys Automatix.  If you did a search I'm surprised you didn't see it.  I upgraded FF on my pc like you are trying, but used automatix for my laptop.  Automatix is definately the way to go.
Here's the link: [http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix](http://www.ubuntuforums.org/showthread.php?t=66563&highlight=automatix)

---

### Post by pinguinus on 2006-03-01
They do mention an experimental Firefox 1.5 deb package building script for Breezy on the FirefoxNewVersion page too: [https://wiki.ubuntu.com/FirefoxNewVersion#head-a14697a00e2bbd64f4d6ee098d69e97b5209ad44](https://wiki.ubuntu.com/FirefoxNewVersion#head-a14697a00e2bbd64f4d6ee098d69e97b5209ad44)

Anybody used that? What kind of experiences did you have?

---

