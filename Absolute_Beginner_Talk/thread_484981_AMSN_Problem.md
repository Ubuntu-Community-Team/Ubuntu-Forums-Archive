---
title: "AMSN Problem"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by XRichX on 2007-06-26
Thought id better open up a new topic, when i try to install Amsn and i get this error:

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'.

Error: Unable to prepare package AMSN MSN client.

can anyone help me here?

---

### Post by Jimmyfj on 2007-06-26
Did you install aMSN from the Programs/add/remove/Internet ? Or did you install it using Synaptic? 

If use use one of the above for installation of aMSN you'd get all dependencies worked out correctly.

---

### Post by XRichX on 2007-06-26
amsn isnt in synaptic or programs/add/remove so i downloaded it off firefox and then it did its thing and i was able to double click it for package installation... then that error comes up.

EDIT: doesnt matter i found it :) haha thanks, is there anyway i can install the drivers ffor my 'DC-3110' webcam for asmn as the drivers are on disk for Windows and is an executable... please help meee! haha :)

Thanks again,

Rich

---

### Post by ubuntu27 on 2007-06-26
> **XRichX said:**
> Thought id better open up a new topic, when i try to install Amsn and i get this error:

Checking for required C library versions ... OK
Checking for X ... OK
Checking for TCL Scripting Language ... failed
-------------------------------
Error: Could not find 'TCL Scripting Language'. Try using the native package manager for Ubuntu 7.04 (apt-get) to install a package with similar name to 'tcl'.

Error: Unable to prepare package AMSN MSN client.

can anyone help me here?

There is a OLD version of aMSN in the repositories. Since you got an error, I bet you downloaded from the aMSN website to get the new version that supports Voice Clip.

You need to install the following:

tcltls
tcl8.4
tk8.4


Those three packages are in the repository. So you can install it using Synaptic package Manager or the Terminal

```
sudo aptitude install tcltls tcl8.4 tk8.4
```

Now you can install the latest aMSN version 0.97

> **XRichX said:**
> 

Is there anyway i can install the drivers ffor my 'DC-3110' webcam for asmn as the drivers are on disk for Windows and is an executable... please help meee! haha :)

Thanks again,

Rich

Did you try to use that webcam already? Maybe the codecs are already installed (usually is, if it is compatible), I didn't install or configure in order to use my webcam an digital cameras. 

Install camorama Webcam Viewer and see if your webcam works.

package name "camorama" 

```
sudo aptitude install camorama
```

---

### Post by gottatrieit on 2007-06-27
Hi Ubuntu27!
I was following the advice given in another thread about browsing the threads looking for answers.  I needed those settings also as I downloaded aMSN from its website and it would not install properly because of the tls malfunction.(?)
I copied and pasted it into my terminal and --- Presto --- I had aMSN working!

 Thank you for your help.

---

### Post by ubuntu27 on 2007-06-28
> **gottatrieit said:**
> Hi Ubuntu27!
I was following the advice given in another thread about browsing the threads looking for answers.  I needed those settings also as I downloaded aMSN from its website and it would not install properly because of the tls malfunction.(?)
I copied and pasted it into my terminal and --- Presto --- I had aMSN working!

 Thank you for your help.

You're very welcome. :)

And welcome to Ubuntu and the community! :KS

---

