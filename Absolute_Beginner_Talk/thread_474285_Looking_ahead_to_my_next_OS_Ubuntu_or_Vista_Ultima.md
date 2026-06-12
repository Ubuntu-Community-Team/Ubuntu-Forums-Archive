---
title: "Looking ahead to my next OS: Ubuntu or Vista Ultimate.  Newb Questions about Ubuntu"
date: 2007-06-14
forum: Absolute Beginner Talk
---

### Post by Triptoph on 2007-06-14
So I'm considering going with either Ubuntu or Vista Ultimate for my next OS.  I'm trying to figure out what the best OS would be for me, irrelevant of price.  I've only used *nix systems while doing a CS major, otherwise i've always had the latest OS from MS, whether it be horrific (Win Me, XP x64) or decent (vanilla XP).  I'm looking for a change though.  I crave being able to change my working environment how I want it changed, and Ubuntu with a few extra programs seems to support that.  

I like the open source philosophy, and I've seen some promising reviews of linux software, however I have some reservations.

On WinXP I run LAMP for testing my own websites before uploading them to a production server.  I can only assume a *nix OS would do the job better than XP.  I also run file sharing programs, WinAmp for music, MSN, Vent and I play World of Warcraft.  I'm using a socket 939 AMD Athlon 64 64 3000+ CPU, and I find things sometimes slow down quite a bit as Windows or one of those other programs randomly decides to do some extra work.  I figure getting a quad core processor would be a huge leap up, and i wouldn't have to worry about other processes slowing down what I'm doing at the moment. 

If someone could bare with me to answer a few newbish questions (some of which i'm sure are laughable):

Is Ubuntu capable of efficiently using a quad-core processor?  Is there any way to specify what cores would take which processes?

Can Ubuntu make full use of a graphics card such as an 8800 GTS in 3D editing programs and video games such as World of Warcraft (which I'm hopelessly addicted to)?

Can I easily network Ubuntu with Windows-based machines?  Will I have problems using networked printers?

Is there support for Creative X-Fi sound cards? How much of the cards' features are usable?

Support for Hauppauge WinTV Go card?

Can I run Photoshop somehow?  Wine perhaps?

I write PHP / Javascript a lot, using dreamweaver.  Is there a nice open source replacement for this?  I use the code view in dreamweaver, and the design viewjust to easily click on an area of a page visually to get to the appropriate place in the code quickly.  I use it's built-in FTP feature to upload when ready, and make use of its check-in/out facility.

Can I run World of Warcraft at similar framerates and quality options as I could in XP, using the AA/AF abilities on my card?  Is Ubuntu's OpenGL support on par with MS' directX support in terms of visual quality for a given video card?

I know that's a lot.  If you've spent the time to read through this my thanks to you :)

---

### Post by freebird54 on 2007-06-14
I don't see any laughable questions - in fact I can't answer tme all either!  However...

1. Not sure how the quad cores will split tasks - or who/what controls it
2. Don't know the card, but WOW is apparently making people happy/addicted here too - probably OK
3. Networkiing and net printers - usually OK - check by model/make if in doubt about its 'standardness'
4. Support for X-Fi?  apparently nonexistent.  Not too healthy a response on their site either.
5. Unknown on Hauppage - sorry
6. earlier Photoshop version can be run under wine - newest not yet.  Tried GIMP or GIMPShop yet?
7. Don't how close you come to dreamweaver - probably not as polished here (though perhaps as functional)
8. See above - people well addicted - suspect framerates are OK :)

Hope other will fill in the blanks for you - but I suspect you may be a dual-boot candidate - at least at first.  Stay clear of Vista for the time being - look again in Jan '08 to see how they're doing....

---

### Post by wolfen69 on 2007-06-14
i second the dual boot thing. just make sure you install windows first. even better i think, is to have 2 seperate drives.

i have the hauppauge pvr150, and it works perfectly. just download the ivtv drivers off of synaptic.

---

### Post by tapio on 2007-06-19
> Can Ubuntu make full use of a graphics card such as an 8800 GTS in 3D editing programs and video games such as World of Warcraft (which I'm hopelessly addicted to)?

I got a 7600GTO (or something like that), and with the opengl switch enabled, it kicks window/direct3d's *** in terms of fps. Haven't seen any visual quality decrease either.
(Peaked at 175fps while rotating the beryl-cube, guess you can live with that, huh? :popcorn:)
Not sure about ventrilo, but I've heard about people using it under linux so I guess that should work out just fine.


> 
Can I easily network Ubuntu with Windows-based machines? Will I have problems using networked printers?

> I write PHP / Javascript a lot, using dreamweaver. Is there a nice open source replacement for this? I use the code view in dreamweaver, and the design viewjust to easily click on an area of a page visually to get to the appropriate place in the code quickly. I use it's built-in FTP feature to upload when ready, and make use of its check-in/out facility.

Dreamweaver seems to work with wine. ([http://appdb.winehq.org/appview.php?iAppId=183](http://appdb.winehq.org/appview.php?iAppId=183))
You can probarbly find native replacements also.


-Tapio

---

### Post by ali4949 on 2007-07-10
Well Dreamweaver 8 works fine with wine version .9.36 and .37, (does not work with latest version which at this time is .9.4). Why not save the money from the OS and spend it on RAM. Check out the new  project [http://www.wine-doors.org](http://www.wine-doors.org) , which is trying to make installing a lot of the apps easier for people migrating from the OTHER  operating systems. 
If you are CS professional then you will like the kind of control  you will have over your system. Remember it takes a little while to get used to a new environment but in the end you will find its worth it.

---

### Post by 3rdalbum on 2007-07-11
Your quad-core processor will rock under Ubuntu. The Linux kernel has fantastic multi-tasking capabilities, with full SMP support, and since a typical Linux system is split up into lots of processes you will see very effective distribution of each running part over the four cores.

Having said that, you will definately see better performance on Ubuntu than you are on Windows, so you might not need the quad-core.

Just a technicality: You can't run LAMP on Windows XP, as LAMP stands for "Linux, Apache, MySQL, PHP". You were actually running "WAMP" :-)  But yes, I've used Ubuntu for this in the past, when I was a noob, and Ubuntu has been doing some work in making this foolproof to set up.

Support for the Creative X-Fi is coming, apparantly.

I think everything else that I can answer has already been answered in the thread.

---

### Post by macogw on 2007-07-11
The 8800 GTS is supported.

For a Dreamweaver replacement, there's Nvu Kompozer [http://www.kompozer.net/](http://www.kompozer.net/) I don't know if it does FTP, but gFTP is a GUI FTP program for GNOME.  I do all mine in vim, load it into Firefox and use Firebug to see what's screwing up where, and then publish with command line ftp.  One neat thing about Nvu is that it actually handles CSS properly.  FrontPage and Dreamweaver, in my experience, did the annoying "put the style stuff hardcoded into it" junk.

Photoshop 6 works in Crossover Office.  Photoshop CS as a portable app run from a flash drive on a computer running Ubuntu with Wine should also work (sounds weird, but someone who got it working blogged a howto).

---

### Post by edthehead101 on 2007-07-11
gah. vista ultimate lagged my comp to death, reduced battery life and used over half of a 40GB HDD. i had used ubuntu before so i came back to it. got to say everything is better and theres always a way of running a program ^_^

---

### Post by rickycodie on 2007-07-11
i concurr with everybody about pi$$ta. don't use it- especially if you want to customize.

---

