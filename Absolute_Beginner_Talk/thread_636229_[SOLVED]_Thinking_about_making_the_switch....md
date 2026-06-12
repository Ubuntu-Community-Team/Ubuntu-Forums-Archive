---
title: "[SOLVED] Thinking about making the switch..."
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by norfair on 2007-12-09
(There might be a better place to post this question, but I searched around and gave up. Please move or delete if this doesn't belong here. Thanks!)

I am a current Windows XP user who after three attempts to switch to Apple has been left completely and utterly digusted with their customer service and overall level of quality. While I don't have a problem with Windows, I want something different. So in searching for alternatives, I've found Linux (the only other alternative I think). I first researched Linspire, but found it to be a little too basic. Then I stumbled upon Ubuntu. While it's a whole new world for me, it looks interesting. I like the name, and logo graphic too! 

What I do on my PC is basic, but I have some things I can't live without. So, I thought I'd list a few of the programs and peripherals I have to see if anyone knows if they'd work with Ubuntu or not. I love, love, love the Opera web browser, but only see FireFox listed as one that Ubuntu works with. Has anyone had luck getting Opera to work? Also, I have mostly Canon branded devices, printer, scanner, digital camera - do Canon devices work well with Ubuntu? I've read of issue with Lexmark, but nothing on Canon. My monitor is a Samsung, but I would think I wouldn't have any issues getting it to work. Then I wonder about getting my cable modem to work. Any issues with modems? There are some games I'd like to try out too, but I see that a program called Wine might be an option. Going back to the web, does it run pretty smoothly in general? That's pretty much where I live, and wonder if I'd notice any hiccups - such as Flash or Java, or speed issues. Oh, and has anyone had any issues going wi-fi with Wii? I'm guessing things like Logitech cordless keyboards and mice work without issue, but I still wonder. Also, what about iTunes? Would it work with Ubuntu? I do like to dabble in photo editing, and am not a fan of GIMP. Are there any good aps that would work with Ubuntu? I have bunches more to ask, but this is all I can think of at the moment.

The computer I am working on now is dying a slow, painful death. So I am in need of a new computer ASAP, and would rather avoid Vista and as I've mentioned, I've been scortched by Apple. While I can get around fairly well and catch on relatively quick, I am still a novice in many ways when it comes to comuters - at least in code and the like. I thought about building my own machine and getting Ubuntu, but would rather buy a complete system with it installed. [I found one at Dell (a company I thought I'd never come crawling back to) at a really good price]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs"). The odd thing is that it's installed with an older version of Ubuntu, 7.04 (at least I would assume that this is an older version). I see that System76 has some offerings, but their prices are rather high for what you get (integrated graphics, pricey components and so forth). I like their Koala Mini, though. If anyone can recommend a place/company that sells nicely equiped desktops installed with Ubuntu, I'd appreciate it.

Whew. Sorry for being so wordy. I hope I didn't put anyone that made it this far asleep. Again, I'd appreciate any sort of feedback whatsoever. Thanks a bunch!

---

### Post by finer recliner on 2007-12-09
-opera works in ubuntu
-most printers and card readers work with ubuntu
-many users use wine to use windows software/games. you're likely to run into issues, but once solved, it will likely stay sovled.
-flash is supported with very rare problems. 
-java is fully supported
-itunes does NOT work.

best thing to do about your monitor and cable modem is to burn the installation disk (which is actually also a live disc) and boot from it. this will give you a chance to try out the entire OS without having to install anything to your hdd and wont touch your current windows installation. if everything works nicely, you can click the install icon on the desktop.

enjoy!

---

### Post by jordanmthomas on 2007-12-09
I can't answer all your questions, but I'll give it a go for some:
1.  Opera works great.
2.  Don't worry about your monitor.  
3.  Flash and Java both work.  Flash can be a little troublesome for some people, but overall it is fine.
4.  As far as performance, I think you will be very pleased with Linux.  It tends to run faster than Windows on the same hardware.
5.  iTunes does not work with Ubuntu.  I think version 6 might work under wine (which lets you run Windows programs in Linux) but I am pretty sure 7 doesn't.  If you're not using iTunes to buy music, then there is no shortage of media players for Linux.  If you're looking to buy music, you're going to be unhappy.
6.  Mice and keyboards shouldn't give you any trouble unless they have tons of extra features.  Even then, you can usually get all the buttons to work though.
7.  No issues with cable modems, unless you connect to it through USB instead of ethernet.
8.  There are some alternatives to GIMP, but they are typically not as feature-rich.  I believe you can (with some work, mind you) get Photoshop to run under wine.

Sorry I went out of order a little bit.

Anyway, before you make up your mind I'd suggest reading this:
[http://linux.oneandoneis2.org/LNW.htm](http://linux.oneandoneis2.org/LNW.htm)
to make sure you know that Linux is not the same as Windows, and you shouldn't expect it to be.

Also, as far as service goes:  you said you didn't like Apple's?  I just thought I would let you know that while you can buy support from Canonical (they own Ubuntu), most people opt for community-given service.  I don't know if you'll be pleased with it or not, but I hear good things about the service around here.

Sorry if I missed anything (aside from the Cannon stuff, which I don't know about) and welcome to the forums.

---

### Post by CCNA_student on 2007-12-09
There is a Linux version of Opera, I have it installed. As for photo editing, there are other applications but I do not edit photos so you would have to ask someone else. Your monitor would work. I believe that most Canon devices run on Linux, but I do not have their products so I cannot say with any certainty. If you DSL or cable modem connect with an ethernet cable, you will probably be fine. As for wireless, that is a little more annoying. I have a laptop that once had a Network Interface Card(NIC) from Broadcom, and I could not get the firmware to work, so I bought a NIC from Intel, and it instantly worked. And if you want to play DVD's use the command under Applications>Accessories>Terminal 
sudo apt-get install libdvdread3 libxine1-ffmpeg totem-xine build-essential debhelper fakeroot sudo /usr/share/doc/libdvdread3/install-css.sh 

  This is very important, as Ubuntu does not natively play non-free formats. You would also have to install Java and Flash player separately. Just type in JRE 6 and Macromedia under Applications>Add/Remove, type in each name separately, and install. Make sure you search for all supported applications. I guess that is all for now.  

     Sin Cere

     CCNA_Student

---

### Post by Ub1476 on 2007-12-09
Opera works brilliant on Ubuntu. It's a .deb (like .exe) package from their website which will automatically install.

I think Canon works alright with Linux. The drivers which isn't already integrated into the system, you're likely to find on the web.

No, no problem on the monitor, but look out for the graphic controller if you want Compiz-Fusion running;)

No, there are no issues with modem/wifi if the manufacture support Linux. 

There are very few games which is built for Linux, but yes Wine can run some. It depends on what you are thinking of. However, Cedega is probably the best option for games, but it cost money.

Flash and java works fine, you just have to install a package called "ubuntu-extras" to get java, flash codecs etc to work. Myself I have never encountered any speed issues, but quite som many have had some problems with flash and Firefox (it freezes), but if you're using Opera or Swiftfox (Firefox built for your CPU) you should be fine. Might be the problem has been fixed by Adobe now though.

Sorry, don't know about bluetooth, but I guess it will work alright. 

iTunes will work on Ubuntu, if you're in for some tweaking, but why use it? There are numerous Linux media players which has iPod support, that be Rhythmbox, Exaile and so on..

Well, you have "Gimpshop" if you don't like Gimp's menus, and you can run some earlier versions of Photoshop in Linux, but there are also [Pixel]("http://www.kanzelsberger.com/pixel/?page_id=12"). It cost money, but looks promising.

Before you buy yourself a new comp I suggest you check it hardware to see if it support Linux. Also, your dyeing laptop might not be so dyeing if you try Linux on it. Ubuntu will be blazing fast compared to XP:)

---

### Post by jordanmthomas on 2007-12-09
> **Ub1476 said:**
> Flash and java works fine, you just have to install a package called "ubuntu-extras" to get java, flash codecs etc to work. 

The package is ubuntu-restricted-extras.  :)

---

### Post by Ub1476 on 2007-12-09
> **jordanmthomas said:**
> The package is ubuntu-restricted-extras.  :)

I know, but didn't find it worth mention so detailedly:)

---

### Post by thelatinist on 2007-12-09
For iPod synchronization, Amarok works great for me.

If you have CS2 you can find tutorials online for making a portable version from your current windows installation. This *will* work under Wine.

---

### Post by norfair on 2007-12-09
Wow! Thanks to everyone that responded, I do appreciate it. Sorry I'm just now following up, but I became preoccupied for a bit. 

Well, I'm super glad to hear that Opera works with Ubuntu and it sounds like most of what I have will, with some minor tweaking of course. So this is good to hear.

Someone did tell me that Linux based browsers such as Ubuntu can't play protected media, is this true? Also, speaking of media, some mentioned that iTunes worked, and others said it didn't. I don't care about buying music on iTunes (as they never have what I am looking for anyway), but I do need it for getting music onto my iPod (or at least I think I do). It seems the majority of those that responded are able to get iTunes working. So hopefully this is true. I really don't care for the iTunes program, nor is my iPod the greatest, so it wouldn't be that big of a deal breaker if it didn't work. 

I know that Ubuntu isn't Windows, nor would I want or expect it to run as such, but I do expect it to be at least somewhat user-friendly and not limiting at all. I know it's more of other companies limiting their products, but I just hope that should I get a system with Ubuntu as my only operting system, I realize that I'm stuck with not being able to get anything to work on it or not being able to buy the latest gadets and accessories for it. If I have to do some mild tweaking, I can deal with it, but if I have to research everytime I buy something or what have you and spend days at it, then perhaps Ubuntu is not for me. I don't know. I just started my research on all of this last night, so I still have much to learn.

One question of mine that I still have is, can anyone recommend a place to buy Ubuntu desktop systems? Does [this]("http://configure.us.dell.com/dellstore/config.aspx?c=us&cs=19&kc=6V440&l=en&oc=DDCWDAL&s=dhs") look like a good one? Or did most build their own, or are you all running Ubuntu along side of another OS. Just curious.

Thanks again to everyone that responed. You were all very helpful.

---

### Post by jordanmthomas on 2007-12-09
> Someone did tell me that Linux based browsers such as Ubuntu can't play protected media, is this true? Also, speaking of media, some mentioned that iTunes worked, and others said it didn't. I don't care about buying music on iTunes (as they never have what I am looking for anyway), but I do need it for getting music onto my iPod (or at least I think I do). It seems the majority of those that responded are able to get iTunes working. So hopefully this is true. I really don't care for the iTunes program, nor is my iPod the greatest, so it wouldn't be that big of a deal breaker if it didn't work.
Ah, if you are just using iTunes to sync up your iPod, you are in luck.  The media player that comes installed with Ubuntu can do this no problem.

You are right about not being able to play DRM-infested media, however.

I can't reccommend where to buy a system with Ubuntu already on it.  People suggest System76, but I think they're a bit expensive.   It is really easy to install it yourself.  If you're not dual-booting with Windows, it's even easier.  Just boot off the CD, and click install once it's booted.  Then, just answer some simple questions like your username and password.  Browse the web while it's installing, and reboot into your new system when it's done.

The system you linked to looks pretty good to me.  It is certainly fast enough to do whatever you want to on Ubuntu.  

I don't use Ubuntu, so I can't answer how people do it in terms of getting it preinstalled, running it alongside Windows, etc.   What I usually do (because I'm a tinkerer) is run my Arch on my first partition and leave another one open for testing out different distributions when they come out with new versions.  Can't say whether or not this is common though.  :)

> if I have to research everytime I buy something or what have you and spend days at it, then perhaps Ubuntu is not for me.
Generally, you will be ok for "standard" hardware.  That USB-powered missile launcher might not work though, etc.  Basically, anywhere you can, get Intel parts (wireless, etc) and you will be fine.  With wireless you just need to stay away from Broadcom I think.  

Days will undoubtedly be spent working things out until you get used to everything though, so be warned.  It probably took me about two weeks when I first used Ubuntu to get used to how everything fits together and I'm still learning.

---

### Post by norfair on 2007-12-09
Thanks for the speedy feedback, but I have just a few more questions and then I'll leave the board alone for a bit...

> **jordanmthomas said:**
> You are right about not being able to play DRM-infested media, however.

This is really going to make me look like an idiot, but what DRM media files and the like won't work, for example? Would this include movies I've downloaded over the years from various websites, streaming content on the web? Most of my video files are in .wmv and .avi format, so now I'm worried that they'll all be rendered useless. Would this also be the same for watching DVDs on my computer? 

> **jordanmthomas said:**
> The system you linked to looks pretty good to me.  It is certainly fast enough to do whatever you want to on Ubuntu.

I don't use Ubuntu, so I can't answer how people do it in terms of getting it preinstalled, running it alongside Windows, etc.   What I usually do (because I'm a tinkerer) is run my Arch on my first partition and leave another one open for testing out different distributions when they come out with new versions.  Can't say whether or not this is common though.  :)  

Do you think it's strange that the system I linked you to from Dell is selling the system with Ubuntu version 7.04 instead of the latest version, 7.10? Is uprgading to the newer versions similar in fashion as how one would upgrade Windowns/Tiger? Or would it be a terribly akward process? I see that System76 sells their systems with the latest version, but as you mentioned they are way overpriced for what they are packing inside their systems. I like their concept, and their environmental stance, but just don't care for their price. I could build my own, but I fear what I put together not working with the OS. My current system is dying, and is so old that upgrading it internally would be pointless.

Well, thanks again for your replies. Sorry to bug you or whomever else again. This should be it for a while.

Thanks!

---

### Post by jordanmthomas on 2007-12-09
> This is really going to make me look like an idiot, but what DRM media files and the like won't work, for example? Would this include movies I've downloaded over the years from various websites, streaming content on the web? Most of my video files are in .wmv and .avi format, so now I'm worried that they'll all be rendered useless. Would this also be the same for watching DVDs on my computer?
Basically, all you can't play are things you a) buy from iTunes or b) things you buy from Microsoft's store.
You can play an .avi you come across.  There is VERY rarely a wmv or wma you can't play.  Whatever it is that you download from iTunes you can't play either if it's encrypted.  You can play DVDs after you install a package called libdvdcss (which I believe is technically illegal in the US, but I know I'm not worried about it)
Streaming web content can be played with the mplayer-plugin and I never have troubles with it with the exception of sites that say "YOU MUST HAVE WINDOWS" although the content should work regardless.  I hate that.  The BBC is notorious for this, and I believe ABC is doing the same.

