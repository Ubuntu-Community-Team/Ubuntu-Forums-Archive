---
title: "Is Ubuntu worthless for wireless?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by dscott60 on 2007-01-23
Well after spending several days trying to get my Zonet ZEW2500P working, I've come to the conclusion that it just won't work in Ubuntu.  And judging from the number of posts in here from people that can't get their wireless adapters to work, I'm guessing it has problems with just about all wireless adapters.  Unless you're a LINUX genius and a troubleshooting god.  Too bad.  With more and more people going wireless that doesn't bode well for Ubuntu.  I had high hopes for Ubuntu and bragged about it to all of my friends.  Guess it's back to windows for this noob.

---

### Post by oilchangeguy on 2007-01-23
open the double screen icon to the left of the clock and tell me what you see.

---

### Post by aysiu on 2007-01-23
I've had no problems using the Intel Pro Wireless 2200 card I bought for my Dell laptop.

Did you research compatibility lists before buying the Zonet ZEW2500P, or did you just hope Ubuntu would automatically detect *any* wireless card you threw at it?

---

### Post by 23meg on 2007-01-23
> And judging from the number of posts in here from people that can't get their wireless adapters to work, I'm guessing it has problems with just about all wireless adapters.You're doing wrong by judging from that, since you don't hear from people like me who have no problems. My wireless adapter has always worked out of the box. I've made zero effort to get it working with any version of Ubuntu. It took me fifteen minutes to do some research before buying one to figure that it was supported and would work without manual configuration.

---

### Post by aysiu on 2007-01-23
> **23meg said:**
> You're doing wrong by judging from that, since you don't head from people like me who have no problems. It's kind of like hanging out by the baggage claim customer service area at an airport and then assuming, by all of the complaints you hear, that most passengers lose their baggage *en route*...

---

### Post by SendDerek on 2007-01-23
> 
 Is Ubuntu worthless for wireless?


No.

---

### Post by aeiah on 2007-01-23
from a quick search of the forum it seems that ZEW2500P is supported by the rt2570 driver, which although broken in edgy i do believe, is a brilliant driver. it supports packet injection and other nice things that you can use to hack encrypted routers. for security auditing purposes obviously 8)

you'll need to follow the howto for the rt2570 if you havent already. ndiswrapper works too by the looks, but i recommend installing the native driver. have you tried this?

---

### Post by Tux Aubrey on 2007-01-23
Many people seem to have joy with wireless, but I've only had limited success.

Ndiswrapper helped get my existing Netgear and D-Link cards working but I have not been able to source (in Australia) a PCMCIA card with drivers that work natively with Ubuntu.

I am therefore reluctantly reluctant to recommend Ubuntu (or Linux generally) to people who absolutely must have wireless connectivity - although I do encourage them to try the LiveCD and search the forums (and other sites) for information aboout their card.

---

### Post by houstonbofh on 2007-01-23
> **dscott60 said:**
> Well after spending several days trying to get my Zonet ZEW2500P working, I've come to the conclusion that it just won't work in Ubuntu.  And judging from the number of posts in here from people that can't get their wireless adapters to work, I'm guessing it has problems with just about all wireless adapters.  Unless you're a LINUX genius and a troubleshooting god.  Too bad.  With more and more people going wireless that doesn't bode well for Ubuntu.  I had high hopes for Ubuntu and bragged about it to all of my friends.  Guess it's back to windows for this noob.
All it shows is that you make poor purchasing decisions.  I have several systems with out of the box wireless support, and no problems.  But I picked my wireless cards carefully.

---

### Post by bionnaki on 2007-01-23
my wireless card works flawlessly. see my signature for info.

---

### Post by IYY on 2007-01-24
> And judging from the number of posts in here from people that can't get their wireless adapters to work, I'm guessing it has problems with just about all wireless adapters.

Your claim: because most questions on a support forum are about wireless, most wireless devices must not work. This is a huge logical fallacy. When wireless works correctly (as it does out of the box for 3 out of 4 of the cards that I have), you just don't read about it in the forum. I'm not talking about some obscure cards either, one is a D-Link and another is a Linksys (the third *is* an obscure card for which I can't even find Windows drivers but surprisingly worked out of the box as well). I have a Motorolla card that didn't work.

---

### Post by mdsmedia on 2007-01-24
I've got a HP Compaq nx6120 (not sure what the wireless card in it is because I'm not at it at the moment) and I've never had any problem with wireless. It's been flawless.

