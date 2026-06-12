---
title: "I can't install exe files"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by lordppm on 2007-10-15
I am trying to install thunderbird.exe file, but when I do double click, it says there is no appropriate application to run the file. I cannot file install shield as if in windows

---

### Post by Perfect Storm on 2007-10-15
.exe files are for windows.
Please read this: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
before advancing further.

---

### Post by mlentink on 2007-10-15
Fortunately, installing software in Ubuntu is usually a lot easier than it is in Windows. Go to Applications > Install Remove Software, take a look at the Internet section scroll down to 'Thunderbird Mail' and tick the check box next to it. Then click Apply and everything will be installed for you.

---

### Post by anaconda on 2007-10-15
or from the command line:
```
sudo apt-get install mozilla-thunderbird
```
would download and install thunderbird for you..

exe-files are for windows, but some of them can be run through wine.

---

### Post by erginemr on 2007-10-15
The following web site:
[http://www.mozilla.com/en-US/thunderbird/all.html](http://www.mozilla.com/en-US/thunderbird/all.html)
has also the latest linux version (2.0.0.6) of thunderbird if you really like to venture. (I didn't try myself.) 

But for a hassle-free installation, I would also suggest using "sudo aptitude install mozilla-thunderbird" from the terminal. 

I prefer using "aptitude" over "apt-get" for installation / uninstallation purposes, because aptitude keeps track of the side effects of the installation much better (i.e. the list of extra packages needed for installation), and lets you remove those residual packages as well when you decide to unsinstall any program installed with the "aptitude" by issuing the command: "sudo aptitude remove mozilla-thunderbird".

Good luck!

---

