---
title: "ATI accelerated graphics driver problem"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by mikethepirate on 2007-12-07
Hey guys :)

Been using ubuntu for a day now and I'm loving it so far :)
I have run into a small problem though.  When I try to enable the ati accelerated graphics driver, I an error message that stats "Could not apply changes! Fix broken packages first."

I know it is most likely a little thing, but I have had no luck searching the forums.  Thank you all in advance

---

### Post by mikethepirate on 2007-12-07
Also, for some reason flash player won't install and audacity won't either because it conflicts with other programs.  Also, my sound has just went out lol.  I hope I'm not messing anything up

---

### Post by Daveth on 2007-12-07
think you need to mend the broken bits first! 

Go System, admin, synaptic,
add your password, and look at the bottom of the Synaptic page. There will be a list of the number of packages listed, the number broken etc. In Edit there is an option to fix broken packages. It should show what is broken. Have you been downloading programs from outside of Synaptic?

---

### Post by overdrank on 2007-12-07
> **mikethepirate said:**
> Hey guys :)

Been using ubuntu for a day now and I'm loving it so far :)
I have run into a small problem though.  When I try to enable the ati accelerated graphics driver, I an error message that stats "Could not apply changes! Fix broken packages first."

I know it is most likely a little thing, but I have had no luck searching the forums.  Thank you all in advance

Hi and welcome, You can fix broken packages in synaptic manager located under system, administration, synaptic. In synaptic manager then under edit is fix broken packages

---

### Post by mikethepirate on 2007-12-07
Hmm.  It says 0 broken packages but I fixed it anyway but it still gives me the same error.  I wonder if it would be best to just reinstall?  Also, how can I tell if something conflicts with another program.  Audacity is having this problem.  Thank you

---

### Post by Majorix on 2007-12-07
> **mikethepirate said:**
> Hmm.  It says 0 broken packages but I fixed it anyway but it still gives me the same error.  I wonder if it would be best to just reinstall?  Also, how can I tell if something conflicts with another program.  Audacity is having this problem.  Thank you

If you are a new user you shouldn't just give up and reinstall. That would be a big mistake, you have to try to fix your system and see what you can learn from your experiences.

I don't think you would need the ATI accelerated graphics drivers. The open source ones (radeon in my case) work juust fine.

Why doesn't flash player install?

What packages does audacity conflict with? I don't think you can have any packages that could conflict with it installed in the only 2 days you have been using Ubuntu.

About your sound problem, what do you have in your alsamixer? To reach it, click Apps in the top panel then Accessories and Terminal. There type in alsamixer and see if your speakers are muted.

---

### Post by mikethepirate on 2007-12-07
> **Majorix said:**
> If you are a new user you shouldn't just give up and reinstall. That would be a big mistake, you have to try to fix your system and see what you can learn from your experiences.

I don't think you would need the ATI accelerated graphics drivers. The open source ones (radeon in my case) work juust fine.

Why doesn't flash player install?

What packages does audacity conflict with? I don't think you can have any packages that could conflict with it installed in the only 2 days you have been using Ubuntu.

About your sound problem, what do you have in your alsamixer? To reach it, click Apps in the top panel then Accessories and Terminal. There type in alsamixer and see if your speakers are muted.

Well, I would be fine with the stock drivers but they won't go up to my monitors native resolution :(

Honestly, I don't know why it won't.  I got it to the point where it will show the loading screen on youtube but it just asks me to download a codec, which when I download it, it won't work.

It doesn't say what audacity conflicts with.  Is there a way to find out?  Thank you so very much.  The interface on ubuntu is so much nicer and I refuse to let my ignorance ruin it :)

---

### Post by mikethepirate on 2007-12-07
Guys, I think I'm going to reinstall.  On top of these problems, my system is locking up about every 30 minutes and only allowing my mouse to move.  When I was installing ubuntu  I did it from ubuntu off of the cd.  after it completed and asked my to restart, i tryed to remove the disc from the drive but it caused it to freeze.  Long story short, I think it's coming back to bite me lol :)

---

