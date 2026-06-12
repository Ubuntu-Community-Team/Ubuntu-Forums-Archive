---
title: "CHALLENGE: Help me put a stop to mysterious system lockups in 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by recursion on 2007-10-21
Ever since I installed 7.10 last Wednesday, my system has been plagued with random, mysterious lockups. 

Everything I know about the problem is as follows:

1. It started almost immediately after setting up 7.10 (clean install, not upgrade). I didn't notice the problem in 7.04, but then again I only ran it for about a week before moving to a pre-release version of 7.10 because it was recommended to me as a way to fix my widescreen resolution problems. The person who told me to do this gave me his own 7.10 ISO, which he had just downloaded and installed on his laptop with no problems.

2. I have been able to find no pattern in the lockups. At first, I thought I had traced them to the use of iTunes-like music players such as Banshee, Listen Player, and Rhythmbox, but a lockup while surfing the web yesterday tells me there wasn't really a link there. Oddly enough, I haven't had a lockup (yet...) when doing things like streaming video and downloading updates, things that should be harder on the system than listening to music and using normal, non graphics-intensive websites.

3. When the system locks up, it isn't a normal "freeze." I can still move my mouse, but all the open windows are stuffed up and nonresponsive. CTRL-ALT-BKSPC and CTRL-SysReq-K have no effect, and I can't use any commands to bring up the terminal in order to kill processes. At first, the only thing I could do was a hard shutdown, but I hated doing that because it's so bad for the system. I did some research and discovered the "RSEIUB" graceful restart method, which has been the *only* thing that has been able to bring the system out of the jam-up.

4. Upon hitting CTRL-SysReq-K, a little patch of red appears at the top of the screen. 

5. If I'm playing music when the system locks up, the song will finish playing but then stop after it's over. I find this sort of disconcerting.

6. I read a thread about a similar problem happening in 7.04, and the advice given there was to disable "powernowd." I ran the command given in the thread and the terminal told me it didn't recognize it. 

Please, dear Ubuntu Wizards, help me fix my system! This problem is very annoying, especially since I know every login is a ticking time bomb --- I know it's going to eventually jam, but I never know when. 

Should I revert back to 7.04 because it appeared to be working? I know that'll mean a long battle with xorg over my resolution settings, but I'll take that over this mystery ailment any day! The one thing I'm scared of, though, is the fact that some people had this very same issue with 7.04, so I wonder if I just didn't give it enough time to appear. 

Also, how do I test my RAM and hard drive to rule out bad hardware? I don't want to completely trash my 7.10 install only to find out the problem is mechanical.

Here's what I can remember of my system specs (I'm at home right now, and the system's at college)
CPU: Pentium 4 
Graphics card: ATI Radeon X300 SE
Hard drive: 250 GB Maxtor

---

### Post by bertilow on 2007-10-21
I have this problem too (on a Lenovo 3000 C200 laptop). Right now it hasn't happened for I while.

I think it's connected to certain programs. I tried Gnotime, and I had these lockups almost every time I tried to resize a Gnotime window. It also happed with a few other programs (that I can't remember now). I don't use Gnotime now, and I try to avoid programs that seem to cause the lockups.

I could also be connected to the Cube or some other fancy desktop effect. I have turned off the Cube now and most other non-essential effects, and since then there have been no lockups.

I got similar lockups when I tried out the alpha version of the second-life program, but that is probably a different problem.

Thanks for the tip about "RSEIUB". I'll try that if it happens again.

---

### Post by Beggar on 2007-10-22
Your plight intrigues me. The problem seems to be related to your window manager.  Have you been able to reproduce this problem outside of compiz, I.E. in metacity? If not try, adding the command ```
metacity --replace
``` to your startup(System->Preferences->session), relog in and do everything you can think of to try and get it to happen.

As far as testing your hardware, at bootup you are given the option to enter the grub menu (I believe its press F12?), do this, and there should be an option to run memtest.

---

### Post by BruisedQuasar07 on 2007-10-22
Regular system lockups are usually caused by a misbehaving program or utility, or hardware problems.  Do you have any Ubuntu team untested programs or utilities? If so, disable or remove them. If this does the trick, re-enable or reinstall one at a time to find the system problem causing software and remove it.

I stick to using only software and utilities from the Official
Ubuntu Repositories. Like over 99% of PC users I want to
invest the bulk of my time in using my PCs, not studying them. 

