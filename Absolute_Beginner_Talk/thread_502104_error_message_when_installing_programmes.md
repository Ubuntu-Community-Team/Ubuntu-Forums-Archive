---
title: "error message when installing programmes"
date: 2007-07-16
forum: Absolute Beginner Talk
---

### Post by tipdrinker on 2007-07-16
This error message keeps popping up when i try to install or update applications...

E: clamav-base: subprocess post-installation script returned error exit status 1

E: clamav-freshclam: dependency problems - leaving unconfigured

E: clamav: dependency problems - leaving unconfigured

E: clamtk: dependency problems - leaving unconfigured

whats d prob?

(btw first post so sorry if this is in the wrong place)

---

### Post by KIAaze on 2007-07-16
It means that the package clamav-base has not been correctly installed.

Try running:
```
sudo dpkg --configure -a
```

If it finishes without error messages, you should be able install/update again.

If it still doesn't work, you can try to remove or reinstall clamav-base through synaptic.

---

### Post by tipdrinker on 2007-07-16
Ok well this is what happened...



Setting up clamav-base (0.90.2-0ubuntu1.2) ...
chown: cannot access `/var/run/clamav': No such file or directory
dpkg: error processing clamav-base (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of clamav-freshclam:
 clamav-freshclam depends on clamav-base (>= 0.90.2-0ubuntu1.2); however:
  Package clamav-base is not configured yet.
dpkg: error processing clamav-freshclam (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamav:
 clamav depends on clamav-freshclam | clamav-data; however:
  Package clamav-freshclam is not configured yet.
  Package clamav-data is not installed.
  Package clamav-freshclam which provides clamav-data is not configured yet.
dpkg: error processing clamav (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of clamtk:
 clamtk depends on clamav (>= 0.83); however:
  Package clamav is not configured yet.
 clamtk depends on clamav-freshclam (>= 0.83); however:
  Package clamav-freshclam is not configured yet.
dpkg: error processing clamtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 clamav-base
 clamav-freshclam
 clamav
 clamtk

---

### Post by KIAaze on 2007-07-16
Can you remove clamav-base completely?
```
sudo apt-get remove clamav-base
```

---

### Post by tipdrinker on 2007-07-16
grand thanks.

would you by any chance have a link to somewhere where i can learn how to use the terminal and basic language to know etc?

---

### Post by KIAaze on 2007-07-16
I'm happy it worked. :)
But remember that clamav (antivirus) is now uninstalled.
That's not such a big deal since GNU/Linux isn't much threatened by viruses.

If you ever want to reinstall it, you can do so through the Synaptic package manager or by command-line:
```
sudo apt-get install clamav
```
Note that clamav is only usable by command-line by default.
But there are several graphical frontends that can be used: [http://wiki.clamav.net/Main/ClamGUI]("http://wiki.clamav.net/Main/ClamGUI")

> would you by any chance have a link to somewhere where i can learn how to use the terminal and basic language to know etc?
Of course.
Here are some good places to start:
[https://help.ubuntu.com/community/UsingTheTerminal]("https://help.ubuntu.com/community/UsingTheTerminal")
[http://www.tuxfiles.org/linuxhelp/cli.html]("http://www.tuxfiles.org/linuxhelp/cli.html")
[http://www.linuxcommand.org/learning_the_shell.php]("http://www.linuxcommand.org/learning_the_shell.php")
Have fun. :)

---

### Post by tipdrinker on 2007-07-21
ive installed and updated a few aps and all is runnin smoothly thanks

---

### Post by raydar on 2007-08-01
I just had the same problem as the original post, with Synaptic in Feisty Ubuntu.  I read this thread, and uninstalled clamav-base and then installed clamav.  Had I read more carefully, I probably would know whether it was folly to remove with "-base" and install without it, but in any case the install went fine the second time, after nothing more than an uninstall.

Unfortunately, I never could find clamav on my system.  I found some kind of log file I think might've been related to the "installation," but nothing showed up in any Ubuntu menu and a file search turned up no executable or other batch of files I would expect.  I suppose I should install an antivirus as root rather than as a particular user, but I tried a couple more times uninstalling and reinstalling clamav and other clam items via Synaptic, logging off and back on (not as root), and restarting the system, and Synaptic shows it as installed, but I'll be darned if I can find any clams or other [insert bivalve joke here].

---

