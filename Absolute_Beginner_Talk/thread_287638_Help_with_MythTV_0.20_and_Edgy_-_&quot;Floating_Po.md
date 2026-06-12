---
title: "Help with MythTV 0.20 and Edgy - &quot;Floating Point Exception&quot;"
date: 2006-10-29
forum: Absolute Beginner Talk
---

### Post by NormInNorman on 2006-10-29
I had heard that setting up MythTV in Edgy was a breeze, so I decided to give it a shot.  Yesterday I set up Ubuntu Edgy for the first time and today I tried to set up MythTV using [a howto I found on ubuntu's help site]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop").  When I get to part that says "sudo mythtv-setup" I always get "Floating point exception (core dumped)".  I swear followed the directions precisely.  Could this be some sort of hardware problem?

Here is what I did: After my initial install of Ubuntu, [I set up the fglrx driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-c966b2cb7c82944d6883f27a2896725db3b90a3a") for my Radeon 9600 (with a little help from [this thread]("http://ubuntuforums.org/showthread.php?t=273934")).  Then I looked around the web and figured out how to enable my TV output, my plan being to run MythTV Frontend on the TV and still use my monitor for the desktop.  Then I installed the drivers for my integrated sound ([nforce soundstorm]("http://ubuntuforums.org/showthread.php?t=253725")).  Finally I installed the [ivtv drivers]("https://wiki.ubuntu.com/Install_IVTV_Edgy").  Then I [followed the directions on on installing MythTV]("https://help.ubuntu.com/community/MythTV_Edgy_Backend_Frontend_Desktop").  And then I get the floating point error.

Any suggestions before I reformat, reinstall Edgy, and try again?  I can't seem to find a solution.

---

### Post by NormInNorman on 2006-10-29
Bump?

---

### Post by lime4x4 on 2006-10-29
can u tell me how u got your tv out to work? I'm currently in the process of installing mythtv myself.

---

### Post by lime4x4 on 2006-10-29
well i followed that guide as well i get a different error

john@john-edgy:~$ sudo /etc/cron.daily/mythtv-backend 
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
john@john-edgy:~$ #
john@john-edgy:~$ 
john@john-edgy:~$     *
john@john-edgy:~$ 
john@john-edgy:~$       sudo /etc/init.d/mythtv-backend start
mythbackend already running, use restart instead.
john@john-edgy:~$ 
john@john-edgy:~$ #
john@john-edgy:~$ 
john@john-edgy:~$ mythfrontend
bash: mythfrontend: command not found

---

### Post by NormInNorman on 2006-10-29
> **lime4x4 said:**
> can u tell me how u got your tv out to work? I'm currently in the process of installing mythtv myself.
I kinda followed this guide:

[http://gentoo-wiki.com/HOWTO_TV-Out#ATI-proprietary-drivers](http://gentoo-wiki.com/HOWTO_TV-Out#ATI-proprietary-drivers)

except when I got to this part:

```
/opt/ati/bin/aticonfig --initial=dual-head --tvf=<TV standard> --tvs=VIDEO --hsync2=<TV hsync> --vrefresh2=<TV vrefresh> --iagp=off --agpl=off --ovon=1 -v
```

It didn't work right, so I did something more like:

```
sudo aticonfig --initial=dual-head --tvf=NTSC-M --tvs=VIDEO --ovon=1 -v
```

And then I skipped the rest, because I couldn't get it to work anyway. The aticonfig command seemed to keep my previous monitor settings, so maybe the cat command wasn't important anyway.  When I restarted it all seemed to work.  I don't know if it matters, but I'm using the composite adapter since my TV doesn't have S-Video.

---

### Post by NormInNorman on 2006-10-29
Oh, and you guys are going to make me re-install, aren't you?

---

### Post by superm1 on 2006-10-30
Norm,

I am the author of those howto pages.  I also have a box with an fglrx based card that sometimes does this when launching myth.  I haven't exactly identified what causes it, but it seems to only happen after the box has been running for some time.  If you come off of a fresh boot, there are no troubles.

You might want to try using the open source driver to at least get myth initially setup, and running for a little bit.  Once you prove that everything else is working, switch to the binary and hopefully this problem will be nailed by then.

---

### Post by NormInNorman on 2006-10-30
> **superm1 said:**
> Norm,

I am the author of those howto pages.  I also have a box with an fglrx based card that sometimes does this when launching myth.  I haven't exactly identified what causes it, but it seems to only happen after the box has been running for some time.  If you come off of a fresh boot, there are no troubles.

You might want to try using the open source driver to at least get myth initially setup, and running for a little bit.  Once you prove that everything else is working, switch to the binary and hopefully this problem will be nailed by then.
Ah, thanks for catching me before I reinstalled.  I had just assumed I did something wrong somewhere.  It seems like my box does this every time whether it's a fresh reboot or not.  I will go back to the open source driver and see how that works.

Question: does the open source driver support the TV out?  Really, right now as long as I can get mythtv going and be able to watch videos I'd be happy.  It's not like I'm going to play 3d games on my machine or anything.  I'd still like to have myth's front end running on my TV and my desktop running on my monitor though.

Thanks again for your response.

---

### Post by superm1 on 2006-10-30
> **NormInNorman said:**
> Ah, thanks for catching me before I reinstalled.  I had just assumed I did something wrong somewhere.  It seems like my box does this every time whether it's a fresh reboot or not.  I will go back to the open source driver and see how that works.

Question: does the open source driver support the TV out?  Really, right now as long as I can get mythtv going and be able to watch videos I'd be happy.  It's not like I'm going to play 3d games on my machine or anything.  I'd still like to have myth's front end running on my TV and my desktop running on my monitor though.

Thanks again for your response.

I'm not sure about the open source ordinary driver supporting TV out.  I know that there are patches to make it do so at [http://gatos.sf.net](http://gatos.sf.net), but I'm not sure if they actually are already included in the latest xorg checkout in edgy.

At this point,  I say make sure that it works using the open source driver (but not necessarily tv out).  As long as it does, then either grab the xorg driver source and apply these patches (I can help you here if you need), or try an older fglrx release.

---

### Post by NormInNorman on 2006-10-31
Well, I think I have it working now.  On a whim I installed the latest ATI driver (8.29.6) using [this guide]("http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide").  After I got it working, I tried the the mythtv-setup command again and it seems to be working.  Time for bed now, but tomorrow night I'm going to work on getting MythTV set up all the way.

As a side note, I did an "sudo ati-config --force --initial", so my TV out is no longer working correctly.  I haven't ruled out the possibility that the TV out was the problem all along OR that I just had some sort of error in my xorg.conf file.  I think I'll go ahead and get MythTV setup first before changing anything.  If I get the TV Out working again and it screws up MythTV, I'll post my results.

Thanks for the help, superm1.

---

### Post by superm1 on 2006-10-31
Norm,

I'd say its probably not the tv-out to blame.  This fglrx problem happens to me on a laptop LCD.

---

### Post by lonce on 2006-10-31
[http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

Follow that website step for step.  Works every time.  If you have any questions hit my support site and ask in our forums.  They are mythtv/ubuntu forums.

---

### Post by superm1 on 2006-10-31
> **lonce said:**
> [http://www.parker1.co.uk/mythtv_ubuntu.php](http://www.parker1.co.uk/mythtv_ubuntu.php)

Follow that website step for step.  Works every time.  If you have any questions hit my support site and ask in our forums.  They are mythtv/ubuntu forums.


This website does not address *anything* related to the fglrx bug.

---

### Post by NormInNorman on 2006-11-01
Well, I got MythTV mostly set up last night.  It appears to be working fine right now.  I ran setup and started the backend and frontend a few times and never got any errors.  Then I tested some recording and playback and it seems to work.  If I get some time tonight I'm going to try my best to break it (try the TVOut, install LIRC).  Otherwise I'm going to assume that the newer drivers fixed whatever the problem happened to be.

---

### Post by NormInNorman on 2006-11-01
> **superm1 said:**
> Norm,

I'd say its probably not the tv-out to blame.  This fglrx problem happens to me on a laptop LCD.
Well, tonight I went back and enabled my TV-out with that command I listed earlier, restarted, and mythfrontend got the floating point error.  I went back to my previous configuration file, restarted, and mythfrontend started working again.

I guess my next thing will be to install the open source driver, get it working with MythTV, then try to get it to work with the second TV like I want it.

I really wish I had bought an nvidia card.

---

### Post by superm1 on 2006-11-02
> **NormInNorman said:**
> Well, tonight I went back and enabled my TV-out with that command I listed earlier, restarted, and mythfrontend got the floating point error.  I went back to my previous configuration file, restarted, and mythfrontend started working again.

I guess my next thing will be to install the open source driver, get it working with MythTV, then try to get it to work with the second TV like I want it.

I really wish I had bought an nvidia card.

I know how you feel with the ATI card.  I'm really not sure how to blame this, or what specifically is causing it/fixing it.

I'm glad I've got a few nvidia cards for my other frontends :)

---

