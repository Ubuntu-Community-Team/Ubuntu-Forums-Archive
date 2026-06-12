---
title: "A beginners frustration with Ubuntu. Help would be appreciated."
date: 2007-06-27
forum: Absolute Beginner Talk
---

### Post by Bripe Klmun on 2007-06-27
Greetings and salutations!

I'm not exactly sure what I'm hoping to get out of this post, but I think I'll post it anyway in hopes that someone has either had similar problems and has good solutions, or can simply just get me on the right track with a kick in the ****.

I got an extra computer from a friend of mine about a month and a half or two ago. It's a Dell Inspiron 1300 - current specs are:

Screen: 15.4" WXGA (800 x 1280) screen
Size: 14" x 10.5" x 1.41", 6.7 pounds
Ports: 3 USB 2.0, VGA out, Modem RJ-11, Ethernet RJ-45, audio line-out (for speakers headphones), external microphone port, ExpressCard 34 slot
OS: Ubuntu 7.04 (Feisty Fawn)
CPU: Intel Pentium M (1.7GHz)
Memory: 1003.5 MB
Graphic: Mobile 915GM/GMS/910GML Express Graphics Controller
Network: PRO/Wireless 2200BG Network Connection
Available Disk Space: 30.8 GB

When I got it, I decided to try something different - our other computers are all running XP, so I installed Ubuntu 7.04 on it right after I got it. I downloaded it and made a CD myself for the first install.

Right off the bat, I loved it - though it took some getting used to. I recieved perfect wireless connections without any problems for about two weeks - then *poof*. Nothing. I couldn't pick up anything at all, so I searched far and wide for solutions. None of the workarounds to get wireless worked for me - either due to them actually not working for everyone or because of my newness to Ubuntu. I'm far from a dummy when it comes to Windows, having used it regularly for 13 or 14 years... but this frustrated me so much I just gave up.

To try and see if a fresh install would work, I installed from the free CD that I ordered online - again, no such luck. Since I have wired connections everywhere I go, I figured that it'd just be something I could live with.

