---
title: "Has anyone had a good experience upgrading?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by ageer1 on 2007-10-24
Hi all,

I've been lurking here for about 6 months since installing Feisty and have learned a lot about Ubuntu,  but still have an awful lot to learn. It's been such a good experience that I've recently deleted XP and am now Feisty only! (I would be a really happy camper if I could get my WinModem to work with Ubuntu so I could trash my old Fax Machine!)

I've been delaying upgrading to Gutsy while watching this forum for problems and am seeing an awful lot of them, to the point where I feel the need to ask if anyone has had an uneventful experience upgrading to Gusty?

I would rather not do a fresh install, if avoidable, because I would rather not reinstall all my applications. Hell, I'm not sure I even remember all that I have installed!

Joe

---

### Post by danm-koder on 2007-10-24
My upgrade was uneventful... well almost :P... the only issue I had was with the fglrx ATI driver I was using on Feisty, which was meant to work with Xorg 7.1, so I upgraded my driverto work with Xorg 7.2 and that was it... pretty much uneventful don't you think??

---

### Post by cybson on 2007-10-24
Mine was pretty much smooth, I just had some HAL-problem with removable devices.

Fixed that in a matter of minutes though, and now everything is working Okay with all my old settings and files/apps.

---

### Post by Anicka on 2007-10-24
Hi Joe!

I've upgraded on both my machines without any issues. A piece of advise could however to look in the forum and see if your hardware has caused any problems. Also I never update during the first couple of days. 1) the load on the servers is very high, so it takes long time and the likelihood of network problems crippling your install is overwhelming, 2) there are always things that can go wrong, but letting the most eager guys to have a weekend to find solutions for any problems they encounter, helps any non-expert.

P.S. Any automatix or other third party repos should be temporarily commented out of the source-list before upgrades.

---

### Post by Paqman on 2007-10-24
> **ageer1 said:**
> 
I would rather not do a fresh install, if avoidable, because I would rather not reinstall all my applications. Hell, I'm not sure I even remember all that I have installed!


That's easily fixed. Ubuntu can [generate a list of all installed packages and reinstall them automatically](http://ubuntuforums.org/showthread.php?t=261366). Of course, that will only work on packages you installed with Synaptic/apt-get.

As for upgrades, I installed Gutsy clean, but before that upgraded Dapper > Edgy > Feisty with absolutely no problems.

---

### Post by haggus on 2007-10-24
Well I tried the dist upgrade with the software updater and everything seemed to go well but it didn't finish now I can log in to a desktop with nothing but a desktop background no taskbar or anything so I'm seeing if the alternate install cd will finish the upgrade hopefully . I think unless you are pretty confident with linux and how to fix things I would backup everything important first before trying to upgrade I did the same with windows when I first learned how upgrade and install for me it's not so important that thing go right the first time although it would be nice but I like to learn and for me I learn the most by doing things first and fixing my mistakes later.

---

### Post by Flyingjester on 2007-10-24
I had a perfectly flawless upgrade.

---

### Post by drs305 on 2007-10-24
> **ageer1 said:**
> 
I would rather not do a fresh install, if avoidable, because I would rather not reinstall all my applications. Hell, I'm not sure I even remember all that I have installed!

Joe

Here is one method to get your installed packages. Run this to get a file named installed-packages on your desktop. It will contain a list of all your installed linux programs:
```
sudo dpkg --get-selections >~/Desktop/installed-pkgs.txt
```

Once you have run this, you can review it to see what programs you had on your machine. You can edit out ones you no longer want if you wish.

I use the following commands to install the same packages on my new computers. Since there are no version numbers listed in the file, I believe you could run the same commands following an upgrade to get the latest versions installed. It will NOT remove any packages already installed.

```

sudo dpkg --clear-selections
dpkg --set-selections <~/installed-pkgs.txt 
sudo apt-get dselect-upgrade 

```

And in answer to your original question, I had a couple of minor issues with an HP printer and networking but both were resolved. I am glad I upgraded.

---

### Post by wthanna on 2007-10-24
My upgrade also went flawlessly on several machines including laptops, servers and desktops.  Remember this is primarily a support forum manned completely by users that volunteer to help.  You are going to hear alot more about the ones that had problems than the ones that didn't.  I read somewhere recently (will try to find the source and post here), that Ubuntu is estimated to have as many as 6 million installs out there. If this is anywhere close to a true number.. and say only 10% have upgraded to Gutsy, then there are a whole lot of people like myself who have had a great experience. Just something to think about! Due to the free availability of Ubuntu we may never know what the true number of installs is.

