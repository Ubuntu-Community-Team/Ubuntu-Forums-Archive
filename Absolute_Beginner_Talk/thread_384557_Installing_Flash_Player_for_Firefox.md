---
title: "Installing Flash Player for Firefox"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by toecutter on 2007-03-14
Just installed Ubuntu 6.10 last night and all seems to be going well. I'm taking care of little issues as they come along and the list is getting shorter surprisingly quickly. :)

Right now, the main issue I have is that Flash doesn't seem to want to install on Firefox. I'm running NoScript but when I go to a site like YouTube and disable NoScript for that (or any site), I get the 'click here to install plugins' placeholder image. When I click on the image I get **'No Suitable Plugins Available: unknown application(x-shockwave-flash)'**

I've gone to the Adobe site to download the tar.gz file but when I try to run them in Terminal I get **'Your architecture, \'x86_64\', is not supported by the Adobe Flash Player Installer'**

Any clues as to what I can do? Any help would be hugely appreciated :)

---

### Post by aysiu on 2007-03-14
That message is correct.

Flash is not supported by the 64-bit architecture. 

There are workarounds, but they're messy. Here's one, for example:
[Howto : Installing Flash on Ubuntu Dapper or Edgy for x86_64](http://ubuntuforums.org/showthread.php?t=290785)

---

### Post by deathbyswiftwind on 2007-03-14
Use synaptic and search for flashplayer or flash plugin. Its in there so is java. Install them and your good to go

---

### Post by aysiu on 2007-03-14
> **deathbyswiftwind said:**
> Use synaptic and search for flashplayer or flash plugin. Its in there so is java. Install them and your good to go
That usually works, but...

1. We don't know if toecutter has [enabled extra repositories](http://www.psychocats.net/ubuntu/sources)

2. toecutter is using the 64-bit Ubuntu, for which Flash is not available.

---

### Post by deathbyswiftwind on 2007-03-14
Og geez sorry I didnt even see he was running 64bit! Sorry that wouldnt work for you. In order to get flash player working youll have to install the 32bit veion of firefox in chroot and install your plugins from there. Sorry about the confusion!

---

### Post by toecutter on 2007-03-14
> **deathbyswiftwind said:**
> Og geez sorry I didnt even see he was running 64bit! Sorry that wouldnt work for you. In order to get flash player working youll have to install the 32bit veion of firefox in chroot and install your plugins from there. Sorry about the confusion!

Whew...okay...chroot...right :) I'll have a look for that! (might have to bust out that Ubuntu Bible)

OK I went into terminal to enable repositories (thanks for that) and tried typing in the commands but it won't take my password for some reason! I'm trying to type in the same password I use to login - am I missing something? 

Thanks very much for the help so far!

next questions are:
1) where can I d/l Firefox 32-bit? Mozilla.com doesn't seem to have it, and add/remove programs doesn't find it
2) ...how do I install it into chroot?

---

### Post by deathbyswiftwind on 2007-03-14
[http://www.mozilla.com/en-US/]("http://www.mozilla.com/en-US/") Heres the link for firefox.

[http://www.ubuntuforums.org/showthread.php?t=202537]("http://www.ubuntuforums.org/showthread.php?t=202537") And here is a link with a howto for flash and java

---

### Post by aysiu on 2007-03-14
Check out [the link I posted earlier](http://ubuntuforums.org/showthread.php?t=290785).

By the way, the terminal won't give you any visual feedback when you're entering your password. It is still accepting your password--you're just not seeing any confirmation it's being accepted.

---

### Post by toecutter on 2007-03-14
Duh :) I was looking for something saying '32-bit Firefox' and didn't realize ALL the links are for 32-bit Firefox :P

Thanks for that.

Anyway, about the password for enabling repositories, when typing in my login password I get a polite 'Sorry, try again' - it gave me 3 tries then stopped the attempt. *no idea*

---

### Post by aysiu on 2007-03-14
That's weird.

In the default Ubuntu installation, there's one user with one password. That password should also work for administrative tasks.

Any chance you have caps lock on or might have mistyped?

I'm trying to think what else might be the problem...

---

### Post by toecutter on 2007-03-14
RE: the password, I hit 'home' on the keyboard to enter some of the characters of my password, I guess terminal doesn't like that, so I had to write out the password and type it in 'manually' :) so that got sorted. 

I tried a variety of different methods (from both sets of links provided) to get it to work, thanks for the help, it's working (a bit clunky, but it's working!) Hopefully future releases will fix this thing. I'll post further in the 64-bit section :)

Cheers!

---

