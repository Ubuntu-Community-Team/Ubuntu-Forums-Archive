---
title: "[SOLVED] I`m not giving up but windows first."
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by robsykes on 2008-01-12
A friend gave me this pc with ubuntu installed on it. I think you will agree that was a mistake. I have never used a computer before. It`s been three and a half weeks now and I really don`t understand what I`m doing. It seems to me that I need to use windows first as most guides and help for ububtu assume a knowledge of windows or osx (whatever that is). I have a windows xp disk with the code/key(?).
 Here is the plan. Wipe ubuntu, install windows, get stuff working. I understand I can mess about with ubuntu from the cd at first until I get my head round it, then have both windows and ubuntu on the same computer, and then when I know exactly  what I`m doing reinstall ubuntu  on the whole thing. 
 Don`t get me wrong, I think this place is brilliant. I love the way you all help each other and everything`s free but it`s way over my head. There is nothing on this computer I need to save, Can somebody tell me how to wipe ubuntu and install windows from the windows cd please. I`ve not given up, I just think I`ll never understand ubuntu until I understand windows. Thank you. Rob Sykes

---

### Post by Pevichaey5 on 2008-01-12
just put in the windows disk, and delete all the existing partitions, or go for a dual boot right away

---

### Post by philinux on 2008-01-12
You will have just as much learning to do with either system.

---

### Post by Stu Ruckus on 2008-01-12
To install Windows XP on a computer on which Linux is currently installed (and assuming that you want to remove Linux), you must manually delete the partitions used by the Linux operating system. The Windows-compatible partition can be created automatically during the installation of Windows XP. 

IMPORTANT: Before you follow the steps in this article, verify that you have a bootable disk or bootable CD-ROM for the Linux operating system, because these steps completely remove the Linux operating system from your computer. If you intend to restore the Linux operating system at a later date, verify that you also have a functional backup of all the information stored on your computer. Additionally, you must have a full release version of Windows XP to use during this installation. If you intend to use a Windows XP upgrade CD-ROM, a CD-ROM of a qualifying Windows product must be available. Setup from the Windows XP upgrade CD-ROM will prompt you for this CD-ROM.

Linux file systems use a superblock at the beginning of a disk partition to identify the basic size, shape, and condition of the file system. 

The Linux operating system is generally installed on partition type 83 (Linux native) or 82 (Linux swap). The Linux boot manager (LILO) can be configured to start from either of the following locations: • The hard disk Master Boot Record (MBR)

-or- 
• The root folder of the Linux partition 
The Fdisk tool included with Linux can be used to delete the partitions. (There are other utilities that work just as well, such as Fdisk from MS-DOS 5.0 and later, or you can delete the partitions during the installation process.) 

To remove Linux from your computer and install Windows XP, follow these steps: 1. Remove the native, swap, and boot partitions used by Linux: a.  Start your computer with the Linux Setup floppy disk, type fdisk at the command prompt, and then press ENTER.

NOTE: For help with using the Fdisk tool, type m at the command prompt, and then press ENTER. 
b.  Type p at the command prompt, and then press ENTER to display partition information. The first item listed is hard disk 1, partition 1 information, and the second item listed is hard disk 1, partition 2 information. 
c.  Type d at the command prompt, and then press ENTER. You are then prompted for the partition number that you want to delete. Type 1, and then press ENTER to delete partition number 1. Repeat this step until all the partitions have been deleted. 
d.  Type w, and then press ENTER to write this information to the partition table. Some error messages may be generated (because information is written to the partition table), but they should not be significant at this point because the next step is to restart the computer and then install the new operating system. 
e.  Type q at the command prompt, and then press ENTER to quit the Fdisk tool. 
f.  Insert either a bootable floppy disk or the bootable Windows XP CD-ROM, and then press CTRL+ALT+DELETE to restart your computer. 
 
2. Follow the instructions on the screen to install Windows XP.

The installation process assists you in creating the appropriate partitions on your computer.

---

### Post by jcwmoore on 2008-01-12
I believe that durring the install of windows you should have the option to wipe the hard drive and use it.  It has been a while sense I have installed win XP though...  I would recommend that you get, if you don't already, get a ubuntu CD first, that way if some thing goes bad you can go right back to where you are now.  For general help with ubuntu, or computing in general, I would say look for a video on youtube on what you want to do.  The best way to learn is by following some one who has already done it.

---

### Post by T-MAN3000 on 2008-01-12
What makes you think you'll learn Windows faster than Ubuntu? I presume that  you just want to surf the internet and check your email, not do any complicated system administration. 
In my opinion it's much more difficult to get a safe and robust Windows system up and running as a beginner, than an Ubuntu system (because Ubuntu is good to go after a fresh install and Windows requires you install a virusscanner, anti-spyware tools etc.)

So my suggestion to you is: keep trying with Ubuntu, find someone near that can help you, or ask on the forums.

---

### Post by isparkes on 2008-01-12
I'll try to give a balanced answer, even if I am thoroughly biased (I was a Windows user, gave up 2 years ago and will never, ever go back).

Pro Windows: You'll find a whole bunch of material to get you going - a good place to start will of course be books and magazines, Of special interest, you might want to get involved in an ECDL (European Computer Driving License) course or something of the like. This is a structured course that should get you up to a good level of competence. People generally understand Windows, and you are likely to find help much more rapidly. This is likely to change as the years go on, but at the moment it's so.

Pro Ubuntu: You'll actually find Ubuntu easier to work with once you have got over the initial learning curve. You'll not have to regularly wipe and re-install your computer's software, and in fact you'll find Adding and Removing applications much much easier in Ubuntu, and it will run for years without major maintenance. The alternative is hunting around for hours and hours looking for the software to do the task you want in Windows, installing and removing software, and generally gumming up your system. The central list of "approved" packages in Ubuntu is actually a rarely mentioned highlight. And of course, all the stuff in the list is available without having to break out the credit card.

In short, in my opinion, it you are a complete n00b, you're probably right to move through the Windows stage first, UNLESS YOU HAVE someone with the time and will to mentor you. Think of it as riding a moped before you get on a real bike...

However, more power to you for even having the foresight to know that there IS an alternative to Windows. Don't forget your dream... ;)

---

### Post by kleo skywalker on 2008-01-12
Your experience is interesting - that you feel help guides presume a knowledge of Windows. That is not something I come across often on these forums.
Like its been said, if you are a first-time computer user, you will need to learn whatever you use. And managing a Windows system will probably be more work than an Ubuntu system, particularly in terms of security (anti-virus and all that). I used Windows for many years before switching to Ubuntu a few months ago, and I'm much more comfortable with Ubuntu. I don't have to worry about virus and malware. And even if there's a problem or I can't figure out how to do something, I post here and it's almost always sorted :)
So if you may be persuaded to try Ubuntu for a little longer, there are somethings that can be done to fix your problems - if you post what guides you're looking at, maybe someone will post links to ones that don't presume Windows experience (there are plenty of those). And if there's something specific you want to find out, like how to do a particular task, post and people will help out.
Best part - if it works out, great; if not, you still have that windows disk.
Whatever you decide to do, good luck!

isparkes, 1) why do you say it takes hours to install and remove software in Ubuntu? I find it fast and simple! 2) Since robsykes is using a computer for the first time, she/he probably doesn't have any set preferences in terms of applications - isn't that a bonus? She/he doesn't have to look for "replacements" for Windows software, simply software to do particular tasks which is really easy for common stuff.

---

### Post by esteckis on 2008-01-12
As a Linux newbie and window XP user, either way that you go, I would suggest you always use the Firefox browser with no script plugin and get an on-line mail account instead of downloading your emails to your computer. Also any messenger that you use, do not allow the send file option through the messenger. If a file is that important to send or receive, email it.

Of course, any windows updates have to be done through the Interent Explorer.

---

### Post by monte48lowes on 2008-01-12
Hey Rob,

A default windows install will have very few programs installed. This is nice since it's simple. The number of programs installed will grow over time as you install the software you find browsing around. By default ubuntu comes with many programs installed. Sometimes there are two programs which accomplish the same things. That can be confusing.

Here are some questions to ask yourself:

1. What do you need to accomplish with the computer?
2. What programs do I have installed that can perform my needed task?
3. Do I have all of the driver CDs for the hardware installed on my PC?

Anything new is always difficult. Be patient which ever path you choose.

Mike

---

### Post by robsykes on 2008-01-12
Thanks for all your help guys.
  People I`ve spoken to can`t believe I`ve tried linux first. I appreciate  what you guys do and are trying to do and I`ll always speak up for it. Has anyone else here started using computers on ubuntu. I`m really sorry but I just don`t get it. I promise you I really have tried, but I can`t do it.
  So what do I do. Some other people tell me I`d be better off if I started with windows. I`ve got to try it.
 By the way, I spoke to the guy who gave me the computer . He is mightily disappointed  in me. But I just want to get this computer thing nailed.