---

### Post by ageer1 on 2007-10-24
Thanks for the feedback Folks, I appreciate it.

Joe

---

### Post by rafkin on 2007-10-24
If I could make one suggestion, I disabled all third party software, universe and multi-universe before the upgrade. After the install I went back in and check marked all my third party and universes and let them update as needed. Rebooted and everything worked flawlessy. In my small opinion (forwhat it is worth) would rather upgrade than clean install. If I wanted to reinstall every 6 months I would have stuck with windows. This is my first upgrade and I had no problems, I will definetly do it again in another 6 months.

---

### Post by Seamyst on 2007-10-25
I just upgraded overnight (because of slow server downloads).  The only problem I had was the upgrader refused to fetch certain 3rd-party files, so I disabled those and it went smoothly.  Everything so far seems to be working just fine, and all my settings (for disabling the MacBook touchpad, etc) have carried over.

---

### Post by marco123 on 2007-10-25
The general rule of thumb is if you use third party software you must disable it before you upgrade.  If you don't use any chances are it will go smoothly.

---

### Post by techpr on 2007-10-25
October 20 was my upgrade, and it was flawless.

---

### Post by Steve1961 on 2007-10-25
Two successful upgrades here as well.  Both machines have been dist-upgraded on each release since dapper.  The Dapper to Edgy upgrade was tricky but all the others have been plain sailing.

---

### Post by tech9 on 2007-10-25
> **ageer1 said:**
> Hi all,

I've been lurking here for about 6 months since installing Feisty and have learned a lot about Ubuntu,  but still have an awful lot to learn. It's been such a good experience that I've recently deleted XP and am now Feisty only! (I would be a really happy camper if I could get my WinModem to work with Ubuntu so I could trash my old Fax Machine!)

I've been delaying upgrading to Gutsy while watching this forum for problems and am seeing an awful lot of them, to the point where I feel the need to ask if anyone has had an uneventful experience upgrading to Gusty?

I would rather not do a fresh install, if avoidable, because I would rather not reinstall all my applications. Hell, I'm not sure I even remember all that I have installed!

Joe

Upgrade was perfect for me

---

### Post by Vaidya on 2007-11-07
Hi,

Thought should also pitch in here and say that this is my second upgrade (I was a noob when I went into etchy, upgraded nonetheless into feisty - no problems- sweated my way into getting things working including Tovid and all dependencies) and this upgrade also went fine!!

Now, I am looking for getting rid of my internet not getting up automatically at boot prob ... i use a ADSL router and I have by now developed a mind block on learning more about it to make it work... so every time I click network manager=>manual connection=>choose location=> desktop=>OK

That is the only grumble I have left at the moment, I am sure more will surface, but very happy with having XP -that is when I need it -  working UNDER me since I use that EXCELLENT virtual machine program called VirtualBox... it make windows play by MY rules :)

Muahhhaah!! (sorry, could not resist!)

---

### Post by DarinB on 2008-03-12
how do you turn off third party upgrades???
universe multiverse packages????

---

### Post by handy on 2008-03-12
I have held the philosophy for years (of Windows use) never upgrade, always do a clean install.  

Anyway, I have done a couple of upgrades with Ubuntu & one with Sabayon, & they worked flawlessly.

I would still recommend to anyone that does go the upgrade path to be sure to have anything that you can't afford to loose backed up, common sense really.

---

### Post by DarinB on 2008-03-12
> Here is one method to get your installed packages. Run this to get a file named installed-packages on your desktop. It will contain a list of all your installed linux programs:
Code:

sudo dpkg --get-selections >~/Desktop/installed-pkgs.txt

Once you have run this, you can review it to see what programs you had on your machine. You can edit out ones you no longer want if you wish.

I use the following commands to install the same packages on my new computers. Since there are no version numbers listed in the file, I believe you could run the same commands following an upgrade to get the latest versions installed. It will NOT remove any packages already installed.

Code:

sudo dpkg --clear-selections
dpkg --set-selections <~/installed-pkgs.txt 
sudo aptitude install dselect-upgrade


Feisty to Gutsy
regarding above what about all the stuff that automatically comes installed in the next version
i.e. cups, compiz etc.???????????????

---