I've read a few anecdotes of wireless problems and it has been a problem with some cards.

I guess if your wireless card was already in your machine when you installed Ubuntu you can't really blame the purchase decision, and I'm not sure how difficult/expensive it would be to replace the wireless card if you can't get yours to work.

That said, Ubuntu isn't worthless for wireless. Maybe just difficult with the card you are using.

---

### Post by aysiu on 2007-01-24
Do your research:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by phr0ze on 2007-01-24
Although he started in on criticizing Ubuntu by making broad uninformed statements, attacking him back by implying he's stupid doesn't help. Neither does telling him that your configuration works fine. Let him go back to windows.  If it wasn't for the wireless problems the next little problem would send him back anyways.

---

### Post by aysiu on 2007-01-24
No one was implying anyone was stupid or attacking anyone. And, yes, as a matter of fact, telling the OP our configurations work does help because the question is "Is Ubuntu worthless for wireless?" And the answer is "No. It's worth something." Chiming in and saying "it works for me" directly counters the OP's perception that almost everyone is having trouble with wireless.

---

### Post by dscott60 on 2007-01-24
Well, for some strange reason, when I turned on my computer this morning, my wireless adapter was working.  I rebooted it last night and it wasn't, so it's strange.  Nevertheless, I'm a happy camper now.  I LOVE Ubuntu!  Hehehehehehehehe.

And, no, I won't desert Ubuntu as soon as I have the least little problem.  Getting connected to the internet is a MAJOR issue.  If you can't, it renders Ubuntu or any operating system pretty much worthless.  If I have a problem with a video driver or my sound card doesn't work, at least I can still use the computer and work on the issue.  

Just in case somebody follows this thread, here's what I did to install my wireless adapter.  I followed the instructions at this link [http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29](http://en.wikipedia.org/wiki/Ubuntu_%28Linux_distribution%29)  After installing ndiswrapper-utils I entered the commands in the terminal window as indicated.  I had a problem because when I entered the sudo modprobe ndiswrapper command it kept coming up with this error

dave@dave-desktop:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument
dave@dave-desktop:~$ 

So, I installed ndisgtk, and went the alternate gui route.  Afterwards, I rebooted, and enabled my wireless adapter under Networking, and everything looked ok, but my adapter wasn't working.  So I rebooted again.  Still nothing.  Then, like I said, I woke up this morning, turned on my computer and voila, it was working.  

I still didn't get an answer to this question and this may be why I had a problem:  

"For ndiswrapper to function, you need to load a module. To do this, type:

sudo depmod -a
sudo modprobe ndiswrapper"

Do I type the first line and hit return, then type the second line and hit return?  Or do I type both commands then hit return?  Stupid question, I know, but I am a stupid noob.

You dudes need to dumb it down for us extreme noobs.  I've used Windows extensively and have had a home network for 6 years.  Opening a terminal window and entering text commands is totally alien to me, and I'm sure to many other posters in here.  The simplest thing can totally screw us up and make us very frustrated.  Remember windows?  Using it makes you really really dumb!  Okay?  

On a positive note, I very much appreciate the fact that Ubuntu is free and so is the advice in this forum.  THANK YOU!!!!!!!!!!!!!!!!  I'm tickled pink to be able to stick it to the man (Bill Gates).  At the very least, I'll keep this operating system on two of my 4 computers, since I only use them for internet and email.  And even with the issues I've had, I'm recommending Ubuntu to everybody I know who has some computer skills.

---

### Post by ArizonaSteve on 2007-07-16
I also found Ubuntu to be worthless because of no wireless support.  I was hoping to use it for added security when using open hotspots and installed it with Wubi.  The install went OK but it didn't find my Dlink wireless card that works fine in Windows! I read that to make wireless cards work you need to use the NDISwrapper.  I tried to read the installation instructions for that but it makes absolutely no sense!  I'm not a programmer so it's nothing but gibberish!  Is there a solution to this?  Don't the Linux geeks ever use wireless, why don't they have support for wireless cards?

---

### Post by aysiu on 2007-07-16
It depends on the wireless card. I have an Intel Pro Wireless 2200, and it works perfectly with no added configuration. In fact, Ubuntu appears to be the only OS in our household that can handle WPA. Because WPA doesn't work on my wife's Powerbook or on my work Windows laptop, we have to use WEP for wireless.

