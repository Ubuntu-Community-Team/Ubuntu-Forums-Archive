---
title: "Opening .exe files"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by BlueEight on 2007-10-29
How do I open .exe files in ubuntu? WINE seems not to be installed in Ubuntu, so I typed "sudo apt-get install wine" Then, I got, " E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" Does anyone know what that means?

---

### Post by petit.padavoine on 2007-10-29
This mean that another application that takes care of software packages is running, and is stopping apt-get from starting. So check to see all the the other package management application are closed (Synaptic, update-manager, etc...)

---

### Post by BlueEight on 2007-10-29
Well, I closed the programs, now it says,
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages"

---

### Post by aysiu on 2007-10-29
Why don't you tell us what you're trying to install?

.exe files are native Windows applications, not Ubuntu ones. So if they don't work, that only makes sense. If they do work, that's a pleasant surprise, but Wine is not a cure-all for running native Windows executables.

---

### Post by aysiu on 2007-10-29
> **BlueEight said:**
> Well, I closed the programs, now it says,
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.

Since you only requested a single operation it is extremely likely that
the package is simply not installable and a bug report against
that package should be filed.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  wine: Depends: binfmt-support (>= 1.1.2) but it is not installable
        Depends: libaudio2 but it is not installable
E: Broken packages"
[Get a fresh sources.list](http://www.psychocats.net/ubuntu/sources#editfile) and then try ```
sudo apt-get update
sudo apt-get -f install
```

---

### Post by BlueEight on 2007-10-29
> **aysiu said:**
> Why don't you tell us what you're trying to install?

.exe files are native Windows applications, not Ubuntu ones. So if they don't work, that only makes sense. If they do work, that's a pleasant surprise, but Wine is not a cure-all for running native Windows executables.
I'm trying to install flash player 8

---

### Post by aysiu on 2007-10-29
> **BlueEight said:**
> I'm trying to install flash player 8
No need for a .exe file, then.

Follow this tutorial:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by perlluver on 2007-10-29
There is a flash player in Ubuntu, just add it in synaptic, or add/remove programs.

edit: or use the link above, sorry about that.

---

### Post by Vadi on 2007-10-29
There is a linux version of it, you shouldn't need to use a .exe to install it.

As for the .exe files thing, install this useful script ([click]("http://ubuntuforums.org/showthread.php?t=533257")), and it'll automatically associate windows-related files to be opened by wine easily.

---

### Post by stchman on 2007-10-29
> **BlueEight said:**
> How do I open .exe files in ubuntu? WINE seems not to be installed in Ubuntu, so I typed "sudo apt-get install wine" Then, I got, " E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?" Does anyone know what that means?

Yes, .exe files are native Wondows files and you will need WINE to run them.

To install WINE follow this:

[http://www.stchman.com/install_wine_IE.html](http://www.stchman.com/install_wine_IE.html)

---

### Post by BlueEight on 2007-10-30
> **aysiu said:**
> No need for a .exe file, then.

Follow this tutorial:
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

I did, but in the middle of it, my computer froze, so I restarted it. Now, when I go to the web page to reinstall flash, it now says, "package flash non-free is already installed restart firefox to complete" I restart firefox, but when I go back to the web page, the same thing happens.

---