By the way, the safe warm boot command is Alt + Print Screen (hold both keys down simultaneously) and type REISUB... You will get a total reboot without
risk of damaging your Linux system. 

--Bruised

---

### Post by trash on 2007-10-22
I was random freezing too till i turned off visual effects(System/appearance). Before that I was freezing a lot with even the normal setting. G3 ibook 900

---

### Post by recursion on 2007-10-22
> **Beggar said:**
> Your plight intrigues me. The problem seems to be related to your window manager.  Have you been able to reproduce this problem outside of compiz, I.E. in metacity? If not try, adding the command ```
metacity --replace
``` to your startup(System->Preferences->session), relog in and do everything you can think of to try and get it to happen.

As far as testing your hardware, at bootup you are given the option to enter the grub menu (I believe its press F12?), do this, and there should be an option to run memtest.

Thanks, this is something I haven't heard of before. I'll try it when I get back to college tomorrow and let you know what happens.

---

### Post by cfaulkner on 2007-10-22
Also, Open up your system (after unplugging everything of course)

Reseat video card, memory sticks and any other card.

Take a leaf blower (yes... a leaf blower) and put it on lowest setting and blow all the dust out of your system.  make sure the power of the air gets in those cracks and in your Power Supply.    be sure to run it across the back of your system too and inside the power supply fan exhaust.

Put it all back together and try again...

---

### Post by Octagonal on 2007-10-22
This happened to me when I was running Feisty, KDE and running superkaramba--(a known bug w/ KDE) this caused lockups like you are describing.  Just throwing that out there.

---

### Post by recursion on 2007-10-22
> **BruisedQuasar07 said:**
> Regular system lockups are usually caused by a misbehaving program or utility, or hardware problems.  Do you have any Ubuntu team untested programs or utilities? If so, disable or remove them. If this does the trick, re-enable or reinstall one at a time to find the system problem causing software and remove it.

Already tried it, unfortunately.

