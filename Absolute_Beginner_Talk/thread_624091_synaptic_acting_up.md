---
title: "synaptic acting up"
date: 2007-11-26
forum: Absolute Beginner Talk
---

### Post by pdlethbridge on 2007-11-26
I've noticed this a couple of times with synaptic in gutsy. When I try to apply changes to preferences, synaptic freezes up and I can't even use update manager. This is happening on a fresh install with all updates current. Anyone else having synaptic freezing up? I get this message in terminal if this helps with the diagnostics
pdleth@pdleth-desktop:~$ sudo apt-get upgrade 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
When I go to the source /var/lib/dpkg/lock there is a x near the upper right corner of lock

---

### Post by pdlethbridge on 2007-11-26
b

---

### Post by Hospadar on 2007-11-26
well you can't use update manager and synaptic at the same time.  Are you sure you are only running one copy of synaptic (check the System Monitor in System->Administration to be sure, it's possible there is some zombie synaptic in the background that shouldn't be there that still has a lock)

---

### Post by pdlethbridge on 2007-11-26
I can't enter synaptic after I force close it. The icon spins for a second and closes. Nothing can be updated until it is rebooted.

---

### Post by bapoumba on 2007-11-26
Do you still have a lock error message after a reboot ?

---

### Post by pdlethbridge on 2007-11-26
No, but if I try to change any preferences it will lock up again. A reboot will clear it.

---

### Post by bapoumba on 2007-11-26
As previously stated, you cannot run apt-get from the command line with synaptic open. Only one package manager can run at a time.

So from a clean reboot, please run:
```
gksudo synaptic
```
and paste any error message, including the ones you get when you try to close synaptic.

---

### Post by pdlethbridge on 2007-11-26
pdleth@pdleth-desktop:~$ gksudo synaptic
Another synaptic is running. Trying to bring it to the foreground
pdleth@pdleth-desktop:~$

---

### Post by bapoumba on 2007-11-26
```
$ ps -aux | grep synaptic
isabella  8405  1.3  2.4  42216 12472 ?        Ss   23:50   0:00 gksu /usr/sbin/synaptic
root      8406  7.5  6.2  62564 32392 ?        Ss   23:50   0:02 /usr/sbin/synaptic
isabella  8415  0.0  0.1   2972   764 pts/2    R+   23:50   0:00 grep synaptic
```

You should get only those lines, with numbers and username according to you own environment.

---

### Post by pdlethbridge on 2007-11-26
I rebooted and copied that command and synaptic opened up. What you saw before was before the reboot

---

### Post by bapoumba on 2007-11-26
Okay, no error message ?

---

### Post by pdlethbridge on 2007-11-26
When I ran ps -aux | grep synaptic, this is what I got after a reboot



pdleth@pdleth-desktop:~$  ps -aux | grep synaptic
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
pdleth    5542  0.0  0.0   2972   760 pts/1    S+   17:58   0:00 grep synaptic

---

### Post by bapoumba on 2007-11-26
So that's fine, no zombie instance of synaptic.

The bottom line: if you have synaptic up and running, do not use apt-get from the command line.
Start synaptic from the command line (gksudo synaptic) so you can get error messages if something goes wrong, and please paste them in here.

---

### Post by pdlethbridge on 2007-11-26
this is from the latest use of synaptic in terminal. Again I tried to change preferences but I got the same results and this message after I force quit synaptic. again this was all done from terminal per your instructions 
pdleth@pdleth-desktop:~$ gksudo synaptic
Another synaptic is running. Trying to bring it to the foreground
pdleth@pdleth-desktop:~$

---

### Post by pdlethbridge on 2007-11-26
b

---

### Post by pdlethbridge on 2007-11-26
b

---

### Post by pdlethbridge on 2007-11-26
b

---

### Post by bapoumba on 2007-11-27
Hmm. Would you be running update-manager with synaptic open ?

---

### Post by pdlethbridge on 2007-11-27
nothing else was running

---

