---
title: "[SOLVED] Problem Upgrading to Flash 9"
date: 2008-02-01
forum: Absolute Beginner Talk
---

### Post by plinydogg on 2008-02-01
Hi everyone,

When attempting to watch a YouTube video earlier this evening, I was told that my flash player was out of date. I downloaded the tar.gz from the Adobe website, extracted it in Nautilus (run as super user), and clicked on the installation script-thingee. I was prompted for the installation path of Firefox and entered what I thought it was but it keeps prompting me for the same thing. What is the proper directory/path?

Thanks in advance!

---

### Post by taurus on 2008-02-01
/usr/lib/firefox/plugins.  However, you need root privilege to write to that directory so maybe that is the problem.  Otherwise, you can install the plugin in your own $HOME if you wish, ~/.mozilla/plugins.

---

### Post by plinydogg on 2008-02-01
Thanks for trying but it still doesn't work. I started the installation process via Nautilus, which I ran as a superuser but it kept saying that the directory I chose didn't exist (even though I pulled it up with Nautilus just to make sure).  =(

---

### Post by taurus on 2008-02-01
Try installing it from a terminal.  Otherwise, just copy the other file (there should be two files in there, one is the installer and the other one is the flash plugin) to /usr/lib/firefox/plugins (or /usr/lib/mozilla/plugins).

---

### Post by plinydogg on 2008-02-01
Alright I just copied that file to both of the directories, reopened Firefox and attempted to watch the YouTube video, without success.

I will now attempt to install via the terminal.

Thanks for your continuing help!

---

### Post by plinydogg on 2008-02-01
No luck. Oh well. Thanks for trying =)

---

### Post by taurus on 2008-02-01
What old version do you have?  Maybe you need to remove it first before you install the newer one, version 9.

---

### Post by plinydogg on 2008-02-01
I'm pretty sure it's 8 but I'm not sure, nor do I know how to figure out the version or how to uninstall the version I have (good thing I posted in the "absolute beginners" forum, right? =)

I wonder if upgrading to the latest version of Firefox would solve this problem? I'm using 2.0.0.6, while the latest version is 2.0.0.11. I downloaded it yesterday but haven't been able to figure out how to install it either(!)...it's just a directory with a bunch of files and subdirectories...no install scripts that I can see or anything...

---

### Post by taurus on 2008-02-01
Do a Search in synaptic to see if you have version 8 of flash.  Then, uninstall it and reinstall version 9 again from a terminal.

---

### Post by plinydogg on 2008-02-02
Actually, this is odd: it says I have the following installed:

flashplugin-nonfree     (installed version: 9.0.48.0.2+really0u)(latest version: 9.0.48.0.2)

Doesn't this mean that I already have version 9?

---

### Post by jan quark on 2008-02-02
if your are still encountering flash issues

try to remove your flash version via synaptic

and try my guide to install the newest flash from the official adobe site

[http://janquark.fatfreehost.com/tutorial3.html](http://janquark.fatfreehost.com/tutorial3.html)

---

### Post by taurus on 2008-02-02
Yes.  Are you still having trouble with sites that require flash?

---

### Post by plinydogg on 2008-02-02
I feel like a total idiot: the problem wasn't Flash afterall but was rather a change in the default settings of NoScript (a Firefox plugin) that occurred as a result of an upgrade to the plugin. 

I'm sorry to have wasted your time and really appreciate the feedback from both of you. I'm also going to bookmark the flash installation tutorial for future reference. 

Thanks again!

---

