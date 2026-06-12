---
title: "upgrade on 3/4/08 killed mplayer/mencoder/k9copy"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by breakerfall on 2008-03-04
hey all...

I just ran a simple mark-all-upgrades (in synaptic) type upgrade on mostly gnome (with kde4 thrown in for messing around) 7.10 box...

it seems that the upgrade, which did a lot of kde4 upgrading, also removed mplayer, mencoder, and k9copy, and im sure some other stuff id like to have back...

now, trying to at least get my k9copy back, i end up bouncing around through synaptic trying to meet dependencies:
k9copy depends on mencoder
mencoder depends on libungif4g

it looks like i _can_ install libungif4g, but in doing so, id lose almost all of KDE, up to and including kubuntu-desktop...

so...

huh?

here's aptitude's take:
```

mike@evbuntu:~$ sudo aptitude install k9copy
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
The following packages are BROKEN:
  libgif4 
The following packages are unused and will be REMOVED:
  blt kaffeine libfame-0.9 libggi2 libgii1 libgii1-target-x libglib1.2 
  libgtk1.2 libgtk1.2-common libpvm3 libsvga1 mplayer-skins normalize-audio 
  pvm python-dev python-imaging python-tk python-wxgtk2.6 python-wxversion 
  toolame transcode transcode-doc txt2tags 
The following NEW packages will be automatically installed:
  libungif4g mencoder 
The following NEW packages will be installed:
  k9copy libungif4g mencoder 
0 packages upgraded, 3 newly installed, 23 to remove and 0 not upgraded.
Need to get 5182kB of archives. After unpacking 27.7MB will be freed.
The following packages have unmet dependencies:
  libgif4: Conflicts: libungif4g but 4.1.4-5 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Remove the following packages:
extragear-plasma
libgif4

Downgrade the following packages:
dolphin-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kappfinder-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kde4libs-bin [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-bin-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-data-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-runtime [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-runtime-bin-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-workspace [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-workspace-bin [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdebase-workspace-data [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdelibs5 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) -> 4:4.0.0-0ubuntu1~gutsy1
(gutsy-backports)]
kdepasswd-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kdepimlibs5 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kfind-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) -> 4:4.0.0-0ubuntu1~gutsy1
(gutsy-backports)]
klipper-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
konqueror-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
konqueror-nsplugins-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
konsole-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
ksysguard-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
kwin-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) -> 4:4.0.0-0ubuntu1~gutsy1
(gutsy-backports)]
kwrite-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]
libkonq5 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) -> 4:4.0.0-0ubuntu1~gutsy1
(gutsy-backports)]
libplasma1 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) -> 4:4.0.0-0ubuntu1~gutsy1
(gutsy-backports)]
systemsettings-kde4 [4:4.0.2-0ubuntu1~gutsy1~ppa1 (gutsy, now) ->
4:4.0.0-0ubuntu1~gutsy1 (gutsy-backports)]

Score is -922

Accept this solution? [Y/n/q/?] 


```

what did I do to deserve this?

any ideas?

thanks much!

---

### Post by dcstar on 2008-03-04
> **breakerfall said:**
> hey all...

I just ran a simple mark-all-upgrades (in synaptic) type upgrade on mostly gnome (with kde4 thrown in for messing around) 7.10 box...
.........
what did I do to deserve this?

any ideas?

thanks much!

Having just manually kicked off an update and seen a lot of missing repository files all over the place, I would speculate that there is a major upload of changed packages finding their way to all the Ubuntu mirror repositories at the moment (this seems to take time), and you unfortunately did an upgrade before all of them (that you require) made it into the mirror server you are using.

You should wait a day or so then do another update, hopefully all of the missing pieces will then be in your repository and you will have a better chance of getting everything sorted out.

---

### Post by Miguellint on 2008-03-06
Hi breakerfall....Can't offer any help but, just you don't feel all alone, I'm pretty much in the same boat. 

Ubuntu 7.10 with KDE4 installed as an alternate desktop. I mostly use KDE 3.5.8

Since the update on Tuesday(?) mplayer has disappeared and adept updater has a few kde4 apps that won't upgrade. If I manually set them to upgrade libgif4 uninstalls and libungif4g installs. 

Thanks to your post I haven't yet hit the "apply updates" button.

Will hang out a few more days to see if a fix appears.

Regards
Miguel

---

### Post by breakerfall on 2008-03-06
well, i decided to go ahead and did an "aptitude install k9copy" to see what would happen... i dont really use the KDE4 stuff that was going to removed, anyway...

it did remove all the stuff it said it would, and it did fix the lib issue that caused mplayer and k9copy to be removed, and k9copy, et al, did get reinstalled...

after aptitude finished, i did "apt-get update" and "apt-get upgrade" which did install a few items, then I went into synaptic and selected kde4-base (or desktop, i forget) for installation...  i was able to apply that change without issue... all the necessary dependencies installed fine, and k9copy and mplayer are unaffected...

i may mark this 'solved' if no one replies with similar issues in a day or two...

thanks for the help, guys!

---

### Post by markoloka on 2008-03-06
I just did update... still have 9 items that won't upgrade. Only thing that worked was something that remove in requested tag. Only problem now is that i cannot use kde4 anymore since it's not there "session type" in login screen.

---

### Post by breakerfall on 2008-03-06
marko, is the kde4 package still installed?
in synaptic, just search for kde4...
if it got uninstalled, try to re-install it...

i had to let the libungif upgrade uninstall all my kde4 stuff and then i was able to re-install kde4...

---

### Post by markoloka on 2008-03-06
> **breakerfall said:**
> marko, is the kde4 package still installed?
in synaptic, just search for kde4...
if it got uninstalled, try to re-install it...

i had to let the libungif upgrade uninstall all my kde4 stuff and then i was able to re-install kde4...

Checked.. and it's uninstalled!! wtf, i didn't choose to uninstall it as i used it 4 hours ago.  Strange. Now i'm gonna reinstall it.

Edit:Here we go again... 138 files to install. Hopefully now those 9 updates will upgrade.

---

### Post by breakerfall on 2008-03-06
any luck, marko?

---

### Post by markoloka on 2008-03-07
Yeah i got it back. Rest of updates upgraded also. Strange update as i needed to reinstall whole kde4. Never thought that was problem. Thanks.

---

