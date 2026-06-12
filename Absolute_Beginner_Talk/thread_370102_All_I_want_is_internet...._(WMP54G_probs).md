---
title: "All I want is internet.... (WMP54G probs)"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by sylathnie on 2007-02-25
<rant>Wow. Linux install is a pain.</rant>
I am trying to get my Linksys WMP54G V4.1 to work. I have the ndiswrapper gz file on my Desktop in ubuntu. I did the tar command and now I have a directory on my desktop. I changed to that directory and typed "make distclean" per wiki instructions, a bunch of lines  scroll by. I then type "make" (again per wiki instructions) and a bunch more lines scroll by. There are a bunch of lines that show errors and warnings. Are those bad? Can I continue? If they are bad what am I to do about them?

Help!

---

### Post by overdrank on 2007-02-25
> **sylathnie said:**
> <rant>Wow. Linux install is a pain.</rant>
I am trying to get my Linksys WMP54G V4.1 to work. I have the ndiswrapper gz file on my Desktop in ubuntu. I did the tar command and now I have a directory on my desktop. I changed to that directory and typed "make distclean" per wiki instructions, a bunch of lines  scroll by. I then type "make" (again per wiki instructions) and a bunch more lines scroll by. There are a bunch of lines that show errors and warnings. Are those bad? Can I continue? If they are bad what am I to do about them?

Help!
Hi I am new also to ubuntu, but what I have seen in the past is if you can post more about what verson of ubuntu and more information on your system. I am sure you will get the help you need.

---

### Post by sylathnie on 2007-02-25
How exactly do I find out what version of Ubuntu I have? And what system information exactly is needed? The wireless card is a Linksys WMP54G V4.1. Is my motherboard/cpu/gfx/powersupply/mem/case/HD pertinent? (I honestly have no idea what matters with what).
Thanks for the reply. I will provide whatever I can.

---

### Post by overdrank on 2007-02-25
> **sylathnie said:**
> How exactly do I find out what version of Ubuntu I have? And what system information exactly is needed? The wireless card is a Linksys WMP54G V4.1. Is my motherboard/cpu/gfx/powersupply/mem/case/HD pertinent? (I honestly have no idea what matters with what).
Thanks for the reply. I will provide whatever I can.
Hi, did you obtain ubuntu, the live dvd or the alternate cd? Specs like AMD or Intel. Like I said I am new to ubuntu also but this info has helped in the past like what you see in my signiture below.

---

### Post by Maestro23 on 2007-02-25
If you keyword search "Linksys WMP54G", you will find threads discussing it.  Some are success stories and might provide some help for you.

---

### Post by soul814 on 2007-02-25
If you go to SYSTEM >> ABOUT UBUNTU, it will say something like this

> 
Thank you for your interest in Ubuntu 6.06 LTS
                - the Dapper Drake - released in June 2006.


--> I agree that setting up wireless is a pain. I installed edgy yesterday and I couldn't get it working so I tried to use Dapper instead and its working now but my card isn't compatiable with a secure wireless network =(, but I tested it on an open network and it works.

---

### Post by infol on 2007-02-25
try typing ```
uname -r
``` in a terminal and post the output from that command (it's the kernel version of your system - with that information, it's possible to determine what type of processor you have, and whether you have dapper, edgy or feisty ...unless you have tweaked your system manually..)

it will also help if you know what motherboard you have, and which chipset your linksys adapter uses..

---

### Post by sylathnie on 2007-02-25
Thanks for all the replies. I did a search and found lots of threads I tried a few of the things that people had suggested but they all failed in one way or another. Perhaps a better title for this thread would have been. Why doesn't ndiswrapper compile (that is what make is doing isn't it?)
I am going to re-boot now and attempt to ascertain what version of ubuntu I have. (I'm very glad I didn't kill my windows partition now...) Be back shortly.

---

### Post by Maestro23 on 2007-02-25
> **sylathnie said:**
> Thanks for all the replies. I did a search and found lots of threads I tried a few of the things that people had suggested but they all failed in one way or another. Perhaps a better title for this thread would have been. Why doesn't ndiswrapper compile (that is what make is doing isn't it?)
I am going to re-boot now and attempt to ascertain what version of ubuntu I have. (I'm very glad I didn't kill my windows partition now...) Be back shortly.

Do you have [COLOR="Red"]build-essential[/COLOR] installed? Need it for working with source stuff. If not:

> sudo aptitude install build-essential


---

### Post by sylathnie on 2007-02-25
Ok my Ubuntu version is 6.10 Edgy Eft.  Should I try Dapper?

How do I check if I have build essentials installed?

My motherboard is a Gigabyte GA-K8N Pro-SLI.

The chipset on the wireless card is RT61.

Ok I think that answers everything.

---

### Post by undertakingyou on 2007-02-25
Run the command that maestro said.  If you have it, it won't let you install.  Then go the directory and to the ./configure then make and then make install.  Edgy is fine, the other shouldn't be a problem.

---