### Post by bapoumba on 2007-11-27
Does this happen with other graphical applications running as root?
(ie, is the a gksudo issue or a synaptic issue).

---

### Post by pdlethbridge on 2007-11-27
this is only a synaptic issue. After a fresh install it does the same thing. There are preferences I would like to change, but I can't. I can change repositories and update that, but not preferences. I only use synaptic by itself, never with terminal, update or anything else running. I tried it again, but froze and I got this message in terminal

pdleth@pdleth-desktop:~$ gksudo synaptic
Another synaptic is running. Trying to bring it to the foreground
pdleth@pdleth-desktop:~$


Could this possibly have something to do with a bad cd during install?

---

### Post by pdlethbridge on 2007-11-27
I think I have found the problem. On a fresh install, if I try to update preferences , synaptic freezes. On a fresh install I tried something else tonight. If you download a couple of packages in synaptic, after they install, you get a screen asking if you want to automatically close, I checked it then changed preferences without a problem except it was  about 15 seconds to satisfy. So, would this be termed a bug?

---

### Post by bapoumba on 2007-11-28
> **pdlethbridge said:**
> I think I have found the problem. On a fresh install, if I try to update preferences , synaptic freezes. On a fresh install I tried something else tonight. If you download a couple of packages in synaptic, after they install, you get a screen asking if you want to automatically close, I checked it then changed preferences without a problem except it was  about 15 seconds to satisfy. So, would this be termed a bug?
Maybe. I suppose you are running GNOME, and a regular Ubuntu install.
Do you have 3D effects enabled?

---

### Post by pdlethbridge on 2007-11-29
I still have the bug and even though I reported the bug nothing has happened. It's a strange issue, still happening on this fresh install. I used envy to install nvidia drivers this time but I still have the problem.

---

### Post by vikramsharma on 2007-11-29
> **pdlethbridge said:**
> I've noticed this a couple of times with synaptic in gutsy. When I try to apply changes to preferences, synaptic freezes up and I can't even use update manager. This is happening on a fresh install with all updates current. Anyone else having synaptic freezing up? I get this message in terminal if this helps with the diagnostics
pdleth@pdleth-desktop:~$ sudo apt-get upgrade 
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
When I go to the source /var/lib/dpkg/lock there is a x near the upper right corner of lock

This happens a lot for me also, the easy way to deal with it is to remove the lock.  Close the synaptic/update manager, remove the lock by typing and running the following command in the terminal "sudo rm /var/lib/dpkg/lock" in the terminal (type without the quotes).  Synaptic/update manager would run without a problem, everytime you have a problem like that you can remove the lock that exists the /var/lib/dpkg directory.

---

### Post by bapoumba on 2007-11-29
> **pdlethbridge said:**
> I still have the bug and even though I reported the bug nothing has happened. It's a strange issue, still happening on this fresh install. I used envy to install nvidia drivers this time but I still have the problem.
Could you please give the link to the bug report?


> **vikramsharma said:**
> This happens a lot for me also, the easy way to deal with it is to remove the lock.  Close the synaptic/update manager, remove the lock by typing and running the following command in the terminal "sudo rm /var/lib/dpkg/lock" in the terminal (type without the quotes).  Synaptic/update manager would run without a problem, everytime you have a problem like that you can remove the lock that exists the /var/lib/dpkg directory.
The lock should go off once a package manager from the GUI is closed (synaptic, update-manager) or the actions are finished in the command line (aptitude, apt-get). Although sometimes it is necessary to remove the lock file because a process got it borked, it should not be a way to fix a recurrent issue.

---

### Post by vikramsharma on 2007-11-29
> **bapoumba said:**
> Could you please give the link to the bug report?



The lock should go off once a package manager from the GUI is closed (synaptic, update-manager) or the actions are finished in the command line (aptitude, apt-get). Although sometimes it is necessary to remove the lock file because a process got it borked, it should not be a way to fix a recurrent issue.

This lock thing happens when  Synaptic hasn't had a clean exit.

---