Upgrading is very easy.  I believe a tooltip will pop up and tell you that you can update to the newest version.  Then you click ok and wait for it to download and install.  Some people say that a clean install is better.  In that case, you just download the latest version on a CD and boot off it.  This won't update, but it will reinstall, so it's more like a Windows upgrade than a Mac one.  In the end, the update is painless usually.

---

### Post by daou on 2007-12-09
> **norfair said:**
> 
Do you think it's strange that the system I linked you to from Dell is selling the system with Ubuntu version 7.04 instead of the latest version, 7.10? Is uprgading to the newer versions similar in fashion as how one would upgrade Windowns/Tiger? Or would it be a terribly akward process? I see that System76 sells their systems with the latest version, but as you mentioned they are way overpriced for what they are packing inside their systems. I like their concept, and their environmental stance, but just don't care for their price. I could build my own, but I fear what I put together not working with the OS. My current system is dying, and is so old that upgrading it internally would be pointless.

Well, thanks again for your replies. Sorry to bug you or whomever else again. This should be it for a while.

Thanks!

Upgrading Ubuntu is easy: click a button and let it do its magic. 

However, I don't know if it is the same for Dell Ubuntus. I heard this somewhere on the net, so I have no idea if it is true or not: apparently Dell packages some modules (drivers) for certain hardware on their systems that aren't found in Ubuntu. So the upgrade might not work as easily. Also, (again a rumor I heard) Dell voids their warranty if you replace the OS, meaning if you install a normal Ubuntu on top of theirs.