That's what I had originally thought might be the culprit, so I removed everything that didn't come with the install aside from some codecs I needed to use certain file formats. The problem was definitely still there. :(

---

### Post by recursion on 2007-10-22
> **cfaulkner said:**
> Also, Open up your system (after unplugging everything of course)

Reseat video card, memory sticks and any other card.

Take a leaf blower (yes... a leaf blower) and put it on lowest setting and blow all the dust out of your system.  make sure the power of the air gets in those cracks and in your Power Supply.    be sure to run it across the back of your system too and inside the power supply fan exhaust.

Put it all back together and try again...

It probably *is* a good idea to clean it out --- I got this particular box from my mom, who said it was "broken" (Windows was corrupted, possibly from a virus). I highly doubt she ever opened it up to dust it.

---

### Post by cfaulkner on 2007-10-22
> **recursion said:**
> It probably *is* a good idea to clean it out --- I got this particular box from my mom, who said it was "broken" (Windows was corrupted, possibly from a virus). I highly doubt she ever opened it up to dust it.


Canned air is too expensive.  I use my leaf blower on every customer's PC they bring in.  THey find it shocking to know that a leaf blower does a better job.  LOL

---

### Post by trash on 2007-10-22
> **trash said:**
> I was random freezing too till i turned off visual effects(System/appearance). Before that I was freezing a lot with even the normal setting. G3 ibook 900

I just had my first random freeze up since turning off visual effects, and instead of running gnome i am now running xfce. My machine did not have any freezing up problems in fiesty or OSX so this problem is a bit suspect. In my case most of the time it freezes up opera and pidgin are all that is running.

EDIT:
Grrr, 2 more lockups since posting! both while running Opera, one quite random but the other froze right after entering my password to open an osX partition.
Now i've got top running so i can see which app is last running that is causing the freeze.

---

### Post by recursion on 2007-10-23
> **trash said:**
> I just had my first random freeze up since turning off visual effects, and instead of running gnome i am now running xfce. My machine did not have any freezing up problems in fiesty or OSX so this problem is a bit suspect. In my case most of the time it freezes up opera and pidgin are all that is running.

EDIT:
Grrr, 2 more lockups since posting! both while running Opera, one quite random but the other froze right after entering my password to open an osX partition.
Now i've got top running so i can see which app is last running that is causing the freeze.

The problem has appeared to clear up for me since turning visual effects off --- I think the effects were upsetting my graphics card.

I'm sorry it's back for you --- seeing as you have an ibook, I'd imagine your underlying hardware is different from mine, but I'm still a bit worried about a relapse. Let me know if you ever figure it out.

---

### Post by trash on 2007-10-23
> **recursion said:**
> The problem has appeared to clear up for me since turning visual effects off --- I think the effects were upsetting my graphics card.

I'm sorry it's back for you --- seeing as you have an ibook, I'd imagine your underlying hardware is different from mine, but I'm still a bit worried about a relapse. Let me know if you ever figure it out.

I thought I had it narrowed down to Opera, I stopped using it and have hard locked up twice since... once while nothing at all was running! I am at a total loss and if it keeps happening i'll be going back to FFawn:(.
I'll keep ya posted should I find anything interesting.

---

### Post by recursion on 2007-10-23
> **trash said:**
> I thought I had it narrowed down to Opera, I stopped using it and have hard locked up twice since... once while nothing at all was running! I am at a total loss and if it keeps happening i'll be going back to FFawn:(.
I'll keep ya posted should I find anything interesting.

I have a few other things I can try that were recommended to me if it happens again, but I'll probably just end up reverting to 7.04 if the issue comes back.

I've done everything I can think of that brought on the lockups before and nothing's happened, so I have high hopes that I'm in the clear.

How long did you go without problems, by the way? And what are your system specs?

---

### Post by ed-koala on 2007-10-23
I haven't seen this mentioned so I'll throw it in - Have you looked into any new driver for your ATI card?  ATI misbehaves, sometimes badly, with Ubuntu.  Considering the amount of checking you have done so far you probably thought of this, but if not it is something that could certainly cause weird problems like yours.

---

### Post by trash on 2007-10-23
> **recursion said:**
> I have a few other things I can try that were recommended to me if it happens again, but I'll probably just end up reverting to 7.04 if the issue comes back.

I've done everything I can think of that brought on the lockups before and nothing's happened, so I have high hopes that I'm in the clear.

How long did you go without problems, by the way? And what are your system specs?

ibook g3 900mhz 640ram
about 12 hours or so was the longest i think. I am going to try removing gnome completely, for some reason I suspect it's a gnome issue as gnome was the reason I switched to xfce in the first place.

---

### Post by mivo on 2007-10-23
I had exactly the same problem with the same behaviour with the 7.10 beta version. I reported it, and posted about it in the dev forum, but I could not find a solution. In the end, I downgraded to 7.04.

In a 12 hours session, I would get about 5-7 lockups, and they happened in all sorts of situations. They, however, ONLY occurred when I was doing something: typing, moving the mouse, etc. It never froze when the computer was idle or downloading (or otherwise being busy, as long as I was not doing anything). I tried different video drivers, turned off each Compiz feature, one by one, then Compiz completely, and my hopes would always get dashed after the next lock-up. I was unable to reproduce it. I also cycled through different applications, but the freezes did not seem to depend on any particular application. My first guess was the browser, but that was only because that is the program I actively use the most, and would happen without it, as well.

Like I said, I went back to 7.04, which has been, and still is, running rock-stable, with the same applications. I expect a new computer next week, so that is where I will put 7.10 on. My current machine will continue to run under 7.04 until the next LTS version. I had some hopes that the problem may have gotten fixed between my most recent try three weeks ago and now, but this thread (and some others) imply that this would probably still be an issue for me.

This machine: P4/3.0/HT, 1 GB, X700 Pro with 256 MB (PCIe), 250 GB disk (no dual boot), PS/2 mouse and keyboard. But, like I said, there are no problems at all in 7.04 (and there were none in Kubuntu, either).

---

### Post by nynoah on 2007-10-23
I am getting REAL bad lock ups on mine.  I look at my system log and it happens every time my system looks for the Wireless internet connection.  the problem is, I DON'T have Wifi and never have.  I have tried to turn it off, but when I do, I lose my internet connection completely.  

Check your system log and see what the last things your system was doing before it locked.

go to SYSTEM - ADMINISTRATION - SYSTEM LOG and see what you can see after you reboot from a lock up.

mine says this

Oct 23 17:00:49 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists. 

Oct 23 17:00:49 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Oct 23 17:00:56 nyn-desktop kernel: [   68.494698] eth0: no IPv6 routers present


I wonder if you all are having the same problem?

---

### Post by ed-koala on 2007-10-23
Hmmmm, definately not a hardware problem then.  Also, since it ONLY happens when you are doing something with input, or motion on the screen, still leads me to believe it's a graphics issue of some kind with 7.10 and your graphics card/settings.

I'm gonna think on this one awhile and see if I can think of a way to test this to really isolate the issue, even tho you went back to 7.04 (good move!)

One other thing I did think of ... monitor refresh rate (Hz).  If it got set too high when you upgraded (not likely) that might cause freezing also.

---

### Post by mivo on 2007-10-23
> I wonder if you all are having the same problem?

No, I had checked for this, there was nothing in the logs -- from the machine's point of view the freezes never happened, as far as the logs were concerned. What froze was just user I/O, the machine itself continued to work -- i.e. sound continued for quite some time, and downloading resumed. The "only" problem was that no keystrokes and mouse clicks were registered, and that the screen froze (mouse cursor could still be moved). It was 100% the same situation as described by the thread starter. (There is some relief in this.)

---

### Post by nynoah on 2007-10-23
> **mivo said:**
> No, I had checked for this, there was nothing in the logs -- from the machine's point of view the freezes never happened, as far as the logs were concerned. What froze was just user I/O, the machine itself continued to work -- i.e. sound continued for quite some time, and downloading resumed. The "only" problem was that no keystrokes and mouse clicks were registered, and that the screen froze (mouse cursor could still be moved). It was 100% the same situation as described by the thread starter. (There is some relief in this.)

Well that is what mine would do, and the log files always show it trying to connect and update my non existent wifi.

---

### Post by mivo on 2007-10-23
> **ed-koala said:**
> One other thing I did think of ... monitor refresh rate (Hz).  If it got set too high when you upgraded (not likely) that might cause freezing also.

it was at 60Hz (LCD). I tried the ATI binary driver and the open source Radeon one, even tested different versions -- no improvement. The thing is, these freezes did not occur after a fixed period of time. There were times I could work for 3-6 hours without a single lock-up, working just as always, lots of typing and moving around, and other times it froze twice in an hour, even though I used the same applications and did the same type of actions. Plus, at one point I had the machine torrent files and ray-trace stuff for 18 hours (no user I/O), and it never froze. User I/O is the only single aspect that all of my freezes had in common. It *could* be Gnome 2.20, that is one thing I had not tried (using a different 7.10 DE).

---

### Post by mivo on 2007-10-23
> **nynoah said:**
> Well that is what mine would do, and the log files always show it trying to connect and update my non existent wifi.

Oh,  please file a bug report at launchpad about this. I did not find this in my logs, so it looks like a different bug, but this really should be reported. Most curious behaviour, too! :)

