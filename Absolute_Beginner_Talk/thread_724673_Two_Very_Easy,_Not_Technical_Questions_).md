---
title: "Two Very Easy, Not Technical Questions :)"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by Literati on 2008-03-14
I just wanted to know, first of all, I've made my "home" as a partition on another hard drive, so that when I want to upgrade to 8.04 I can, without losing my media files in Home and such. However, I was thinking, wouldn't all my installed programs go away too? As those AREN'T in my home partition. Is there an easy way to recover these after an upgrade? Or a script that you could sort of, take an image of what's on Ubuntu right now, and when you install 8.04, it'll go grab all those things for you? Or, basically, how do you suggest going about upgrading? :) (When the time comes of course)

Secondly, I know windows has a REGISTRY where basically eveerytime you install or uninstall something, it gets edited, ultimately slowing down windows entirely. Does Linux do something like this? Or is it consistently fast? What do you suggest I do to keep my Ubuntu fast? :) 

Thanks!

---

### Post by Sef on 2008-03-14
> Secondly, I know windows has a REGISTRY where basically eveerytime you install or uninstall something, it gets edited, ultimately slowing down windows entirely. Does Linux do something like this?

No.  GNU/Linux does not have a registry.

> Or, basically, how do you suggest going about upgrading?

Back up everything before you attempt to upgrade.

---

### Post by Duck2006 on 2008-03-14
If you do an upgrade from 7.10 to 8.04 all your programs will still be there and should work ok.

> Secondly, I know windows has a REGISTRY where basically eveerytime you install or uninstall something, it gets edited, ultimately slowing down windows entirely. Does Linux do something like this? Or is it consistently fast? What do you suggest I do to keep my Ubuntu fast?

Today there was a thread on speeding up ubuntu if you do a search on it you should find it.

---

### Post by Joeb454 on 2008-03-14
I think your programs go after an upgrade, if so just reinstall them, because all the config files containing your settings will still be in /home :)

That's why a lot of people recommend having /home on a separate partition or HDD :)

---

### Post by handydan918 on 2008-03-14
> **Literati said:**
> I just wanted to know, first of all, I've made my "home" as a partition on another hard drive, so that when I want to upgrade to 8.04 I can, without losing my media files in Home and such. However, I was thinking, wouldn't all my installed programs go away too? As those AREN'T in my home partition. Is there an easy way to recover these after an upgrade? Or a script that you could sort of, take an image of what's on Ubuntu right now, and when you install 8.04, it'll go grab all those things for you? Or, basically, how do you suggest going about upgrading? :) (When the time comes of course)

Secondly, I know windows has a REGISTRY where basically eveerytime you install or uninstall something, it gets edited, ultimately slowing down windows entirely. Does Linux do something like this? Or is it consistently fast? What do you suggest I do to keep my Ubuntu fast? :) 

Thanks!
Q1-You can do ```
dpkg --get-selections>>filename-of-your-choice.txt
```
This will create a small text file that lists all installed packages, assuming they were installed with the Debian package management system. 
tarball installations won't be included.
To restore your software on a newly installed system, do
```
dpkg --set-selections<filename-of-your-choice.txt
```
This will install and configure all your previously installed packages.

Q2- Thankfully, no ##%^&%@* registry in Linux! No significant file fragmentation, either.

---

### Post by Vadi on 2008-03-14
I think there's gconf which stores settings for values. It never slows down though like the Windows one.

Linux shouldn't (and does't that I've seen so far) slow down over time either.

---

### Post by Duck2006 on 2008-03-14
[http://ubuntuforums.org/showthread.php?t=712625](http://ubuntuforums.org/showthread.php?t=712625)

---

### Post by iansane on 2008-03-14
mine seems to have slowed down just a very little bit with some things but it's not because of something like a registry. It's probably cause of haveing to sort through tons of unnessesary files on the hard drive from where I install tons of programs to see what they do and then don't get around to removing them. It seems to run faster when I have a fresh install and only the apps I need. Like I said its only a very little bit. Maybe it's all in my head and I'm just getting faster. LOL

---

### Post by Literati on 2008-03-14
> **handydan918 said:**
> Q1-You can do ```
dpkg --get-selections>>filename-of-your-choice.txt
```
This will create a small text file that lists all installed packages, assuming they were installed with the Debian package management system. 
tarball installations won't be included.
To restore your software on a newly installed system, do
```
dpkg --set-selections<filename-of-your-choice.txt
```
This will install and configure all your previously installed packages.

Q2- Thankfully, no ##%^&%@* registry in Linux! No significant file fragmentation, either.

Wow! That backup list is fantastic! This will make my switch to HH much easier :) There won't be any like "This program isn't compatible in 8.04" will there? Or maybe just minimally?

