---
title: "Easy Internet connection for Newbies"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by richbarna on 2006-04-22
If you know zero about Linux /Computers in general and you want to get an internet connection, this is in my honest opinion the easy way.
1st - You are probably dual booting with Windows Xp because you still haven't worked out how to get Linux to do everything you want yet.
2nd - You probably have a USB modem that comes free from your ISP.

I know this is a general assumption, but after having my own problems and spending many hours reading forums, this seems to be the majority.

Solution:- 
1. Get rid of the USB modem they are a pain in the arse if you know nothing   about Linux.
2. Get a router, I have tried new and second hand ( I would however recommend the router that your ISP supplies )
3. Download the router installation/ setup software from yor ISP's web site and configure the router from XP then test and make sure you have an internet connection.
4. Install your chosen Linux distro, (for beginners I recommend Kubuntu or Xandros) 
Both these distros will detect and configure your internet connection step by step or in most cases automatically.

Voila!! you are online in Linux, now you can access the forums and all the help you need without having to resort to searching for all the information from Xp and then booting Linux to impliment the changes.

A message to experienced Linux users :-
You may disagree with this approach, but IMHO it's the easiest, It was advice given to me by a close friend.
You would be surprised at how many newbies are still posting on forums asking about how to get a USB modem to work.
These people get frustrated and go back to windows, depriving them of an amazing experience and amazing distros.

Rich S

---

### Post by Malac on 2006-05-05
I totally agree with the above post, forget USB modems they really are unbelievably difficult to set up.
Even if you know what you are doing, which I don't. :confused:

:-({|= You run through all the steps on the various websites you find and download several drivers to try, still nothing.

Most of the time the instructions fail at some point and you're left with no option but to try and remove the files manually.

Even when they do seem to succeed and they get to the last step of installation.
You reboot, run some command like startADSL and lo the modem lights do stay dark #-o.

Trouble is you ask most UK ISP's for a different modem than USB and they just say sorry that's what you get with the deal. Anything else and you'll have to pay extra.

Then you have to try and figure out is it worth buying a seperate one and trying to set all the protocols up so the ISP Servers will recognise the bloomin' thing. AARGH!

I thought USB was supposed to be a "standard" if that were the case surely it should be easier than this.
After all it's only an interface like the Cat5E interface.
Yet hook up via ethernet is what you see everywhere.

Until ALL linux distros give USB modems serious consideration it will never get sorted.

:idea: Maybe if everyone who works on the various versions of Linux could all get together and work on the kernel for a couple of months? :razz:
If there is a request section stick this in there.

Anyway I'm not giving up, one way or another I will get this damn modem to work. Where is that manual?????? :)

---

### Post by Malac on 2006-05-05
:idea: OR maybe if I just soldered it to the motherboard. ;)

---

### Post by a_0000 on 2006-05-05
What if your a newbie and your only means of getting online is through a USB wireless adaptor?... :(

---

### Post by jethro10 on 2006-05-05
[QUOTE=a_0000]What if your a newbie and your only means of getting online is through a USB wireless adaptor?... :([/QUOTE]
I used a $30 wireless bridge connected to my normal internal network card, much less hassle and works every time.

J

---

### Post by a_0000 on 2006-05-05
[QUOTE=jethro10]I used a $30 wireless bridge connected to my normal internal network card, much less hassle and works every time.

J[/QUOTE]

please provide more info, more details... how does this work?!? :o

---

### Post by Malac on 2006-05-05
The problem I have is that I can see the modem listed in the device manager (which is possibly more annoying than not at all), it even lists it as USB ADSL Modem.

But there are no instructions on where to go from there, if it is not an option in the **various** "standard"  connection setup programs, what's a newbie supposed to do.

My understanding is sadly lacking on linux and hardware but if it's listed by the OS why is it not an option that is on offer. i.e. "Which device do you want to connect through?"

If anyone can give me a URL to a description of what is going on in the various levels of the process between hardware and software it would possibly help as I hate just not knowing.

I assume it is Hardware -> OS -> [Driver] -> GUI and it's at the [Driver] stage I'm getting stuck.

One thing I don't understand is why the firmware on the modem needs changing.

Anyway back to the Ubuntu Box.:)

---

### Post by Malac on 2006-05-15
:DOkay I finally managed to extract the firmware from the cnxetu.sys file and get the firmware to load into the Zoom modem.:D

At last I have a Green:mrgreen: link light but now what do I do.

The device is still not appearing in the network list with eth0 and ppp0.
Or, if it's supposed to be mapped as ppp0 it isn't being detected.:confused: ](*,)

Oh well keep plugging away at it.
"Brute Force and Ignorance" may win the day yet.

---

### Post by Malac on 2006-05-17
Okay I'm finally online.:D

I will be posting a "walkthrough" in this thread soon, I hope.

[http://www.ubuntuforums.org/showthread.php?t=168295]("http://www.ubuntuforums.org/showthread.php?t=168295")

My dialup script is there already. If this is any use to anyone.

---

### Post by Malac on 2006-05-26
Okay my "walkthrough" is posted on this thread.

[http://www.ubuntuforums.org/showthread.php?t=182567]("http://www.ubuntuforums.org/showthread.php?t=168295&page=2")

---

### Post by Sef on 2006-05-26
> 3. Download the router installation/ setup software from yor ISP's web site and configure the router from XP then test and make sure you have an internet connection.

Things are complicated in the states.  Here, I just plugged in my dsl box and put in my password.  When I got my router, just had to re-enter my password.  (Just had to do it once and that's it.)

> 4. Install your chosen Linux distro, (for beginners I recommend Kubuntu or Xandros) 

Ubuntu is also a good choice.  Easy to set up and tons of support.

---

### Post by Malac on 2006-05-26
Actually Virus is a plural already :)

---

### Post by popkid on 2006-05-26
[QUOTE=richbarna]You would be surprised at how many newbies are still posting on forums asking about how to get a USB modem to work.
These people get frustrated and go back to windows, depriving them of an amazing experience and amazing distros.

Rich S[/QUOTE]

I second this from personal experience, the first linux distro I tried was Fedora Core 1 (dual booting with XP) a couple of years back, it took me about a week to get my alcatel speedtouch usb modem working

(I had to build a load of stuff from source, not the easiest when I had to keep downloading tar.gz files in windows then mounting from linux to get the necessary resources)

About a month later I upgraded to FC2, which promptly broke my connection again, and the modem fix for FC1 wouldn't work for FC2! 

To cap it all, when I removed FC, it took my MBR with it and I lost Windows too! This was enough to put me off linux for a while...

Not sure I totally learned my lesson though, my ubuntu box uses a broadcom wireless pcmcia card... (though I do at least have an ethernet fallback!)

Routers are definitely the easiest way to go.

pK

---

### Post by Malac on 2006-05-26
If you could just tick a box that said "Use USB Modem" for internet connection.
Then just put the firmware and driver in a certain folder (e.g. /usbmodem/) and the whole thing would run from the box as it were.

If you ticked this box Ubuntu would try to load the firmware file and the driver at boot from that folder, if this box wasn't ticked it would just move on to next boot step.
It would then show up in ppp config programs or something.

This sounds simple to me but then it probably involves loads of complicated programming to get this to work. But for a newbie this would be great and wouldn't hack off Windows users considering transfering over to Linux.

Personally it took me 4 weeks of floundering around to get my USB Modem to work. I did it but I'm not sure I'm any the wiser. :)

---

### Post by dmizer on 2006-05-26
man ... it is so sad to hear that isp's are handing out usb only modems.  usb is slower than cat5, and much less stable ... even in windows.

they would likely save themselves a huge amount of money in telephone support by offering real modems rather than the usb junk.

but the usb modems are cheaper, and it looks so good on the flier when they can say "free modem with 1 year contract!!!!"  having worked for an isp before, if you complain enough, they'll cave and give you a real modem with cat5 connects.

just never tell 'em that you're using linux ... lol

---

### Post by richbarna on 2006-05-26
[QUOTE=Sef]Things are complicated in the states.  Here, I just plugged in my dsl box and put in my password.  When I got my router, just had to re-enter my password.  (Just had to do it once and that's it.)

Ubuntu is also a good choice.  Easy to set up and tons of support.[/QUOTE]

Yeah, sorry, I forgot to point out that I was talking from a European perspective. Most EU ISP's supply cheap rubbish usb modems for free or you can opt to pay for a router. These come with a cd with the installation setup, or you can download a setup.exe that configures your modem or router.

I also recommended Kubuntu and Xandros as starter distros for Windows users as they are very GUI orientated, come with almost everything you need preinstalled, and are easy to find your way around. After changing from Gnome to KDE I found a modern, faster, prettier desktop environment. (but this is just a personal opinion I know some people love gnome).
The other reason is that after using various distro's and various desktop environments/ window managers, I found Kubuntu and Xandros had less tweaking problems than others. For example, I couldn't get Amarok to work with gnome, whereas in KDE it arrived ready to run.

Everybody has his or her preferences and problems, I just tried to use my personal experiences to help get new users on line quickly with a Linux distro that wasn't too much of a culture shock.

---

### Post by Malac on 2006-05-26
In reference to post 16.

I still find it strange that (k)Ubuntu doesn't come with the sources(and other stuff you need) on the CD, as you need these to compile, which you have to do for any non-standard installation. Or a single package that has everything for kernel compilation. Or seperate ISO with it on when you first download (k)Ubuntu.
The number of times I went into Windows, downloaded what I thought was the required components only to have Synaptic tell me package XXXXXX depends on packages YYYYYY and ZZZZZZ before it will install. Hacked me off no end.

Tried KDE, but I like Gnome as it has a certain retro feel which I quite like, personal preference only. :)

---

### Post by %hMa@?b&lt;C on 2006-05-26
that is not a very helpful guide for the millions that use PPPoE and ADSL.  i will post how if anyone needs it for easy PPPoE configuration

---

### Post by richbarna on 2006-05-26
[QUOTE=jeffc313]that is not a very helpful guide for the millions that use PPPoE and ADSL.  i will post how if anyone needs it for easy PPPoE configuration[/QUOTE]

If you have an "easy" PPPoE guide, PLEASE post it, you will be helping millions of people.
Personally I find using a router better because I have 2 PC's, a Laptop and a Mac.

I first tried Linux 5 years ago when there wasn't much support for USB devices, and getting and configuring drivers was near impossible.

However, "easy" guide or not, I stand by my opinion that a router is better for new users and experienced users alike.

---