---

### Post by Octagonal on 2007-10-24
what helped me pinpoint my lockups was opening up a terminal and running "top" and just leaving that somewhere on my desktop that was unobstructed.  You could see what was going on when the keyboard and mouse become unresponsive.

---

### Post by trash on 2007-10-24
Hohum... It's not gnome, nor Opera lol. It froze again some time after I went to bed and there were no programs running. Syslog is no help either, everything looks fine right up to 'REBOOT'.
The only thing that is the same each and everytime is Xorg is one of the first 3-4 in the list  while top is running. I can say that not running Gnome and Opera have again lessened the frequency of the lockups.

Some other stuff i've notice but can't really say if they are related are network manager and mouseemu, they have just cought my eye at some point.

---

### Post by mivo on 2007-10-24
I wonder if it is X. What version are you running in Gutsy? You can find out by typing:

```
X -version
```

My crash-free, stable Feisty uses 7.2.0.

---

### Post by trash on 2007-10-24
> **mivo said:**
> I wonder if it is X. What version are you running in Gutsy? You can find out by typing:

```
X -version
```

My crash-free, stable Feisty uses 7.2.0.

X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8)
Current Operating System: Linux xbook 2.6.22-14-powerpc #1 Sun Oct 14 21:42:06 GMT 2007 ppc


Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon Mobility M7 LW [Radeon Mobility 7500]"
	Monitor		"Color LCD"
	DefaultDepth	16
	SubSection "Display"
		Modes		"1024x768"
	EndSubSection
