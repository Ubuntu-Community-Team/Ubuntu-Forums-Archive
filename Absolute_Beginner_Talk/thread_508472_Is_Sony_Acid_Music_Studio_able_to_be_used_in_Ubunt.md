---
title: "Is Sony Acid Music Studio able to be used in Ubuntu???"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by PsychedelicWonders on 2007-07-24
Hello all, new to the board, and the world of linux.  I am going to be building a computer shortly, and would like to try out Ubuntu because frankly, I am just sick of all of the problems windows has.

A few things that are going to be a main focus on this new computer is the fact its going to be an HTPC first off.  I am going to run MythTV in order to have a complete "Media Center" for Tv, videos and music.  (I am going to use the iMon software and remote as a major angle of this HTPC.)

Second most important function Is to be able to create and edit music and videos.  I don't actually plan to make the music myself with instuments, but only use loops with Sony's Acid program.  I for sure want to use the Acid program, because it is the best looping software out there.  

There is also a program called Sony Vegas which is the video version of Acid basically.  They run in conjunction with each other.

Are there any patches that you can run with Acid in order for it to work on Ubuntu?  I really hope so, it could be the fatal straw as whether I chose Ubunu over windows.

And I would prefer to not have to run two OS, I want to do away with windows entirely.

Thanks for the help.

---

### Post by Mornedhel on 2007-07-24
Searching for "Sony Acid" in the Wine database returns a status of "Garbage" for Acid 6 (apparently the latest version as far as the Wine testers are concerned) : sorry about that, but it seems Acid 6 won't run under Linux. Acid 2 however is rated "Platinum", as in "installs and works perfectly". Vegas 6 and 4 are reported as Garbage as well, other versions were not tested.

Sadly, the Linux world is still a bit behind as far as music and video edition are concerned.

---

### Post by dmizer on 2007-07-24
without looking intensively ... i'll go out on a limb and say no.  typically sony's software doesn't even work well in windows.  or won't work unless you're logged in as administrator (read: rootkit).

if this is going to be a killer app for you, i suspect you're going to be disappointed.

however, you're already considering alternatives (ie, alternatives to windows). why not take a look at some of the offerings that ubuntu has that may be able to do what you need without relying on sony.

