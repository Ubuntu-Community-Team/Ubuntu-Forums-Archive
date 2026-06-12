---
title: "Upgrade to 7.10 Fails"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by ziffnabb on 2007-10-20
Hi:
I am trying to upgrade to Gutsy, and during the course of fetching files, it stops and displays this:

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found

Is it because so many people are trying to upgrade or do I need to fix something?

Thanks,
Ziffnabb

---

### Post by Perfect Storm on 2007-10-20
Disable all non-official sources in your repo. You can do that via synaptic.

---

### Post by Desiree on 2007-10-20
I'm experienceing a similar problem. 

> 
Error during update

A problem occured during the update. This is usually some sort of network problem, please check your network connection and retry.

Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/binary-i386/Packages.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/free/source/Sources.gz) 302 Found
Failed to fetch [http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz](http://medibuntu.sos-sts.com/repo/dists/feisty/non-free/source/Sources.gz) 302 Found

There doesn't appear to be a problem with my network as far as I can tell.

Artificial Intelligence:
> Disable all non-official sources in your repo. You can do that via synaptic.

As a new user, which sources in the repo would be considered "non-official"? 

Also, does installing 7.10 require formatting my computer?  eg will I loose all my data/programs?

Thanks.
:confused:

---

### Post by fjf314 on 2007-10-20
Doing the network update from Feisty to Gusty will NOT format your computer. All of your personal files and many of your settings will remain intact. I just did it last night, I can vouch for this first-hand, haha.

---

### Post by 005david on 2007-10-20
im getting kinda sick of all you people thinking that noobs like us know how to do things like that.

if you want us to do things, DESCRIBE HOW.

---

### Post by fjf314 on 2007-10-20
> **005david said:**
> im getting kinda sick of all you people thinking that noobs like us know how to do things like that.

if you want us to do things, DESCRIBE HOW.

Relax. Getting angry with the people who you want to help you doesn't seem like a particularly good idea. When you only know someone through a forum, you have no clue how experienced they are. I'm sure that most people here don't want to type out a book with their replies, so they just give the short, simple answer. If you don't know how to do something, just ask the person to give you more directions. Getting angry won't solve anything.

---

### Post by 005david on 2007-10-20
> **fjf314 said:**
> Relax. Getting angry with the people who you want to help you doesn't seem like a particularly good idea. When you only know someone through a forum, you have no clue how experienced they are. I'm sure that most people here don't want to type out a book with their replies, so they just give the short, simple answer. If you don't know how to do something, just ask the person to give you more directions. Getting angry won't solve anything.

i'm saying that because this is the "absolute beginner talk" section

the people here are, hmm, idk, *absolute beginners?*

---

### Post by Kymus on 2007-10-20
I've had similar problems myself

> Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg](http://wine.lowvoice.nl/apt/dists/feisty/Release.gpg) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2](http://wine.lowvoice.nl/apt/dists/feisty/main/i18n/Translation-en_US.bz2) Could not resolve 'wine.lowvoice.nl'
Failed to fetch [http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz](http://wine.lowvoice.nl/apt/dists/feisty/main/binary-i386/Packages.gz) Could not resolve 'wine.lowvoice.nl' 

it sounds like a network issue, but considering my luck (bad luck) I can't help but be suspicious that the problem is on my end (although everything else works fine as far as the network goes)

---

### Post by psycosmyth on 2007-10-20
Hey, if you have not already done this, open synaptic package manager, click "settings" then "repositories" now un-check all but the Canonical-supported and source code, it will say to reload and click the refresh icon on top. Now upgrade with the upgrade manager. You can go back and add them later to update the non supported stuff.
You might encounter a hardware issue, if you do, hit esc at boot for your grub menu and use the older kernel, then you can restart after checking you restricted drivers.
I hope this is helpful and I was a newbie not too long ago.

---

### Post by genterminl on 2007-10-20
The site for medibuntu has changed names.  See [http://ubuntuforums.org/showthread.php?t=58405](http://ubuntuforums.org/showthread.php?t=58405) for instructions on fixing it.  However, as  Artificial Intelligence suggested, disabling non-official sources during the upgrade is probably a good idea.  There are two places you can do this.  The above link mentions using the 'Software Sources' application, which is under the System/Administration menu.  This is actually the same thing you get from running "Synaptic Package Manager' (same menu location) and selecting the settings/repositories menu.  The "Third-Party Software" tab is the unsupported software.  Uncheck them until you basic upgrade is complete.  Then re-enable them.

Note that you may get errors about problems upgrading some packages, since it obviously won't know how to upgrade any package that temporarily has it's repository disabled.  You can temporarily ignore those messages until you re-enable the repositories.  However, when you do - for the medibuntu - note you may have to edit the server name according to the above link.

---

### Post by fjf314 on 2007-10-20
> **005david said:**
> i'm saying that because this is the "absolute beginner talk" section

the people here are, hmm, idk, *absolute beginners?*

What qualifies as a "beginner" is relative, though. I still consider myself to be a beginner even though I have been using Ubuntu since 6.06. I don't know how to do a lot of advanced things with the system, but I have become familiar with some of the basics. What I know how to do and what another beginner knows how to do would be different.

---

### Post by frayalejandro on 2007-10-20
> **Artificial Intelligence said:**
> Disable all non-official sources in your repo. You can do that via synaptic.

This solved my same problem.

---

### Post by jdong on 2007-10-20
Medibuntu also recently changed their packages server. Please go to their homepage for updated instructions on activating their repository.

In general, Medibuntu is safe to use (it's managed by a group  of Ubuntu developers and all packages are derived from Ubuntu ones with minimal modification, or from other equally trustworthy high-quality sources)

However, during an **upgrade** it is best to disable all unofficial repositories.

---

### Post by Perfect Storm on 2007-10-21
> **Desiree said:**
> I'm experienceing a similar problem. 



There doesn't appear to be a problem with my network as far as I can tell.

Artificial Intelligence:


As a new user, which sources in the repo would be considered "non-official"? 

Also, does installing 7.10 require formatting my computer?  eg will I loose all my data/programs?

Thanks.
:confused:

In synaptic, go to settings tab ---> Repositories.
There's a third party software tab, disable them. Then Close.
push the reload button.

---

### Post by Perfect Storm on 2007-10-21
> **005david said:**
> im getting kinda sick of all you people thinking that noobs like us know how to do things like that.

if you want us to do things, DESCRIBE HOW.

Well, people aren't mind readers. It's hardly to know how much they know. I strongly think/hope that people report back if they don't understand the explanation. This aren't one way communication ;)

---

### Post by Desiree on 2007-10-22
It worked.  Thanks =)

:guitar:

---