### Post by bapoumba on 2007-11-29
> **vikramsharma said:**
> This lock thing happens when  Synaptic hasn't had a clean exit.

Sort of.

Only one package manager can run at a time. The lock file is used to prevent a second package manager to run when one is already in use.
After the application is closed, or the CLI operations done, the lock file is released.

Looks to me, as the problem is recurring and as a reboot cleans it, that some other process is still running in the background. Probably dpkg. So this is why I asked for the bug report link.

---

### Post by pdlethbridge on 2007-11-29
Here's the link, finally

[https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/172487](https://bugs.launchpad.net/ubuntu/+source/synaptic/+bug/172487)

---

### Post by pdlethbridge on 2007-11-30
bump

---

### Post by bapoumba on 2007-12-01
```
ps -aux | grep dpkg
```
Could you please try this when you have synaptic frozen?

---

### Post by pdlethbridge on 2007-12-03
here you go!
pdleth@pdleth-desktop:~$ ps -aux | grep dpkg
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
pdleth    8492  0.0  0.0   2976   760 pts/0    S+   06:05   0:00 grep dpkg
pdleth@pdleth-desktop:~$ sudo ps -aux | grep dpkg
[sudo] password for pdleth:
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
pdleth    8494  0.0  0.0   2976   752 pts/0    R+   06:05   0:00 grep dpkg
pdleth@pdleth-desktop:~$

pdleth@pdleth-desktop:~$ sudo  ps -aux | grep dpkg
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
pdleth    8518  0.0  0.0   2976   752 pts/0    R+   06:07   0:00 grep dpkg
pdleth@pdleth-desktop:~$

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
pdleth@pdleth-desktop:~$

---

### Post by pdlethbridge on 2007-12-06
I tried something different on this fresh install. As an experiment, I let the install rename the home directory and I created a new home directory with a new /. It has gotten rid of all the problems I had with synaptic as well as some other issues that were unsolvable. It looks like this may be the only save way to reinstall a OS. I still have the old home directory, but it did not apply the settings that were messing me up.

---

### Post by bapoumba on 2007-12-07
Oh, so there was something with your previous user config then. Sorry I did not help you more, and I am very gad you got it sorted out :)
Thanks for coming back and post the way you fixed it, I'll remember this point if I come across other threads with the same kind of problem!

---

### Post by pdlethbridge on 2007-12-07
I thought it was rather strange that so many errors were caused and saved in the home directory. My assumption was that only things like web urls and pics and docs were saved in home. Guess I have to rethink how I handle a fresh install.

---

### Post by bapoumba on 2007-12-07
All user configurations are in /home, usually in hidden files (name starting with a ".").

It is convenient to have /home on a separate partition because you keep your config when reinstalling (this is what I do). For some reason, one config file may have been changed or corrupted and was kept with a fresh install. A new user had default working config files.

One way to go is to rename the config file (here, probably .synaptic). When the application is started over, a new default config is created and usually solves the problems.

---