If someone has better knowledge about this, feel free to correct me.

---

### Post by norfair on 2007-12-09
> **jordanmthomas said:**
> Basically, all you can't play are things you a) buy from iTunes or b) things you buy from Microsoft's store.
You can play an .avi you come across.  There is VERY rarely a wmv or wma you can't play.  Whatever it is that you download from iTunes you can't play either if it's encrypted.  You can play DVDs after you install a package called libdvdcss (which I believe is technically illegal in the US, but I know I'm not worried about it)
Streaming web content can be played with the mplayer-plugin and I never have troubles with it with the exception of sites that say "YOU MUST HAVE WINDOWS" although the content should work regardless.  I hate that.  The BBC is notorious for this, and I believe ABC is doing the same.

Upgrading is very easy.  I believe a tooltip will pop up and tell you that you can update to the newest version.  Then you click ok and wait for it to download and install.  Some people say that a clean install is better.  In that case, you just download the latest version on a CD and boot off it.  This won't update, but it will reinstall, so it's more like a Windows upgrade than a Mac one.  In the end, the update is painless usually.

Thanks again. You've been most helpful! It seems again as though I shouldn't be too terribly inconvenienced should I "switch" to Ubuntu soley. 

> **daou said:**
> Upgrading Ubuntu is easy: click a button and let it do its magic. 

