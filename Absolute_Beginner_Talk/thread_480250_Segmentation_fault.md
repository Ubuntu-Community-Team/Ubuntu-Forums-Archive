---
title: "Segmentation fault"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by yuzz on 2007-06-21
Hi, I've treid to install thunderbird 2.0.4 on my Kubuntu 7.04. I have followed instructions installing it with automatic script and manual installation - the result is the same I get Segmentation fault (core dumped) after starting thunderbird in console.
I've read that forum but resolutions with scim and lightning doesn't work for me (this programs are not installed on my computer).
I have AMD64 machine, matbe that is because of this?
Help me please!
Thank you!

---

### Post by Happy_Man on 2007-06-21
Why not just install the repo version? ```
sudo apt-get install mozilla-thunderbird
```

---

### Post by yuzz on 2007-06-21
yudin@aquarius:/homeT/yudin$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree
Reading state information... Done
mozilla-thunderbird is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
yudin@aquarius:/homeT/yudin$ thunderbird
Segmentation fault (core dumped)
yudin@aquarius:/homeT/yudin$ sudo apt-get remove mozilla-thunderbird
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages will be REMOVED
  mozilla-thunderbird
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 30.4MB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 113489 files and directories currently installed.)
Removing mozilla-thunderbird ...
yudin@aquarius:/homeT/yudin$ sudo apt-get install mozilla-thunderbird
Reading package lists... Done
Building dependency tree
Reading state information... Done
Suggested packages:
  mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector mozilla-thunderbird-enigmail
The following NEW packages will be installed
  mozilla-thunderbird
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/10.9MB of archives.
After unpacking 30.4MB of additional disk space will be used.
Preconfiguring packages ...
Selecting previously deselected package mozilla-thunderbird.
(Reading database ... 112967 files and directories currently installed.)
Unpacking mozilla-thunderbird (from .../mozilla-thunderbird_1.5.0.12-0ubuntu0.7.04_i386.deb) ...
Setting up mozilla-thunderbird (1.5.0.12-0ubuntu0.7.04) ...
Please restart any running Thunderbirds, or you will experience problems.

yudin@aquarius:/homeT/yudin$ thunderbird
Segmentation fault (core dumped)
yudin@aquarius:/homeT/yudin$ sudo apt-get install mozilla-thunderbird-typeaheadfind mozilla-thunderbird-inspector mozilla-thunderbird-enigmail
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed
  mozilla-thunderbird-enigmail mozilla-thunderbird-inspector mozilla-thunderbird-typeaheadfind
0 upgraded, 3 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/571kB of archives.
After unpacking 2642kB of additional disk space will be used.
Selecting previously deselected package mozilla-thunderbird-enigmail.
(Reading database ... 113490 files and directories currently installed.)
Unpacking mozilla-thunderbird-enigmail (from .../mozilla-thunderbird-enigmail_0.94.2-0ubuntu1_i386.deb) ...
Selecting previously deselected package mozilla-thunderbird-inspector.
Unpacking mozilla-thunderbird-inspector (from .../mozilla-thunderbird-inspector_1.5.0.12-0ubuntu0.7.04_i386.deb) ...
Selecting previously deselected package mozilla-thunderbird-typeaheadfind.
Unpacking mozilla-thunderbird-typeaheadfind (from .../mozilla-thunderbird-typeaheadfind_1.5.0.12-0ubuntu0.7.04_i386.deb) ...
Setting up mozilla-thunderbird-enigmail (0.94.2-0ubuntu1) ...
Setting up mozilla-thunderbird-inspector (1.5.0.12-0ubuntu0.7.04) ...
Setting up mozilla-thunderbird-typeaheadfind (1.5.0.12-0ubuntu0.7.04) ...
yudin@aquarius:/homeT/yudin$ thunderbird
Segmentation fault (core dumped)
yudin@aquarius:/homeT/yudin$

---