### Post by Maestro23 on 2007-02-25
> **sylathnie said:**
> Ok my Ubuntu version is 6.10 Edgy Eft.  Should I try Dapper?

How do I check if I have build essentials installed?

My motherboard is a Gigabyte GA-K8N Pro-SLI.

The chipset on the wireless card is RT61.

Ok I think that answers everything.

Run the command for installing build essential.  Then do what the guy above me said.

Also, I saw some post regarding that RT61 chipset when I ran that keyword search on your router earlier.  Might check those out again.

---

### Post by sylathnie on 2007-02-25
Ok sudo aptitude install build-essential displays a bunch of things  including "Couldn't find any packages whose name...."
Any thoughts?

---

### Post by sylathnie on 2007-02-25
Well I'm out of time again. I will be back again later to work on this some more. Thanks for all the help so far all!

---

### Post by houstonbofh on 2007-02-25
Start here.
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

It sounds like you need to add the repositories, and download the indexes.  Or is the WiFi card you only way to the Internet?

Note that almost all of the WiFi problem posts I see are Linksys WMP54Gs.  Buying a supported card will save you time.

---

### Post by sylathnie on 2007-02-25
> **houstonbofh said:**
> Start here.
[http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)

It sounds like you need to add the repositories, and download the indexes.  Or is the WiFi card you only way to the Internet?

Note that almost all of the WiFi problem posts I see are Linksys WMP54Gs.  Buying a supported card will save you time.

I'm not sure what that first sentence means at all.

I just read through your link. This all assumes that I have a working internet connection. WiFi is my only way to the internet right now. I think I found a link for build essentials. I will download it and give it a try.

I purchased this card when I was just using windows and compatability wasn't an issue. Others have gotten it working but their methods don't seem to work for me.

Ok downloading and rebooting. I'll be back in a while to ask more questions!

---

### Post by sylathnie on 2007-02-25
Ok downloaded the .deb package for build-essentials and guess what.... it didn't install either!
It gives me a "Dependency is not satisfiable: librc6-dev|libc-dev"
Is this something else I need to download and install or is this a totally different error now?

---

### Post by Maestro23 on 2007-02-25
> **sylathnie said:**
> Ok downloaded the .deb package for build-essentials and guess what.... it didn't install either!
It gives me a "Dependency is not satisfiable: librc6-dev|libc-dev"
Is this something else I need to download and install or is this a totally different error now?

Yeah, it needs the lib6c-dev libraries.

---

### Post by captgadget on 2007-02-25
Hey, I'm new to this as well so be patient. I have the same card you do except my is v1.2. I used this website here and I finally got it to work and it works well. I had to go back and do some of the steps over, but never the less I got it to working. Hang in there.

[http://www.ubuntuforums.org/showthread.php?t=340689&highlight=bcm4306](http://www.ubuntuforums.org/showthread.php?t=340689&highlight=bcm4306)

---

### Post by ramjet_1953 on 2007-02-26
Hi, slyathnie!

This information will not help you to get your wireless notworking going, but instead I hope it will explain to you why this and other hardware issues occur, when trying to install a Linux operating system.

Firstly, hardware manufacturers often do not "open Source" their drivers. The reason that they give for this is that if they were to do this, it would also open-up the hardware design to their competitors.

Secondly some hardware manufacturers seem to go out of their way to lock their hardware into the Windows operating system.

It takes many hours of time and resources for hackers to reverse-engineer a driver for a particular piece of hardware to work with Linux and they do it for free.

To sum up, the point that I am trying to make is that often people become frustrated when they can't get something to work and then take out their frustration by blaming Linux. The reality is that this anger is mis-directed and should be pointed at hardware manufacturers, who want to make you use Windows and not have the freedom to choose.

Regards,
Roger 8)

---

### Post by houstonbofh on 2007-02-26
> **sylathnie said:**
> I'm not sure what that first sentence means at all.
That ain't good... :(   Repositories are the online keepers of the software.  They are divided into catagories.  "Main" is the fully supported stuff.  "Universe" is not as supported, and has much of the good stuff...  Once you add a repository, you have to reload the software indexes to see what stuff they have.  Since you have no internet, your only software is on the CD.
> **sylathnie said:**
> I just read through your link. This all assumes that I have a working internet connection. WiFi is my only way to the internet right now. I think I found a link for build essentials. I will download it and give it a try.

I purchased this card when I was just using windows and compatability wasn't an issue. Others have gotten it working but their methods don't seem to work for me.
I have been in that boat with you.  Same card, same conditions, and same problems. But I have experience, and guess what I did?  I bought a card.  After one day working at it, I realized I was loosing money by **not** buying the card.  Unless you can get wired internet to install all the software, you will go insane trying to meet all the dependencies.

Good luck!

---

### Post by paculz on 2007-02-26
Ok,

Quick and easy for linksys wireless users:

1. Go to synaptec pacakge manager and search for ndiswrapper. Check all and install it.
2. In synaptec package manager, search for 'ndisgtk' (make sure you have enabled the multiverse and universe option in pacakge mangement).