To find out if your card is natively compatible or needs *ndiswrapper* in order to work, check out this page:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

---

### Post by kknd on 2007-07-16
Depends the card you have, but in fact is wireless cards  faults to don't have drivers for other O.S.

Ubuntu and OpenSUSE are GNU / Linux distros that have a good support to wireless (limited by the distros that I've tried).

---

### Post by Zzl1xndd on 2007-07-16
I have a Toshiba m70 with an Intel Wireless card (on board) worked out of the box no issues what so ever and just over the weekend I helped a friend install Linux Mint with a Broadcom 43XX card downloaded 1 think and he was up and running. Wireless can be trying but its all in the hardware some work better then others.

Oh and Im glad to hear your card is working now :)

---

### Post by ArizonaSteve on 2007-07-16
The fact that a few of you have Intel cards that work doesn't help everyone else out there and there's no point in telling someone to use the NDISwrapper since it's nearly impossible to install anything in Linux.  I've never been able to do it at all except with Redhat package manager.
All the Linux geeks need to get out of their D&D fantasy world and try to get wireless cards and things like that to work in the real world the same as in Windows or Linux will never catch on!

---

### Post by asmoore82 on 2007-07-16
IBM's, iBooks, Powerbooks....

WiFi works automagically on everything I've tried.

Answer to thread: no.

---

### Post by aysiu on 2007-07-16
> **ArizonaSteve said:**
> The fact that a few of you have Intel cards that work doesn't help everyone else out there and there's no point in telling someone to use the NDISwrapper since it's nearly impossible to install anything in Linux.  I've never been able to do it at all except with Redhat package manager. And there's no point in telling other people that Ubuntu is "worthless for wireless" when you select wireless cards that are incompatible. 

What is so hard about installing *ndiswrapper*, anyway? Plug your computer into the wired connection, go to System > Administration > Synaptic Package Manager. Search for the word *ndiswrapper*, right-click to install the appropriate packages, then click *Apply* to install it.

---

### Post by Zzl1xndd on 2007-07-16
> **ArizonaSteve said:**
> The fact that a few of you have Intel cards that work doesn't help everyone else out there and there's no point in telling someone to use the NDISwrapper since it's nearly impossible to install anything in Linux.  I've never been able to do it at all except with Redhat package manager.
All the Linux geeks need to get out of their D&D fantasy world and try to get wireless cards and things like that to work in the real world the same as in Windows or Linux will never catch on!

Um I believe I also mentioned the Broadcom 43XX and the does require NDISwrapper granted the Mint Distro I mentioned has NDISwrapper Pre-installed it is only one extra step to installing the card with Ubuntu. And how is it hard to install something in Linux I have not once and an issue with anything be it a .deb, .sh or .run

---

### Post by aysiu on 2007-07-16
Anything in the repositories ("anything" definitely including *ndiswrapper*) is easy to install... easier to install than any Windows software.

Outside the repositories (**not** *ndiswrapper*) can be difficult, depending on which software we're talking about.

---

### Post by jvc26 on 2007-07-16
I have installed Ubuntu on five laptops now all with a whole range of wireless cards. All worked out of the box, no config and up and running. I'd dispute it is worthless for wireless.
Il

---

### Post by ArizonaSteve on 2007-07-16
>Plug your computer into the wired connection, go to System > Administration > Synaptic Package Manager. Search for the word ndiswrapper, right-click to install the appropriate packages, then click Apply to install it.

It says that is already installed but my wireless card is still not working!

---

### Post by dmorand on 2007-07-16
I used this guide to get my wireless working in my laptop:

