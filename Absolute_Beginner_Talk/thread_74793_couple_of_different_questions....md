---
title: "couple of different questions..."
date: 2005-10-12
forum: Absolute Beginner Talk
---

### Post by allroz on 2005-10-12
I have attemtped to install limewire as instructed in the ubuntu installation guide. It installs, or so i think , but when i go to click on it it it will not open up. Also, there are errrors when i try to install macromedia flash player and the java plugin it. Root command doens't recognize the command. Lastly, is there some kind of restore on here, just like as on windows? BTW, i did update my repositories. Thanks.

---

### Post by mlomker on 2005-10-12
Have you installed Sun's Java yet?  There's a [how-to here.]("http://www.ubuntuforums.org/showthread.php?t=70428")

---

### Post by allroz on 2005-10-12
Ahh. Thanks. Working on it now although im running into some problems. I keep getting this error when i do apt-update. It says..

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by Kapre on 2005-10-12
[QUOTE=allroz]Ahh. Thanks. Working on it now although im running into some problems. I keep getting this error when i do apt-update. It says..

W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.[/QUOTE]

allroz - I think that port is down. Anyways, did you try installing the fakeroot already. It may already be in your list. Try it first (dont mind that error for now)

K

---

### Post by allroz on 2005-10-12
Yea, i've already tried to install the fakeroot and it just errors saying it doens't exist. Another question i had, was when i try to go into the office program, it gives me an error and says:

Details: Failed to execute child process "/usr/bin/ooimpress" (No such file or directory)


What's going on with that now. I think i have the problem for the java fixed. Now this office thing is bothering me. I also have broken packets. Am i just a failure at linux?

---

### Post by allroz on 2005-10-12
I get this error as well when i first enter into synaptic:


W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/main Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_main_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/universe Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_universe_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/multiverse Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_multiverse_binary-amd64_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://ubuntu-backports.mirrormax.net](http://ubuntu-backports.mirrormax.net) hoary-backports/restricted Packages (/var/lib/apt/lists/ubuntu-backports.mirrormax.net_dists_hoary-backports_restricted_binary-amd64_Packages) - stat (2 No such file or directory)

---

### Post by Kapre on 2005-10-12
allroz - I would assume you've followed the instructions on the how to on updating your repos. After updating the repos, I would assume you also run apt-get update and after that those errors showed up. I'm saying this because I just tried it and got to download the fakeroot package (I also have the errors for the other ports [that's why I wrote earlier to dont mind it]).

Regarding the problem with Oo now. This is something new. Assuming you have not install anything new, I would suggest you reboot and check if the same problem with exist.

K

---

### Post by allroz on 2005-10-12
Just rebooted, and im still having the same problem. Everything is up to date, and still have broken packages. Got this error when i booted up:

Error activating XKB configuration.
It can happen under various circumstances:
- a bug in libxklavier library
- a bug in X server (xkbcomp, xmodmap utilities)
- X server with incompatible libxkbfile implementation

X server version data:
The X.Org Foundation
60802000

If you report this situation as a bug, please include:
- The result of <b>xprop -root | grep XKB</b>
- The result of <b>gconftool-2 -R /desktop/gnome/peripherals/keyboard/kbd</b>

---

### Post by allroz on 2005-10-13
Anyone have any idea? Im running the 64 bit version of Breezy. Could it be that the 64 is a wee bit buggy? Should i go back to the original version? I have nothing valuable at all on this system. Thanks.

---