EndSection

Somebody mentioned refresh rate but where would I change it and what should i change it to? at the moment it's 60

---

### Post by mivo on 2007-10-24
It says 1.3.0? Hrm. Mine says, "X Protocol Version 11, Revision 0, Release 7.2". I know too little about X for this to  make sense to me. :confused:

---

### Post by crane on 2007-10-24
I really wonder if you guys all having lock up are suffering from the same thing. System lock ups can be a number of things. My Gutsy install is running rock solid so I think we may need to look at a hardware comparison. First and for most to 2 things. First like someone mentioned earlier. Blow all the dust out of your system. Some people don't believe their system is dusty but trust me it the computer it 6 months to a year old and you have never cleaned it, it IS dusty.

 Second, on start up you should see a memtest option in the grub menu. Select it and run memtest . I would suggest running it overnight. If you only run it for a few minutes your problem may not show up.
At the very least run it for an hour. I suggest memtest because I had the exact same problems about a year ago. After weeks of pulling out my hair I ran memtest and found out I had a memory stick going bad and causing all my problems.
 Don't assume it not memory because Windows runns OK or another OS seems OK. They can all address and treat accessing memory completely different.

 Now if all goes well and your still having lock ups. Lets look at hardware.
 Maybe we can put up a side by side comparison of the computers and see what the similarities are, this may give us a better direction to look.

---

### Post by trash on 2007-10-24
Well just to rule out dust completely i will give mine a cleaning this week.. however, running osX and FFawn problem free with a temperature monitor running that showed no problems at all I really don't think this is the issue in my case... that said, fingers crossed lol.

---

### Post by mivo on 2007-10-24
Same here. The problems only occur in Gutsy (I tried with two different installs from scratch), and Feisty worked before, and works again -- it never locked up on me. I would rule out a hardware defect in my case, though it is entirely possible that it is a hardware incompatibility with something that Gutsy introduced.

I can't really fiddle around with the machine this week (some work to get done), but when my new production box arrives on the weekend or early next week, I'm going to wipe clean this computer, put Gutsy on it again and enable the Hardy repositories. This way I will have a dedicated testing machine.

I think what we have all in common is an ATI card, but not the same model. Note that I tried different versions of the binary driver and the open source one, which made no difference (both work fine in Feisty). I think we also have LCD displays, running at 50 or 60 Hz. The rest of the machines seem to be different.

The crashes are different from most lock-ups that I have seen reported insofar that sound and other operations continue (i.e. downloads) and that only user I/O and the screen freeze (though the mouse cursor can still be moved) -- and that nothing is recorded in the logs. I guess we only need to find out which software or hardware components eqully affect mouse clicks, any keyboard actions, and the screen output, but nothing else. ;)

---

### Post by Bannor on 2007-10-24
same problem here!

random freezes.  

last night I ran a couple of torrents closed my laptop cover and morning when I opened up the cover the screen remained black like the screen was this closed, and was compeletely unresponcive. 

1.Did anyone here need to Use Noapic nolapic to load gutsy?

2. how about wireless drivers is everyone using ndis wrapper (cause that and my Nvidia driver are the only programs I have loaded).  

Rule out dust Windows doesn't freeze (witch it would if dust was the culprit) and the computer came out of the box 2 weeks ago. 

here are my stats

AMD Turion 64 X2 Dual-Core Mobile Technology TL-62 (2.1 GHz, 512KB+512KB L2 Cache )

Nvidia GeForce Go 7150M

1.5 gigs of ram

---

### Post by mivo on 2007-10-24
No wireless here. Just a standard wired connection to the router (DHCP).

---

### Post by Bannor on 2007-10-24
how about nvidia

or noapic nolapic ?

---

### Post by mivo on 2007-10-24
No, and using an ATI card in the box that locks up in Gutsy. But your freezes differ from mine: I only experienced lock ups when I was actively doing something at the computer. I could let it run all night and torrent files without any freezes. Lock-ups exclusively occurred when I was typing or using the mouse. That is one of the few common aspects of every lock-up I observed.

---

### Post by rykel on 2007-10-24
Pals, I am also having Gutsy freezes... except that mine are TERRIBLE... the whole Toshiba M40 laptop just locks itself up within 10 min of use, and NOTHING moves (not even the mouse). No virtual desktops (Ctrl-Alt-F1-6) either. Only thing I can do is to unplug the power.

