---
title: "What The ... Firefox Agrrrrrr"
date: 2005-11-01
forum: Absolute Beginner Talk
---

### Post by Micro Rotors on 2005-11-01
Ok I try to surf the web this morning on my NEW found friend "UBUNTU" ;)  and Firefox doesn't show up when I hit the icon! What happend?:confused: 

Im on Breezy 64

---

### Post by heimo on 2005-11-01
When this (rarely) happens to me, it's because firefox didn't close cleanly last time. If you haven't rebooted, it may help to run (alt+F2)
```
killall firefox-bin
```

If that doesn't help, open terminal Applications->Accessories->Terminal and type firefox on it. That may give you hints why it doesn't start. Post any errors / warnings and we may be able to help you. :) Until then... use epiphany or some other browser.

---

### Post by Micro Rotors on 2005-11-01
Is this what you wanted to see, I ran this;

bill@ubuntumicro-rotor:/usr/lib/mozilla-firefox$ ls
chrome             libmozjs.so                     pkg-ver
components         libnspr4.so                     plugins
components.ini     libnss3.so                      regchrome
defaults           libnssckbi.so                   regxpcom
defaults.ini       libplc4.so                      res
extensions         libplds4.so                     run-mozilla.sh
firefox            libsmime3.so                    searchplugins
firefox-bin        libsoftokn3.chk                 xpcshell
greprefs           libsoftokn3.so                  xpicleanup
icons              libssl3.so                      xpidl
libgkgfx.so        libxpcom_compat.so              xpt_dump
libgtkembedmoz.so  libxpcom.so                     xpt_link
libgtkxtbin.so     libxpistub.so
libjsj.so          mozilla-firefox-xremote-client
bill@ubuntumicro-rotor:/usr/lib/mozilla-firefox$ ./firefox
LoadPlugin: failed to initialize shared library libXt.so [libXt.so: cannot open shared object file: No such file or directory]
LoadPlugin: failed to initialize shared library libXext.so [libXext.so: cannot o pen shared object file: No such file or directory]
Segmentation fault
bill@ubuntumicro-rotor:/usr/lib/mozilla-firefox$

---

### Post by Kyral on 2005-11-01
There is a depend missing somewhere...
Try

sudo apt-get -f install

---

### Post by Micro Rotors on 2005-11-01
[QUOTE=Kyral]There is a depend missing somewhere...
Try

sudo apt-get -f install[/QUOTE]

Hi Kyral, I did and it still is not working. I even tried the lifesaver help icon and I get a message that says "Yelp" quite unexpectedly. heres the message I got from the sudo line;

bill@ubuntumicro-rotor:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
4 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up apache (1.3.33-8) ...

Creating config file /etc/apache/httpd.conf with new version

Creating config file /etc/apache/srm.conf with new version

Creating config file /etc/apache/access.conf with new version

Creating config file /etc/apache/modules.conf with new version
Starting web server: apache.

Setting up dwww (1.9.23) ...

Building dwww pages in the background...

Setting up info2www (1.2.2.9-23) ...

Setting up dpkg-www (2.47) ...
Updating apache configuration file: /etc/apache/httpd.conf
Restarting apache...
/usr/sbin/apachectl restart: httpd restarted

bill@ubuntumicro-rotor:~$



What do you think it is or happend?

Thanks
 Bill

---

### Post by poofyhairguy on 2005-11-01
Lets try to see what the problem is. First lets see if Firefox's package can be used. TO do that install the Epiphany browser:

> sudo apt-get install epiphany-browser

And it should ne in you applications menu. If it works then something weird is going on. I would follow this guide if I was you to get Firefox back:

[https://wiki.ubuntu.com/FirefoxNewVersion](https://wiki.ubuntu.com/FirefoxNewVersion)

(by the way, if you are on a slower machine Epiphany is way faster than Firefox)

---

### Post by Micro Rotors on 2005-11-01
I installed Epiphany just fine, but when I go to run it, It say it quite unexpectedly just like firefox,,, Agrrr, Im almost ready to just do a total reinstall of ubutu.

Bill

---

### Post by erikpiper on 2005-11-01
Wait- just so you know, Epiphany uses parts of firefox. (Just so you don';t go do a reinstall because of it...)

---

### Post by poofyhairguy on 2005-11-01
[QUOTE=erikpiper]Wait- just so you know, Epiphany uses parts of firefox. (Just so you don';t go do a reinstall because of it...)[/QUOTE]

Thats why I wanted to the user to install it.

My next suggestion is to uninstall then resinstall the Firefox package in synaptic.

---

### Post by bdash on 2005-11-01
sudo apt-get install libxt-dev

---

### Post by heimo on 2005-11-01
[quote=bdash]sudo apt-get install libxt-dev[/quote]
Seconded.

---

### Post by GreyFox503 on 2005-11-02
I don't know if this is your problem, but early on in my Ubuntu experience, I couldn't access the help screens and had a similar error to yours.  I would double check in synaptic and make sure the "ubuntu-desktop" package is installed.  If not, check the box next to it and it should install everything normally that comes with an ubuntu desktop.

---

### Post by Micro Rotors on 2005-11-02
Ok I played taps to the whole computer last night. I tried some of the stuff posted here and the problem got worse, everything was shutting down. So I went into windows and formatted that part of the drive to go for a complete re-install with the NON 64 version this time! 

MISTAKE, BIG MISTAKE![-X 

Now the computer won&#8217;t boot up even in windows, 

Grub error 17

I guess I wiped out the duel boot section!](*,)  Well at 2:30 am I wiped the drive clean from everything. So today I am re-installing all my @^%^&(**^%*%$#& *&(^&$%# stuff.

I would like to thank everyone for all there help, I know it can be tough trying to help other with this stuff when you&#8217;re not there to see what is exactly going on, kinda like threading a needle in the dark.

Figures this is the 13th post in this thread!

Thanks Again
Bill

---

### Post by heimo on 2005-11-02
You should be able to run fixmbr on Windows install cd, or reinstall grub:
[https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub]("https://wiki.ubuntu.com/RecoveringUbuntuAfterInstallingWindows?action=show&redirect=RecoveringGrub")


It sounds like a fresh install of Ubuntu might be smart choice. If you do, during install pay attention to any warnings or errors. Good luck and thanks for your patience. :) It's sometimes really hard to help people through discussion forum, but we try to do our best.

---

### Post by nrayever on 2005-12-11
[QUOTE=bdash]sudo apt-get install libxt-dev[/QUOTE]

pretty good!!! that worked for me!!! nice!! thanks for the help!! :D :D :D :D :D :D :D :D 

nrayever

edit
---------------------------------------------------
ooh man!!! this is magic!!!

---