About two weeks ago, whenever I would go to a site with Flash content - say YouTube or another Flash-heavy site, Firefox would crash. Again, I looked all over for a decent workaround, but found that none of them were that great (ie, they didn't work). I installed Opera to see if there was a difference, but there was not. Finally, yesterday I backed up everything and did another fresh install. The crashing problem with Flash was gone in Firefox - however when I restarted the system yesterday afternoon - it would not load Ubuntu again (it is the only OS on the disk). I got the basic Dell bootscreen, the short system notice, and then the cursor just hung on the screen for about 3 hours - until I tried rebooting again. Nothing - same problem.

So, I *again* reinstalled from the CD I had ordered - this time, after the installation was complete and I clicked "restart now" - it hung again and would not restart. I finally shut it down after 45 minutes and restarted it, to find that there was an error and Ubuntu would not load.

Again I reinstalled Ubuntu and everything went fine - I downloaded all of the updates and such and installed all of the plugins and missing files for Firefox - and aside from the wireless still not working, everything is good again. Flash videos only crash Firefox about 25% of the time now, so I'll take that over anything else.

What the heck is that all about, anyway? Am I the only one that has gone though all of this nonsense? I was very close to giving up on Ubuntu and buying a copy of Windows - but I love the package so much I just wanted to keep trying.

There is nothing wrong with the Dell itself - I wanted to add this in case it came up later. I've checked and checked to make sure there were no errors there.

I'd love to get a good solution to my wireless issue and the Flash issue with Firefox - and hope that my system remains stable for good. Is that too much to ask, or am I just dealing with the normal problems of Ubuntu?

Thanks for reading... any advice, help, or whatever is appreciated.

---

### Post by tcoffeep on 2007-06-27
I've read in alot of places that Ubuntu isn't exactly the most friendly with wireless connections. I've never had firefox issues with flash after downloading the restricted-files, and everything.

Although I have had some reinstallation problems. I know where you're coming from on that angle.

---

### Post by Swankyman on 2007-06-27
Hi there,

A few things to think about:

Is it a hardware problem? (thus meaning you get random crashes all the time)

Is the computer over heating i.e. do the fans run all the time or never at all? (are they full of dust?)

Is the memory any good? Try a full mem check with the live cd!!

Did what ever was installed on it run perfectly fine before you installed Ubuntu?

Rich

---

### Post by Bripe Klmun on 2007-06-27
Thanks for the replies, guys.

Rich, to answer your questions:

Is it a hardware problem? (thus meaning you get random crashes all the time)

- Nope. The hardware is tip-top

Is the computer over heating i.e. do the fans run all the time or never at all? (are they full of dust?)

- Temperature is perfect

Is the memory any good? Try a full mem check with the live cd!!

- Been there and done that yesterday - memory is fine

Did what ever was installed on it run perfectly fine before you installed Ubuntu?

- It had Vista installed on it and ran perfectly (as perfect as Vista can get right now)

Now - as a follow up, I've discovered just now that I actually can get wireless access without any difficulty whatsoever. After all I've been through, I have to ask "those in the know" if there is actually a possibility that the CDs that I have used for installing (the last two days I have used 2 different) actually contain slight differences?

---

### Post by Pinger05 on 2007-06-27
Bripe,

     I hate to keep harping on an issue but I am leaning  in the hardware direction along with Rich.  Since you checked the memory I would try checking the Power Supply too.  The fastest way to check that would be to replace the Power Supply with a new one and see if you get the same problems.  You can take the PS to a comptuer repair shop to have it checked out, but that check would cost as much as buying a new one.

     I have heard of L2 cache going bad, but if the power supply is good then I am voting that it is a computer gremlin.

---

### Post by paradoxni on 2007-06-27
I will hazard a guess that you have an onboard sound card, probably a realtek / intel HD? if so I have the exact same issue with firefox and flash, videos will play ok, but if i hit "home", "back" or close the window sometimes firefox will crash. 

this problem has been well documented, but so far it has not been fixed. It seems to be related to the realtek sound card somehow as people have disabled onboard sound and/or added a pci soundcard and solved the issue this way.

---

### Post by Nekiruhs on 2007-06-27
Yes, its possible. Canonical could have remastered the ISO with some of the updates. Maybe an update killed your WiFi

---

### Post by Ziox on 2007-06-27
> **Nekiruhs said:**
> Yes, its possible. Canonical could have remastered the ISO with some of the updates. Maybe an update killed your WiFi

I seriously doubt your statement, because each Ubuntu release has a feature freeze date that's couple weeks before the final release.  Which means no new updates/packages will be added to the final products, that's why whenever you install a new system, you always have to update your system, no matter when you downloaded/bought the ISO/DVD. 

Although, Ubuntu did have an 6.06.1 LTS update release, but they always notify those who downloads about the differences of each release.

---

### Post by Nekiruhs on 2007-06-27
> **Ziox said:**
> I seriously doubt your statement, because each Ubuntu release has a feature freeze date that's couple weeks before the final release.  Which means no new updates/packages will be added to the final products, that's why whenever you install a new system, you always have to update your system, no matter when you downloaded/bought the ISO/DVD. 

Although, Ubuntu did have an 6.06.1 LTS update release, but they always notify those who downloads about the differences of each release.
I said could. I don't know the inner workings of Canonical, so forgive me for my ignorance.

---

### Post by paradoxni on 2007-06-27
as for your wireless issue..what is the output when you run this from terminal:

```
iwconfig
```

---

### Post by Zannax on 2007-06-27
For wireless working only sometimes I had a similar problem (I've seen it's common) with my router: wireless was ok because I could access router (192.168.1.1) from FF, but I couldn't access any web site.
That was a problem of DNS assignment and I had to configure the router differently...

So, check if you can see your router at least, if not check if the "wireless interface" is corrctly configured (ESSID, key) and up.
Although I guess you've tried these basic steps...

---

### Post by JAS510 on 2007-06-27
Bripe,

I'm also a newb at this game.  I've had a similar problem w/ flash and my wireless card.  I gotta AMD64 and for some reason AMD's are the step child for this O.S.  Nothing works for me.  I had loaded a script just to get the flash going.  When i loaded the flash script my browser started to load pages really slow (really hated that).  Ubuntu doesnt recognize my USB flash drive, no icon, nothing. (i've asked for help searched the net and still no answers) and to put the icing on the cake, my wireless signal dropped.  It recongnized my card (thankd god) but it just cant connect to the net!!!!!!!!!!!!!!!  I figured since i'm a noob, i'll load easyubuntu to make things work.  Nope! Once you load easyubuntu, YOU CANT remove the software.  I'm just basically fed up w/ this O.S. 