I did NOT have problems in Dapper, Edgy or Feisty...

Anybody can help??   :confused:

---

### Post by philinux on 2007-10-24
Until problem solved dont unplug , use your pinkies to hold down ALT and SYS RQ then type 

[FONT="Times New Roman"]R E I S U B[/FONT]

You system will reboot safely.

---

### Post by Bannor on 2007-10-24
> **rykel said:**
> Pals, I am also having Gutsy freezes... except that mine are TERRIBLE... the whole Toshiba M40 laptop just locks itself up within 10 min of use, and NOTHING moves (not even the mouse). No virtual desktops (Ctrl-Alt-F1-6) either. Only thing I can do is to unplug the power.

I did NOT have problems in Dapper, Edgy or Feisty...

Anybody can help??   :confused:

this problem sounds a lot like my problem.  

have you tried booting noapic nolapic?

---

### Post by brennydoogles on 2007-10-24
> **BruisedQuasar07 said:**
> . 

By the way, the safe warm boot command is Alt + Print Screen (hold both keys down simultaneously) and type REISUB... You will get a total reboot without
risk of damaging your Linux system. 

--Bruised

Maybe it's just my keyboard, but do you have to be some kind of contortionist to accomplish this maneuver?

---

### Post by trash on 2007-10-24
Ati here too and no to noapic.

I've had NetworkManager problems before so I have just killed it.. will see how long i last running Opera:popcorn:

---

### Post by buntunub on 2007-10-24
I was having this exact problem so I went into Nvidia-settings and turned off Xinerama. No clue why it was enabled, but it seems to be enabled by default. Anyway, havent had a single lockup since.

---

### Post by trash on 2007-10-24
> **trash said:**
> Ati here too and no to noapic.

I've had NetworkManager problems before so I have just killed it.. will see how long i last running Opera:popcorn:

Well it's early to tell for sure but so far I have been able to do everything that before made me lock up such as running Opera, opening synaptic, mounting an osX partition. So if anybody out there with really bad lockups whats to try...

sudo killall NetworkManager

or if you don't use/need them...

sudo apt-get remove network-manager network-manager-gnome


Don't worry about removing them you can still use network-admin to configure your connection:)

---

### Post by nynoah on 2007-10-24
well I tried sudo killall NetworkManager and it killed my whole internet connection.  So that is not the answer.  But BOY did it speed up my computer.

---

### Post by trash on 2007-10-24
> **nynoah said:**
> well I tried sudo killall NetworkManager and it killed my whole internet connection.  So that is not the answer.  But BOY did it speed up my computer.


Thats ok, use network-admin to get your connection back up and running.

---

### Post by nynoah on 2007-10-24
Well I turned it back on by going into - SYSTEM - ADMINISTRATION - NETWORK.   But then it still does it again.  It did the same thing.  

Oct 24 20:21:36 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists. 

Oct 24 20:21:36 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Same thing just before lock up.  This is driving me INSANE.  I can not use my system.  I lock up 2 times an hour.  I want to toss my computer out the window, this is so frustrating.

---

### Post by trash on 2007-10-24
> **nynoah said:**
> Well I turned it back on by going into - SYSTEM - ADMINISTRATION - NETWORK.   But then it still does it again.  It did the same thing.  

Oct 24 20:21:36 nyn-desktop NetworkManager: <info>  Updating allowed wireless network lists. 

Oct 24 20:21:36 nyn-desktop NetworkManager: <WARN>  nm_dbus_get_networks_cb(): error received: org.freedesktop.NetworkManagerInfo.NoNetworks - There are no wireless networks stored.. 

Same thing just before lock up.  This is driving me INSANE.  I can not use my system.  I lock up 2 times an hour.  I want to toss my computer out the window, this is so frustrating.

k not sure what programs are being used so try running sudo network-admin in a terminal and see if it's a different tool, if so use it that way. Dunno why there are so many tools named so similarly I find it makes like really confusing lol

BTW I have not locked up since!!!!!!:D

---

### Post by nynoah on 2007-10-24
I tried that.  It is the same tool.  I am not sure if I am doing something wrong.  But I will let you know if I lock again.

Noah

---