However, I don't know if it is the same for Dell Ubuntus. I heard this somewhere on the net, so I have no idea if it is true or not: apparently Dell packages some modules (drivers) for certain hardware on their systems that aren't found in Ubuntu. So the upgrade might not work as easily. Also, (again a rumor I heard) Dell voids their warranty if you replace the OS, meaning if you install a normal Ubuntu on top of theirs.

If someone has better knowledge about this, feel free to correct me.

Interesting. I'm really not even a fan of Dell, but they are one of the very, very few computer companies that make a system with Ubuntu/Linux. I might shoot them an email and hopefully verify/debunk the rumor. Thanks for the heads up!

---

### Post by jordanmthomas on 2007-12-09
It probably just voids any support you get from them, not hardware warranty (I pray to God, because that would be retarded)

---

### Post by norfair on 2007-12-09
Just to quickly make note, I just contacted Dell regarding my possibly upgrading their installed 7.04 Ubuntu to a new version should I buy their system, and here's what they had to say just now via my online chat session with them (Dell's responses are in blue):

[COLOR="Blue"]How may I help you with your purchase today?[/COLOR]

I am interested in purchasing your Dell Inspiron 530N with the Ubuntu OS and have a question or two...

[COLOR="#0000ff"]What is the question?[/COLOR]