### Post by pdlethbridge on 2007-12-07
Or you could just do what I did and transfer over only the files needed. This to me was a much safer way to handle it. Any time you alter a file, problems may arise. Now where would I start? In config there were over 80 undo menus
/media/sda2/pdleth/bin
/media/sda2/pdleth/Desktop
/media/sda2/pdleth/Digital Wave Player
/media/sda2/pdleth/Documents
/media/sda2/pdleth/downloads
/media/sda2/pdleth/Examples
/media/sda2/pdleth/file:
/media/sda2/pdleth/google-earth
/media/sda2/pdleth/ies4linux-2.0.5
/media/sda2/pdleth/Maildir
/media/sda2/pdleth/Music
/media/sda2/pdleth/opt
/media/sda2/pdleth/pauls files
/media/sda2/pdleth/Photos
/media/sda2/pdleth/Pictures
/media/sda2/pdleth/Public
/media/sda2/pdleth/Templates
/media/sda2/pdleth/Videos
/media/sda2/pdleth/vmware
/media/sda2/pdleth/.adobe
/media/sda2/pdleth/.aptitude
/media/sda2/pdleth/.assistant
/media/sda2/pdleth/.automatix
/media/sda2/pdleth/.beagle
/media/sda2/pdleth/.cache
/media/sda2/pdleth/.clamtk
/media/sda2/pdleth/.config
/media/sda2/pdleth/.cups
/media/sda2/pdleth/.dbus
/media/sda2/pdleth/.dbus-keyrings
/media/sda2/pdleth/.emilia
/media/sda2/pdleth/.evolution
/media/sda2/pdleth/.fgfs
/media/sda2/pdleth/.fontconfig
/media/sda2/pdleth/.FontForge
/media/sda2/pdleth/.gcjwebplugin
/media/sda2/pdleth/.gconf
/media/sda2/pdleth/.gconfd
/media/sda2/pdleth/.gimp-2.2
/media/sda2/pdleth/.gimp-2.4
/media/sda2/pdleth/.gnome
/media/sda2/pdleth/.gnome2
/media/sda2/pdleth/.gnome2_private
/media/sda2/pdleth/.gnucash
/media/sda2/pdleth/.gnupg
/media/sda2/pdleth/.googleearth
/media/sda2/pdleth/.gstreamer-0.10
/media/sda2/pdleth/.icons
/media/sda2/pdleth/.ies4linux
/media/sda2/pdleth/.java
/media/sda2/pdleth/.kde
/media/sda2/pdleth/.lgames
/media/sda2/pdleth/.local
/media/sda2/pdleth/.loki
/media/sda2/pdleth/.lprof
/media/sda2/pdleth/.macromedia
/media/sda2/pdleth/.mcop
/media/sda2/pdleth/.metacity
/media/sda2/pdleth/.mozilla
/media/sda2/pdleth/.mplayer
/media/sda2/pdleth/.nautilus
/media/sda2/pdleth/.neverball
/media/sda2/pdleth/.openoffice.org2
/media/sda2/pdleth/.picpuz
/media/sda2/pdleth/.pysol
/media/sda2/pdleth/.qt
/media/sda2/pdleth/.sane
/media/sda2/pdleth/.scorched3d
/media/sda2/pdleth/.scribus
/media/sda2/pdleth/.subversion
/media/sda2/pdleth/.supertux
/media/sda2/pdleth/.supertuxkart
/media/sda2/pdleth/.themes
/media/sda2/pdleth/.thumbnails
/media/sda2/pdleth/.tomboy
/media/sda2/pdleth/.Trash
/media/sda2/pdleth/.tremulous
/media/sda2/pdleth/.tvtime
/media/sda2/pdleth/.update-manager-core
/media/sda2/pdleth/.update-notifier
/media/sda2/pdleth/.VirtualBox
/media/sda2/pdleth/.vmware
/media/sda2/pdleth/.w3m
/media/sda2/pdleth/.wapi

---

### Post by hyper_ch on 2007-12-07
> **pdlethbridge said:**
> 
pdleth@pdleth-desktop:~$ sudo ps -aux | grep dpkg
[sudo] password for pdleth:
Warning: bad ps syntax, perhaps a bogus '-'? See [http://procps.sf.net/faq.html](http://procps.sf.net/faq.html)
pdleth    8494  0.0  0.0   2976   752 pts/0    R+   06:05   0:00 grep dpkg
pdleth@pdleth-desktop:~$


You were given the wrong command here. The proper would be:

```

ps aux | grep dpkg

```


bapumba just made a little mistake there ;)

---

### Post by pdlethbridge on 2007-12-07
How dashing! How would that change the results?

---

### Post by hyper_ch on 2007-12-07
try both commands....

---

### Post by pdlethbridge on 2007-12-07
can't now, problems been fixed

---

### Post by hyper_ch on 2007-12-07
you can run them anyway...

---

### Post by bapoumba on 2007-12-07
Woops, I'm sorry, I'm used to the -aux option.. ps just outputs a warning, in case the user is really "x", it's working normally though. Thanks hyper_ch  :)

---

