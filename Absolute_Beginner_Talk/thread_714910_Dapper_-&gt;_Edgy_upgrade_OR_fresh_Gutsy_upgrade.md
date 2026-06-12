---
title: "Dapper -&gt; Edgy upgrade OR fresh Gutsy upgrade?"
date: 2008-03-04
forum: Absolute Beginner Talk
---

### Post by der_moth on 2008-03-04
Hello there - first post here, and I'm more or less a total noob. Apologies in advance if I mess up, and also for my general lack of understanding of what I'm doing.

SO. I recently resurrected my Kubuntu box, which had been lying dormant for about a year or so. It still works fine, but I'm keen to upgrade it to the latest stable release, and my attempts at getting Update Manager to move me from my current build (6.06 LTS) to Edgy are failing miserably.

If I take the advice of the Ubuntu upgrade notes and run gksu "update-manager -c", it runs the upgrade check and returns no available upgrades. Following some googling, I have seen advice suggesting that gksu "update-manager -c -d" may work, but sadly it works too well; it only offers me the option to upgrade to a Hardy alpha, which I'm not keen to do. I'm keen to upgrade through an upgrade manager if possible, so if anyone has any suggestions, I'm all ears. 

Failing that, it seems like my only other available options are to either manually upgrade the thing (desperately keen to avoid this), or do a fresh install of the latest release. This is a problem because of my noobishness; it's been a good 18 months since I first installed Kubuntu, and I've forgotten the process... do I just download and burn the Kubuntu 7.10 package from [here]("http://www.kubuntu.org/download.php#latest") and take it from there? I am fully backed up... is this the best way to go? 

Apologies once again for my general cluelessness, and thanks in advance!

---

### Post by Exonimus on 2008-03-04
Hello and welcome to the forums!

I'd say fresh install. I'm no expert in any way, but I reckon going from edgy through feisty to gutsy is going to take longer and might give trouble, not saying it would/should, but a fresh install is always easier. Installing kubuntu should be the same as ubuntu, just downloading the thing from the website, putting it on a cd(or ordering a new cd, if you want to) putting in it your cd drive, let it boot the live cd, press install, and the rest is should be a breeze.

If anyone know another command to upgrade the distro, feel free to post. I'm still more or less a newbie myself =)

good luck, and if you have any questions, please feel free to post :)

also, if I understand correctly, just running the update manager doesn't show the message 'a new distribution release is available'  somewhere in the top of the screen?

---

### Post by Tatty on 2008-03-04
Yes its probably best to start with a clean install.  

Its generally best to start clean for each new version anyway really, and since you are so many versions behind (you would have to go Dapper-Edgy-Feisty-Gutsy) it would make sense to just start fresh.

---

### Post by dca on 2008-03-04
I always perform clean upgrades.  I wipe the old partition and install new.  Mileage may vary on if an upgrade will go well w/o a hitch.  
 
D/L the install CD from the website and burn as ISO image to CD.  Then reboot w/ CD in drive.  Make sure you've backed up the contents of your '/home' directory because that's where your personal info (data, music, etc) is stored.
 
What you will have to reconfig or fix after your Ubuntu install is totally dependent upon the hardware in your machine.

---

### Post by philinux on 2008-03-04
I agree fresh install is the way to go. I've just done one last night. I've got home on its own partition so its a doddle. I did go into my home folder from the live cd and deleted all the config files except FF and TB.

---

### Post by maestrobwh1 on 2008-03-20
There is a way to kind of sort of "clone" your current install.  I forget the command, and will look it up and post back, but you can export a package list from your current install to a file, then import it after your fresh install.  You then do an apt-get update/upgrade and it will install the package names from the new distro (there will be a few issues, as some packages won't exist so you'll need to edit the list a few times and re run apt).   I found it in "Ubuntu Hacks" but am at work.  If you want me to look it up and post it here, just let me know by posting the request here.  I'll check back.  

If you don't have a huge list of optional packages, it might be easier to just write them down from your menu and search in synaptic.  I needed to tweak a lot with installing codecs and such, so it might be more useful for people who really have done this.  

Also, before upgrading, or reinstalling, just copy your /etc/X11/xorg.cong to an external drive.  I have found that if I am ever going to have an issue with a clean install, it will be with xorg.  If you get to a point where you can't get into X, you can just mount the media and sudo cp (external drive path) /etc/X11/

I have been meaning to move my /home to a new partition but have been lazy.  That way a clean install won't wipe out my home directory.  There are lots of posts here and there for that.

---

### Post by hyper_ch on 2008-03-20
the devs will provide a dapper --> hardy upgrade... if you want to upgrade...

I however do a clean install on every release... it's always good to "throw" stuff away that I don't need anylonger on the system.

---

### Post by notwen on 2008-03-20
I would also recommend a fresh install over upgrading.  I've had mixed results when upgrading via Update Manager.  I've gotten to the point where I always backup /home, format and run a clean install.  Helps me remember the steps I take to setting up my desktop to my liking.  I've even ran into a couple of instances where Ubuntu had fixed and/or made one of my customizations for me.  You may wish to read up a small bit on Compiz-Fusion, since it comes by default now.  On my work/server boxes I tend to remove it completely, while I like some of it's features on my daily usage laptop.  Best of luck.  =]

---

### Post by maestrobwh1 on 2008-03-20
> **hyper_ch said:**
> the devs will provide a dapper --> hardy upgrade... if you want to upgrade...

I however do a clean install on every release... it's always good to "throw" stuff away that I don't need anylonger on the system.

I am kind of slow on picking up on "the devs"  I think that means one thing.  Developers?

At any rate, I can't seem to get update-manager -c to recognize a new release anyway.  Really old machine and I have decided to just go with a fresh install to get it back in better working order.

---

### Post by stchman on 2008-03-20
I recommend a fresh install.  It is actually quicker than the upgrade route.

---

### Post by maestrobwh1 on 2008-03-20
Seriously, my install is faster than a regular update/upgrade of packages (within the same distro).  It is almost 70% done and my last post was  an hour ago.  Not fast, but it is an old fujitsu PII 200MHz Laptop, its such a tank though.  Sturdiest little thing and it always works.  

I opted to put xubuntu dapper rather than hardy on it for now.  I had issues where and update did something to my install such that the buttons and scroll bars would go white unless you moused over them, and the display looked very funky (washed out) and it drove me nuts.  It wasn't that I had an issue with Dapper per se.  I tried to resolve it but could not seem to get it back to the way it was.  DamnSmallLinux looks fine on it so I assume it is not the hardware.

I'll just install ICEwm and use that as my default window manager.  Light and fast.

---

