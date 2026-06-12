---
title: "Can't run update-manager"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by Shadowgaze on 2008-01-01
I tried running update manager to update from 6.06 and I got this warning.

Command 'gksu /usr/bin/update-manager ' not found.

I looked and the file is there.

---

### Post by kellemes on 2008-01-01
> **Shadowgaze said:**
> I tried running update manager to update from 6.06 and I got this warning.

Command 'gksu /usr/bin/update-manager ' not found.

I looked and the file is there.


from terminal..
- sudo updatedb
- sudo locate update-manager
- sudo gksu <path to>/update-manager

Edit: Have you installed gksu?

---

### Post by gmjs on 2008-01-01
I'm in the wrong operating system to check at the moment :), but try substituting gksudo for gksu in the command you're using:

# ** gksudo ** /usr/bin/update-manager

---

### Post by Shadowgaze on 2008-01-01
The first 2 parts worked, but the third didn't  This is what I got.


shadowgaze@Think-Brick:~$ sudo gksu usr/bin/update-manager
sudo: gksu: command not found
shadowgaze@Think-Brick:~$

---

### Post by Shadowgaze on 2008-01-01
That didn't work either 
shadowgaze@Think-Brick:~$ gksudo /usr/bin/update-manager
bash: gksudo: command not found

---

### Post by bapoumba on 2008-01-01
Do you have an error to **update-manager **? (just plain).

---

### Post by gmjs on 2008-01-01
Sorry about the last post - I got the instructions the wrong way round.

I'm running out of ideas!  All I can suggest is that you try installing gksu and then try the command again:

**# sudo aptitude install gksu**

(Answer questions to complete download and installation of gksu.)

**# gksudo /usr/bin/update-manager**

---

### Post by Shadowgaze on 2008-01-01
This is what I got

shadowgaze@Think-Brick:~$ update-manager
/usr/lib/python2.4/site-packages/apt/__init__.py:17: FutureWarning: apt API not stable yet
  warnings.warn("apt API not stable yet", FutureWarning)
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 168
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
Error in atexit._run_exitfuncs:
Traceback (most recent call last):
  File "/usr/lib/python2.4/atexit.py", line 24, in _run_exitfuncs
    func(*targs, **kargs)
  File "/usr/lib/python2.4/site-packages/UpdateManager/fakegconf.py", line 65, in fakegconf_atexit
    fakegconf.save()
  File "/usr/lib/python2.4/site-packages/UpdateManager/fakegconf.py", line 48, in save
    file = open(CONFIG_FILE, "w")
IOError: [Errno 13] Permission denied: '/root/.update-manager-conf'
Error in sys.exitfunc:
Traceback (most recent call last):
  File "/usr/lib/python2.4/atexit.py", line 24, in _run_exitfuncs
    func(*targs, **kargs)
  File "/usr/lib/python2.4/site-packages/UpdateManager/fakegconf.py", line 65, in fakegconf_atexit
    fakegconf.save()
  File "/usr/lib/python2.4/site-packages/UpdateManager/fakegconf.py", line 48, in save
    file = open(CONFIG_FILE, "w")
IOError: [Errno 13] Permission denied: '/root/.update-manager-conf'

---

### Post by Shadowgaze on 2008-01-01
Thanks gmjs that did the trick.  Thanks everyone else too.

---

### Post by bapoumba on 2008-01-01
Hmm..
Are you trying to upgrade from dapper to feisty ?
This in not quite normal. Update-manager should run from a regular user.

Could you post your sources.list?
```
cat /etc/apt/sources.list
```

---

### Post by rahul_bhise on 2008-01-04
i am also having the same problem. i was upgrading to gusty from festy. through synaptic manager then this problem happened when i click on system>administration>update manager nothing happens 
```
brahul@uhome:~$ update-manager
/var/lib/python-support/python2.5/gtk-2.0/gtk/__init__.py:48: RuntimeWarning: tp_compare didn't return -1 or -2 for exception
  from gtk import _gtk
ImportError: could not import atk
Traceback (most recent call last):
  File "/usr/bin/update-manager", line 29, in <module>
    import gtk.glade
ImportError: cannot import name Widget from gtk
brahul@uhome:~
```$
```
brahul@uhome:~$ sudo gksu /usr/bin/update-manage
brahul@uhome:~$ gksudo /usr/bin/update-manager
ImportError: could not import atk
brahul@uhome:~$
``` 
```
brahul@uhome:~$ cat /etc/apt/sources.list
# Automatically generated sources.list
# http://www.ubuntu-nl.org/source-o-matic/
#
# If you get GPG errors with this sources.list, locate the GPG key in this file
# and run these commands (where KEY is replaced with that key)
#
# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -
#
# If you don't know what to do with this file, read
# https://help.ubuntu.com/community/Repositories/CommandLine

# Ubuntu supported packages
# GPG key: 437D05B5
deb http://in.archive.ubuntu.com/ubuntu gutsy main restricted 
deb http://in.archive.ubuntu.com/ubuntu gutsy-updates main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security main restricted

# Ubuntu community supported packages
# GPG key: 437D05B5
deb http://in.archive.ubuntu.com/ubuntu gutsy universe multiverse 
deb http://in.archive.ubuntu.com/ubuntu gutsy-updates universe multiverse
deb http://security.ubuntu.com/ubuntu gutsy-security universe multiverse

```

