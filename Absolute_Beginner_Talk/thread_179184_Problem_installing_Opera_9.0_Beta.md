---
title: "Problem installing Opera 9.0 Beta"
date: 2006-05-19
forum: Absolute Beginner Talk
---

### Post by lodravah on 2006-05-19
I'm having problems installing Opera 9,0 Beta.. I run the downloaded .deb - package in terminal but it stops at Error: libqt3c102-mt, which it can't find. So I tried downloading and installing libqt3c102-mt, but then in was in conflict with another version, um... just have to paste a bit..  This version: libqt3-mt. Ended up with a broken package which I had to remove.. Someone know whats going down? 

And another question: With regular intervals I have to gedit sources.list after running "sudo apt-get update" because it keeps trying to download from a dead link. First it was "theli.fr" - something, and today it was 
"mobit.fi" - something. Is there some other update I should regulary do?

lodravah

---

### Post by Sef on 2006-05-19
Are you using Dapper or Breezy?

---

### Post by lodravah on 2006-05-19
[QUOTE=Sef]Are you using Dapper or Breezy?[/QUOTE]

breezy 5.10

---

### Post by helphope on 2006-05-19
Hi.
I installed Opera 9 beta last night. Great!
Just follow step by step this link

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

if you make your mind to install the plug-in for flash, when youdownload the package, there's an html file in it which explains how to proceed with the installation.
Easy!

I run on breezy too.

---

### Post by Sef on 2006-05-19
> I installed Opera 9 beta last night. Great!
Just follow step by step this link

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

if you make your mind to install the plug-in for flash, when youdownload the package, there's an html file in it which explains how to proceed with the installation.
Easy!

Dapper is even easier.  Just click on the install Opera icon and it will automatically install.

---

### Post by lodravah on 2006-05-19
[QUOTE=helphope]Hi.
I installed Opera 9 beta last night. Great!
Just follow step by step this link

[https://wiki.ubuntu.com/OperaBrowser](https://wiki.ubuntu.com/OperaBrowser)

if you make your mind to install the plug-in for flash, when youdownload the package, there's an html file in it which explains how to proceed with the installation.
Easy!

I run on breezy too.[/QUOTE]

All right.. I'll give it a shout and we'll see what happens.. But should I try to install the libqt3-mt before I try to run Opera install?

lodravah

---

### Post by Sef on 2006-05-19
> But should I try to install the libqt3-mt before I try to run Opera install?

Yes.

From the Terminal:

sudo apt-get update

sudo apt-get install libqt3-mt

---

### Post by lodravah on 2006-05-19
Erm.. *shameful*

As it turns out, I've downloaded the wrong file from Opera, it was not meant for Breezy 5.10, but for Xandros. I don't know how compatible these are, but now I've downloaded the right one, and installed it and everything is working without a hitch. Thank you for the link "helphope".. I'll tweak along now.. :)

lodravah

---

### Post by helphope on 2006-05-19
[QUOTE=lodravah]Erm.. *shameful*

As it turns out, I've downloaded the wrong file from Opera, it was not meant for Breezy 5.10, but for Xandros. I don't know how compatible these are, but now I've downloaded the right one, and installed it and everything is working without a hitch. Thank you for the link "helphope".. I'll tweak along now.. :)

lodravah[/QUOTE]

Just think that yesterday I was asking for the same problem. Help was given to me

Take care;)

---