[https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff](https://help.ubuntu.com/community/WifiDocs/Driver/bcm43xx/Feisty_No-Fluff)

---

### Post by ArizonaSteve on 2007-07-16
OK, now it's working, sort of.  It can connect to my FON router, I can browse the web and if I click the network icon once it shows the wireless network. 
HOWEVER, if I click on Manual Configuration it opens a window called Network Settings and doesn't show any connections!  If I right click the network icon and select Connection Information a window opens called Connection Information that says the Active Connection is the Wired Ethernet (eth0) that's no longer connected!  This is really screwed up!

---

### Post by dmorand on 2007-07-16
I use wifi radar.  You can install it from Synaptic.

---

### Post by stchman on 2007-07-16
> **dscott60 said:**
> Well after spending several days trying to get my Zonet ZEW2500P working, I've come to the conclusion that it just won't work in Ubuntu.  And judging from the number of posts in here from people that can't get their wireless adapters to work, I'm guessing it has problems with just about all wireless adapters.  Unless you're a LINUX genius and a troubleshooting god.  Too bad.  With more and more people going wireless that doesn't bode well for Ubuntu.  I had high hopes for Ubuntu and bragged about it to all of my friends.  Guess it's back to windows for this noob.

My Atheros wireless card works very well in Ubuntu.

---

### Post by cavaliercrazy on 2007-07-16
Hi,

ive spent the last 2 days trying to get my MA111 wireless adapter to work. and all of the forums i have found and tried to follow the directions on just confused me. im a linux noob. 

im using a compaq presario 1200. and currently have a wired connection througha d-link adapter. 

any help in getting a driver or whatever i need to do will be greatly appreciated. 

thanks.

---

### Post by C.S.Cameron on 2007-07-16
I know Ubuntu is not worthless for wireless, but I suspect networkmanager is.
Cork

---

### Post by ArizonaSteve on 2007-07-16
There isn't anything called wifi radar.  Any other ideas?

---

### Post by aysiu on 2007-07-16
> **C.S.Cameron said:**
> I know Ubuntu is not worthless for wireless, but I suspect networkmanager is.
Cork
Can't speak for anyone else, but Network Manager works for me. I have fewer wireless problems in Ubuntu than I do in WIndows or my wife does on her Mac.

---

### Post by richie42 on 2007-07-16
how does UBUNTU go for the USB wifi cards

---

### Post by ArizonaSteve on 2007-07-16
Finally found wifi radar, it was really well hidden! I had to change the search option to Name
or something like that. 
Nothing is ever easy with Linux is it.
Now when I tell it to connect it wants to configure a profile or else it won't work!
I have no idea what to put in all those empty boxes!
Now it says it's connected but with NO IP address! Am I supposed to guess what it is and
put a number in there?  This is ridiculous!

---

### Post by dscott60 on 2007-07-16
Actually, I eventually got wireless to work with my cheapo Zonet usb wireless.  I used the instructions and figured it out.  I agree that they are confusing.  As were almost all of the Ubuntu instructions.

The sad thing is, I ended up taking Ubuntu off my computer and loading Vista.  Why?  No support for my video card.  It was making me go blind because I could only get 60Hz refresh.  It's a shame because I only use this computer for the internet and email, and Ubuntu was perfect except for that one thing.  I HATED giving Microsoft yet another $118 for Vista, but it was a last resort.  

Ubuntu is so close to being a viable OS for the average user.  Initially, I talked it up bigtime to my family and coworkers.  If only it had a little bit better support for hardware.  i.e., drivers.  And unfortunately, I found the help in this forum to be geared towards people much more experienced with LINUX operating systems than I am.  What a shame.

---

### Post by houstonbofh on 2007-07-16
Actually, this is just about the most noob friendly technical forum I have ever been on...  I have been doing this for 25 years, and it never ceases to amaze me how the uninformed try to make there poor choices my problem.  Just a few minutes before purchase saves a lot of time.  Actually, tossing away a perfectly good **Windows** WiFi card and getting one that works native with Linux is a good plan, if your sanity has any value at all.  However, calling me names is **Not** a way to get me to help you.

My best advice is to print out the list at [http://ralink.rapla.net/](http://ralink.rapla.net/) and go to the local computer store. (I use Fry's)  I usually can find 3 or 4 from it, and one is usually under $50.  Then you plug it in and it just works.  No CD, or driver download.  (Do that in windows!)

---

### Post by eldepeche on 2007-07-17
> **ArizonaSteve said:**
> The fact that a few of you have Intel cards that work doesn't help everyone else out there and there's no point in telling someone to use the NDISwrapper since it's nearly impossible to install anything in Linux.  I've never been able to do it at all except with Redhat package manager.
All the Linux geeks need to get out of their D&D fantasy world and try to get wireless cards and things like that to work in the real world the same as in Windows or Linux will never catch on!

Man, you're lucky people on this primarily (totally?) VOLUNTEER TECHNICAL SUPPORT FORUM are way nicer than I am, because I definitely wouldn't bother helping someone who just acted like a jerk to me, as you are.

---

### Post by sw1995 on 2007-07-17
I was able to get my laptop's modem working in Ubuntu, so I am convinced anything is possible:)

-S

---

### Post by bradmayne on 2007-07-17
i actually have two wireless cards that work great! I have an atheros wireless that came with my laptop and I have an old orinoco gold classic pcm/cia card also. The atheros wireless that is integrated into my lappy took a little messing with and i had to get madwifi-tools from synaptic.  If your having problems let me know what kind of chipset you have with this command from bash: lspci -v

---

### Post by playme123 on 2007-07-17
Ive got to laptops sitting about one running xp and one running win98, but as im new am going to wait till Im a bit more knoweldgable before putting on ubuntu, as  you will only have me whinging on the forums that I can get me wireless to work

---

### Post by ArizonaSteve on 2007-07-17
Demorand, how were you able to use wifi radar?  All it seems to be able to do is see the wifi hotspots but it can't connect.  It's not able to acquire an IP address or anything so it won't work.  At the same time the built-in wireless networking was able to acquire an IP address and connect while wifi radar just sits there doing nothing.

---

### Post by dmorand on 2007-07-17
> **ArizonaSteve said:**
> Demorand, how were you able to use wifi radar?  All it seems to be able to do is see the wifi hotspots but it can't connect.  It's not able to acquire an IP address or anything so it won't work.  At the same time the built-in wireless networking was able to acquire an IP address and connect while wifi radar just sits there doing nothing.

I really just followed this guide:
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

I then rebooted, and it saw my wireless cards.  I'm actually connecting from the network manager on the top right of the screen.  I forget the actual name of it.  What happens when you connect that way?  Are you able to access the internet?

---

### Post by ArizonaSteve on 2007-07-17
Playme123, try the Wubi method of installing Ubuntu in Windows.  It's pretty much all automatic and if it doesn't work you can always uninstall it. The only hangup seems to be the wireless networking.  Wubi automatically installed the NDISwrapper and then wireless should work EXCEPT it doesn't tell you anywhere that it's been installed and the status window says there's no connection so the only way to find out if it works or not is to try it.

---

### Post by ArizonaSteve on 2007-07-17
> **dmorand said:**
> I really just followed this guide:
[https://help.ubuntu.com/community/Wi...eisty_No-Fluff](https://help.ubuntu.com/community/Wi...eisty_No-Fluff)

I then rebooted, and it saw my wireless cards.  I'm actually connecting from the network manager on the top right of the screen.  I forget the actual name of it.  What happens when you connect that way?  Are you able to access the internet?

I'm also connected using the network manager on the top right of the screen. Couldn't get wifi radar to do anything.

---

### Post by regomodo on 2007-07-17
short answer. no.

of the 2 cards i bought randomly both work. 1 out of the box but not with wpa support. neither were hard to setup

---

### Post by gn2 on 2007-07-17
I have a D-Link DWL-650+ EU.B4 which has a Texas Instruments ACX100 chipset.
It has worked flawlessly "out of the box" with every version of Ubuntu since I started with 5.10.

On my UK ADSL Max connection it typically gives a throughput of 6-7mbps, whereas using W2kPro, with the latest driver available it gives an absolute maximum of 4.4mbps, typically 3.5-4mbps.

So Ubuntu rocks for wireless, it's a sad fact however that not all wireless hardware has Linux driver support, which is most definitely the fault of the maker, not Ubuntu.

---

### Post by cavaliercrazy on 2007-07-17
> **cavaliercrazy said:**
> Hi,

ive spent the last 2 days trying to get my MA111 wireless adapter to work. and all of the forums i have found and tried to follow the directions on just confused me. im a linux noob. 

im using a compaq presario 1200. and currently have a wired connection througha d-link adapter. 

any help in getting a driver or whatever i need to do will be greatly appreciated. 

thanks.


Allright. felt i should update this. i got the wireless MA111 USB adapter to finally work. 

what i ended up doing was using automatix to download wine. which allowed me to emulate the driver. after i got the wireless noticed. now it work with no problems at all. 

this method is much easier then building the kernel drivers and using all the prism_2 stuff.

---

### Post by cavaliercrazy on 2007-07-17
> **cavaliercrazy said:**
> Allright. felt i should update this. i got the wireless MA111 USB adapter to finally work. 

what i ended up doing was using automatix to download wine. which allowed me to emulate the driver. after i got the wireless noticed. now it work with no problems at all. 

this method is much easier then building the kernel drivers and using all the prism_2 stuff.


i also had the ndiswrappers installed not sure if the helped. but i think they did.

---