---

### Post by bapoumba on 2008-01-04
Your sources.list is fine. Please paste the output to:
```
sudo apt-get update
sudo apt-get dist-upgrade
```

---

### Post by rahul_bhise on 2008-01-04
**brahul@uhome:~$ sudo apt-get update**
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/main Translation-en_IN
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1) gutsy/restricted Translation-en_IN
Get:1 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release.gpg [191B]                    
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Translation-en_IN
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release.gpg [191B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Translation-en_IN
Get:3 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Translation-en_IN
Ign [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Translation-en_IN
Get:4 [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release.gpg [191B]
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Translation-en_IN
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Translation-en_IN
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release
Ign [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Translation-en_IN
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates Release
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports Release            
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/main Packages         
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-updates/multiverse Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/main Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/restricted Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/universe Packages
Hit [http://in.archive.ubuntu.com](http://in.archive.ubuntu.com) gutsy-backports/multiverse Packages
Fetched 4B in 3s (1B/s)  
Reading package lists... Done
**brahul@uhome:~$ sudo apt-get dist-upgrade**
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
brahul@uhome:~$

---

### Post by bapoumba on 2008-01-04
Your system is up-to-date :)
There should be a menu somewhere (I'm not logged into a GNOME session, so I cannot tell exactly where, in administration I suppose) for services launched at startup. Make sure update-notifier is there, and you should be all good.

---

### Post by rahul_bhise on 2008-01-04
in system>preferences>sessions   on startup programs tab update notifier is there
but when i click on system>administration>*most of the utilities*  they wont work
also system>about Ubuntu  windows appear only for 2 seconds
or any help buttons on any application does not open any help window

---

### Post by bapoumba on 2008-01-04
Hmm..

Could you please see if with another user you get the same thing? Just make a test user:

```
sudo adduser test
```
or any other login, and see if you can get the "help" windows.

---

### Post by rahul_bhise on 2008-01-04
i made a new user and gave it a password logged out and logged in with new user and password
when the gutsy completely opened there was an error message
```
the panel encountered a problem while loading "OAFIID:Deskbar_Applet".
do you want to delete the applet from your configuration
```
i chosed  "don't delete"
the update manager, advance desktop manager etc. was not working, the* help and support* and *about Ubuntu* appeared only for 2 seconds

---

### Post by rahul_bhise on 2008-01-04
but the windows opened and closed differently (which was very cool )than my current user

---

### Post by bapoumba on 2008-01-04
A new user has default configuration files, this is why it is interesting to know. Looks like there is some problem with applets you are using. Try to remove every non-standard applet from your deskbar and see if it helps (I had once a problem with a GNOME applet running on Xfce, but I do not recall which one..).

Any particular theme? Running compiz or desktop effects?

---

### Post by rahul_bhise on 2008-01-04
what are applets how to distinguish between standard and non standard applets and lastly how to remove them
yesterday i did did something with compiz i thought they were default in gutsy and something to do with genome desktop

---

### Post by bapoumba on 2008-01-04
Your test user should have only the basic ones. I'll have to see which ones are provided with a basic GNOME install. I remembered it was the weather applet that gave me trouble.
To remove an applet, just right click and you should have the option.

Yes compiz is provided with gutsy, and you can run it if your video card supports 3D acceleration (did you install the restricted drivers?).

---

### Post by rahul_bhise on 2008-01-05
i have intel(r) 82845 g graphics controller card
and i may have installed its driver. i do not remember clearly that they where restricted or not.
and for the applets where are they listed.so i can deleat them.

---

### Post by rahul_bhise on 2008-01-06
problem solved
i installed some software
libiconv-1.11
glib-2.14.3
atk-1.9.1
and my update-manager, yelp and all the system>administration>*all application*  started working properly

---

### Post by bapoumba on 2008-01-06
Nice, I'm glad to see you got it fixed :)

---