I see that it is installed with Ubuntu version 7.04, but the latest version is 7.10. If I upgrade once I get the system, does this void any kind of agreement or anything?

Furthermore, would it cause problems with the configured hardware? I didn't know if the system was specifically built around 7.04 or simply Ubuntu/Linux in general. 

**[COLOR="#0000ff"]yes you can upgrade the OS, however you need to call the technical support for this not to void the warranty of your computer so that they would have history of what happened to your computer[/COLOR]**

I see. So I can upgrade and so forth, but after doing so I have to call in. Is this is the same should I add memory or swap out the hard drive, or is this added step for the operating system only? Thanks.

[COLOR="#0000ff"]yes that is right[/COLOR]

One more question, and I don't mean this to sound abrasive, but what would the reason be for my needing to contact you regarding the OS upgrade? Is is just in case there is an issue with the OS and it messes up my system. Thereby having the liabilty of reparing be mine and not Dell's? 

[B][COLOR="#0000ff"]So that anything happens to your computer, once you call the technical support for help for repair, our specialist can diagnose the trouble in your computer[/COLOR]
[/B]
Gotcha. That makes sense. You've been very helpful. I have no more questions. Thanks again!

---

So, it seems it can be done, but in order not to void the warranty, I simply need to let them know of any major changes so as to keep the system info they have on me updated should I ever have a problem. Sounds okay with me, I guess. Thanks, though, for pointing this potential issue out to me!

---

### Post by webdr on 2007-12-09
Please do yourself a favor, I know it is difficult to leave windows, but even as awesome as gutsy is, it still requires a commitment on your part. I left Windows two years ago, here's a screencast of my latest machine: [http://www.markw.net/out2.ogg](http://www.markw.net/out2.ogg)

As recent as 6 months ago I had thought about leaving linux to return to windows because that was the environment I was VERY proficient in. But upon consideration of windows crashes, viruses, spyware, security, I chose to stay the course. 

In short that decision was one of the best I've made. I moved to python and gambas for programming,   open office automation still isn't quite as friendly as MSO's VBA, but I am sure it will get there soon.

Everyday I encourage and support people whom are leaving the windows and even mac world behind, like anything worthwhile, you may wonder about the decision to leave windose, but in the long run, you'll be glad you did.

God's Speed,
-WebDr

---

### Post by norfair on 2007-12-09
> **webdr said:**
> Please do yourself a favor, I know it is difficult to leave windows, but even as awesome as gutsy is, it still requires a commitment on your part. I left Windows two years ago, here's a screencast of my latest machine: [http://www.markw.net/out2.ogg](http://www.markw.net/out2.ogg)

As recent as 6 months ago I had thought about leaving linux to return to windows because that was the environment I was VERY proficient in. But upon consideration of windows crashes, viruses, spyware, security, I chose to stay the course. 

In short that decision was one of the best I've made. I moved to python and gambas for programming,   open office automation still isn't quite as friendly as MSO's VBA, but I am sure it will get there soon.