### Post by trash on 2007-10-24
> **nynoah said:**
> I tried that.  It is the same tool.  I am not sure if I am doing something wrong.  But I will let you know if I lock again.

Noah

$%#@!!! never mind false alarm:(... I locked up hard again!

---

### Post by rykel on 2007-10-24
> **Bannor said:**
> this problem sounds a lot like my problem.  

have you tried booting noapic nolapic?

No, but I removed all compiz and using only nvidia-glx-new... no lock-ups so far, but I have messed up my screen resolution. (/etc/X11/xorg.conf)   :popcorn:

Is there a way to replace the Gutsy default xorg.conf file automatically within the system? I have deleted all the backups yesterday...

---

### Post by trash on 2007-10-24
Originally Posted by Bannor  
this problem sounds a lot like my problem. 

have you tried booting noapic nolapic?


I forgot to try that so i'm trying it now!..........:popcorn:

---

### Post by nynoah on 2007-10-24
Sorry what are these programs, noapic nolapic?

  Never heard of them.

---

### Post by trash on 2007-10-25
> **nynoah said:**
> Sorry what are these programs, noapic nolapic?

  Never heard of them.

I'm not sure but it didn't work for me:(

---

### Post by Bannor on 2007-10-25
> **nynoah said:**
> Sorry what are these programs, noapic nolapic?

  Never heard of them.


napic nolapic are boot commands, after a double check that is not my issue either.  

noapic and nolapic have something to do with CPU scaling. I couldn't install ubuntu so I added them to my cd boot and Wa la it worked.  Aparently amd processors and linux don't play well unless you add those two words to you boot command.

I don't see a lot of ideas being thrown around here I think that might be because we are in the beginners forum with a legit (non beginner) system problem.  Is there a way to put this thread infront of some legit Ubuntu guys and get their thoughts?

---

### Post by ed-koala on 2007-10-25
This thread is getting a bit confusing to figure out, since several people are posting similar, tho not identical, problems.

Might I suggest each user who is having a problem start a new thread and report these things in their post:

-All system hardware
-Description of problem
-Steps already taken to resolve the problem
-All processes running at boot up
-All programs (such as compiz-fusion or any others) running when booted.

The processes running can be found at *System - Administrator - System Monitor - Processes tab.* 

This will help the problem solvers narrow down solutions for each user having trouble.

---

### Post by rykel on 2007-10-26
Hi all,

I have narrowed down my Gutsy freezes to BITTORRENT... and it freezes with any client. (I have tried Azureus, ktorrent and Deluge so far)... there is another thread where many others report the same freeze-up.

btw, it is NOT a Java issue.

:popcorn:

---

### Post by trash on 2007-10-27
There was one update today libpng.. i've been running rtorrent, opera, pidgin and synaptic all evening. I also installed fluxbox to try it out(it's been a year or two) and so far no problems.... knocking on wood as i type:popcorn:

---