And when you say to backup all my data before an upgrade, do you mean (for example)

My 80GB drive is my boot drive which has all the installed files on it, and such. But my 400GB drive is my "stuff" drive with all my music, videos, etc (My /home HDD) Should I just copy all the contents of the 80GB to it temporarily while making sure the upgrade went okay, then delete it? 

When I say upgrade by the way, I know many people say to not upgrade, and I'm not, it's just the word I'm using. I would format it, and install fresh.

And hooray for no registry! I also installed the preload program. Other than that, I didn't touch anything yet, I'm still trying to get my setup working properly, so I won't tweak too much yet! :D

Secondly, it's great that now I'll be able to re-install my programs fast, but since I DO have my other HDD set as "/home", is there something that will help me set that up to use as home again? Or should I just reinput the commands? (I would have to find them again) 

Thanks!

EDIT: Handydan, I'm proud to say that I understand your sig! I knew the saying before the command obviously, but I remember what that command does. :) Very clever ;)

---

### Post by handydan918 on 2008-03-14
> **Literati said:**
> Wow! That backup list is fantastic! This will make my switch to HH much easier :) There won't be any like "This program isn't compatible in 8.04" will there? Or maybe just minimally?There shouldn't be anything like that, assuming all your apps got into the new repos...
> 

And when you say to backup all my data before an upgrade, do you mean (for example)

My 80GB drive is my boot drive which has all the installed files on it, and such. But my 400GB drive is my "stuff" drive with all my music, videos, etc (My /home HDD) Should I just copy all the contents of the 80GB to it temporarily while making sure the upgrade went okay, then delete it? 
Never mind! If you have a separate disk for your /home, that should be all the backup you need for the purposes of these proceedings. Just don't let the installer touch that disk....
> 

Secondly, it's great that now I'll be able to re-install my programs fast, but since I DO have my other HDD set as "/home", is there something that will help me set that up to use as home again? Or should I just reinput the commands? (I would have to find them again) 
I can't recall if you can do this from the livecd installer or not. Pretty sure you can, but definitely possible from the alternative install disk, which is pretty much just the standard Debian installer.> 
Thanks!

EDIT: Handydan, I'm proud to say that I understand your sig! I knew the saying before the command obviously, but I remember what that command does. :) Very clever ;)

Thanks, but I stole it....from the Wikipedia section on chown, believe it or not. They just used it as an example, without explanation or comment...and I about busted a gut.

---

### Post by Joeb454 on 2008-03-14
Out of curiosity, what does it do?

---

### Post by Literati on 2008-03-14
> **Joeb454 said:**
> Out of curiosity, what does it do?

Don't quote me on this, but doesn't Chown allow you do allow another user to have rights to read/write to a hard disk? At least, that's how I remember using it (Remember, I've been on Linux for a total of 2 days, so seriously, don't quote me on that)

But it's funny, because the quote, if you don't know, is:

"All your base are belong to us."

So that command would give ownership rights of "base" to "us"

---

### Post by forrestcupp on 2008-03-14
There's really no reason to* not* upgrade instead of a clean install.  Many people upgrade without any issues, and you don't have to reinstall all of your apps.  Doing an upgrade will automatically bring all of your installed apps up to date.

The only real reason to do a clean install is if you want the experience of installing everything from scratch again.  When Hardy comes out, I will upgrade and not mess with a clean install.

---

### Post by Literati on 2008-03-14
> **forrestcupp said:**
> There's really no reason to* not* upgrade instead of a clean install.  Many people upgrade without any issues, and you don't have to reinstall all of your apps.  Doing an upgrade will automatically bring all of your installed apps up to date.

The only real reason to do a clean install is if you want the experience of installing everything from scratch again.  When Hardy comes out, I will upgrade and not mess with a clean install.

Really? Since I've been looking at Ubuntu, everyone always says you should clean install upgrades.

Hm, maybe I'll see when the time comes. :)

---

### Post by forrestcupp on 2008-03-14
> **Literati said:**
> Really? Since I've been looking at Ubuntu, everyone always says you should clean install upgrades.

Hm, maybe I'll see when the time comes. :)

Think of it this way.  If you upgrade and screw something up, you were just going to format it and do a clean install anyway.  So why not try it first?

---

### Post by Literati on 2008-03-14
> **forrestcupp said:**
> Think of it this way.  If you upgrade and screw something up, you were just going to format it and do a clean install anyway.  So why not try it first?

You make a very good point. 
But say, if I did screw something up in the upgrade, and it's porting my /home drive, could that no potentially mess up my /home drive?

---

