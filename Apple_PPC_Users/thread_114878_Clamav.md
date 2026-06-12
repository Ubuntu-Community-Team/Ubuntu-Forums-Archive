---
title: "Clamav?"
date: 2006-01-09
forum: Apple PPC Users
---

### Post by nuke on 2006-01-09
Hi!

I looked to install Clamav onto my Powerbook (G3 Bronze )running Kubuntu but couldn't find a binary using apt-get or the GUI installer.

Is Clamav available for the PPC? If yes, where or how do I install it.

Thanks

---

### Post by hezekiahb on 2006-08-15
I'm not certain about this but I believe you can get the source for ClamXAV, which is ClamAV ported for OS X.  If you can you should be able to compile it for Ubuntu on your PPC.  I don't think there is a GUI version available for Linux on PPC.  Here is the site.

[http://www.markallan.co.uk/clamXav/](http://www.markallan.co.uk/clamXav/)

If anything the developer may be familiar with where you could get a Linux version (or may be able to get it from him).  Hope this helps. :)

-Hezekiah

---

### Post by Malac on 2006-08-15
I'm probably misunderstanding the question,so please forgive, but......

To install the GUI for ClamAV is :
```
sudo apt-get install clamtk
```
This should tell you that you need to install dependencies all the clamav files.

Hope this helps.

---

### Post by three-cushion on 2007-01-14
I have Ver 6.06 LTS installed on my G4 (OS 10.4.8 ). The G4 Mac system has ClamXav from Mark Allan running quite nicely.

On Ubuntu I tried once to install clamav, but did not suceed. And, I had updated Universal search in *sources.list*. 
In my Latest re-install, I still had 3 unresolved dependicies:
..... all are gnome: -terminal-data; -terminal; and ubuntu-desktop

When I try to update these (w/ Synaptic), it always fails.

The last (and initial) clamav try ended up with unresolves as well. 3 of the clam files refused to install b/c libclamav1 was unresolved. And, I *think* that was b/c the install still had the ver -2 engine... whereas the -7 engine source is available.

Questions:
1) How are the gnome-  & Ubuntu items resolved?
2) Should I re-install clamav (after complete removal first of all Ver -2 files) with 
    sudo apt install clamav?
3) After a download of the -7 clam engine, how does one install that source? and should it come before or after the clamav installs?

Any help will be greatly appreciated. ](*,) 

Cheers, Jim B

---

### Post by gottatrieit on 2007-01-16
I have basically one question and one problem associated with ClamAV.

  Question: Is it really necessary to have an anti-virus checker? I presume the answer is yes, but I had to ask.  I attempted to download ClamAV with Firestarter package, but ClamAV failed.

Problem: ClamAV failed to install on three attempts; one with Firestarter package and two from terminal using code as a single install. :confused: 

 Code:
             apt-get install clamav

  This is the message at the end of the installation process:

       [COLOR="Red"]E: Sub-process /usr/bin/dpkg  returned an error message (1)[/COLOR]

  [COLOR="Black"]I have a screenshot but I could not get it to copy into here.[/COLOR]

---