### Post by mivo on 2007-10-27
Now if you manage to work five or more hours in Gnome, I will open a bottle! :p (I sure wish my other machine would arrive ... it's somewhere between Finland and Germany with no tracking number.)

---

### Post by trash on 2007-10-27
> **mivo said:**
> Now if you manage to work five or more hours in Gnome, I will open a bottle! :p (I sure wish my other machine would arrive ... it's somewhere between Finland and Germany with no tracking number.)

well, i never had a great time in gnome I just installed it this time because I couldn't find Xubuntu but they both gave me problems this time around... now as I said in my last post I installed Fluxbox yesterday, I've been up and running all night long with apps open! Something seems to have fixed itself here!
Could it have been libpng update? I can only guess but it is graphics related.

---

### Post by Astrodan on 2007-10-27
1:  Just a quick question or two, are your screensavers running at the time the machine locks up?  i.e. you come to  a frozen machine with a screensaver on the screen.  

Suggestion :  Please set screensaver to blank.  

2:   As for other lockup times, are you selecting something inside a window within a window?

i.e. selecting to change an option in a program.

3:  Has your machine ever locked up while in terminal?  i.e. using apt-get install...etc.

---

### Post by bonzini on 2007-10-28
Are you sure your problem isn't fixed by adding noapic and related flags to your boot?

I used to have an unresponsive window / desktop / but I can move the mouse situation, in 6.10, 7.04.  In those I fixed it with a noapic but in 7.10 I seem to be Ok.  Of course YMMV.

---

### Post by emil.s on 2007-10-28
> **rykel said:**
> Hi all,

I have narrowed down my Gutsy freezes to BITTORRENT... and it freezes with any client. (I have tried Azureus, ktorrent and Deluge so far)... there is another thread where many others report the same freeze-up.

btw, it is NOT a Java issue.

:popcorn:

With any BitTorren client!? Finally we are going for a solution if so. Or i mean, now we know the problem...
My down stripped server crashes if i start rTorrent. I had a uptime of 9 days, but when i started rTorrent it was dead in some hours...

For more info, se:
[http://ubuntuforums.org/showthread.php?t=586753](http://ubuntuforums.org/showthread.php?t=586753)

---

### Post by mivo on 2007-10-28
I had 7.10 lock-ups without any torrent program running. In fact, Deluge could easily run all night without a system-lockup. 

The problem with this thread is that it deals with different types of lockups. :)

---

### Post by smbm on 2007-10-28
I'm getting hard locks with Azureus here!

---

### Post by icechen1 on 2007-10-28
Happened the same to me,seems to be fixed by disabling some compiz-fusion plugins,hope this helps!

---

### Post by emil.s on 2007-10-28
> **icechen1 said:**
> Happened the same to me,seems to be fixed by disabling some compiz-fusion plugins,hope this helps!

I'm running my server without X, so probably not. 

Reported this as a bug:
[https://bugs.launchpad.net/ubuntu/+bug/158037](https://bugs.launchpad.net/ubuntu/+bug/158037)

Can everybody who have this problems post a comment and confirm this? :)

---

### Post by Cochise on 2007-10-28
i havent read the whole thread but i have the same graphics card and was getting lock ups in gutsy i used the new ati driver and its stopped. i followed the instructions here: [http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support](http://forlong.blogage.de/article/2007/10/23/fglrx-8423---finally-with-AIGLX-support)

---

### Post by rykel on 2007-10-28
Hi, here to confirm one more **BITTORRENT**-related lockup... (not Java)

I ran BitLet.org through Firefox and without fail, Ubuntu would dead freeze the system, just like it does with Azureus, Deluge and KTorrent.   :confused:

I know that there are other non-BT-induced lockups in this thread, but I think the majority of us are facing this dreaded bug due to BT.

UPDATE: I had another freeze 10 minutes ago which is NOT related to Bittorrent... however, I was DOWNLOADING updates from Ubuntu repositories at 60kB/s. So it seems that in my case, **downloading** (the speed? the writing to the hard disk?) is the culprit.

I have just stopped hdparm... let me see if it might be the mastermind behind all the lockups!!

---

### Post by trash on 2007-10-29
I think it's a way more serious problem, I will start a new thread because this time I didn't lockup but my machine just shut off complately. I can restart but my laptop screen is now completely dead.

Yes it could be an unrelated hardware issue but that is a bit too much of a coincidence for me to swallow since I have had no problems at all with my screen before now.

---

### Post by urk_nono on 2007-11-02
Hello!

I've also been struggling with random freezes, mostly occurring after 30 minutes of uptime. I'm currently running the system monitor, that ed-koala proposed. Hopefully I can diagnose the problem. For my part I upgraded instead of using a live-CD, that's when the freezes started. Unlike most of you my entire computer freezes, the mouse and even the keyboard. I tried then to install Gutsy using the liveCD, still the freezes occurred. 

I also did a memtest, where I got [this output.]("http://img125.imageshack.us/img125/8486/memtest2pz4.jpg")

Could this have anything to do with the freezes?

Kind regards
Urk

---

### Post by pieralle on 2007-11-11
Hello, 
I have tried to make some trials and:

- decreasing the speed of connection in .. torrent: still freeze
- upgrading kernel to 2.6.24.rc1 ..............torrent: still freeze
- downgrading to 2.6.20.16 ....................OK! (until now):popcorn:

My configuration is:

AMD64, ati x1600, 1GB
Gusty AMD64

Now restricted drivers won't work, i suppose that I should install the 2.6.20.16 restricted

---

### Post by rykel on 2007-11-11
Hi all,

I got so sick and tired of the freezes that I did a clean format and reinstall of Ubuntu Gutsy... so far, so good, no lockups, despite downloading huge chunks of data at speeds of more than 200kB/s.

---

