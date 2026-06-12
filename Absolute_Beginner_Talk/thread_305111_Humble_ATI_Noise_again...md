---
title: "Humble ATI Noise again.."
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by petrus66 on 2006-11-22
Hi All

Fetched before the:
 "Ubuntu Edgy Installation Guide"

I got 3D graphics working with ATI X800 GTO card working on Suse 10.1 and with Ubuntu last year, but on this time its seems to be hiliariasly difficult.

Googled for it as any of we mortal people can do and got "look a like solution"

---------

1. Sudo gedit /etc/X11/xorg.conf

--------

1.a nice try, the only proper ubuntu I can boot on, is the recovery mode, and there I got to give a root password to get on

"give a root password or Ctrl to pass...bla, bla"

I give my root password to pass, because otherways my Ubuntu with the Ctrl+D (Or something) goes on booting into something that is no graphichally possible and stops on to black screen..

1.b gedit is not recovered so I run nano instead:

sudo nano /etc/X11/xonf

#here I add these lines at the end of the file:

EndSection

Section "Extensions"
                    Option  "Composite" "Disable"
EndSection

#Happy with that done, I save the file and I'm going for the #next line of this "anti-wiki, with no offence to the real #hackers"

...Contents

 "1.2 Installing the driver:"

sudo apt-get update
sudo apt-get install linux-restricted-modules-$(uname -r)
sudo apt-get install xorg-driverfglrx

...I never get this far... something is between me and the divine
..lol..

because some of the recovery boot options or the localisations repos I got this:

Err [http://fi.archive.ubuntu.com](http://fi.archive.ubuntu.com) edgy release.gpg
Temporary failure resolving 'bl.archive.bla'

or something and at last:

" Some index files failed to download"

Sorry to beeing so neeew to Linux but, before I change my graphics from ATI to nVidia:

Do I have to rise my eth on recovery mode to acces internet and all repos,
or is there any else I have to concider?

Humble mumle..mm




 
hmmm, somehow in recovery mode that is the only mode I can boot into do some things...

---

### Post by jordanmthomas on 2006-11-22
You can try to bring up your eth card like this:
```
ifconfig
```
Find which one you want to set up.
```
sudo ifup ethX
```
where X is the connection
try pinging google or something to make sure you're connected:
```
ping www.google.com
```
Ctrl-C when you're done there.

Also, why can't you boot normally?  Even if X doesn't start, you can still get to your terminals with Ctrl - Alt - F{1..6}
Then, your internet would already be up...just a thought.

---