---

### Post by ubuntu-freak on 2008-01-12
STAY!! 
 
We don't mind how basic your questions are. You will get more help with learning linux than windows. 
 
The terminal people mention for commands is in applications>accessories
 
Open that and follow my guide to get all multimedia working and streams streaming.
 
[http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)
 
Oh and STAY:)
 
Nathan

---

### Post by eolson on 2008-01-12
Did not start on Ubuntu,  but before Windows was even a thought.  In the days when you had a fron t panel with diodes and dip switches and my first large computer was an IBM 360/20 not even tiny by todays standards except in sheer bulk.  Moved on to Unix,  CPM, DOS, and finally Windows.   Turned the whole mess off in 1993.   Started again in something like 2000 and tried Windows and really wasn't happy with all the hidden stuff going on.  Got a copy of Redhat 7 and Mandrake something (both Linux Distros)  and felt right at home.  Been Windows free ever since and couldn't be happier.

Short answer,  stick with Ubuntu.

---

### Post by bagguley on 2008-01-12
Rob

Id like to back up reassuringlyoffence's comments. Whilst being asked to enter lines into the terminal sounds daunting it isnt so. Further more you can almost avoid it completly nowadys with ubuntu. I am not an experience computer user at all, it does however come with time. Ubuntu is no harder than windows to master (easier if anything). Give it a little more time, post every question you can think of onto this forum and you will get help!

