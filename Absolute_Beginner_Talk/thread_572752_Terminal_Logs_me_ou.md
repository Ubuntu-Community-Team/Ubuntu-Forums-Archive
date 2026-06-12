---
title: "Terminal Logs me ou"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by wesb on 2007-10-10
I am trying to install flash. The instructions say to do this and that in terminal but when I click on terminal the screen goes away and when it comes back I am logged out. What am I doing wrong?
This forum has been a wealth of info for me today BTW. Thanks to all who have helped and once again I apologize for all the n00b questions.

---

### Post by wesb on 2007-10-10
I am trying to install flash. The instructions say to do this and that in terminal but when I click on terminal the screen goes away and when it comes back I am logged out. What am I doing wrong?
This forum has been a wealth of info for me today BTW. Thanks to all who have helped and once again I apologize for all the n00b questions.

---

### Post by frup on 2007-10-10
It is logging you out to the main ubuntu log in screen? Sounds like X is crashing, the instructions aren't asking you to press CTRL ALT Backspace are they?

---

### Post by wesb on 2007-10-10
Here is a link to the files and the isntructions.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Instruction #4 Says the following:
In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

When I click on the Terminal it goes to a black screen and then to the main log in screen.

---

### Post by frup on 2007-10-10
What release of ubuntu are you using and for what machine architecture?

There are easier ways to install flash... on ubuntu 7.04 I thought it happened reasonably automatically.

---

### Post by overdrank on 2007-10-10
> **wesb said:**
> Here is a link to the files and the isntructions.
[http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash](http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash)

Instruction #4 Says the following:
In terminal, navigate to this directory and type ./flashplayer-installer to run the installer. Click Enter. The installer will instruct you to shut down your browser(s).

When I click on the Terminal it goes to a black screen and then to the main log in screen.

Hi you can use these links to install your restricted formats and codecs
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
[https://help.ubuntu.com/community/Re.../WindowsCodecs](https://help.ubuntu.com/community/Re.../WindowsCodecs)
Good luck!

---

### Post by -grubby on 2007-10-10
you can install flash (in firefox, at least) by going to a flash-enabled site (such as google video) and say play a video in google video and it will say at the top something like "missing plugin" so you click there

---

### Post by wesb on 2007-10-10
Thanks guys!! NathanGrubb got me fixed up with his method. So here is the question. In the future I will still have a need for the Terminal correct? If so how do I fix the logout issue?
The machine is a Dell Dimension 2200 straight out of the box. It had Win2k on it until today. :D

---

### Post by overdrank on 2007-10-10
> **wesb said:**
> Thanks guys!! NathanGrubb got me fixed up with his method. So here is the question. In the future I will still have a need for the Terminal correct? If so how do I fix the logout issue?
The machine is a Dell Dimension 2200 straight out of the box. It had Win2k on it until today. :D

Hi you can try and access the terminal with the alt,F2 keys and use this command
```
gnome-terminal
```

---

### Post by wesb on 2007-10-10
This is what I get..

The command "gnome-terminal" failed to run:

Failed to execute child process "gnome-terminal" (No such file or directory)

So I take it at some point it did not install for some reason???

---

### Post by wesb on 2007-10-10
ok fixed it by going to synaptic and installing it. I am learning the Linux thing.. w00t.. Thanks guys..

---

### Post by SoloSalsa on 2007-10-10
Are you using Xubuntu?  Yeah, that bug has been here for a long time, yet to be fixed.  xfterm4, the Xfce terminal emulator, has been killing X on some systems.  Some people found that using 16-bit graphics fixes it.  Otherwise, use plain-old xterm, or install gnome-terminal.

You can add your comments to the bug here: [Launchpad Bug #91849]("https://bugs.launchpad.net/xfce/+bug/91849").

---

