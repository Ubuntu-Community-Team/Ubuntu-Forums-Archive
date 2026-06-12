---
title: "help with &quot;Wine&quot;"
date: 2006-07-30
forum: Absolute Beginner Talk
---

### Post by IBiteGently on 2006-07-30
Good day everyone :)
I am hoping someone could help out installing wine on linux.  I have did everything one the Wine website, but when it came to installing wine, I have a few lib's missing.  They are th following:

The following packages have unmet dependencies:
  wine: Depends: libartsc0 (>= 1.5.2-0) but 1.4.3-0ubuntu1 is to be installed
        Depends: libasound2 (> 1.0.10) but 1.0.9-2 is to be installed
        Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
        Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed
        Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
        Depends: libxml2 (>= 2.6.24) but 2.6.21-0ubuntu1 is to be installed

Is there a package available with these lib's in them?

Any help would be greatly appreciated.

Thanks

---

### Post by x64Jimbo on 2006-07-30
Why don't you just install from the repositories? It's in there.

---

### Post by wombat20 on 2006-07-30
Yep, by far the best way to install almost all new stuff is with apt-get or Synaptic.

Synaptic can be found under the System -> Administration menu.

---

### Post by x64Jimbo on 2006-07-30
Dang, I need to get Ubuntu running in a VM so I can look this stuff up instead of having to be vague when I don't remember where to find stuff. Kubuntu is my desktop of choice, and it's nerve wracking that I often know the way to fix a problem in KDE or CLI, but not in Gnome.

---

### Post by IBiteGently on 2006-07-30
I do have them in my synaptic.  In my terminal I typed: sudo apt-get install wine, it looks like it installs but then I get the above messages after installation.  Also to note the lib's in synaptic listed above have a green box, is this normal?

---

### Post by IBiteGently on 2006-07-30
here is what I get when I try to install....

Reading package lists... Done
Building dependency tree... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: libartsc0 (>= 1.5.2-0) but 1.4.3-0ubuntu1 is to be installed
        Depends: libasound2 (> 1.0.10) but 1.0.9-2 is to be installed
        Depends: libgcc1 (>= 1:4.0.2) but 1:4.0.1-4ubuntu9 is to be installed
        Depends: libglib2.0-0 (>= 2.10.0) but 2.8.3-0ubuntu1 is to be installed
        Depends: libstdc++6 (>= 4.0.2-4) but 4.0.1-4ubuntu9 is to be installed
        Depends: libxml2 (>= 2.6.24) but 2.6.21-0ubuntu1 is to be installed
E: Broken packages

---

### Post by x64Jimbo on 2006-07-30
Sounds like you may be running a 64 bit system. Check out this thread:
[http://ubuntuforums.org/showthread.php?t=185557](http://ubuntuforums.org/showthread.php?t=185557)

---

### Post by samma on 2006-08-23
Is there a way to install libartsc0 and wine Without the computer your installing it on to have an internet connection?

---

### Post by x64Jimbo on 2006-08-24
you could download the necessary packages on another computer and then install them with dpkg

---