On another note, its an interesting reflection that their seems to be little absoloute beginner guides out there and maybe something we could look at, Ubuntu ECDL?Or UCDL....or something..

---

### Post by oldos2er on 2008-01-12
There's no reason, if you're new to computers, to go with Windows first. In fact, you'd have to unlearn Win* concepts to fully understand Ubuntu. I think you should just go with Ubuntu, and avoid Windows altogether.

---

### Post by Roaster on 2008-01-12
As other posters have said, I think I have had problems learning Linux,i.e. Ubuntu, because I've had to 'unlearn Windows". As time passes you will find Linux easier in many respects than Windows. At any rate, just boot from the Windows XP cd and format your hard drive and install. I'll almost bet that over time you will be back. Have a good trip and return soon:)

---

### Post by gruss on 2008-01-12
Stick with it a bit, if you are a complete newbie.  Most of the "windows" people telling you that linux is hard probably dont know how to use windows either.  I've just recently made the leap to ubuntu on a couple pc's at the house and to be honest out of the box Ubuntu blows a clean XP install out of the water.  pc's that I always had to find drivers forin xp or w2k ubuntu loaded on install, had a word processor, internet email prog already there...
I'm a long time windows guy for no other reason than it was convienant and I have to work on it every day.  Biggest prob with Ubuntu?  no friendly expert next door to help you out, biggest prob with windows?  everyone is an expert and wants to help you out ;)  Seriously though from what I've seen an XP install would be more invlolved than and Ubuntu install and it really isnt "easier" to learn, and if I had to do it all over again I would have started on linux.

Plus this is one of the friendliest forums for newbs that I have ever encountered, on par with a good motorcycle forum.  Quick responses and just a good vibe.  If you need something ask, Im a sys admin in a windows evironment irl and the folks here have been a huge help to me in my recent ubuntu dabblings and I can assure you that my windows knowledge was of little help figuring the stuff out and I'm "one of those guys" that drops back to a command line to fix stuff, so although it can be frustrating learning something new, its not any harder than the alternative.

---

### Post by doorknob60 on 2008-01-12
Trust me, installing Windows is a pain in the butt! You need to download loads of drivers, it comes with no software so you need to download software and it's not the kind of thing a computer newbie could do. So I HIGHLY recommend staying with Ubuntu, and any problems you have we can help you fix.

---

