---
title: "Thinking about switching.."
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by Sootah on 2008-04-17
Yes, yet another 'switch' thread. (Perhaps you should make some commercials like Apple did ;) ) 

Anyway, a little background on me: I've been in to computers since my very first 386 DX 40 over 16 years ago. Because of learning how to use DOS at the age of 9, command lines do not scare me. (In some ways, I prefer them) More recently I did computer repair for a living up until a couple of years ago.

Linux for some reason has always called to me. I do not know why. I installed Slackware on a machine forever and a day ago, was completely unfamiliar with the command syntax and as such took it off shortly thereafter. A while later I installed a different distro, it may have been Mandrake and got X Windows working. This was actually before Linux (at least the distros I was looking at) had decent install interfaces and X Windows didn't actually install and start up by default. 

Later on I installed a later version of Mandrake, got KDE running, most of the hardware working too. It's always at this point I think to myself "now what?" screw around with it a bit and then promptly go back to Windows.

My main issue is that I just don't like the idea of dual-boot. I've no problem partitioning the hard drive, but when my computer is fully booted, damnit, I don't want to have to reboot to access some other application.

**Mkay then, now that you have my overly long-winded introduction let's get down to business:**

The primary things I use my computer for are:

[LIST=1]
[*]Regular computer stuff (Typing/Document editing, surfing the web, email, etc)
[*]Programming (Primarily HTML and PHP web development, although I like to dabble with app programming and customization)
[*]Games
[*]TiVo
[/LIST]

**Item #1** I know that Linux can handle just fine natively. I already use OpenOffice pretty exclusively so there's no learning curve there. FireFox is also my primary web browser as I much prefer it to IE, which also makes the transition easy. Up until now I have used Outlook Express and Windows Mail (Vista) for my POP3 accounts, but a mail client is an effing mail client so using Thunderbird or whatever won't be a big deal. Hell, maybe there's an app that has some nice Microsoft Office Outlook-like features that I don't know about.

**Item #2** I'm also quite sure that Linux can handle amply for me as well. I'll have to find a good IDE for my HTML/PHP/Javascript (know of a good, clean one?) but that'll just take a little looking around. Or, better yet, one of you will have a nice solution for me. I've been fond of [phpDesigner ]("http://www.mpsoftware.dk/phpdesigner.php")by MP Software but the later versions have seemed a bit bloated to me.

**Item #3** This is the first one that concerns me. Obviously dual boot solves this problem in its entirety but if you paid any attention to my above rant I just hate having to reboot. I do know that some things will run under Wine, but how extensive is that? Will most things run OK, or is it a complete crapshoot? It's unfortunate that apps like Virtualbox won't support 3D acceleration or the whole issue would be resolved - I'd just run a Windows virtual machine from within Linux.

Whenever possible I use Valve's Steam to purchase my games as I love the delivery platform as well as the fact that I don't have to keep track of boxes/CD keys/CDs/etc. Does Steam function at all under Wine? If so, do the underlying applications? I don't expect everything to run, but most of it would be nice.

**Item #4** is also a big one. Currently I am running Windows Vista Ultimate edition. It is a PITA (and I haven't even had that many problems with it) with two saving graces - The Aero interface and Windows Media Center.

I can run Compiz Fusion, so the Aero thing isn't a problem (or doesn't appear to be, from what I've seen Fusion is nice) I'm not sure, however, that Linux has anything as nice as Windows Media Center. It's seriously great. For the most part, and I do mean *most*, I just use it to automatically record programs for me. I then fast-forward through commercials, pause live TV, all that jazz. WMC periodically connects to the internet to download a program guide, so that makes scheduling recordings easy. Other apps I've used for Windows attempted to charge you for the guide service, so perhaps any Linux equiv doesn't have this feature.

The fact that Linux is, or perhaps my impression of it is wrong, completely customizable is nice to me. I like to monkey with different things, and love to learn new systems. It'd be nice to be able to exactly configure my machine to behave precisely as I think it should. Programming little features might be entertaining.