Now you would go to Administration> wireless drivers and there you will browse and select you LVMDNS.inf filr from your linksys drivers cd. Click ok and follw the procedure.. you will find you have internet and wireles working all ok.

Note: everything is explained from memory as Iam not on my machine at the moment. But Im sure you shall find your way through.

---

### Post by paculz on 2007-02-26
--------------------------------------------------------------------------------

Ok,

Quick and easy for linksys wireless users:

1. Go to synaptec pacakge manager and search for ndiswrapper. Check all and install it.
2. In synaptec package manager, search for 'ndisgtk' (make sure you have enabled the multiverse and universe option in pacakge mangement).

Now you would go to Administration> wireless drivers and there you will browse and select you LVMDNS.inf filr from your linksys drivers cd. Click ok and follw the procedure.. you will find you have internet and wireles working all ok.

Note: everything is explained from memory as Iam not on my machine at the moment. But Im sure you shall find your way through.
__________________

---

### Post by Pikestaff on 2007-04-07
> **sylathnie said:**
> Ok my Ubuntu version is 6.10 Edgy Eft.  Should I try Dapper?

How do I check if I have build essentials installed?

My motherboard is a Gigabyte GA-K8N Pro-SLI.

The chipset on the wireless card is RT61.

Ok I think that answers everything.

I know this is a late response, but your card happens to be the same one I have and it runs perfectly fine, out of the box in Dapper (at least, it did for me.)  I've had no success getting it to work in Edgy, however.  So if you have to stick with that card, you may want to use Dapper.

---

### Post by ushills on 2007-04-11
I have exactly the same card and got it to work in Edgy following these instructions:

Follow the walk-though exactly:

[http://ubuntuforums.org/showthread.php?t=296822]("http://ubuntuforums.org/showthread.php?t=296822")

---

### Post by pmenefee on 2007-04-16
> **paculz said:**
> --------------------------------------------------------------------------------

Ok,

Quick and easy for linksys wireless users:

1. Go to synaptec pacakge manager and search for ndiswrapper. Check all and install it.
2. In synaptec package manager, search for 'ndisgtk' (make sure you have enabled the multiverse and universe option in pacakge mangement).

Now you would go to Administration> wireless drivers and there you will browse and select you LVMDNS.inf filr from your linksys drivers cd. Click ok and follw the procedure.. you will find you have internet and wireles working all ok.

Note: everything is explained from memory as Iam not on my machine at the moment. But Im sure you shall find your way through.
__________________

I'm an absolute new Ubuntu user, and quite frustrated.  I'm trying to install the same linksys wireless card.  I don't want to play with Ubuntu, I just want to use it.  I'm using 7.04, upgraded using the upgrade cd, downloaded and burned.

I tried your suggestion and Ubuntu says to insert the cd into the drive to install ndiswrapper.  Ubuntu can't find the files and won't respond, as if it doesn't recognize the drive, but I can search the drive and find the files on the cd.  It says please insert the CD into the drive and I do, and click OK, and get no response from the install frame.

---

### Post by pmenefee on 2007-04-19
Just re-installed 7.04 after it crashed.  I had beta in, but now I have the new release.

The OS sees my wireless network, but will not connect.  No security is installed on the network.  ??

---

### Post by Comzee on 2007-04-19
I thought windows was easy with wireless. Just install driver and windows wireless manager was great.
With Linux, I didn't have to do anything. It just worked, it's odd how many people have trouble with it.

---

### Post by neodarksaver on 2007-04-19
is ur ubuntu 64-bit or 32-bit, because i had problems with that using openSUSE 64-bit.

---

### Post by houstonbofh on 2007-04-19
> **Comzee said:**
> I thought windows was easy with wireless. Just install driver and windows wireless manager was great.
With Linux, I didn't have to do anything. It just worked, it's odd how many people have trouble with it.
It all depends on the card.  Some cards have many versions with different chipsets, but the same model number.  The Linksys WMP54G is one of those.

---

### Post by pmenefee on 2007-04-20
> **pmenefee said:**
> Just re-installed 7.04 after it crashed.  I had beta in, but now I have the new release.

The OS sees my wireless network, but will not connect.  No security is installed on the network.  ??

It's me again reporting success!  After I re-installed 7.04 my system would see the network, but would not get on the network.
I went in found the wireless network under systems and set it up there.  Works now.  Amazing.

I tried the same thing on the upgrade to feisty,  but it seemed to work when I just re-installed.

Glad to see it working.:)

---

### Post by ushills on 2007-04-23
As posted previously I managed to get this card to work with Edgy, I have tried the Live CD version of Fiesty and although I can enter all of the settings in network manager I cannot ping the router on 192.168.1.1.

I use WPA encryption for my connection.

Should Fiesty work with this card out of the box, if not until a fix comes out I will have to stick with Edgy as I cannot connect to internet without wireless.

Ian

---

