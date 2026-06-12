---
title: "Macromedia install problem"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by j0eb0b on 2006-08-04
i am trying to install Macromedia Flash Player in both Foxfire and Opera.  I downloaded the application from Adobe and extracted the installer to my desktop.  When I run it in terminal I get the following error.

"Copyright(C) 2002-2003 Macromedia, Inc.  All rights reserved.

Macromedia Flash Player 7 for Linux

Macromedia Flash Player 7 will be installed on this machine.

You are running the Macromedia Flash Player installer as a non-root user.
Macromedia Flash Player 7 will be installed in your home directory.

Support is available at [http://www.macromedia.com/support/flashplayer/](http://www.macromedia.com/support/flashplayer/)

To install Macromedia Flash Player 7 now, press ENTER.

To cancel the installation at any time, press Control-C.



NOTE: Macromedia Flash Player requires two font packages
      to be installed, gsfonts and gsfonts-x11.

Press ENTER to continue...



NOTE: Please exit any browsers you may have running.

Press ENTER to continue...




Please choose which directory to install Macromedia Flash Player 7:

  [m] Install Macromedia Flash Player 7 into Mozilla user
      directory: /home/j0eb0b/.mozilla

  [o] Install Macromedia Flash Player 7 into Opera user
      directory: /home/j0eb0b/.opera

  [a] All

Please choose a directory: a


----------- Install Action Summary -----------

Macromedia Flash Player 7 will be installed in the following directory:

Mozilla installation directory  = /home/j0eb0b/.mozilla
Opera installation directory    = /home/j0eb0b/.opera

Proceed with the installation? (y/n/q): y
cp: cannot stat `/home/j0eb0b/Desktop/libflashplayer.so': No such file or directory
cp: cannot stat `/home/j0eb0b/Desktop/flashplayer.xpt': No such file or directory
cp: cannot stat `/home/j0eb0b/Desktop/libflashplayer.so': No such file or directory

NOTE: Please ask your administrator to remove the xpti.dat from the
      components directory of the Mozilla or Netscape browser.

chmod: cannot access `/home/j0eb0b/.mozilla/plugins/libflashplayer.so': No such file or directory
chmod: cannot access `/home/j0eb0b/.mozilla/plugins/flashplayer.xpt': No such file or directory
chmod: cannot access `/home/j0eb0b/.opera/plugins/libflashplayer.so': No such file or directory

Installation complete.


Perform another installation? (y/n):"

What have i done wrong?

Thanks,
joe

---

### Post by ovimunt on 2006-08-04
You need to be root.

Try:

```

sudo ./flashplayer-installer

```

***EDIT: ***Also make sure that you enter the correct plugins locations of Firefox and Opera! 

Fifefox usually is:

```

/usr/lib/firefox/plugins

```

---

### Post by Jagot on 2006-08-04
You are aware that Flash is available from the repos?  Enable the multiverse repo, then:

```
sudo aptitude update
sudo aptitude install flashplugin-nonfree
```

---

### Post by j0eb0b on 2006-08-04
Sorry I'm dumb as a post but things are still failing.

When I used your commands from root, here's what I get:

j0eb0b@ubuntu:~$ sudo aptitude update
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release.gpg [189B]
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release.gpg
Hit [http://www.getautomatix.com](http://www.getautomatix.com) dapper/main Packages
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release.gpg [189B]
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release.gpg
Ign [http://deb.opera.com](http://deb.opera.com) etch Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Release
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release.gpg [189B]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release.gpg
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Release
Ign [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates Release
Ign [http://theli.free.fr](http://theli.free.fr) ./ Packages
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper Release
Ign [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://deb.opera.com](http://deb.opera.com) etch/non-free Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Ign [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://people.ubuntu.com](http://people.ubuntu.com) ./ Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Sources
Err [http://theli.free.fr](http://theli.free.fr) ./ Packages
  404 Not Found
Hit [http://wine.lowvoice.nl](http://wine.lowvoice.nl) dapper/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-updates/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper-backports/multiverse Sources
Fetched 5B in 2s (2B/s)
Reading package lists... Done
j0eb0b@ubuntu:~$ sudo aptitude install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
j0eb0b@ubuntu:~$

Does this mean that flashplayer is installed and not working for some other reason?

Thanks,
Joe

---

### Post by Jagot on 2006-08-04
Well, that would suggest it is installed.  Try running the command sudo update-flashplugin

---

### Post by j0eb0b on 2006-08-04
OK,

ran the update command from root and was once again prompted for a password.  Nothing apparently downloaded and installed. Went back to a root prompt with no erors. Do you know how I can display Foxfire/Opera configured plugins?

Thanks,
Joe

---

### Post by Jagot on 2006-08-04
In Firefox in the address bar type 'about : plugins' - without the spaces.

---

### Post by j0eb0b on 2006-08-04
Can i ask you a favor.  Go the [www.abc.com](www.abc.com) and pick a random video feed with either Opera or Mozilla and tell me if you can open it?  On my system from Mozilla i get a blank screen that says "done" and with Opera it is sound only with occasional still video frames and an address bar (that won't respond) with a link to upgrade Macromedia.

Dapper is a stable OS but the multimedia configuration problems and limitations inhibit appeal for the general population.

---

### Post by j0eb0b on 2006-08-05
I have gotten to the point where macromedia appeares to install successfully but I still get the following coment during the install:

"NOTE: Please ask your administrator to remove the xpti.dat from the
components directory of the Mozilla or Netscape browser."

What does this means and is it the reason the macromedia does not run?

In spite of the successful installation message, I don't see the helper in Mozilla when I do an about:plugins.

Anyone else having problems with this?

Thanks.
Joe

---

### Post by Jellymountain on 2006-08-05
I've been having the same problems as you - i think it is because we don't know what we are doing - there must be an answer out there!

---

### Post by Jellymountain on 2006-08-05
I've has the same problem as you - still not found a way round it though....i don't know what stage i have got to at all!

---

### Post by trigo on 2006-08-23
i have the same problem with the 2 missing font but have installed them properly.  now the macromedia flash works but no font is visible.  how do i fix this?

---

### Post by ivan8r on 2006-08-27
> **Jagot said:**
> In Firefox in the address bar type 'about : plugins' - without the spaces.

I did this, and Firefox returned:

application/x-shockwave-flash 	Shockwave Flash 	swf 	Yes

To me, this indicates that Flash is installed correctly. I then try to go to a disney site for my son, and I get 

Software Detect
You do not have the most current version of Flash TM

Is there anything I can do?

---

### Post by CameronCalver on 2006-08-31
What i want to do is get all the miniclip games working try going to [http://www.miniclip.com/games/motocross-fever/en/](http://www.miniclip.com/games/motocross-fever/en/) and see if it works

---

