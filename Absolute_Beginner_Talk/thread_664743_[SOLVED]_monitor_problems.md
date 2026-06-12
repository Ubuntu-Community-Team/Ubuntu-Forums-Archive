---
title: "[SOLVED] monitor problems"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by bighomer on 2008-01-11
Wasn't quite sure where to post this...so I figured this was the best place. 
I'm new to Ubuntu, and have only have a small bit of experience with Fedora Core. The install process went well (aside from countless frustrations I've faced as a result of bad media CDs...), but after the install, I noticed the monitor didn't look right. It wasn't showing the whole screen, just most of it.

_____________________________________________
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|***********************************                  |
|                                                                                        |
|                                                                                        |
|____________________________________________|

The *asterisks indicate the visible part of the screen. I know, I know...I suck at ascii art (not even sure that's what it's called). Anyway, my monitor's resolution is set to 1600x something or 1200x1600 I can't remember which. Whenever I set it to 1024x768 the screen goes black and stays that way. I force the computer to shut down by holding the power button down, it's all I can do at this point. 

Well, I go back into ubuntu and start tinkering with the monitor settings. I set it to Compaq Presario something or other (it doesn't have 1525 listed as an option) and it says all users must log off before changes will take effect. So I go a step further. I restart the computer. Ubuntu loading screen visible just fine, but I never see the login screen. Instead I see solid black, nothing else. 

Long story short, I'm using an old Compaq monitor on my laptop because its original monitor died on me (yes, I took my laptop apart and completely removed the monitor from the computer) This setup has worked fine for a while now, on windows and Fedora Core 3. On a side note, after being on a while, the monitor stops showing green. 

I have:
Dell Inspiron 5100 (minus the monitor)
ATI Mobility M7 Graphics Card
Compaq Presario 1525
Ubuntu 7.10 i386

Looking forward to rejoining the Linux world (you know how long it takes to download a linux distro over dialup? ; )
Thanks in advance for any assistance you can give.


Edit: Okay the ascii didn't post right. It deleted all the spaces. But I guess you can see what I mean.

---

### Post by nikoPSK on 2008-01-11
well, you could always goto System->Preferences->Screen Resolution. Was it fine before? If so do this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by eapache on 2008-01-11
It looks like you hosed your screen config by choosing the wrong monitor type (if it doesn't have the exact model, choosing the right brand won't help at all).

After you boot and the splash disappears, press ctrl-alt-F1 which should give you a terminal. Log in, then run the command in nikoPSK's post. Then try rebooting.

---

### Post by nikoPSK on 2008-01-11
> **eapache said:**
> It looks like you hosed your screen config by choosing the wrong monitor type (if it doesn't have the exact model, choosing the right brand won't help at all).

After you boot and the splash disappears, press ctrl-alt-F1 which should give you a terminal. Log in, then run the command in nikoPSK's post. Then try rebooting.

well, now I know how to get into terminal at boot :lolflag:

(I am still a n00b at ubuntu, not linux though)

---

### Post by bighomer on 2008-01-11
OK, tried
sudo dpkg-reconfigure -phigh xserver-xorg

I assume this would have reset my monitor back to 1200x1600 (sorry for not posting earlier, but I went ahead and reinstalled).
What gets me is that it displays some of the screen in this mode but when I switch to any other resolution (leaving the monitor on its default, generic monitor), the screen goes black and stays that way. I'm lost. 
Maybe I need a driver for my specific monitor?

---

### Post by nikoPSK on 2008-01-11
> **bighomer said:**
> OK, tried
sudo dpkg-reconfigure -phigh xserver-xorg

I assume this would have reset my monitor back to 1200x1600 (sorry for not posting earlier, but I went ahead and reinstalled).
What gets me is that it displays some of the screen in this mode but when I switch to any other resolution (leaving the monitor on its default, generic monitor), the screen goes black and stays that way. I'm lost. 
Maybe I need a driver for my specific monitor?

well, so you can't change resolution? is the one you have fine with you?

---

### Post by bighomer on 2008-01-11
No, that's the thing. What part of the screen I can see is okay but the bottom and right sides are cut off. My first assumption was that changing the resolution to 1024x768 would fix this problem, but if I change it, I get nothing but a black screen. 
Honestly, I've had it with this old monitor.

---

### Post by nikoPSK on 2008-01-11
hrm, so the fresh install held the same thing? then it just might be your GPU or monitor. :|

---

### Post by bighomer on 2008-01-11
Yeah, I think it's the monitor. It's a shame the original laptop screen died on me. Not giving up on ubuntu just yet, but I think I'm through for tonight. 
Thanks for the suggestions.

---

### Post by quadrantids on 2008-01-12
Hi there,

I think I have a similar problem. I wanted to install Ubuntu on an old Dell server with CRT 17" screen. The install CD start booting (using run and install) but after a minute or two the screen goes black with a blue window that says "OUT OF SCAN RANGE"

I then tried booting from the CD in safe graphics mode. This seemed to work but there's a considerable part of the screen missing. I wasn't aware of this until I clicked on the install icon and started the process only to find I couldn't answer the initial questions because the arrows or whatever were off the bottom of the screen...

I immediately tried resetting the screen resolution from preferences but there was only the one setting.

Would appreciate any help

---

### Post by bighomer on 2008-01-14
Posting my solution to a previous problem--I couldn't see the bottom or right portions of the screen. I'd like to post my solution for anyone else that's had this issue.

First off, I said I had a Compaq monitor. Well, I replaced it with a Zenith ZCM-1440. This did nothing to resolve the issue. 

Then I found this page:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Basically, it said to edit the xorg.conf file in /etc/X11/

The 'monitor' portion of the file looked like this:
Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

I added two lines to it to make it look like this:

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync		30-62
	VertRefresh		48-100
EndSection

For your specific monitor, try this page:
[http://svn.pardus.org.tr/uludag/trunk/comar/zorg/MonitorsDB](http://svn.pardus.org.tr/uludag/trunk/comar/zorg/MonitorsDB)

Under the 'screen' section, there was only "1600x1200" under modes. I added a 1024 option to make it look like this:

		Modes		"1600x1200" "1024x768"

I honestly don't think all these steps are necessary, but I'm not sure, so I'll list everything I did. 

Ubuntu is slightly different from Fedora Core 3, so I had some slight trouble saving my changes. I'm sure there are easier methods, but I'm glad I found this bit of information:
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

Okay, then I rebooted ubuntu and logged into my normal profile. I could see more of the screen but not all of it. It looked a little glitchy. I navigated to System --> Administration --> Screens and Graphics and changed my monitor settings to:
Monitor 1024x768
resolution 1024x768 60Hz
Upon clicking ok, a message box told me that changes would take effect after all users logged off. So I just restarted, holding my breath. 

When the screen came up (it's set to automatically log in) it looked a little off, but it was all visible. Tweaking a few settings on the monitor's panel, the screen now looks perfect. For some reason, in System --> Administration --> Screens and Graphics, the resolution set itself to 1280x768, but it looks all right for the time being, so I dare not touch it. 

Well, that's it. Finally got Ubuntu up and running. I was really hoping this would work. The thing I like most about Linux is how customizable it is. Thanks to nikoPSK and all others who tried to assist in this problem. Now I gotta get my crappy modem up and running, and I'll be all set!:)

---

### Post by nikoPSK on 2008-01-14
> **bighomer said:**
> Posting my solution to a previous problem--I couldn't see the bottom or right portions of the screen. I'd like to post my solution for anyone else that's had this issue.

First off, I said I had a Compaq monitor. Well, I replaced it with a Zenith ZCM-1440. This did nothing to resolve the issue. 

Then I found this page:
[https://help.ubuntu.com/community/FixVideoResolutionHowto](https://help.ubuntu.com/community/FixVideoResolutionHowto)

Basically, it said to edit the xorg.conf file in /etc/X11/

The 'monitor' portion of the file looked like this:
Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
EndSection

I added two lines to it to make it look like this:

Section "Monitor"
    Identifier    "Generic Monitor"
    Option        "DPMS"
    HorizSync        30-62
    VertRefresh        48-100
EndSection

For your specific monitor, try this page:
[http://svn.pardus.org.tr/uludag/trunk/comar/zorg/MonitorsDB](http://svn.pardus.org.tr/uludag/trunk/comar/zorg/MonitorsDB)

Under the 'screen' section, there was only "1600x1200" under modes. I added a 1024 option to make it look like this:

        Modes        "1600x1200" "1024x768"

I honestly don't think all these steps are necessary, but I'm not sure, so I'll list everything I did. 

Ubuntu is slightly different from Fedora Core 3, so I had some slight trouble saving my changes. I'm sure there are easier methods, but I'm glad I found this bit of information:
[http://ubuntuforums.org/showthread.php?t=31053](http://ubuntuforums.org/showthread.php?t=31053)

Okay, then I rebooted ubuntu and logged into my normal profile. I could see more of the screen but not all of it. It looked a little glitchy. I navigated to System --> Administration --> Screens and Graphics and changed my monitor settings to:
Monitor 1024x768
resolution 1024x768 60Hz
Upon clicking ok, a message box told me that changes would take effect after all users logged off. So I just restarted, holding my breath. 

When the screen came up (it's set to automatically log in) it looked a little off, but it was all visible. Tweaking a few settings on the monitor's panel, the screen now looks perfect. For some reason, in System --> Administration --> Screens and Graphics, the resolution set itself to 1280x768, but it looks all right for the time being, so I dare not touch it. 

Well, that's it. Finally got Ubuntu up and running. I was really hoping this would work. The thing I like most about Linux is how customizable it is. Thanks to nikoPSK and all others who tried to assist in this problem. Now I gotta get my crappy modem up and running, and I'll be all set!:)

No problem, I am glad you posted the instructions for help, sometimes, people just say they've solved it and no clue how they did... Please mark this thread as "SOLVED".

nikoPSK

---

