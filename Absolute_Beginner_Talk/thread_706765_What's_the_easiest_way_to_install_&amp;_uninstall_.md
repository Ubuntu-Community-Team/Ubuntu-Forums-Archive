---
title: "What's the easiest way to install &amp; uninstall Pidgin?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by ahuman on 2008-02-24
[COLOR="DarkSlateBlue"]**How would _you_ install _and/or_ uninstall Pidgin?**

The Pidgin-program can be compiled from it's source code, if you don't want to try any other ways of installing it to Ubuntu, but it takes quite awhile for it to completely install[/B][/COLOR]

**[COLOR="Green"]What's the easiest way to install & uninstall Pidgin?[/COLOR]**

---

### Post by wireddad on 2008-02-24
Synaptic package manager or [http://www.getdeb.net/release.php?id=1867](http://www.getdeb.net/release.php?id=1867)

---

### Post by jordanmthomas on 2008-02-24
How would I do it?
```
pacman -S pidgin
``` but I don't use Ubuntu

The easiest way for Ubuntu users is to just get it from the repositories.
```
sudo apt-get install pidgin
```
If this version isn't up to date enough for you, get it from 
[http://www.getdeb.net](http://www.getdeb.net)

On arch compiling pidgin from source would be trivial, but it's a little more difficult on Ubuntu, so why do it if you don't have to?

---

### Post by Paqman on 2008-02-24
It's installed by default. If I wanted to unistall/reinstall it later i'd use Synaptic. Add/Remove or apt-get would achieve exactly the same thing , though.

---

### Post by ahuman on 2008-02-24
**Thanks for your help, all of you. I appreciate all of those answers.**

---

### Post by Joeb454 on 2008-02-24
Actually as of Ubuntu 7.10 pidgin is included by default :)

It's under Applications>Internet

Hope this helps

---

### Post by aktiwers on 2008-02-24
[Click Here]("apt:pidgin")

---

### Post by tango_ninja on 2008-02-24
i believe with Gutsy it is installed by default...

```
sudo apt-get install pidgin
```
```
sudo apt-get remove pidgin
```

---

### Post by rambn on 2008-02-24
How about with a 64 bit machine running Dapper? I notice getdeb specifies for gutsy or fiesty.  Will fiesty pidgin work under dapper?  I had way to much trouble installing a working version of Ubuntu to change right now, thanks.

---

### Post by mivo on 2008-02-24
It depends on whether you want the latest version or just a working version. :) Gutsy / 7.10 includes or updates to 2.2.1, which is a solid and stable release. If you prefer the latest and newest, you need to uninstall the current version (*System -> Administration -> Synaptic Package Manager*, search for Pidgin and uninstall it) and then get the latest version from Getdeb.com at [http://www.getdeb.net/app/Pidgin]("http://www.getdeb.net/app/Pidgin"). I'm still using the version of the official repository, and it works just fine. :)

---

### Post by warbird on 2008-02-24
same as all above, except replace all instances of "apt-get" with "aptitude"

---

### Post by rambn on 2008-02-24
I don't mean to hijack, I think this is on topic (if not, please let me know)

When trying to install Pidgin, I get

XML::Parser perl module is required for intltool

looking into [http://search.cpan.org/~msergeant/XML-Parser-2.34/](http://search.cpan.org/~msergeant/XML-Parser-2.34/) but having trouble installing that as well.

thoughts?

---

### Post by mivo on 2008-02-24
rambn, how are you trying to install it? From Synaptic? The downloaded .deb from GetDeb.net? (see above) Compiling the source?

---

### Post by rambn on 2008-02-24
Mivo

Thanks for the reply!

Downloaded pidgin-2.3.1.tar.bz2 from sourceforge (couldn't find it in package manager.).

Then I just untared it and ran ./configure.  That's when I got the XML parser not found error.

---

### Post by mivo on 2008-02-24
I'd uninstall/delete the files, and get the proper Ubuntu installer from here: [http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)  (make sure Pidgin is properly uninstalled). Double-click the file and it'll be installed. Compiling it from source seems really troublesome. I tried this a few months back and couldn't get it to work; ended up throwing the towel -- others ran into the same problem. Using the file from GetDeb bypasses these issues, though, and it is the newest version, too. :)

---

### Post by rambn on 2008-02-24
Excellent advice. How do I uninstall?

---

### Post by mivo on 2008-02-24
Check *System -> Administration -> Synaptic* if Pidigin is installed. If it is, uninstall it. If it isn't, download the .deb from GetDeb and see if it works. It *should* work. Hopefully it *will,* too! :)

---

### Post by rambn on 2008-02-24
Dependency issues: 
dpkg: dependency problems prevent configuration of pidgin:
 pidgin depends on pidgin-data (<< 1:2.2.0-z); however:
  Version of pidgin-data on system is 1:2.3.0-1~getdeb1.
 pidgin depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 pidgin depends on libavahi-client3 (>= 0.6.13); however:
  Version of libavahi-client3 on system is 0.6.10-0ubuntu3.4.
 pidgin depends on libavahi-glib1 (>= 0.6.12); however:
  Version of libavahi-glib1 on system is 0.6.10-0ubuntu3.4.
 pidgin depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 pidgin depends on libcairo2 (>= 1.4.2); however:
  Version of libcairo2 on system is 1.0.4-0ubuntu1.2.
 pidgin depends on libdbus-1-3 (>= 0.94); however:
  Package libdbus-1-3 is not installed.
 pidgin depends on libdbus-glib-1-2 (>= 0.73); however:
  Version of libdbus-glib-1-2 on system is 0.60-6ubuntu8.1.
 pidgin depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 pidgin depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 pidgin depends on libgnutls13 (>= 1.4.0-0); however:
  Package libgnutls13 is not installed.
 pidgin depends on libgstreamer0.10-0 (>= 0.10.12); however:
  Version of libgstreamer0.10-0 on system is 0.10.6-0ubuntu2.
 pidgin depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 pidgin depends on libnm-glib0; however:
  Package libnm-glib0 is not installed.
 pidgin depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 pidgin depends on libperl5.8 (>= 5.8.8); however:
  Version of libperl5.8 on system is 5.8.7-10ubuntu1.1.
 pidgin depends on libsasl2-2; however:
  Package libsasl2-2 is not installed.
 pidgin depends on libsilc-1.0-2; however:
  Package libsilc-1.0-2 is not installed.
 pidgin depends on libxfixes3 (>= 1:4.0.1); however:
  Version of libxfixes3 on system is 1:3.0.1.2-0ubuntu3.
 pidgin depends on libxml2 (>= 2.6.27); however:
  Version of libxml2 on system is 2.6.24.dfsg-1ubuntu1.1.
 pidgin depends on libxrandr2 (>= 2:1.2.0); however:
  Version of libxrandr2 on system is 1:1.1.0.2-0ubuntu4.
dpkg: error processing pidgin (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 pidgin


just download and installed pidgin-data... what's up with all these dependency issues.

---

### Post by rambn on 2008-02-24
got the pidgin-data dependency figured out. now:

pidgin depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.

I'm thinking since I'm running Dapper, dependency issues are going to be too much to surmount. 

Package Manager won't give me an option of updating libatk. Thinking it's a no-go.

I would really like to update to Fiesty, so worried about video and wifi.

just trying to IM client so I can more easily post to twitter.com.

---

### Post by mivo on 2008-02-25
Oh, you hadn't mentioned Dapper before. Yes, that's the problem. Gutsy has been working well for me (not for everyone, granted), but perhaps you could try the Live CD and see if video and wifi work, without risking your current installation?

---

### Post by Golem XIV on 2008-02-25
When you uninstall Pidgin you need to remove all three modules

```
sudo apt-get remove pidgin pidgin-data libpurple0
```

and then install the new version from GetDeb.

At least that's what I had to do.  Once I did it this way, Pidgin 2.3.1 is working flawlessly.

---