take a look at what's going on here: [http://ubuntuforums.org/forumdisplay.php?f=254](http://ubuntuforums.org/forumdisplay.php?f=254)
and here: [http://ubuntustudio.org/](http://ubuntustudio.org/)

---

### Post by PsychedelicWonders on 2007-07-24
Well I'll be honest with you, I'm a newbie when it comes to linux and music studios.  I have just been told that Acid is the best looping software around.    I never have used any type of music creating studio.  Obviously when people speak of it "the best looping softwear" they assume you are windows based.  

Plus I'm biased to the name.  :)  But not on the actual software.  It looks very "plain jane" but like i said, it's supposed to be "the best" looping program out there.

But if someone can show me a program that can stand up to Acid and works in Ubuntu, I'm open ears.

---

### Post by Tomosaur on 2007-07-24
I can vouch that Sony Sound Acid is incredibly good at what it's intended to do. For musical PRODUCTION - then no, Sound Acid will limit you in that respect, but if you need a good sequencer, you'll be hard pushed to find one better than Sound Acid. It is, in all honesty, one of the very few reasons I need to keep Windows. It is very quick, and although I couldn't call it 'versatile', if all you need is to record, sequence and do some minimal touch ups and whatnot, then Acid is the way to go.

On Linux, Jamendo is just far too buggy for me to rely on at the moment, and Ardour simply refuses to work, it keeps telling me my disk is too slow (Ardour reads from disk rather than memory, as far as I'm aware), although I really, really want to use it because it's supposed to be very powerful. Linux has a wide variety of apps for music production, but unfortunately for me there's either some problem with my computer, or the app doesn't do specifically what I need it to do. The only solution which actually works for me personally on Linux is Audacity, and although it is actually a fairly powerful tool, it's interface is just blown apart by Sound Acid, so I use that instead.

EDIT: Forgot to say - you could try installing Windows in a virtual machine and running Sound Acid that way.

---

### Post by PsychedelicWonders on 2007-07-24
Hmm.  Now I'm reconsidering going with Ubuntu.  Why is linux still so behind?

How does that work exaclty?  If Ubuntu would be registered on my hard drive as my main OS, then where and how would windows run on a virtual machine?  

Does anyone know if Acid will work well on Apple's OS?

I'm just trying to steer away from windows in general.

---

### Post by Mornedhel on 2007-07-24
> **PsychedelicWonders said:**
> Why is linux still so behind?

Linux used to be an OS by hackers for hackers (in the good sense of the word). I see Windows and ask myself, "Why is Windows so behind that it doesn't come with Perl and Python pre-installed ?"

---

### Post by dmizer on 2007-07-24
married to sony = married to windows

[http://www.sonycreativesoftware.com/products/product.asp?PID=443&PageID=70](http://www.sonycreativesoftware.com/products/product.asp?PID=443&PageID=70)

> System Requirements

    * Microsoft® Windows® XP or Windows Vista&#8482;
    * 800 MHz processor (1 GHz if using video)
    * 200 MB hard-disk space for program installation
    * 256 MB RAM
    * Windows-compatible sound card
    * DVD-ROM drive (for installation)
    * Supported CD-Recordable drive (for CD burning)
    * Microsoft DirectX® 9.0c or later (included on application disc)

edit:
that said, i understand there are some decent options in mac for music studio functionality (not sony).

---

### Post by PsychedelicWonders on 2007-07-24
If I run this dual boot system, with Ubuntu being my main platform, and I configure all of my hardware to work with that paticular OS (i.e. microsoft wireless keyboard and mouse, & iMon's remote control and software - I know for sure the remote can be transfered over to be used with Ubuntu, I'm not sure if you need the software at all, or you strictly use MythTv)

But will I have to then reconfigure all my extra hardware to work in Windows every time i boot up and want to use Windows?

I would only want to use windows when I absolutely have to.  For things like Acid & Vegas.  Everything else I want to do should run fine in Ubuntu.  

Or will each OS save my preferences on particular pieces of hardware like the wireless keyboard and remote?

I'm just trying to have my computer run as fast as possible, and windows just lags everything too much with all of the BS, which obviously all of you are already aware of.

---

### Post by Mornedhel on 2007-07-24
> **PsychedelicWonders said:**
> will I have to then reconfigure all my extra hardware to work in Windows every time i boot up and want to use Windows?

Short answer : no.

Long answer : nope.

(Not if you configured it under Windows as you would have in any other situation)

---

### Post by xpod on 2007-07-24
> How does that work exaclty? If Ubuntu would be registered on my hard drive as my main OS, then where and how would windows run on a virtual machine?


[http://www.virtualbox.org/](http://www.virtualbox.org/)
Has to be one of the simplest ways of setting up a virtual machine.

Makes the need for dualbooting obsolete.
With beryl or compiz also installed flipping back & forward betwen os`s is so much more fun that rebooting:)
Anyway,you should mabey get to know your new OS of choice first before you go worrying about virtual machine from within it.
Dualbooting is really your best bet for now, until you at least know wether it is for you or not .

> Hmm. Now I'm reconsidering going with Ubuntu. Why is linux still so behind?

It`s not meant as replacement for Windows unfortunately but mearly an alternative.

---

### Post by dmizer on 2007-07-24
i don't think a virtual machine is going to have enough power to handle the sound card in the way that visual studio will need to.

i wouldn't count on a virtual machine being your answer here.

---

### Post by dmizer on 2007-07-24
i already said it, but i'll say it again.  if you want to get away from windows, you're going to have to consider alternatives to sony acid music studio.

i despise mac, but that's personal preference.

that said; i think in your case, the best solution might be to take your concerns to your local mac store/vendor and have them show you something mac specific which might be able to accomplish what you desire.  just be wary of high pressure sales.

---

### Post by PsychedelicWonders on 2007-07-24
Well, the wireless keyboard, mouse and imon remote, all would work standard in windows, so i wouldn't really need to configure anything for that OS.  But I do know I need to configure things like the media center on the keyboard to work well in Ubuntu.  I just don't want to have to reconfigure it everytime I start up Ubuntu.

I'm not trying to base my studios on apple's OS.  I want Acid for sure, so I am willing to configure the proper OS it needs.  And I guess the best is to run a dual system.

Would it be a good idea to keep other music based programs like itunes in windows, or do these run fine in Ubuntu?

Like I said, I want to use Ubuntu as much as possible.  So if I can use itunes (only for purposes of an ipod) in Ubuntu, that would be sweet.

And then I would just keep the windows for Acid & Vegas only.

Does anyone have a good link on how to run a dual boot system that I could check out?

---

### Post by dmizer on 2007-07-24
frankly ... you're probably going to be much better off with two computers rather than a single dual boot system.

ubuntu doesn't need much.  i have a 750mhz pIII that boots as fast as my boss's 3.2g p4 win xp machine.

it will save you the hastle of having to reboot when you need studio, and you will have both ubuntu and windows at your fingertips.  if a single system is your only option, then do good research about how to correctly install a dual boot system.  it can and does cause problems if you make a mistake.

---

### Post by Mornedhel on 2007-07-24
iPod management was working in Ubuntu last time I checked, but I don't have an iPod, so I'm not actively checking. Some music players (Amarok comes to mind, and kudos to Exaile! for providing a GTK based quality player) are excellent when compared to the usual stuff running on Windows.

Dual-booting is extremely easy to achieve if you start from scratch. Just install Windows first, as it's used to writing its own MBR in a rather aggressive way, and leave enough space for Linux and a common partition (FAT32 is the best choice if you want to be able to use the contents under both OSes). Then run through the Ubuntu install process. But do be careful when you're partitioning.

---

### Post by dmizer on 2007-07-24
here's a good guide. [http://www.psychocats.net/ubuntu/partitioning](http://www.psychocats.net/ubuntu/partitioning)

DO make backups of your important data, or if you have your important data on a separate drive, disconnect the drive.

---

### Post by PsychedelicWonders on 2007-07-24
I'd really like to have just one computer.  It would make my world a lot easier, even if I have to reboot everytime I want to use Acid, which is not going to be that often to where rebooting would be a problem or a hassle.

Is there anyway you can have both OS's running at the same time, and somehow "toggle" back and forth between each one with some type of "hot key"?

And if in fact you have to restart/reboot your computer each time in order to run a particular OS, how do you make the computer dictate which OS it is going to start up when it reboots?

---

### Post by SPRL on 2007-07-24
I tried installing Sony Acid using Wine - total no go.

---

### Post by Mornedhel on 2007-07-24
You can "toggle" OSes, that's what virtual machines are for, but as pointed, it's not the best choice. If you manage to get dual-boot working, there's going to be a boot manager that lets you choose between your OSes (the Ubuntu-installed default one is GRUB), or automatically runs the first one (default setting) if you do not do anything for a while.

---

### Post by dmizer on 2007-07-24
> **Mornedhel said:**
> You can "toggle" OSes, that's what virtual machines are for, but as pointed, it's not the best choice.

i'll elaborate on that for clarity.

a virtual machine is a piece of software that pretends to be hardware.  it pretends to be a cpu, video card, network adapter, sound card etc.  but what it's really doing is using your actual hardware and piping it through to your virtual operating system so that your guest operating system can use it as though it was real hardware.

but the problem is ... that it's NOT real hardware.  so it causes problems for things which require special interaction with hardware ... eg, high fps video games and/or sound editing software; both of which would need to rely heavily on the physical capabilities of graphics cards and audio cards respectively.

what IS a virtual machine good for?  software based interaction.  stuff like quicken, or microsoft office, and internet explorer.  it's also fantastic for troubleshooting, and testing, among other things.

---

### Post by PsychedelicWonders on 2007-07-24
I like the fact that you can toggle back and forth with the virtual machine, but you scare me a bit when you say that a virtual machine might not be powerful enough to run a audio or video editing program.

So what if I were to set up a hard drive to run just Ubuntu, a hard drive to run just windows based programs, and then 3 additional hard drives employing RAID to save all of my files, one main one, one to make a back up of the main, and then one to make a back up of the back up. 

Is this possible?

Is there anyway to toggle back and forth between hard drives this way?  I would only be running windows for purposes of using Acid, and the only other program I would really need is the internet.  so toggling might not really be a concern of mine anymore, but the option would always be nice I suppose.  I do not want to have windows running all the time, only when wanting to do music stuff.  I just don't trust it to run in the back ground 24/7 along side of Ubuntu.  

How would I dictate which harddrive/OS I then would want to boot up upon startup?  Will it still give me a little dialog box to decide?

---

### Post by dmizer on 2007-07-24
i don't want to scare you.  i am just trying to make sure you really understand what your options are, and why.

as far as i know ... there is no way to have two actual operating systems simultaneously running on the same hardware such that you can toggle between them.

i believe your options are thus:
1) two computers (one ubuntu, one windows)
2) dual boot
3) mac

but there's always a chance someone will come along and prove me wrong.  in which case i'd be genuinely interested to see how it's done.

---

### Post by Torajima on 2007-07-24
> **PsychedelicWonders said:**
> I'm not trying to base my studios on apple's OS.  I want Acid for sure, so I am willing to configure the proper OS it needs.  

I don't get it, you admit you've never used Acid, or tried similar software on other platforms... so why are you so set on Acid?

If you use OSX, you can create loop-based music in Garageband, it comes pre-installed on every new Mac. As for more full-featured applications, none of the music professionals I know use Acid... they either use Digital Performer, Logic, or Pro Tools.

And yes, there are similar programs available on Linux. I've never tried them, so I can't tell you how good they are... but some of them look pretty slick.

---

### Post by PsychedelicWonders on 2007-07-24
When you say you can't have two simultaneously running OS' on one computer, do you actually mean to have them running at the same time to toggle back and forth?

Or you can't have two OS' on one system in general, even with a separate hard drives for each, and booting each one up and shutting down individually before booting up the second one?

The only reason I'm set on Acid is everyone over at cakewalk.com and one guy here has said Acid is the best looping program out there.

That's the only reason why I'm kinda set on it.  

I will admist it does look blande, but that doesn't dictate how it works.  Apparently, nothing else can touch it.  If someone can suggest something similar, by all means, but no one really seems to think there is anything comparable.

---

### Post by Henry Rayker on 2007-07-24
If you can try it out, ardour2 is a really good app. I don't know what is in the Ubuntu repos, but Fedora only had ardour 0.9, I believe, which wasn't nearly as nice as ardour2...if you can, build from source. However, I believe ardour is mostly for recording from an input...

However, if you have never even used Acid, I would give a couple of apps a shot before pigeon-holing yourself in to just one. There are a LOT of different recording and sequencing apps out there and so far. All of them have benefits, but all of them have their own pitfalls. Rosegarden, ardour and wired are some of the good ones that run under linux, though.

I would suggest giving the Musix distro a quick download. It's a live cd, so you can try everything without installing at all. I haven't used it, but I've heard really good things about it.

---

### Post by Tomosaur on 2007-07-24
> **PsychedelicWonders said:**
> I like the fact that you can toggle back and forth with the virtual machine, but you scare me a bit when you say that a virtual machine might not be powerful enough to run a audio or video editing program.

So what if I were to set up a hard drive to run just Ubuntu, a hard drive to run just windows based programs, and then 3 additional hard drives employing RAID to save all of my files, one main one, one to make a back up of the main, and then one to make a back up of the back up. 

Is this possible?

Is there anyway to toggle back and forth between hard drives this way?  I would only be running windows for purposes of using Acid, and the only other program I would really need is the internet.  so toggling might not really be a concern of mine anymore, but the option would always be nice I suppose.  I do not want to have windows running all the time, only when wanting to do music stuff.  I just don't trust it to run in the back ground 24/7 along side of Ubuntu.  

How would I dictate which harddrive/OS I then would want to boot up upon startup?  Will it still give me a little dialog box to decide?

I suppose theoretically it is possible, but it would be far from the best solution, and I wouldn't like to think of the consequences should something go wrong :O

The easiest solution, by far, is to just TRY the virtual machine. If it doesn't work well, then you can look for an alternative, but I personally don't think you'll have a problem. Acid is essentially just a glorified media player, but requires more memory / processing power. The least you could do is try it out, if it works, great - but if not, then you can try something else. If the problem is that you don't currently own Acid, and are thus wary of committing yourself to it until you're sure it will work - then you could get a friend to lend you his / her copy while you try it out I guess.

I really don't think a virtual machine would present a problem though.

However - while I personally think Acid is a great piece of software, I'm sure I could find something else to suit my needs. There's absolutely no reason to limit yourself to just Acid, it's well worth looking around to see if there are any native Linux apps (and read up on Linux audio production, there are lots of incredibly useful things you can do. Look into Jack, for example, which lets you connect the audio output and input of different pieces of software into each other, and a myriad of other things) which are suitable. If you ABSOLUTELY need Windows software, then the only solution guaranteed to be right for you is to just use Windows.

---

### Post by PsychedelicWonders on 2007-07-24
I see your guys' point on trying other software.

But you said theoretically, my idea of running 2 hard drives for 2 different OS would work, but it's not the best... what makes it a bad idea?

Is this at all common to run a system like this?

I have no problem with having to shutdown and reboot each OS for my particular needs of that evening.  

Mind you, I'm not going to be using Acid everyday, or that often.  So it's not my main focus, just something I would like to incorporate into my new design.

---

### Post by octaedro7 on 2007-07-24
You don't have nothing like acid in linux, not that good at least. I'm new to linux but an long time acid user, when it belonged to sonic foundry. I disagree with acid not being a full music producer environment. in fact it is.  I will have to disagree with your info PsychedelicWonders also, the best looping software is Ableton Live.  Believe me, is such a piece of software, letting you do almost anything in realtime.  This one has an OSX version.
Music production is the main reason I cannot let MS XP behind completelly.
There is great audio software in ubuntu, like JACK, ardour, rosegarden, lmms, wired, H2, etc.  Take also in count that you can have Ubuntu with a realtime kernel, that can produce very low latencies (5-15ms) even in cheap builtin soundcards, far superior to what you can achieve in XP with top hardware.
Think of linux audio software as being like 3-4 years behind windows.  But this gap is decreasing amazingly quick, so I won't be surprised if in a year or two ultra-powerfull DAWs arise in the free linux world, or maybe the same big comercial ones, like cubase, live and even acid and vegas.  Am I dreaming two much?

Well My advice is to go for a dualboot system, is not painful as you might think.  Grub is rough but simple and quick.  This way you will have a more smooth transition to linux.

---

### Post by PsychedelicWonders on 2007-07-24
I'm not new to computers, but new to both the idea of Linux and a music studio.

I am a pretty smart individual, so with time, I'm sure I will be able to learn both.  

Setting up my computer with Ubuntu is going to be the first major task at hand, because I want to totally switch the OS I use on a daily basis.  I'm sick of spyware and viruses etc.  And I'm sick of having to pay for virus protection, only to have it outdate in a day, and needed to be totally replaced in a year.  And all of the free crap out there is just that, crap.

I will try the virtual machine, but I would first like to get to the bottom of running dual hard drives for dual OS.

---

### Post by alex_anthony on 2007-07-24
Dual boot is very easy. You don't even have to have two hard disks. As long as you know what you want and read up a bit on how to do it, it is very easy. GRUB will just pick up an XP partition and be ready to go.

---

### Post by PsychedelicWonders on 2007-07-24
But it seems now to be more a matter of, is a virtual machine going to be able to pull enough power to run a music and or video studio?

I am going to be running a 1.86 core 2 duo if that makes a difference with the virtual machine?

Honestly, if its possible, I would prefer to have two separate hard drives for both OS.  I don't want windows to corrupt my main stuff in anyway.  I really don't like it anymore.

---

### Post by steve.horsley on 2007-07-24
Fine. Go ahead with 2 hard drives and dual boot then. The pain will be the time spent rebooting to switch between apps. 

As for running XP in a VM, you could always try it and see. I found VirtualBox very easy to install, and XP seems to run pretty-much as fast as native (I can't tell any difference). But I haven't tried any programs that really stress the hardware, and I don't know how well the emulated sound card will work for you.

---

### Post by PsychedelicWonders on 2007-07-24
So even though I would have two separate hard drives, I would still use the dual boot program?  It will work fine?

The only downfall I see to it is, having to take an extra minute to boot back and forth.  But to me, it's worth the extra time to isolate windows so I won't have any problems with it screwing my whole system up.

---

### Post by BlueNoteExpress on 2007-07-24
Yes, you'll still need the dual-boot program if you want to dual boot.  Ubuntu and Windows can be on seperate hard drives or on the same hard drive (just on different partitions).  How you decide to do it is up to you.  I'm dual booting my desktop right now.  I've got each OS on its own hard drive, but I could've just as easily put them on the same drive.  As long as you partition your drive and leave room for another OS, you'll be fine.

---

### Post by octaedro7 on 2007-07-25
don't be scared with dual booting, with the current partition softwares and grub it's not difficult at all.  Plus you have us ;)
In my case I multi boot XP and kubuntu on an internal sata drive and ubuntu studio on an external esata.  I haven't had issues of any kind.  If you plan to do music production and video editing, forget about virtual machines.
One thing you ought to do is to check linux compatibility of your new hardware, that way you will have everything working out of the box (don't worry much about windows compatibility except if you plan to run vista (pile of ****)

---

### Post by hessiess on 2007-07-25
devide the hard drive into 2 equal sised partitions, and the linux swap. i curently have a windows partition hogging most of the drive, canot resise it becose it has errors:(

---

### Post by PsychedelicWonders on 2007-07-25
How do you check compatiablity with linux and my new hardware (and old hardware)?

I would also like to install Ubuntu on my current machine (500 mhz dell) to learn what I can before my new computer is built and I switch over for good.

---

### Post by Mornedhel on 2007-07-25
Running the LiveCD is a basic hardware compatibility test, but it does not catch everything. If you want to use Ubuntu on a lower-end machine, I recommend using XFCE for lightweightness.

---

### Post by octaedro7 on 2007-07-31
> **hessiess said:**
> devide the hard drive into 2 equal sised partitions, and the linux swap. i curently have a windows partition hogging most of the drive, canot resise it becose it has errors:(

Try Acronis Disk Director, it comes in Hiren's Boot cd also.  You can do all of that in a minute.
:popcorn:

---

### Post by andyho on 2007-08-07
I also have been trying to get Acid to work with Wine as well. About the only problem I'm running into is it's telling me I need .net framework installed, which needs IE. So I'm about to see if I can get it working.. Acid is definitely an awesome prog and really is straightforward and easier to use than other music production software.. I've used Cakewalk, Abelton, FruityLoops, and a few others. I'm looking into what's available for Linux, but thus far no such luck really. I'll let everyone know if I get it workin. :)

---

### Post by eternal-one on 2008-02-29
sony products rock (to anyone who says otherwise) actually are sonic-foundry products.. and acid6 can do more than what most people think. No sotware has faster editing features.

Enuff fanboy talk.

Answer to original question:

RUN REAPER UNDER WINEASIO

(flawless performance)

---