### Post by blueridgedog on 2008-01-12
To the original poster, I was going to repeat what others have stated, that Ubuntu comes with most everything you need, that you could clarify your expectations and define what you are trying accomplish with your computer and that we could help fine tune Ubuntu to work with your needs...but

I get the impression that you have some specific learning objectives in mind and part of that may be fitting in with a a world or employment paradigm that has MSWindows at its core.

I wish you luck, put in the MS CDROM, delete all partitions (I think it is highlight them, Delete, L to confirm - going from memory).

That said, a lot of the people I know who have "figured out this computer thing" have come to Linux and Ubuntu is be best example I have seen of a desktop Linux.

---

### Post by kleo skywalker on 2008-01-13
> **robsykes said:**
>  I`m really sorry but I just don`t get it. I promise you I really have tried, but I can`t do it.
  So what do I do.

What is it exactly that you don't get? If you could be a little more specific with your problems (for example, I want to do *task* but don't know how or I can't find this *application* anywhere), people will try to solve them. 

Quite a few people have posted recommending you stick with Ubuntu, it's simply because they believe Ubuntu is easier. Like, in all the years I've used a computer, I never installed Windows - the tech always came and asked me for all the disks that came with different hardware and did it. I didn't even attempt it when the tech offered to talk me through it over the phone. Installing Ubuntu was a breeze - I did it several times just for the kick of being able to install an OS! I've never even needed to look at those disks with drivers since I got Ubuntu, because everything was detected automatically. I don't worry about viruses and similar rubbish ruining or bloating my computer anymore. I don't have to worry about paying lots of money for original software or suffer the hassle of pirated copies. Installing things is easy and centralized. Even the simplest (and seemingly silly) questions such as "what music players can I choose from" yields loads of answers on these forums.

Point being, if you say something generic like "it's hard" or "I don't get it", the responses will be generic too like "it's easy" or "give it another shot". On the other hand, if you ask specific questions like "I don't know how to chat with my friend", you'll get help with the tasks you need to do like "try this instant messenger, here's where to find it and here's how to log in". 

For starters, what do you want to do on the computer? (Examples - browse the internet, make documents, listen to music, and so on.)

And a very important point, are you sure you want to go totally by what other people are saying? Who are these people who say Windows is easier and Ubuntu is hard? Chances are, they're people who've never used Ubuntu, or have used Windows for a long time and find it hard to deal with something different (neutral statement, no offense meant to them at all). Or your friend who you say is "disappointed in you" - in my (humble) opinion that's not fair because it's alright if you're finding things hard. Or the people posting and trying to persuade you to stick with Ubuntu :D - that's their opinion, and you can evaluate their reasons. It's **your** choice after all!

---

### Post by tylerspaska on 2008-01-13
give this tutorial a try if you have having trouble setting up your ubuntu box

[http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html](http://linuxondesktop.blogspot.com/2007/11/creating-your-ultimate-ubuntu-710.html)

---

### Post by ugm6hr on 2008-01-13
> **robsykes said:**
> By the way, I spoke to the guy who gave me the computer . He is mightily disappointed  in me. But I just want to get this computer thing nailed.

I use Ubuntu and XP (although predominanlty Ubuntu), and appreciate the differences.  

The reason most advice here compares Ubuntu to Windows (Microsoft) is that the majority of users come from Windows.  However, there are people who learn on Linux (including in some schools), but the difficulty is finding someone to *teach* you on Linux / Ubuntu.  Problems start when you can't do something, and there is no one who you know who can tell you how (cos they all use Windows).  The other reason is that IT concepts can be quite abstract to explain from scratch.  It's not quite a direct comparison, but think about how you would describe the colour red to someone who was blind....  It's much easier if you can relate it to other similar colours or objects that are red - but obviously they will never have seen any of those colours before.  Of course, you can teach someone how to use a computer if you are stood beside them, telling them exactly what to do, but this is not possible in an internet guide.

Anyway, I digress...

My first suggestion: Installing an Operating System is not something that someone who has *never* used a computer should be attempting.  That holds true for both Windows and Linux.  If you are struggling to *use* a computer, then installing an OS will not be straightforward.  Perhaps the person who gave you the computer could do it for you?

However, I would like to say you've obviously come a long way from knowing nothing.  You have obviously found out what Firefox is, and how to get online, and worked out how to post on this forum.  That itself is a big achievement, and I think you should be proud of yourself.  Even logging into a computer can be confusing if you've never done it before.

Having said all that - what else do you want / need to do on your computer?  Perhaps if you gave us an idea of what you want to do, we could point you in the right direction.  Most people's initial experience is limited to internet / email / word processing, all of which behaves in a similar way to Windows.  In fact, the analogy of describing a colour stands with regard to typing a letter in Windows vs in Ubuntu - both are just as difficult to describe.

I hope that helps clarify things, and if you want any further advice - feel free to ask here.  I know it will be hard having your advice offered by strangers, rather than people you can talk to face-to-face, but you can see how many people offer help here.  If you do end up going down the Windows route - be aware that forums like this don't exist.  So if none of the people who have suggested you try Windows have been willing to install it for you, I would be inclined to say you will probably be on your own if you run into problems on Windows.

PS: If I was you, I would be disappointed in my friend who gave me a computer with Ubuntu installed, but couldn't be bothered to pre-install Flash for you.

---

### Post by fiddledd on 2008-01-13
Ok, I'm going to be honest here, IMHO Ubuntu isn't easier than Windows, Ubuntu is more secure than Windows and it's free. You can get tons of software for linux and its all (mostly) free. You also don't need the latest CPU, GFX card etc, to run Ubuntu (Linux doesn't play the game that MS does with hardware manufacturers). However some of your hardware may not work with Ubuntu (Webcams, USB framegrabber are commonish examples), Most, if not all of your hardware will work with Windows. This is because all hardware comes with an install cd with drivers for Windows, sadly this is not the case with linux (not the fault of Linux the words "free" and "manufacturer" don't go well together). My setup (which is not exactly high end) will easily handle all the eye candy Ubuntu has to offer, 3D effects etc (I disable them after testing they work :) ), I doubt my system will handle all the eye candy Vista has to offer, in fact I'd struggle to run Vista at all, unless it was at a snails pace, with any 3D effects. 
There is howerver one reason I would say stick with Ubuntu, if you are new to computers you are going to want help. If you need help with Windows you will spend a lot of time searching Google, and eventually (if you don't give up) you may find some of the answers you are looking for. The best thing about Ubuntu, IMHO, are these Forums. Here you will find thousands of people willing to help with any problems you have. You can't buy that kind of help, it really is priceless.

(Let's hope i don't get flammed now because I didn't sing from the same Hymn sheet :) )

---

### Post by robsykes on 2008-01-13
First thank you all, you have persuaded me to keep on trying. So here`s the deal. My friend is coming over to get everything working. I`m not going to install windows.
 When he has, I`m going to browse the internet, get my music going have a mess about and see where we go.
 I assure you I will be back on this forum soon.
