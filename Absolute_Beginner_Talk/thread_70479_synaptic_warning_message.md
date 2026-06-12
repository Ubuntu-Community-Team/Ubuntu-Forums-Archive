---
title: "synaptic warning message"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by Patrissimo on 2005-09-30
when I open synaptic I get a warning

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-i386_Packages) - stat (2 No such file or directory)

then when i run reload package I get

[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/main/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/universe/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/multiverse/binary-i386/Packages.gz:) 404 Not Found
[http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:](http://ubuntu-backports.mirrormax.net/dists/hoary-backports/restricted/binary-i386/Packages.gz:) 404 Not Found

when I close the window, I get

W: GPG error: [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) hoary-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

I've run apt-get update from the terminal but I get much the same thing.

All this started after I did something I probably shouldn't have done, which I found on a thread about automating script [http://www.ubuntuforums.org/showthread.php?t=22646&highlight=backport](http://www.ubuntuforums.org/showthread.php?t=22646&highlight=backport)

The instructions were:

Open a terminal session and enter:
wget [http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh](http://download.ubuntuforums.org/ubuntusetup/ubuntusetup.sh)
sudo sh ubuntusetup.sh
You will be asked to select "Yes" or "No" on various things you will want to select yes on them.

The "yes or no" thing didn't happen.



That set of code erased all my universe stuff in synaptic, so I did the extra repositories thing from ubuntuguide and they came back. 
Add/remove programs doesn't work anymore and it even seems to have goofed up an open office document on my desktop.
How much trouble am I in?

---

### Post by drogoh on 2005-09-30
Read the Backports forum, especially the first two stickies.

Edit:  That script adds old backports mirrors, change them in your repositories.

Correction:  I checked that script and mirrormax isn't in there ANYWHERE.  Are you sure you didn't add this yourself?

Note:  I have not personally tried said script, merely looked through its contents.

---

### Post by Patrissimo on 2005-09-30
Thanks Drogoh, I'll check it out now

---