Everyday I encourage and support people whom are leaving the windows and even mac world behind, like anything worthwhile, you may wonder about the decision to leave windose, but in the long run, you'll be glad you did.

God's Speed,
-WebDr

Thanks for the encouragement! It's nice posting here, as when I was trying to buy an iMac last month (which I did twice and had to return due to quality and customer service issues) almost everyone from users on the various Mac boards to Apple staff members in the stores had this terrible elitest aire about them (though there were some very helpful people on the boards, they were just outshined by the overzealous Apple enthusiants/Windows bashers). This board is quite refereshing! I hope to give Ubuntu a try soon... Well, as soon as I can find an Ubuntu PC! Thanks again for your comments.

---

### Post by CaptainInsaneO on 2007-12-09
> **jordanmthomas said:**
> It probably just voids any support you get from them, not hardware warranty (I pray to God, because that would be retarded)

lol. Are we brothers?! You talk just like me!

---

### Post by philinux on 2007-12-09
Everything works for me except my microphone either headset or webcam :(

---

### Post by jordanmthomas on 2007-12-09
> **CaptainInsaneO said:**
> lol. Are we brothers?! You talk just like me!

I suppose anything is possible.

---

### Post by SunnyRabbiera on 2007-12-09
Its really up to you, its a very good thing to look at alternatives.
The coolest thing about Ubuntu is that you can use it without even installing it to get the feel of the OS, this is due to the live CD function witch is sort of like a "try before you buy" thing without even laying down a nickel.
Running linux is almost like running a apple, not everything will work but it gets the job done.
But if its one thing to like about Ubuntu is its community, trust me you are in for a ride.

---

### Post by baxterdog on 2007-12-09
I like windoze for some things, probably because I am just plain used to the way things are organized. I also like mac for some things due to the way they are organized.

BUT, I finally feel like I'm at home with Ubuntu. I have used Redhat, knoppix, & moeppis. The setup just feels right. I used to reinstall Windoze every ~6 months because I stopped installing updates when they broke something that worked and the OS just got 'cobwebby'.

Got totally tired of resetting Everything, Every Time. 

With Ubuntu I spent maybe a half hour customizing and now just get back to work.

As far as the hardware goes... build your own! It's easy, rewarding, and fun. For $400US you can put together a decent desktop at newegg. The 3 year maintenance from Dell is just not worth the extra cost.

Remember, have fun, life is a journey.

---

### Post by merlinDwizzard on 2007-12-09
Go for it !!!  I made the switch myself and I am not going back !! I am an IT student and windows is the primary OS of study, although last semester included managing and maintaining a Linux operating system. With that being said, I dual boot my acer aspire 5601awlmi with the ubuntu at/around 50 gig. I still have the windows on a separate partition, but that is going to change now that I figured out how to use Virtualbox.(really quite simple). You most likely fall in love with linux as I did. To quote something I read on this forum,"Linux in not a better windows than windows. It's a better operating system than windows." Just be prepared for the learning curve. Hey, if I can do it so can you. Good luck

---

### Post by crimesaucer on 2007-12-09
I would just recommend dual-booting ubuntu and xp. That way you can learn ubuntu, and still have a backup xp just in case. You'll love ubuntu, and soon you'll learn how to do most everything that you did on Windows in Linux.

---

### Post by eriksallstrom on 2007-12-09
SWITCH!

I switched a little more than 6 months ago. In the beginning a lot of simple things were tricky because I didn't know how to do them, but now I find my self rebooting in Windows not even once a month.

Some advantages are:
- Ubuntu uses a lot less system resources (could give your old computer a new life, maybe with Xubuntu?)
- Installing programs for anything is usually so much simpler: Just start the package manager, search for what you need of you don't already know a specific program, and then just select and click install. That's so much better than Windows!
- You don't need an antivirus program hogging your system and you don't have to worry about viruses.
- There's a neverending learning curve - after you reach the point were you work more efficiently with Linux than Windows, you'll just keep on getting better and more efficient!
- It's free! I recently compared the chepest configuration of Dell's Ubuntu desktop computer with the same configuration with Windows, $329 vs $479! Plus there are so many open source programs to go with it.
- This forum! You can find answers to almost all your questions here and if not, just ask!

I hope you make the switch, but try running with dual boot for a while if you don't want to make the final decision yet.

Good luck!

---

