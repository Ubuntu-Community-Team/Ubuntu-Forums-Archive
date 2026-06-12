---
title: "Will Firefox 2.0 eventually be in the Dapper repos? (Solved)"
date: 2006-11-06
forum: Absolute Beginner Talk
---

### Post by MakLeod on 2006-11-06
Will it ever be in the 6.06 repos?  If yes, then how long do you think until it appears?

---

### Post by aysiu on 2006-11-06
> **MakLeod said:**
> Will it ever be in the 6.06 repos?  If yes, then how long do you think until it appears?
No, they won't be.

If you want 2.0, upgrade to Edgy or use this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by MakLeod on 2006-11-06
You Sir, aysiu, are a GOD for making that script.  Was so easy to upgrade.  Thank you!!

---

### Post by MakLeod on 2006-11-06
Sorry one more question though.  I noticed that my "check for updates" section is still greyed out.  I noticed the script did something with my sources.list.  Will I now be eligible for updates through the update manager?

---

### Post by aysiu on 2006-11-06
> **MakLeod said:**
> You Sir, aysiu, are a GOD for making that script.  Was so easy to upgrade.  Thank you!!
In all fairness, another forum member named *nanotube* made the script--all I did was test it out and supply a few ideas for it.

Glad it all worked out for you, though.

---

### Post by teasum on 2006-11-06
Aysiu, this is official news, that Firefox 2.0 will not be backported to Dapper?  Please tell me that's not the case... how can Dapper be truly "LTS" if it doesn't support FF 2.0?  This is not a random piece of bleeding-edge software; it's the main open source browser on the market.  

Just curious.  If I have to use the script, I will.  I just prefer, if possible, to wait for a backport.  

Thanks!

---

### Post by nanotube on 2006-11-06
> **MakLeod said:**
> Sorry one more question though.  I noticed that my "check for updates" section is still greyed out.  I noticed the script did something with my sources.list.  Will I now be eligible for updates through the update manager?

hi
i'm the nanotube referred to earlier :)
yes, check for updates is greyed out, because you need to be root to update firefox. 

to see detailed instructions for using the native firefox updater, see the first link in my sig, and go to the "update official mozilla build of firefox" section. 

the script does not change your sources.list, so you can get updates and everything else through apt-get as usual.

---

### Post by shimrah on 2006-11-06
I concur. I'm surprised that this isn't an automatic update. Any plans to make it so?

Other than that -- I'm loving Ubuntu (new Linux user here). Kudos to everyone involved!

Shim


> **teasum said:**
> Aysiu, this is official news, that Firefox 2.0 will not be backported to Dapper?  Please tell me that's not the case... how can Dapper be truly "LTS" if it doesn't support FF 2.0?  This is not a random piece of bleeding-edge software; it's the main open source browser on the market.  

Just curious.  If I have to use the script, I will.  I just prefer, if possible, to wait for a backport.  

Thanks!

---

### Post by Frak on 2006-11-06
I will say aysiu you are too smart for your own good.  You take the credit and merit from the underachievers.

---

### Post by teasum on 2006-11-06
Here's some more information regarding the process of backporting FF 2.0:

[https://launchpad.net/products/dapper-backports/+bug/68158](https://launchpad.net/products/dapper-backports/+bug/68158)

It seems that since so many elements depend on Firefox, backporting is very complex and dangerous for FF 2.0.  Still, it would be nice if there was some way for FF updates to be included or integrated in the Dapper installation.  

Normally, I wouldn't mind staying with an older version of a program (heck, I'm sticking with Dapper over Edgy, for example).  In the case of Firefox, however, there are a bunch of extensions and themes I want to use that ONLY work with 2.0.  

In any case, I'll try out the script.  Perhaps FF upgrades could make it into Automatix or Easy Ubuntu, so as to make it easier for users afraid of the command line?  Just a thought.

Thanks.

EDIT: The script worked, of course!  Thanks again.

---

### Post by jis on 2006-11-07
> **aysiu said:**
> No, they won't be.