SO to sum it up, WE'RE IN THE SAME BOAT.  

Do you have AMD64?

---

### Post by Bripe Klmun on 2007-06-27
Thanks loads for the input, guys. I really appreciate it.

Pinger05 - I hope it doesn't come to something that extreme. If I have more troubles, I will have to go that route, as I would very much like to continue using ubuntu and am in no hurry to go back to Windoze whatsoever.

JAS510 - no, I don't have an AMD64, I've got a Pentium M

Well, the wireless issue has been resolved (on it's own), para, but since you asked:

lo        no wireless extensions.

eth0      no wireless extensions.

eth1      unassociated  ESSID:""  
          Mode:Managed  Channel=0  Access Point: Not-Associated   
          Bit Rate:0 kb/s   Tx-Power=20 dBm   Sensitivity=8/0  
          Retry limit:7   RTS thr: off   Fragment thr: off
          Power Management: off
          Link Quality:0  Signal level:0  Noise level: 0
          Rx invalid nwid: 0  Rx invalid crypt: 0  Rx invalid frag: 0
          Tx excessive retries: 0  Invalid misc: 0   Missed beacon: 0

Now, if I can only figure out how to get Ubuntu to recognize my Sony DSC T10 and my Sony Ericsson K610 - I'll be good to go. Any suggestions there, while I have you all as a captive audience?

---

### Post by Bripe Klmun on 2007-06-27
Scratch the last two - my camera and phone are now easily discovered, which has never happened with ubuntu before. This rocks! :)

---

### Post by ITdrummer on 2007-06-27
I honestly thing that there are "Ubuntu Gods"  watching new Ubuntu users to see if they will stick with it.  It seems like every issue i have read about in these forums eventually....just work.  The gods are watching, waiting, until the very last moment the users are about fed up](*,), then they make everything work fine!  The gods are making sure that the noobs(myself included) realize that there will be work involved in installing a new OS.It wont just be handed to them.  

Just an observation! :smile:

---

### Post by paradoxni on 2007-06-27
the reason i love linux (especially ubuntu) is that you have to roll up your sleeves and do some hardwork sometime, you learn from the experience and over all it makes it more enjoyable (althou sometimes it doesnt seem so at the time)

---

### Post by ITdrummer on 2007-06-27
> **paradoxni said:**
> the reason i love linux (especially ubuntu) is that you have to roll up your sleeves and do some hardwork sometime, you learn from the experience and over all it makes it more enjoyable (althou sometimes it doesnt seem so at the time)

I agree 100%.  I have been using Ubuntu/linux for a couple of weeks now and the road has not been easy.  It has totally sucked at times.  Saying that makes me feel like ive accomplished something.  Not everyone could install Ubuntu and get everything working correctly. All of my problems now have been fixed(thanks to the peeps in this bad a$$ forum): but i know that there will be more problems to face.  I love it because it is a challenge and will give you whatever you put into it.

---

### Post by bokono on 2007-07-05
I have the same wireless controller in my hp pavilion and I was able to fix the issue using the wlassistant and wireless network drivers ndiswrapper. I'm also new to ubuntu so I bought a book. There are quite a few good ones on the market.

---

