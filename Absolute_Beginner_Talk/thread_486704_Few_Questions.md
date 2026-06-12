---
title: "Few Questions"
date: 2007-06-28
forum: Absolute Beginner Talk
---

### Post by mikeypc2006 on 2007-06-28
I've been using Ubuntu on my laptop for a few months now and slowly but surely it has started to grow on me and I have no regrets giving up Windows.

However, I want to put Ubuntu on my desktop though I have a few questions before I take the plunge.  The first is, will Ubuntu work without problems on my computer (see spec below)?

AMD Athlon&#8482; 64 X2 4200+ - Socket AM2 
Microsoft® Windows® XP Professional Edition 
Midi-Tower ATX Case +550W PSU -Black/Silver
ASUS M2N32-SLI Deluxe ,AM2 ,nForce 590 SLI, PCIe, WiFi-AP Solo - ATX Mainboard
Realtek RTL8187 Wireless 802.11g 54Mbps
1024MB DDR2 533MHz Memory - (2x512MB)
250GB Serial ATA Hard Drive with 16MB Buffer
Super Format SONY 18x Dual Layer DVD Writer +R/-R/RW/RAM
256MB nVIDIA GeForce 7600 GS - DVI,HDTV & TV-Out - PCI-Express
19" Widescreen LCD TFT Display with Multi Media, DVI-D, 8ms - TS902W
Creative Labs Sound Blaster Audigy 4 Sound Card
Creative Labs T6060 - 5.1 Speakers with Subwoofer
Logitech Desktop Keyboard & Optical Mouse
10x USB 2.0 Ports (onboard)
Firewire PCI Card - adds IEEE1394 Connectivity to your PC
1x Gigabit LAN (onboard)

What is support for surround sound like in Ubuntu?

Can I buy a TV adapter and watch TV on my PC (any recommendations? (preferably USB))?

Will my Belkin Bluetooth dongle work?

Can I synchronise my Nokia 7373 mobile phone with my computer eg with Evolution?

What software would you recommend to enable me to synchronise data between my laptop and desktop?  I want to be able to easily synchronise my Firefox bookmarks and data in Evolution.

Is it easy to setup Microsoft Office 2003 and Internet Explorer under WINE and how would I do this step by step (I need Office 2003 as I have dealings with people who don't use Open Office and also for Uni work.  I need Internet Explorer to test websites that I've written)?

This probably isn't the place to ask but how do you setup DSL (Damn Small Linux) as an FTP server/enable remote control of the computer?

Is there any free software out there that you would recommend like Windows Media Centre?

What would you recommend as a good iTunes alternative?  Ideally I'd like something that recognises the playlists I have created under iTunes (I don't have an iPod, I just like iTunes for its ease of use with playlists and quick recognition of albums from an online database when you put a CD in.  I also like the MP3 compression rates available).