Cheers all

---

### Post by blueridgedog on 2008-01-13
Right On! +1

---

### Post by kleo skywalker on 2008-01-13
> **robsykes said:**
> First thank you all, you have persuaded me to keep on trying. So here`s the deal. My friend is coming over to get everything working. I`m not going to install windows.
 When he has, I`m going to browse the internet, get my music going have a mess about and see where we go.
 I assure you I will be back on this forum soon.
Cheers all

You have finally been persuaded!
When your friend comes over, do ask him to show you how she/he is doing things - at least the basic stuff. If she/he could show you the following, you'd be good to go: how to install stuff using **Synaptic Package Manager** and **Add/ Remove** (it's just 3-4 simple steps), where the **Terminal** is and how to use it (people may offer you command line solutions which may be easy but puzzling), get your music and videos playing (this includes giving you a music playing application you like in case you don't like the default one), installing Flash and codecs.
Good luck!

---

### Post by bagguley on 2008-01-13
Awesome! Any help you need just post! Its all worthwhile I assure you.

---

### Post by StooJ on 2008-01-13
Thrilled to hear that you're staying after all.

I would say that Windows is only ever easier to use if you've never used windows before. The hardware question is a little trickier, as hardware manufacturers do tend to ignore everything but Windows when the sell a product.
There are very few bits that I haven't been able to get working with Ubuntu though, and most of them work straight out of the box.
In comparison, most hardware installed in Windows needs driver disks and sometimes even a reboot.
If I buy an electronic doo-hickey out of a store, I'd say it's more likely to work straight away in Ubuntu than it is in Windows.

Installing programmes might seem more difficult to a Windows user who expects to be able to download a programme, double click on the exe, click next, click I agree, click next, click next, click finish.

Finding things with the package manager may seem difficult. When you google "Media player" the second result will be winamp. You can download Winamp from the comfort of your browser. Then install it. Sounds pretty simple, and it didn't take long.

Installing a programme in Ubuntu is very very different, and counter-intuitive to windows users. However, I think it makes a lot more sense to someone that has never used an OS before. In your applications menu is an option to add/remove. Click on it and you're presented with a list of programmes that will definitely work with your computer.

The terminal is for solving problems. Like regedit. Something to be used when there is a problem, something to be talked through without needing to really know what you're doing.
However, I find it a lot easier to explain and understand terminal commands than regedit. I can break apart a terminal command step by step and see exactly what it is doing. I've a harder time explaining what HKEY Classes are and why they need changed to fix something.

There is an illusion that help is hard to find with Ubuntu. You can't throw a stone these days without hitting a "Windows expert". I spend a lot of my time cleaning up their mess. When I ask for help here, I can be confident that I will quickly get a solution to my problem from someone who really does know what he's or she is talking about.

There is also an illusion that people who come to Ubuntu (or linux in general) need to "learn" linux. I'm not really sure why people think this, I never had to "learn" windows when I installed it for the first time. I have learned windows after years (16 in my case) of using it. I am now learning Ubuntu as I use it from day to day, but I did not need to sit down and read a manual in order to play Solitaire or play music on either operating system.

Should you decide someday to really learn the nitty gritty of computers, then linux will give you a much better grounding in how a computer actually works, because you really can dive to the bottom of the pool, rather than skim the surface of implementation layers.

In the mean time, all the best with your computing adventure. You've had the good fortune of being provided with a pre-installed linux OS (an uncommon luxury). You have a worry-free computing environment with lots of useful pre-installed software, and a worry-free way of getting more. Please post any questions you have so that people can help you out. They're very keen to do so.

---

### Post by robsykes on 2008-01-14
Ok. My friend came over yesterday and got everything sorted and now I`m cooking!!
  He sorted flash out, he fixed the sound and showed me how to sort my music out. He installed Amarok. So now I`m enjoying the world wide web - youtube and livemusicarchive esp.
  Can you believe the problem with the sound was that I`d plugged the wire into the wrong hole doh! Imagine, I've no idea what I'm doing and I'm looking at this forum and typing lspci into the terminal and looking at all this stuff I`ve know idea the meaning of, and searching for soundcards without knowing what they are, and banging my head against a brick wall for days and days, about to chuck the stupid thing in the bin and the whole time the speakers aren't plugged in.
 Anyway a huge thank you to everyone who offered their help and advice and.....    ( I don`t know how to do this but)    ......... I think we can mark this one SOLVED!

---

### Post by ugm6hr on 2008-01-14
Glad you got it sorted.

Computers are great when they work!  Not so great when they don't!

PS: You can mark this solved by going up to the "Thread Tools" near the top.

---

### Post by kleo skywalker on 2008-01-15
> **robsykes said:**
> Ok. My friend came over yesterday and got everything sorted and now I`m cooking!!
  He sorted flash out, he fixed the sound and showed me how to sort my music out. He installed Amarok. So now I`m enjoying the world wide web - youtube and livemusicarchive esp.
  Can you believe the problem with the sound was that I`d plugged the wire into the wrong hole doh! Imagine, I've no idea what I'm doing and I'm looking at this forum and typing lspci into the terminal and looking at all this stuff I`ve know idea the meaning of, and searching for soundcards without knowing what they are, and banging my head against a brick wall for days and days, about to chuck the stupid thing in the bin and the whole time the speakers aren't plugged in.
 Anyway a huge thank you to everyone who offered their help and advice and.....    ( I don`t know how to do this but)    ......... I think we can mark this one SOLVED!

Lol if it makes you feel any better, I once plugged in something upside down and fried my hard disk.
It's great you have your Ubuntu up and running. Just one idea - when I first tried Amarok, I found it's interface too complex, so I switched to Exaile. Point - you always have loads of options.
Good luck and have fun!

---

### Post by mdpalow on 2008-01-15
> **robsykes said:**
> Ok. My friend came over yesterday and got everything sorted and now I`m cooking!!
  He sorted flash out, he fixed the sound and showed me how to sort my music out. He installed Amarok. So now I`m enjoying the world wide web - youtube and livemusicarchive esp.
  Can you believe the problem with the sound was that I`d plugged the wire into the wrong hole doh! Imagine, I've no idea what I'm doing and I'm looking at this forum and typing lspci into the terminal and looking at all this stuff I`ve know idea the meaning of, and searching for soundcards without knowing what they are, and banging my head against a brick wall for days and days, about to chuck the stupid thing in the bin and the whole time the speakers aren't plugged in.
 Anyway a huge thank you to everyone who offered their help and advice and.....    ( I don`t know how to do this but)    ......... I think we can mark this one SOLVED!

One thing you probably learned after all this is there are many people here to help you. Tomorrow or the next day if/when you have a problem or don't understand something - do a search in the forum or on google to see if you get any immediate information on what you're having problems with and if no luck or you don't understand then post in the forum. Of all the questions I've posted in this forum, there's only been one post I never got an answer to. :)

Also, if your computer is running like you want right now - you might want to make a back-up. :)  Just in case... 

See link in my signature below and Private Message me if you need any one on one help. If you don't know how to private message, click my name in the top left corner of this message and select the option to private message.

good luck...

---

### Post by monte48lowes on 2008-01-18
When performing any troubleshooting remember [Occam's Razor]("http://en.wikipedia.org/wiki/Occam's_Razor").

> The simplest answer is usually the correct answer.

I think you've had some experience with that now.

Mike

---

### Post by robsykes on 2008-01-18
Wow, I didn`t think this would be still up and running. Up to now I`m just ripping my cds with sound juicer and browsing. 
 It seems to me that once you've got everything up and working the rest is easy - and thats where (in a sense) I'm lucky. I don't have to solve all the windows issues that most people do - I don`t have to make my m4as play or get `word of warcraft` or whatever working.
 ( I got the compiz cube thing going all on my on my own ...... cool.)
 For new users, my advice, for what it's worth (which in computing terms is nothing) is to forget everything you know and start again. - Easy for me to say ..... I know. But honestly, since my problems were resolved I`ve had no worries with ubuntu .......... but then, I haven't tried to do anything difficult .................... yet...

---

### Post by pollywog on 2008-01-18
For what it is worth, I've got my Grandfather (82) using Ubuntu, with no Windows partition at all, and my Mother (62), doing the same. The hard part is for people to unlearn Windows. They never learned windows, so this is not an issue with them. It is odd that you seldom hear people complain about how different MacOSX is from windows, which I feel is more dissimilar to windows than Ubuntu is. But then again they had to sink alot of $$$ into that switch, and are therefore more likely to try hard to learn to use the new OS. Glad to hear that you decided to hang in there.

---

### Post by JoshuaRL on 2008-01-18
> **robsykes said:**
> For new users, my advice, for what it's worth (which in computing terms is nothing)

Man, you have a unique experience.  I'm younger, but almost all the people I know have at least a rudimentary brush with windows.  And I would think it'd be hard from a developer's side to think the way a person new to computers does.  And you seem to be able to be pretty comfortable with things already, so congratulations!

---

### Post by doctapeppa on 2008-01-18
I'm sorry, but I'm going to have to call shennanigans on this whole story. Am I the only one that thinks this is fake? 

Not only did he find ubuntu forums and is successfully posting and replying correctly; he is ripping CD's and has Compiz figured out! and all this several days after: "never used a computer before"

I have met A LOT of people who have very little computer experience in my day and things like "drag and drop", "copy/paste", saving files, zipping and unzipping are all foreign to them. Hell, those things are even difficult for people who have been "using" computers for years. 

Someone who is learning to use a computer for the first time is learning how to click with the mouse and drag and drop. They are completely new to the concept of an icon, a menu, a file and an archive. Yet this guy is talking about trying a different OPERATING SYSTEM! for god sakes..

I have no doubt that someone could learn to use a ubuntu computer easier that a windows one but c'mon. Some people learn faster than others but to be doing all of the things that this guy is aparently doing in three weeks is way beyond anything I can believe to be true.

Skeptical, 
doctapeppa

---