### Post by melojo on 2007-12-07
try this link to fix flashplayer it worked for me.
[http://ubuntuforums.org/showthread.php?t=632107](http://ubuntuforums.org/showthread.php?t=632107)

---

### Post by mikethepirate on 2007-12-07
Do you guys think I might have a bad cd? 
Honestly, even after a reinstall, the same stuff.

---

### Post by mikethepirate on 2007-12-09
OK guys, I've reinstalled twice, made my own iso cd and searched for more answers and still no luck. It still says I have broken packages when i try to install the ati accelerated graphics drive when the synaptic package manager says I have none. Flash is still acting up and Audacity stills says that it must have uninstallable packages (that I wish I could name but now my package manager won't even find it anymore),  I REALLY REALLY REALLY want to learn how do use this OS and I'm just so used being spoiled with tools that fix things for me in window's command prompt.  I know there is a way to fix it, I just need to know what commands will help me.  Thank you guys in advance :)

---

### Post by mikethepirate on 2007-12-10
I am desparate here.  Is there anything I can type into the terminal and paste here so you guys will know what I am dealing with?  This is leaving a sour taste in my mouth because I am looking foward to using this OS, and on day 3, I'm still lost and in the dark.  Please help me out if you can, your help will be greatly appreciated.  

FYI, the one of the uninstallable packages Audacity needs is libstdc++5.  Hiope it helps

---

### Post by Perfect Storm on 2007-12-10
First of all are you running 32-bit or 64-bit Ubuntu?

---

### Post by mikethepirate on 2007-12-10
I'm running the 32-bit version of 7.10.  My system specs are:

3 ghz P4 HT
1GB PC2-4200 RAM
80GB Hard Drive
and 256mb ATI Radeon x600.

---

### Post by Perfect Storm on 2007-12-10
Flash player: [http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb](http://launchpadlibrarian.net/10761023/flashplugin-nonfree_9.0.115.0ubuntu2_i386.deb)
Note if you have gnash install, uninstall gnash first.

The audacity stuff:
```
sudo apt-get update && sudo apt-get upgrade
sudo apt-get install libstdc++5
```

The ATI stuff I can't help you with as I'm a Nvidia user.

---

### Post by mikethepirate on 2007-12-10
Thank you, I will try that as soon as I get home :). I'm just worried that it might be more because the system hangs up every so often and the sound will shut itself off after running ubuntu for about an hour.  Also, when I tried to install something from the add/remove application, it would always bring up the reload thing every time I went to check the box next to the program.  This is all very confusing :(

If it helps any, I am running a dual boot system with an xp partition and the computer is a Dell Dimension E510.

---

### Post by Letori on 2007-12-12
I'm having exactly the same problem. Don't know what to do about it. Everything is the same including the error message, the fixing packages thing doing nothing. I'm working off a clean install of Gutsy so I doubt anything I could have installed would be the problem. A corrupt CD seems pretty unlikely as I burned it at 1x on a burner that has never given me a bad burn. Any assistance with this would be very appreciated.

1.8 ghz p4
40gb Seagate barracuda
1gb ram (hell if I know what kind)
ATI Radeon x700

and yes, 32-bit Ubuntu


Unlike my friend here, I'm running on an older, single processor system. Is a corrupt CD the only viable explanation? The other thing would be that unlike mike, I'm not experiencing any other adverse effects, Ubuntu is running like a bloody dream and has been since I installed it yesterday.

---

### Post by Letori on 2007-12-12
Hey mike, think I may have found something. It's not a pretty fix, but it does work - I just know very little as to why.

[http://cybernetnews.com/2007/10/20/install-and-enable-restricted-drivers-in-ubuntu/](http://cybernetnews.com/2007/10/20/install-and-enable-restricted-drivers-in-ubuntu/)

I started checking the boxes that this guy did. I actually checked everything EXCLUDING "source code" and "Canonical-supported Open Source software (main)" and it didn't work. Didn't work until the "Canonical" box was checked.

Which as far as I can tell means you might just need the top canonical box checked.
Anyways, hope this works for you too.

---

### Post by mikethepirate on 2007-12-13
Thank you Letori!  I did that a couple days ago and it fixed everything that was going wrong.  Sorry I didn't tell you guys sooner :(

I would like to give all of you who posted on this thread a huge thank you :)  It makes my day to see people that are so willing to help :)

Now it's time for me to get Counter-Strike source on ubuntu thus ridding my computer of windows :)  Wish me luck!

---

### Post by nmiilne on 2008-01-18
Thanks for that guys - been hitting my head over this problem the last few days, and the solution comes down to selecting an option that isn't obviously linked to the configuration that is trying to be applied.  Quite possibly a dependency behind the scenes somewhere.

This should really be up in a sticky/faq somewhere and hopefully reported as a bug...

---