How do you get a £ on an English British keyboard under Ubuntu?  On my laptop, holding down shift and 3 gets 3.  Is there a driver or something that I need? (No, the shift keys aren't broken)

Is there anything like 'Device Manager' under Ubuntu?

What software would you recommend to connect to FTP servers as well as creating one on a local machine?

That's all I think :)  Cheers guys!

---

### Post by thornomad on 2007-06-28
Have you tried running the LiveCD yet on your desktop system?  A lot of those questions probably could be tested using just the LiveCD (without making any changes to your system).  For the other questions, a couple google searches might find good answers.  But I would start with the LiveCD.

From my limited experience, almost anything is possible in Linux if you have the time and the will.

---

### Post by mikeypc2006 on 2007-06-28
See, the thing is, I don't have the time and the will.  I want to break free from Microsoft but I want to do it easily and painlessly without having to muck around tirelessly with thousands of lines of code.  I don't mind a bit of coding, I just don't want to have to do vast quantities to get anything to work.

Another question, are there any benefits/downsides to using 64bit Ubuntu over the 32bit edition?

Is there anything like Areo in Windows Vista?

---

### Post by thornomad on 2007-06-28
I don't think you have to muck around aimlessly but you will need to take some time to learn a new OS ... that isn't something that happens in the blink of an eye.  It isn't "free windows" ... so you there is a learning curve.  

The LiveCD is a great way to explore Ubuntu without making changes to your system.

---

### Post by mikeypc2006 on 2007-06-28
Surely the point of this forum is for newbies to ask questions of more experienced users and get helpful replies?

---

### Post by Seisen on 2007-06-28
> **mikeypc2006 said:**
> See, the thing is, I don't have the time and the will.  I want to break free from Microsoft but I want to do it easily and painlessly without having to muck around tirelessly with thousands of lines of code.  I don't mind a bit of coding, I just don't want to have to do vast quantities to get anything to work.

Another question, are there any benefits/downsides to using 64bit Ubuntu over the 32bit edition?

Is there anything like Areo in Windows Vista?

Installing Flash and Java are a pain to install on 64bit but it can be done.

---

### Post by nyvalbanat on 2007-06-28
All valid questions. I can only answer a handful, but in general my migration strategy is to do so gradually rather than instantaneously. 

MS Office and IE under wine - the chances are you might run into a few annoyances. If it doesn't work for you, consider buying Crossover Office.

FTP - consider using ssh instead (sudo apt-get install ssh) and connect using sftp (or psftp on windows) - I'm sure there are lots UI-based utilities out there - ftp is insecure and there's really no reason to continue using it

There are some really nice playlist managers like amarok (check out the skins!), but I'm not sure how to migrate your iTunes playlists; I can manage my ipod playlists without any problems - but I can't play DRM'd musing from iTunes on linux.

Yes, there's a Device Manager equivalent - but things may not be in the same places and occasionally you may need to resort to the command line. Otoh, you may be amazed how cool some of the tools are on linux. Again, a gradual migration would provide leeway for the necessary learning curve.

---

### Post by hyper_ch on 2007-06-28
> 
What software would you recommend to enable me to synchronise data between my laptop and desktop?  I want to be able to easily synchronise my Firefox bookmarks and data in Evolution.

hmmm, there are addons for ff bookmarks that lets you store them online... and not sure about evolution sync....

> 
Is it easy to setup Microsoft Office 2003 and Internet Explorer under WINE and how would I do this step by step (I need Office 2003 as I have dealings with people who don't use Open Office and also for Uni work.  I need Internet Explorer to test websites that I've written)?

If you know how then most things are easy to do ;)
Well, regarding OOo at uni: I just wrote my master thesis and a few other papers in OOo... it was much less hassle than using M$ Office....

> 
This probably isn't the place to ask but how do you setup DSL (Damn Small Linux) as an FTP server/enable remote control of the computer?

Why DSL? Why FTP? What exactely do you want to accomplish?

> 
Is there any free software out there that you would recommend like Windows Media Centre?

[http://www.linuxmce.com](http://www.linuxmce.com)

> 
What would you recommend as a good iTunes alternative?  Ideally I'd like something that recognises the playlists I have created under iTunes (I don't have an iPod, I just like iTunes for its ease of use with playlists and quick recognition of albums from an online database when you put a CD in.  I also like the MP3 compression rates available).

I think Amarok is the best music player out there... but I never used iTunes so I can't tell...

> 
How do you get a £ on an English British keyboard under Ubuntu?  On my laptop, holding down shift and 3 gets 3.  Is there a driver or something that I need? (No, the shift keys aren't broken)

Then you did not select the proper keyboard layout I suspect

> 
Is there anything like 'Device Manager' under Ubuntu?

Nope....

> 
What software would you recommend to connect to FTP servers as well as creating one on a local machine?

See the above answer: What do you want to do with ftp?

---

### Post by mikeypc2006 on 2007-06-28
> **hyper_ch said:**
> hmmm, there are addons for ff bookmarks that lets you store them online... and not sure about evolution sync....
Do you have a URL so I could have a look?


> **hyper_ch said:**
> If you know how then most things are easy to do ;)
Well, regarding OOo at uni: I just wrote my master thesis and a few other papers in OOo... it was much less hassle than using M$ Office....
I need Office 2003, when I send documents like my CV (resume) out to companies, Open Office looses some of the formatting (no fault of it, no one knows/understands the workings of Microsoft software, but I need to be able to use Office 2003)


> **hyper_ch said:**
> Why DSL? Why FTP? What exactely do you want to accomplish?
Old computer incapable of running Ubuntu, I want to be able to connect through it from Uni into my home network and transfer files between uni and home.

> **hyper_ch said:**
> Then you did not select the proper keyboard layout I suspect
All the other keys function as a British keyboard......




> **hyper_ch said:**
> See the above answer: What do you want to do with ftp?
Like I said, connect to my home network but also to connect to the FTP server on which my website is hosted.

