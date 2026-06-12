---
title: "Clueless as a snail.."
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by Recon42 on 2007-05-27
Hey guys! I'm here to ask you guys some questions that will get me on my way on understanding how EXACTLY Ubuntu (7.04) works. I have no idea how this new operationg system works and have no experience with linux or any other program except Windows. I'm bored of Microsoft trying to pinch every cent from my pockets for rediculous "upgrades". I understand that I'll still need it for purposes such as school and video games. I also know the long road on understanding this operating system won't be easy, but I love a good challenge and so far this operating system seems to be the easiest to work with. 

To start of:
1st. Can someone link me to a site that shows me EXACTLY how to do basic operations on Ubuntu? (Stuff like installing drivers and fixing bugs like the ATI X**** Series cards since I have an ATI X850XT)

2nd. Is it truly as easy as WIndows when it comes to BASICLY running this program (checking emails, web surfing, streaming music,etc)?

3rd. How about drivers? Will I need to download 3rd party drivers? Is there a key site that can get me drivers for: Lite-On DVD/CD burner, ATi, AMD Athlon 64 Proc, sound drivers, etc

4th. Most Importantly* Is there text based commands required to do certain things? If so can someone link me to a place to learn how to type and understand the required macros and such?

I truly apologize if there are millions of posts like this. Honestly I just want to not get ahead of myself and screw up since I sorta lost my Windows XP cd and don't have 100 bucks laying around to buy another one ;)

Thanks so much and I truly love how the community here are supportive of each other and the whole "community" aspect of the operating system is truly what technology is about and M/S should take notes (other than "borrowing" ideas and calling it their own)..

Cheers :popcorn:

---

### Post by bukwirm on 2007-05-27
1. [This site]("http://ubuntuguide.org/wiki/Ubuntu:Feisty") gives fairly detailed directions for many common Ubuntu tasks.

2. I think that it's much easier to use Ubuntu for basic tasks because I can customize Ubuntu much more then Windows.

4. Yes, there are a few tasks that can only be accomplished though the command line. Any of [these sites]("http://www.google.com/search?q=bash+tutorial") should help you get started.

---

### Post by ryanVickers on 2007-05-27
3. sound should work fine, but 3D is not enabled by default.  to get it to automatically download the right driver for you, go System > Administration > Restricted Drivers Manager and click it on.  It will download and install the right one for your card and then ask you to reboot - the first and last time this will ever happen in ubuntu :)

---

### Post by Tux Aubrey on 2007-05-27
re drivers - you will find a lot of them already built-in and others (like the ATI video drivers) are generally easy to find and install, especially in the latest 'buntu release (7.04).

A lot of these questions you can answer for yourself using the Live CD (BTW, I'd suggest you start with the 32 bit version as a few things are not yet fully supported in 64 bit).  

Welcome and enjoy!

---

### Post by BaffledMollusc on 2007-05-27
> **Recon42 said:**
> Hey guys! I'm here to ask you guys some questions that will get me on my way 
To start of:
1st. Can someone link me to a site that shows me EXACTLY how to do basic operations on Ubuntu? (Stuff like installing drivers and fixing bugs like the ATI X**** Series cards since I have an ATI X850XT)

2nd. Is it truly as easy as WIndows when it comes to BASICLY running this program (checking emails, web surfing, streaming music,etc)?

3rd. How about drivers? Will I need to download 3rd party drivers? Is there a key site that can get me drivers for: Lite-On DVD/CD burner, ATi, AMD Athlon 64 Proc, sound drivers, etc

4th. Most Importantly* Is there text based commands required to do certain things? If so can someone link me to a place to learn how to type and understand the required macros and such?

Cheers :popcorn:
Welcome to the Ubuntu community! Okay, here are some quick answers to your questions:

1) As someone already said, [http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty) is a good place to find out how to do things. It's not so good for helping you understand why the things work, though.

2) Yes. The thing about the open source universe is that there are often dozens of programs that do roughly the same thing, so you should feel free to experiment until you find one that works well for you. For example, the standard browser and email client that come with Ubuntu is Firefox and Evolution, but there are lots of other applications you can try instead. As another example, my favourite music player (Amarok) isn't included in Ubuntu to start with, so that's one of the first things I always add. Going to Applications->Add Remove is probably the easiest way for you to add more programs to start with.

3) Drivers work a bit differently under Linux to what you're used to. Most of the drivers you need are already included in the Linux kernel - certainly stuff like motherboard/CPU drivers and most sound drivers. Unless you have really weird pieces of hardware, you probably won't need to install any drivers. The exception is video cards. Since manufacturers won't release their specs, the proprietary drivers from ATI/Nvidia are faster than the open source ones included in the kernel. If you're 3D gaming you might want to install these proprietary drivers. To do this go to System->Restricted Driver Management.

