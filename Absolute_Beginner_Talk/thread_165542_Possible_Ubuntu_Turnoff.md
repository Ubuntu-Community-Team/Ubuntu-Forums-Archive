---
title: "Possible Ubuntu Turnoff?"
date: 2006-04-24
forum: Absolute Beginner Talk
---

### Post by 322 on 2006-04-24
Alright, I'm in the process of making the switch from Windows to Linux, and I have heard many good things about Ubuntu. However, I looked at the program list and found out that the only Ubuntu equivalent for Photoshop is GIMP. I use Photoshop for probably 3-4 hours a day, and GIMP isn't a suitable equivalent for Photoshop. Is there any other distro or app that will allow me to run Photoshop? Because if I can't run Photoshop, I'm sticking with Windows.

---

### Post by gingermark on 2006-04-24
I think you can run Photoshop in WINE. A quick google search threw up [this guide](http://www.alexandern.com/Photoshop_on_Linux_(how_to).html), although I'm not sure how up-to-date it is.

But yeah, I'd search for review and guides to get an impression of how well it'll work in WINE.

EDIT: Have a look [here](http://appdb.winehq.org/appview.php?appId=17) to get a sense of how well it might work.

---

### Post by aysiu on 2006-04-24
First of all, there's nothing wrong with using Windows if that's what works for you.

If, however, you're determined to use Ubuntu *and* Photoshop, consider purchasing [Crossover Office](http://www.codeweavers.com/), as that will help you run Photoshop in Linux.

Lastly, can you just mention some of the features the GIMP lacks that Photoshop has? I mean *features* (the ability to do things), not just how it looks. I've heard many times that GIMP doesn't measure up, but I'm just curious as to what features specifically it's missing. No one has been able to tell me this.

---

### Post by sunrex on 2006-04-24
" Is there any other distro or app that will allow me to run Photoshop?"

No, there is no other distro that can run photoshop due to the simple fact photoshop is not made for linux. however, there is a program called wine that sould run it, it works on all linux os's, (i think), Just search photoshop or wine/photoshop, and wine.

---

### Post by aysiu on 2006-04-24
As far as I know, it's only older versions of Photoshop that can be run in Wine. Don't you need Crossover Office to run newer versions of Photoshop (say, from Creative Suite 2)?

---

### Post by nalmeth on 2006-04-24
Yes, I think you will need crossover office to run photoshop.
If you want a version of gimp customized to look more like photoshop, checkout the gimpSHOP.
I haven't been able to understand what Photoshop does that gimp doesn't. Same as asiyu, all I keep hearing is that it doesn't have some features.. I've also *heard* gimp has features that photoshop doesn't. 
It's all so vague. I think it all comes down to the layout of the app, and people needing to stick with what they're used to.

---

### Post by aysiu on 2006-04-24
I don't doubt that GIMP lacks certain features Photoshop has--I've just yet to hear what they actually *are*.

---

### Post by arsenic23 on 2006-04-24
I use Photoshop 7 on both Windows and linux boxes.  It works perfectly in wine.  Just 
[INDENT]$sudo apt-get wine[/INDENT]
and then right click on the installer on your photoshop CD and select the run in wine option.  That's it, it'll install just like in windows.  But, like those guys said, you'll have more trouble with newer versions.  I've never seen a good reason to use anything newer then 7 though.

---

### Post by 322 on 2006-04-24
[QUOTE=arsenic23]I use Photoshop 7 on both Windows and linux boxes.  It works perfectly in wine.  Just 
[INDENT]$sudo apt-get wine[/INDENT]
and then right click on the installer on your photoshop CD and select the run in wine option.  That's it, it'll install just like in windows.  But, like those guys said, you'll have more trouble with newer versions.  I've never seen a good reason to use anything newer then 7 though.[/QUOTE]

Ah, but there are so many wonderful reasons to use PS CS2! Many more useful filters, the smudge tool is improved, and it runs a lot smoother and loads faster.

There are many differences between the GIMP and Photoshop. First and foremost, GIMP's image files lack a certain quality. Basically, your images will come out looking "dusty" and dull. Also (and you must keep in mind, I've never used GIMP, I've only heard about it), I don't believe GIMP has the pen tool, which is one of the most useful tools in Photoshop. It uses mathematical equations to make vector lines, which will never lose quality, even when zoomed in/out on. It doesn't have as good of a smudge tool, I believe it has a different layering system, and many filters are missing. Photoshop has a lot of fun extras (adjustment layers, photo filters, etc) that most people don't use, but they're extremely useful if you figure them out.

As of now, I'm not 100% sure if I'll use Ubuntu. I don't have a means of backup right now, and I'm pretty much a technical noob. Perhaps I should use something more user friendly?

---

### Post by gingermark on 2006-04-24
May I ask, what are your reasons for wanting to switch? Have you read ayisiu's excellent [Is Ubuntu for You?](http://ubuntuforums.org/showthread.php?t=63315) essay?

---

### Post by arsenic23 on 2006-04-24
[QUOTE=322]Ah, but there are so many wonderful reasons to use PS CS2! Many more useful filters, the smudge tool is improved, and it runs a lot smoother and loads faster.[/QUOTE]

I tried the demo and it didn't really do anything for me.  I mainly use Photoshop as a canvas to doodle with my tablet, mostly recreational.  Also, I'm not in the money right now, and I'd rather not pirate Photoshop... on moral grounds I suppose.

---

### Post by ncappel1 on 2006-04-24
Maybe you could get the best of both worlds and set up a system that dual boots, there's plenty of people that use windows for work and ubuntu for play, it could work out really well!

ps, you should email your comments about what makes photoshop better to the developers who work on GIMP. They work really hard to get things the best they can, they need valuable user input like yours to make it better in future versions.

---

### Post by 322 on 2006-04-24
[QUOTE=ncappel1]Maybe you could get the best of both worlds and set up a system that dual boots, there's plenty of people that use windows for work and ubuntu for play, it could work out really well!

ps, you should email your comments about what makes photoshop better to the developers who work on GIMP. They work really hard to get things the best they can, they need valuable user input like yours to make it better in future versions.[/QUOTE]

1. Dual booting seems like a good idea, although it may turn out to be a RAM monster. My specs are as follows: Intel Pentium 4 HT processor, 512 MB RAM, 80GB hard drive (85% full), 96 MB Intel Integrated Graphics Controller (I know :( ). I'm just not sure if I have the RAM (or HDD space, for that matter) to try dual booting.

2. Yeah, I wouldn't mind helping out the GIMP program. Of course you have to remember that above all, it is a shareware program, and I don't believe it's right to make a shareware program to compete with Adobe. I would suggest offering the current GIMP as a sort of trial program, and have a GIMP Premium program for maybe $400-500. I can imagine that the most difficult part of the whole deal to program would be the pentool. Such an  amazing little toy :KS 

3. The whole reason I want Linux is to have a "system without walls," per se. I want to have a system that does what I want to do and is completely open to user input. I figure Linux would be the best for this, and I've heard enough about Ubuntu to want to try it. If I could think out a system that would work for me (Photoshop CS2 and LimeWire are a must, among other programs), I might be willing to upgrade to 2GB of RAM to support the RAM monster this might turn out to be. I've heard FrostWire is terribly slow.

---

### Post by arsenic23 on 2006-04-24
I wouldn't worry about RAM for dual booting, if 512 RAM works for you and Photoshop now, I see no reason why you'd want more.  I'm not a big fan of running 'shop on less then a gig, but like I said, if it works now, it'll keep working when you dual boot. 

If your serious about this, I'd mess with the live CD a bit before I put money into anything, this is what I'd do:  I'd just pick up another hard drive, maybe you have an old 20gig laying around?  And put Ubuntu on it, leaving your windows disc unmodified.  That's just me though.  You could more then likely shrink your currant windows partition down and use the free space for ubuntu... but if your already 85% full it may have a negative impact on your windows performance.

Also, just to let you know, there is a linux version of Limewire.

---

### Post by 322 on 2006-04-24
[QUOTE=arsenic23]I wouldn't worry about RAM for dual booting, if 512 RAM works for you and Photoshop now, I see no reason why you'd want more.  I'm not a big fan of running 'shop on less then a gig, but like I said, if it works now, it'll keep working when you dual boot. 

If your serious about this, I'd mess with the live CD a bit before I put money into anything, this is what I'd do:  I'd just pick up another hard drive, maybe you have an old 20gig laying around?  And put Ubuntu on it, leaving your windows disc unmodified.  That's just me though.  You could more then likely shrink your currant windows partition down and use the free space for ubuntu... but if your already 85% full it may have a negative impact on your windows performance.

Also, just to let you know, there is a linux version of Limewire.[/QUOTE]

Thanks for the help. As of right now I'm going to leave the idea of Ubuntu alone, because I don't have an efficient way of backing up my hard drive (I'm worried about breaking my system and screwing up my hard drive). I'm looking into buying a reasonably priced external to back my files up, then I'll play around with it. I have another comp laying around with about a 40gig HD, but I think I fried the PSU. When I try and boot it up it makes these loud clicking noises and overheats until I unplug it. I'm not sure what I can even do with the hard drive because I don't know what all got fried.

EDIT: I put Breezy on a CD, but my computer doesn't recognize it as anything and won't autorun. I got the Windows XP SP2 version, burnt it with ISO Recorder, and went through everything it says, but still nothing. I know it said something in there about reconfiguring the BIOS, but I have no clue how to do that and I don't want to screw anything up this early in the game.

---

### Post by nalmeth on 2006-04-24
GIMP isn't shareware
People can pay $400 for Photoshop if they want to do that instead, this won't happen with GIMP as it will always be free.
i believe you can get it for windows aswell, you should try it out anyway. Try the gimpSHOP as I suggested to have gimp with a more photoshop feel. 
Of all the things I've heard lacking from GIMP, I've never heard of this "dusty dull image quality". You say you've only heard this, so you should just try the gimp anyway.
I must admit gimp's interface is not the easiest to understand at first. You wonder where everything is, but go to plugins, there are a world of effects you can use.
It's perfectly understandable if you must use Photoshop, but don't be discouraged from GIMP because you heard some rumours about poor quality.
Let the GIMP speak for itself!
Also, dual-booting won't have any effect on your ram.

Backing up is a tricky thing sometimes.. I think the liveCD has gimp on it, you could play around with ubuntu until you find a way to back up windows to your needs. I think there are free utilities that do this.. Do you have a DVD-burner?
Another harddrive is another good idea, just to keep enough space for both systems. 
Also, you won't Physically hurt your harddrive by dual-booting, etc, the only thing you risk is pre-existing data. 
There is low likelyhood that you will have data loss, but backing up is imperative anyway.
The biggest risk in shrinking your windows partition, is if it is fragmented.
I've been advised to defrag many times before thinking about shrinking NTFS.

EDIT: Just read your edit!
When your PC boots up, and you see "Hit delete for settings" or something similar (this is before windows starts anything)
go ahead and hit delete (or F10 whatever it asks) to enter your BIOS settings.
Don't worry, you are not doing anything here that can risk your system.
All you want to do, is find the page with boot order, and tell your BIOS to boot from the CD-Drive ahead of the harddrive. Save and Exit

---

### Post by aysiu on 2006-04-25
322,

You say the features GIMP lacks, but you say you haven't actually used GIMP--I'm a bit confused here. I've never seen this dusty quality you're talking about.

By the way, you should use a live CD. A dual-boot is a pretty serious commitment (though, I don't see how it would affect your RAM--and 512 MB is *plenty*... that's what I have right now), but a live CD runs completely off RAM and will give you a chance to try out Ubuntu without installing it and see how well it recognizes your hardware and familiarize yourself with the Gnome interface.

Also, there's a version of GIMP for Windows, too, so you can try it out there and see how it is.

---

### Post by mostwanted on 2006-04-25
The only feature I know Photoshop has over GIMP is CMYK-colour editing.

---