Alright, now that I'm done with my novel - what are your thoughts? I have pretty stringent standards and don't deal well with things that don't work the way I'd like them to. However, so long as I can get it to perform the majority of functions I'd like it to better than Vista currently does then I'm ready to take the plunge.

Thanks for your time,

-Sootah

---

### Post by Sootah on 2008-04-17
Also, here is my hardware setup:

[LIST]
[*]ASUS P5N32-E Motherboard
[*]nVidia 8800 GTS 640 MB
[*]Intel Core 2 Duo E6600
[*]VisionTek Xtasy Theater 550 Pro PVR (ATi chipset) - My TV tuner
[*]Using the on-board Realtek soundcard
[*]Dual Samsung SyncMaster 216BW monitors
[/LIST]

Any issues with any of that? I hear that nVidia's Linux drivers are quite good, but have no idea how support will be for my motherboards chipset, sound card, network cards, TV tuner, all that jazz.

Thanks again.

---

### Post by stchman on 2008-04-17
> **Sootah said:**
> Also, here is my hardware setup:

[LIST]
[*]ASUS P5N32-E Motherboard
[*]nVidia 8800 GTS 640 MB
[*]Intel Core 2 Duo E6600
[*]VisionTek Xtasy Theater 550 Pro PVR (ATi chipset) - My TV tuner
[*]Using the on-board Realtek soundcard
[*]Dual Samsung SyncMaster 216BW monitors
[/LIST]

Any issues with any of that? I hear that nVidia's Linux drivers are quite good, but have no idea how support will be for my motherboards chipset, sound card, network cards, TV tuner, all that jazz.

Thanks again.

Everything will work out of the box except the 8800GT.  To install Nvidia drivers use Envy 0.9.10 in Gutsy or earlier or EnvyNG in Hardy.  You will need the 169.12 drivers.  I have an 8800GT and it works flawlessly.

---

### Post by Sootah on 2008-04-17
Sounds good. Any advice on the non-hardware related stuff?

Also, I actually attempted to install the 8.04 64 bit beta last night to no avail. I get to the first screen where I select that I'd like to install the OS, after this the screen just goes blank and my computer does nothing.

I also tried to run the CD integrity checker with the same result. Select it, something looks like it loads for a second, the screen goes blank and that's it.

---

### Post by dca on 2008-04-17
For the media center stuff you could try:
 