If you want 2.0, upgrade to Edgy or use this script:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

AFAIK, this doesn't upgrade FF 1.5 to FF 2.0, but installs FF 2.0 to a system that has an older version and does not remove the old version. This is also stated in a ubuntu documentation [page]("https://help.ubuntu.com/community/FirefoxNewVersion"), which also includes link to the psychocats.net page. If you have followed the instructions, 
1) how do you launch FF 2.0,
2) how do you launch FF 1.5?
(I would like to use the older one to test my html pages.)

Have you tried installing Swiftfox 2.0? There are scripts for installing and uninstalling [here]("http://getswiftfox.com/installer.htm"). I think that installer does not offer localizations, but are there other differences to mention, when compared to the scripts given at the psychocats.net page? Which one would you recommend and why?

I don't see why ubuntu people couldn't make another repository, from which FF 2.0 could be installed next to another instance of FF. I think using the synaptic or equivalent would be the most elegant way to install the FF 2.0 in Dapper.

---

### Post by aysiu on 2006-11-07
> **jis said:**
> AFAIK, this doesn't upgrade FF 1.5 to FF 2.0, but installs FF 2.0 to a system that has an older version and does not remove the old version. This is also stated in a ubuntu documentation [page]("https://help.ubuntu.com/community/FirefoxNewVersion"), which also includes link to the psychocats.net page. If you have followed the instructions, 
1) how do you launch FF 2.0,
2) how do you launch FF 1.5?
(I would like to use the older one to test my html pages.) Yes, this script does, in fact, install the Mozilla build of Firefox next to the Ubuntu build of Firefox.

The script install Firefox 2.0 to the /opt directory and symlinks it so that the command *firefox* launches Firefox 2.0 (Mozilla build) and the command *firefox.ubuntu* launches Firefox 1.5 (Ubuntu build).

It's not really an upgrade of the Ubuntu build, but for all intents and purposes, it is an upgrade to the end-user, who just knows when she clicks the Firefox icon that 2.0 launches.

---

### Post by JayTee on 2006-11-07
aysiu's website has by far some of the best How-to's and tutorials for Ubuntu and Linux in general that I've found yet. There are so many incredibly smart people staffing this forum and he stands out as one of the best. If you haven't been to his site yet check it out at:
[http://www.psychocats.net](http://www.psychocats.net). You'll be glad you did.

---

### Post by geodude on 2006-11-08
Maybe the Ubuntu folks could ask the Slackware guys how to do it. Slackware had an upgrade package our quite quickly.

---

### Post by jis on 2006-11-08
> **aysiu said:**
> 
The script install Firefox 2.0 to the /opt directory and symlinks it so that the command *firefox* launches Firefox 2.0 (Mozilla build) and the command *firefox.ubuntu* launches Firefox 1.5 (Ubuntu build).


Thanks. I wonder if Swiftfox installation enables similar commands?

BTW there are also .deb files in 
[http://getswiftfox.com/ubuntu.htm](http://getswiftfox.com/ubuntu.htm). I don't guarantee that they are good! How can you build an optimized package yourself?

The previously mentioned installation [methods]("https://help.ubuntu.com/ubuntu/desktopguide/C/install-file.html") have the disadvantage that they don't allow automatic update notifications. I think in that aspect a separate repository would be better. I wonder, if it would be too much work to create such a repository and would it be possible to install new Firefox next to the old one by it?

---

### Post by taelatus on 2006-11-08
I just tried using the installnewfirefox script.  This is what I get as output:

```
Enter your choice of localization: 11
You have chosen localization "en-US". Is that correct [y/n]? y

Updating repositories list

Password:
Reading package lists... Done
Building dependency tree... Done
Initializing package states... Done
Building tag database... Done
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
Previous command did not complete successfully. Exiting.
chris@cminetti:~/Desktop$
```

adding a sudo before the command does not fix the "are you root?"

---

### Post by aysiu on 2006-11-08
It looks as if you have Synaptic, Adept, or some other package manager open while you're trying to run the script.

---