4) Yes, the command line can be useful and is very powerful, but it's certainly not something you <i>need</i> to know. Google "linux command line" to get lots of helpful hits. Here's one: [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

To use the command line you'll need the terminal window, which you can access from Applications->Accessories->Terminal.

---

### Post by Recon42 on 2007-05-27
Wow this has to be the best forum I've been on ever (I've been using forums since I was 8 and now I'm 16 hehe)! Honestly thanks so much. I viewed the sticky on whether or not Ubunu was for me and I think I can handle the challenge especially with my 2 month Summer vacation, I think I'll have plenty of time. I know how to mount an iso on a blank disc (which I ran out of), but how's the shipping of one disc for a free copy? Does it actually take 2 months to deliver (I live in Boynton Beach, Florida in U.S.A)?

---

### Post by ryanVickers on 2007-05-27
I would download and burn it myself if I were you, just find some blank disks.  Even on the first day ubuntu 7.04 came out I was downloading it and it was done in a couple of hours - great speed!  I remember when I was about 9 and I started using red hat 6, and now not many more years than that later, I'm using ubuntu 7.04 and the quality and easiness of everything is so incredible in comparison!

---

### Post by mmikee66 on 2007-05-27
Get a live CD of Ubuntu and have a look for yourself about checking emails, web surfing... I use Thunderbird and Firefox in windows also, the programs are identical so no change for me when jumping systems (annoying thing is windows XP does not have multiple desktops and a window always on top feature;))

streaming music,etc may not be 100% testable because you will need to install additional programs to get them to run from the base configuration on the Live CD. But you can have a look at the Synaptic package manager to see how easy it is to install new programs in Ubuntu.

More than  enough information here in the forum to deal with any questions you have after installing ubuntu to get individual things working. Just get started, update the software repositories (get access to more software :D) and start using.

---

### Post by GrueTamer on 2007-05-28
> **Recon42 said:**
> Hey guys! I'm here to ask you guys some questions that will get me on my way on understanding how EXACTLY Ubuntu (7.04) works. I have no idea how this new operationg system works and have no experience with linux or any other program except Windows. I'm bored of Microsoft trying to pinch every cent from my pockets for rediculous "upgrades". I understand that I'll still need it for purposes such as school and video games. I also know the long road on understanding this operating system won't be easy, but I love a good challenge and so far this operating system seems to be the easiest to work with. 

To start of:
1st. Can someone link me to a site that shows me EXACTLY how to do basic operations on Ubuntu? (Stuff like installing drivers and fixing bugs like the ATI X**** Series cards since I have an ATI X850XT)

2nd. Is it truly as easy as WIndows when it comes to BASICLY running this program (checking emails, web surfing, streaming music,etc)?

3rd. How about drivers? Will I need to download 3rd party drivers? Is there a key site that can get me drivers for: Lite-On DVD/CD burner, ATi, AMD Athlon 64 Proc, sound drivers, etc

4th. Most Importantly* Is there text based commands required to do certain things? If so can someone link me to a place to learn how to type and understand the required macros and such?

I truly apologize if there are millions of posts like this. Honestly I just want to not get ahead of myself and screw up since I sorta lost my Windows XP cd and don't have 100 bucks laying around to buy another one ;)

Thanks so much and I truly love how the community here are supportive of each other and the whole "community" aspect of the operating system is truly what technology is about and M/S should take notes (other than "borrowing" ideas and calling it their own)..

Cheers :popcorn:Welcome to ubuntu, recon!  As I have a few things to add to the discussion here, I believe that I will...well, add them, I guess.

1.  The ubuntu guide page linked by many people is a very good page, but I've found that [this]("http://psychocats.net/ubuntu/index.php") has a lot of information on it, including some things I didn't even know existed, such as the minimal cd information.  It also has some pretty cool info relating to other desktop environments besides gnome, and I firmly believe that finding the right desktop environment/window manager can greatly increase your system productivity.  If you ever want a long list and some explanations, just give me a call on msn or on the forums, but I'll save that info for another place.  It really doesn't belong here.

2.  It can be as easy as you want it to be, really.  Most of the time, there are multiple ways to do things, each with their own pros and cons.  Some of the better programs might not be easy to start out with, but are in the end great things to use.  On the flipside, some programs are extremely easy to use, but aren't that innovative or all that great, either.  To put this into a real example, let's talk about...text editors, of all things.  Vim is lightning quick and extremely efficient when put in front of someone who understands it, but learning vim can be very difficult.  Nano, on the other hand, is quite simple, with all the common shortcuts on the bottom (^=ctrl), but it's not nearly as efficient as vim.  NOTE:  this is my personal preference ONLY, I don't want to start arguments, that's why I avoided emacs and vim, but vim can be a good example here.  This is only to visualize how the above idea might work, and in no way guarantees 100% accuracy for every person, as I know people that find vim easier to learn than nano.

3.  Usually, the only driver you need is the video driver.  A good way to do this is to go into the restricted driver manager and enable the restricted drivers, as said before.  BUT, some people don't want to use the restricted drivers, and will only use open source ones.  Installing these drivers can be harder, and they don't offer as optimal performance most of the time, but hey, they're open source :) .  But to the average user who doesn't care, I recommend the restricted drivers, mostly because of how they perform better most of the time.  As for the other drivers, these are already installed (to simplify how it really works), so you don't usually have to worry about this.

4.  Well...yeah, there are things that you have to do in a command line interface (CLI), but you don't have to use these things, do you?  Some CLI things don't have GUI counterparts, but for the most part, these commands aren't essential to use.  And, of course, if you want to use them...you have a terminal, of course :) .  A good site for learning the terminal well is [this site]("http://linuxcommand.org").  It examines the basic ways of the terminal in a simple and easy to follow manner, and then goes on to scripts, which can be a lot of fun to write :)

Anyway, I hope that at least one thing that I've posted here helps you out, recon.  I hope that your experience with ubuntu is a good one, and that you enjoy your stay at the ubuntu forums.

---