[http://elisa.fluendo.com/](http://elisa.fluendo.com/)

---

### Post by Hendrixski on 2008-04-17
> **Sootah said:**
> 
[LIST=1]
[*]Regular computer stuff (Typing/Document editing, surfing the web, email, etc)
[*]Programming (Primarily HTML and PHP web development, although I like to dabble with app programming and customization)
[*]Games
[*]TiVo
[/LIST]


pretty much everybody in the linux community does those... and better & more efficiently than they could on Windows.  PHP development was intended for Linux, and the LAMP stack is powerful and easy (compared to IIS on Windows which sucks).

> **Sootah said:**
> 
**Item #1** I know that Linux can handle just fine natively. I already use OpenOffice pretty exclusively so there's no learning curve there. FireFox is also my primary web browser as I much prefer it to IE, which also makes the transition easy. Up until now I have used Outlook Express and Windows Mail (Vista) for my POP3 accounts, but a mail client is an effing mail client so using Thunderbird or whatever won't be a big deal. Hell, maybe there's an app that has some nice Microsoft Office Outlook-like features that I don't know about.


By outlook like features you mean passing along viruses, having security holes that let  crackers compromise your computer and not-having mail threading?  No, a mail client is not a mail client... and Outlook should not be a mail client anybody uses.  Try thunderbird , install a theme that you like and turn on mail threading, then ask yourself why anybody ever used outlook.

> **Sootah said:**
> 
**Item #2** I'm also quite sure that Linux can handle amply for me as well. I'll have to find a good IDE for my HTML/PHP/Javascript (know of a good, clean one?) but that'll just take a little looking around. Or, better yet, one of you will have a nice solution for me. I've been fond of [phpDesigner ]("http://www.mpsoftware.dk/phpdesigner.php")by MP Software but the later versions have seemed a bit bloated to me.


There's like 5 million IDE's.  I recommend Eclipse.  It is the best IDE ever made as far as I'm concerned, and it gets better every day.  There are plugins for every language imaginable, even though it primarily does Java.  The PHP plugin pretty much has the php language reference embedded inside of it, so you can develop really quickly with tab completion.

> **Sootah said:**
> 
**Item #3** This is the first one that concerns me. Obviously dual boot solves this problem in its entirety but if you paid any attention to my above rant I just hate having to reboot. I do know that some things will run under Wine, but how extensive is that? Will most things run OK, or is it a complete crapshoot? It's unfortunate that apps like Virtualbox won't support 3D acceleration or the whole issue would be resolved - I'd just run a Windows virtual machine from within Linux.


Windows XP programs run better under wine than they do in Vista.  I kid you not.  There are more XP games that run on Linux than on Vista.

Windows doesn't work with Windows, so don't worry about Linux working with it.


> **Sootah said:**
> 
Thanks for your time,

-Sootah

hit the little thank you button under the post :-p

---

### Post by Sootah on 2008-04-18
Well, I dedicated a whole 30 GB of my hard drive to Ubuntu and now have it installed. I believe my previous burn was bad, so I redownloaded the (32 bit this time) image using BitTorrent for its error checking features and then burnt the image at a nice slow 8x. 

I must say - installation was an absolute dream. My dual monitors came on right away, the correct resolution was already selected, it offered to update my nVidia drivers right off the bat and to *boot* networking and everything immediately worked.

I've done absolutely *zero* configuration so far and I'm up and running. "It just works" so far seems to be accurate. We'll see how it goes in regards to my TV Tuner card, that one has me worried.

So - how do I set up an extended desktop? Currently the screens are cloned. While it's handy to see everything I'm doing from the same perspective twice, it's not that useful. Where do I go about extending the desktop?

Also, this autoupdater blows my effing mind. I booted up, it said I had 400-someodd updates, and after two clicks of a mouse button the packages are installing. Nice.

Oh - another random thing. How can I make the default font just a *teensy* bit bigger? At my resolution some of the letters are so close together that they touch and that irritates me. For instance: "le" The e touches the l. This bugs me.

---

### Post by Sootah on 2008-04-18
Actually, the touching letter issue only appears to be a problem with the font that this forums Reply box utilizes.

New issue now - after configuring Ubuntu to use the nVidia drivers and letting the system reboot my secondary display neither displays anything, nor is detected in the system resolution settings.

Suggestions?

---

### Post by zoro on 2008-04-18
1: OpenOffice, Thunderbird+Lightening :)

2: I'm a PHP developer, and I use Ubuntu exclusively in work. For coding, I use a combination of vim and Eclipse, with the PDT plugin ( [http://www.eclipse.org/pdt/](http://www.eclipse.org/pdt/) ).
If I could, I would love to move away from eclipse - its horribly bloated, ugly, and quite unintuitive for me (speaking as a PHP dev). That said, when I use it for Java work, its absolutely fantastic.

3: At home, I'd kill to be able to run Ubuntu, but I'm a gamer. And that fact alone means that linux is just not an option for me. There's no 2 ways about it - if you want to game easily, reliably and regularly, you have absolutely no choice but to use Windows. (I'm fully aware of the capabilities of WINE, but if I have to troubleshoot _1_ more more-than-1-sound-source problem in linux, I'll scream).

The Ubuntu Nvidia drivers are great - really great. As is always the case, however, Ubuntu falls down on ease-of-configuration when compared to Windows. It took me 4 hours to get a dual-screen setup working in a way that I felt was satisfactory, and I'm now afraid to touch the settings again incase I break it. The lack of a rotate-1-monitor-but-leave-the-other-one-alone functionality is a serious pain in the ***, but if you're willing to ignore some of the failings of linux in this regard, and just be happy that you got it working at all, then you'll be fine :)

---