---

### Post by RanulfWolfSage on 2007-06-28
Try Foxmarks for your Firefox bookmarks:

[https://addons.mozilla.org/en-US/firefox/addon/2410]("https://addons.mozilla.org/en-US/firefox/addon/2410")

You setup a quick free account, and then it will synchronize your bookmarks between any Firefox browser you install it on, regardless of OS. I use it and LOVE it!

---

### Post by into_311 on 2007-06-28
In regards to your questions about something like Windows Vista Aero. There is something better, in many people's opinion, than Aero.  It sort of combines some of the best of Mac OS's Expose as well as some features like Windows Vista's Aero.  Its called Beryl & Compiz. If you haven't heard of it, you might want to do a quick search on youtube for some videos of it.  Their latest release (with the two projects merged is called Compiz Fusion) there is currently a how-to to get it instaleld with ubuntu fiesty fawn. I would suggest playing with that till you get a good feel for Linux and the prioprietary video drivers as a whole though. or you could spent countless hours of frustration trying to get it to work.

[http://ubuntuforums.org/showthread.php?t=481314]("http://ubuntuforums.org/showthread.php?t=481314")
[http://www.youtube.com/watch?v=rEepK-fBa3c&mode=related&search=](http://www.youtube.com/watch?v=rEepK-fBa3c&mode=related&search=)

It's definetely worth checking out.

Ubuntu has something much more s imple already built into the system if you would rather. Just enable Deskop Effects.
Here is a good Tour Guide that will help you along your way. It has instructions on how to enable those. Even though they aren't quite as cool as Beryl, Compiz, or Compiz Fusion though..
But it is much easier to setup, and fairly stable.

[https://wiki.ubuntu.com/7.04Tour#head-72e463e7c61a66c61b567f361d2ad3fe38af39f8](https://wiki.ubuntu.com/7.04Tour#head-72e463e7c61a66c61b567f361d2ad3fe38af39f8)

THe features you are looking for in Windows Media Center Edition, are you looking for a good Tivo/PVR piece of software? If so, I would recommend MythTV all the way. There are live cd's with Mythtv enabled frontends already setup, like KnoppMyth. Or I'm sure its in the ubuntu repositories and you can install it that way.

There is lots of tv tuner cards ( i hear) that run well under Linux. one I have heard of specifically is called winttv. Interestingly enough:

[http://www.hauppauge.com/pages/prods.html](http://www.hauppauge.com/pages/prods.html)

One thing I feel strongly to urge you to keep in mind though. is that this is a FREE operating system. By that I mean in EVERY way possible. Not just free of charge, but free of many of the restrictions imposed on you by other OS'. As such, not everything CAN BE simple. The purpose of Linux is to give you choices, unlike M$ who makes all the decisions for you on what desktop environment to use. How you will command it through a command prompt. What minimal changes you can make to your taskbar, start menu, etc. Including after installing TweakUI.  What wallpapers you are provided. Yes, you can tweak windows somewhat. But that is the power of linux, the amount of configuration/tweaking you can do. For example : You can even make linux accept ms-dos commands to do similar things in Linux (through the power of alias). Also, the plethora of choices in software, depending on what you are looking for your system to do.

Having been there, I can say, its a struggle at first. Coming over from a windows world to using Linux full-time. but its definetely doable. You just have to have the right approach and be looking to help others as well as not being afraid to ask for help. Don't give up, as you encounter a little struggling at first. As we all must struggle in this existence before we are truly free. As opposed to expecting everything to just be handed to you on a silver platter.

Linux is only as good as the people who believe in it, and  contribute to it.

Just a few words of advice...

---

### Post by thornomad on 2007-06-28
> **mikeypc2006 said:**
> Surely the point of this forum is for newbies to ask questions of more experienced users and get helpful replies?

I sincerely apologize if it was me you directed this piece of constructive criticism towards for it was not my intention for providing un-helpful replies -- sorry for having wasted your time having to read my posts.  I can attempt to refrain, in the future, from posting and remember my place as a "less" expereienced user.

Thank you.

Ubuntu is wonderful.

---

### Post by hyper_ch on 2007-06-28
You do send out your word docs to companies?
I'd never do that... I'd (and I have in the past) sent pdfs and you have a pdf converter directly integrated into OOo...

Well, for what you seem to describe I wouldn't use FTP but SSH... with DSL you just need to install openssh-server and there you go...

---

