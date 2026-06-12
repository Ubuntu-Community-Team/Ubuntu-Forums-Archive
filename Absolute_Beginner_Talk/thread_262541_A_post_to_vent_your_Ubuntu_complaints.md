---
title: "A post to vent your Ubuntu complaints"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by zkaufman on 2006-09-21
Please bear with me here, I have some major Ubuntu venting to do...

I have had Ubuntu for over two months and initially was quite happy. Thing however have only gone down hill.

1) Soon after installing Ubuntu I realized I could not play YouTube videos (they would stop after 2 seconds of play time) and the sound did not work at all. I literally spent two weeks debugging the problem. This involved searching the forums, following instructions on various webpages and endless hours adjusting the settings/files whatever. It was a total nightmare. Finally, after typing in some of the most OBSCURE commands in the shell which was recommended by some page, I was able to get Flash and sound it to work. Woohoo...Well until the next update that is. Now its No More Sound/No More Flash again! If you think I am going to embark on the endeavor of attempting to fix these things again your are wrong, not in a million years. 

2) Now I am still trying to give Ubuntu a chance. Not having video and sound isn't helping. BUT NOW I CAN'T USE FIREFOX!?! My last update (I always try and stay up to date) was 2006-09-20 (yesterday) and now everytime I open Firefox it goes to my homepage (CNN.com) but then freezes whenever I try and go anywhere else! I am only able to make this post because I 'sudo apt-get install opera'. Sure, I can just use Opera now, but should I have too?  I like Firefox.

3) Do you honestly think I am going to recommend Ubuntu for my family? No way. My brother, who is not computer savy at all, likes to watch videos online (YouTube) and likes to listen to music. Apparently this would be a major problem for him to do this with Ubuntu. I wouldn't even consider making the recommendation to him. 

I would also like to add that I am a somewhat computer savy person. At least to the extant where I can use the online forums and have the patience to attempt to fix these problems. I am no Windows fan but I will say these were not issues I had when my machine was XP. I defintely never spent 2 weeks attempting to get sound to work!

But I am going to stay the course. 

-I will spend a week trying to make Firefox not freeze anytime I leave my homepage.

-As soon as I feel like commiting to a self imposed 2 week house arrest, I will try and get my sound working again.

-Getting flash to work I think is damn near impossible. I'm not even going to try. 

Yeah Ubuntu! Just don't expect me to recommend it to my brother who likes to use the internet but doesn't want to spend weeks getting sound to work or would maybe like to go to any web page other than his home page.

Anyone else have any venting...or just me!

---

### Post by skymt on 2006-09-21
Sorry to hear about your problems. Firefox and Flash both work well for me.

---

### Post by aysiu on 2006-09-21
> **zkaufman said:**
> 
But I am going to stay the course. Wow!

If I had the problems you've been having... I wouldn't stay the course.

---

### Post by zkaufman on 2006-09-21
I'm just really angry because I can not get firefox to leave my home page...grrrr. No matter if I click a bookmark or just type a new address in the address bar, it just freezes. Whats the deal?!?

I can deal with no sound (sort of)...

I can deal with no flash (barely)...

I can not deal with no Firefox.

---

### Post by aysiu on 2006-09-21
Well, my guess is that the problem with Firefox has something to do with your video card configuration. Do you need NVidia drivers installed or something?

The other possibility is that you have a corrupt Firefox profile. You can fix that by following [these instructions](http://ubuntuforums.org/showthread.php?t=103930).

---

### Post by [S|G] on 2006-09-21
I was experiencing freezes like that whenever I had a webpage with flash+sound opened. I uninstalled flash, went to macromedia's website, downloaded it again and reinstalled. That seemed to fix my problems.

I'm also running firefox with aoss ("sudo apt-get install alsa-oss", then "aoss firefox") so I can listen both to flash sound, use my skype (also working using aoss) and listen to amarok.

---

### Post by skymt on 2006-09-21
In my experience, aoss tends to make Firefox crash with certain sites. Maybe your problem is related?

---

### Post by Scarlett on 2006-09-21
For the most part I'm very happy with Ubuntu and you really can't beat the security and the price.

However trying to configure this thing is somewhat akin to poking my eye with a pencil.  I have yet to successfully install Flash.  I'm pretty sure my nVidia card is not correctly set up but at least my screen has the correct refresh rate.  Every time I think I might want to get drivers for my mouse or set up my scanner and printer or get the latest BIOS update for my mobo I think back to the Flash that hasn't been installed yet and it seems like a daunting task.  I found a howto for getting stuff to work on 64bit architecture but just reading through it let alone actually comprehending it seems a little out of my league.

As long as I'm "just using" Ubuntu, it "just works".  But tweaking things has been a nightmare. (For me.  YMMV.)

---

### Post by james_san on 2006-09-21
Well I have to say it seems like nearly all your problems stem from Flash. This is really quite simple, it's just that it is by no means intuative. It also doesn't help that people give you command-line instructions when you can achieve the same thing using the GUI.
I would bet that Flash is causing Firefox to crash (some sort of video on the cnn homepage?)

What you should do is open up Synaptic (System Preferences->Syaptic Package Manager), and then search for "flash", and remove programs like "flashplugin-mozilla" and that sort of crap. Next, you should go to Settings->Repositories and tick all the ones there.
What I usually do is remove all the repositories listed in there, and then go through and all them all again, making sure to include all the options (there are four repositories, and each has four options, like "updates", and "restricted").
Once you have completed that, you should have four repositories listed, and each one will have four sub-categores listed under it. Close the repository dialog, and press the refresh button to get an updated list of software available.
Finally, you only need to install one program: "flashplugin-nonfree". This is the official version of Flash, and should work perfectly. Also sound worked straight away for me with no issues.

With regard to your other issues:

You should be able to set your refresh rate/resolution by going System Preferences-> Desktop Resolution or something like that. If it is wrong and you can't change it there, let us know and we can figure out why.

In linux (in general), if there are drivers worth using, they are already installed, or in rare cases (such as 3D drivers from ATI or Nvidia) need downloading (through software you already have, NOT by downloading it from their site). Therefore your mouse should not need drivers. If there are some buttons on it that don't work, explain that and we should be able to help.

Don't even bother with 64-bit. It is bad enough on Windows, imagine the problems using it on a less-well-known-by-the-big-companies OS. Just use a normal 32-bit distribution and it will work just fine. One reason for this is that many companies who make software for linux (such as flash, or Nvidia drivers) are very generous just providing stuff at all, for the small percentage of users using other operating systems. It is highly unlikely that they will make 64-bit builds as well. So while most free and included software works fine, those little necessary extras do not.

Also don't even bother trying to do BOIS updates. Chances are that your mobo manufacturer will give you a Windows program that can be run to patch your mobo firmware. They don't make a linux program, and they don't share information with people who do want to make one.

---

### Post by james_san on 2006-09-21
Oh and forgot to mention. If firefox is playing up, then perhaps you should try to delete your profile. Unfortunately this will delete your bookmarks/passwords so make sure you have them backed up. Restart your computer first to make sure that firefox is definately not running. Then just open up your home folder, press Ctrl+H to show hidden files, and delete the folder called ".mozilla". Then open firefox again and see what happens.

Another note: any time someone says to type "apt-get install blahblahblah", you can do the same thing by opening up "Synaptic Package Manager" in the preferences menu, and then ticking that particular program and pressing "Apply", just like I said to do with "flashplugin-nonfree"

---

### Post by telegramsam on 2006-09-21
Dude-

[www.getautomatix.com](www.getautomatix.com)

This HELPS.

Flash, Java, W32codecs, all of it is in there.  I would highly recommend getting it.

If nothing else, back up your personal stuff and reload Ubuntu.  I've had to do that 12 or 13 times, just because of mistakes.  Sometimes honest mistakes, sometimes silly ones.  Sometimes experiments go horribly wrong. I had very little trouble getting Ubuntu configured to the way I like it (that is in NO WAY a commentary on your skills!!).  Some things are just outside of your control. Hope things improve for you!

---

### Post by Brunellus on 2006-09-21
> **james_san said:**
> Oh and forgot to mention. If firefox is playing up, then perhaps you should try to delete your profile. Unfortunately this will delete your bookmarks/passwords so make sure you have them backed up. Restart your computer first to make sure that firefox is definately not running. Then just open up your home folder, press Ctrl+H to show hidden files, and delete the folder called ".mozilla". Then open firefox again and see what happens.

Another note: any time someone says to type "apt-get install blahblahblah", you can do the same thing by opening up "Synaptic Package Manager" in the preferences menu, and then ticking that particular program and pressing "Apply", just like I said to do with "flashplugin-nonfree"
we like giving command-line instructions because there is zero chance of misinterpretation.  just copy and paste.  It might seem like voodoo to a new user, I'll grant, but it's a LOT less frustrating for those of us giving help--we can actually solve someone's problems rather than arguing over where to go and what to click.  

Offtopic:  I recently had [ c ause to reflect ](http://ouij.livejournal.com/176473.html) on why we ubuntuforums regulars prefer giving command-line help.  I'd given my dad verbal instructions on what to click...and he ended up hosing his Windows install.  If I could have told him "just type apt-get install package" there would have been no chance of confusion.

Ontopic, to the OP:  You want [EasyUbuntu](http://easyubuntu.freecontrib.org) for all your setup needs.  If you want to learn WHY the setup script does what it does, go [here](http://wiki.ubuntu.com/RestrictedFormats)

---

### Post by Brunellus on 2006-09-21
> **telegramsam said:**
> Dude-

[www.getautomatix.com](www.getautomatix.com)

This HELPS.

Flash, Java, W32codecs, all of it is in there.  I would highly recommend getting it.

If nothing else, back up your personal stuff and reload Ubuntu.  I've had to do that 12 or 13 times, just because of mistakes.  Sometimes honest mistakes, sometimes silly ones.  Sometimes experiments go horribly wrong. I had very little trouble getting Ubuntu configured to the way I like it (that is in NO WAY a commentary on your skills!!).  Some things are just outside of your control. Hope things improve for you!
Caution is a very very VERY important quality.  If you don't feel comfortable doing anything--don't do it.  Ask first, either on the forums or on IRC.  I think too many users go barrelling into tweaking their installations before they get a fair grasp of what might be involved....and end up getting so stuck, they feel like they have to reinstall.

Advice:  take it slow.  It's like learning to play the piano:  one finger first, one hand, two hands.

---

### Post by Scarlett on 2006-09-21
> **james_san said:**
> It also doesn't help that people give you command-line instructions when you can achieve the same thing using the GUI.

Isn't that the truth!  I have managed to use the terminal for a few things but I'd rather avoid it if at all possible.  I know all the Linux gurus say it's easier and more powerful, but as a almost-former Windows user I'm much more comfortable with a graphical interface.

In the Synaptic repositories I've checked all the options, refreshed it, searched for flashplugin-mozilla and it doesn't find anything.  I have duplicates of all the repositories (no idea how that happened) and they're in binary and source (I don't know what the difference is except that when I click edit they have different options) and I've got one that says [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu).  All total, I have 12 repositories.  When I tried doing it with the command line it said it couldn't find the file or the source wasn't available or something like that.

Nothing is crashing though.  I just want to see videos and stuff and I keep getting the message that I don't have the latest plugin installed.

As for the other things, my back and forward button on my mouse doesn't work.  I should also be able to map the buttons to specific commands in different programs.  Not really an issue in Ubuntu since AutoCAD doesn't work anyway but as an example but I used to have 'undo' on my back button and 'line' on the forward button.  Kind of a nice little feature.  I also liked how my mobo kept track of my CPU temp and the fan speed and would shut the system down if it got too hot.  It's been doing that lately since one of my fans isn't working.  The fan is a hardware problem and right now I've got my case open with a small electric fan pointed at it but I still want to keep track of the temp.  

It also seems like I should have more options with my nVidia settings.  In Windows I was able to create profiles specific to different programs and change settings on the fly.  It also had a pop-up blocker.  And a big dialogue box.  I'm thinking I should have something like that in Ubuntu but really I'm just happy my screen is staying in one place and not blinking and resizing anymore.  I'll get it all together one of these days.

---

### Post by james_san on 2006-09-21
> **Brunellus said:**
> we like giving command-line instructions because there is zero chance of misinterpretation.  just copy and paste.  It might seem like voodoo to a new user, I'll grant, but it's a LOT less frustrating for those of us giving help--we can actually solve someone's problems rather than arguing over where to go and what to click.

Fair enough. As you can tell, I'm new to the forums, just thought I'd do my share of helping out. In any case, I prefer using the GUI, so that is probably how I will continue to explain how to do things.

---

### Post by james_san on 2006-09-21
> **Scarlett said:**
> Isn't that the truth!  I have managed to use the terminal for a few things but I'd rather avoid it if at all possible.  I know all the Linux gurus say it's easier and more powerful, but as a almost-former Windows user I'm much more comfortable with a graphical interface.

Great to know I'm not the only one!

> **Scarlett said:**
> In the Synaptic repositories I've checked all the options, refreshed it, searched for flashplugin-mozilla and it doesn't find anything.  I have duplicates of all the repositories (no idea how that happened) and they're in binary and source (I don't know what the difference is except that when I click edit they have different options) and I've got one that says [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu).  All total, I have 12 repositories.  When I tried doing it with the command line it said it couldn't find the file or the source wasn't available or something like that.

Nothing is crashing though.  I just want to see videos and stuff and I keep getting the message that I don't have the latest plugin installed.

You don't need the "source" ones. They are only for developers or fiddlers. Although they won't do any harm.

"flashplugin-mozilla" doesn't work for me. Use "flashplugin-nonfree". God knows why there are so many versions of flash in there. If you can't find it, they your repositories aren't setup properly. Try deleting them all, and adding them (it looks much cleaner to, when you just have 4 repositories listed).  You don't need the "source" ones. Then refresh and try again. If it still doesn't work, open the file "/etc/apt/repositories" (that is from memory, may not be exact), and paste the contents here.

---

### Post by Scarlett on 2006-09-21
> **Brunellus said:**
> Offtopic:  I recently had [ c ause to reflect ](http://ouij.livejournal.com/176473.html) on why we ubuntuforums regulars prefer giving command-line help.  I'd given my dad verbal instructions on what to click...and he ended up hosing his Windows install.  If I could have told him "just type apt-get install package" there would have been no chance of confusion.


I guess that makes sense.  I think it comes down to, if I'm using a GUI, I can usually remember where I've gone and how to do it again or how it might apply in a similar situation.  With the command line I'm typing in things that I have no idea what it means or why it's doing whatever it's doing.  So it works for fixing an immediate problem but I'll never be able to apply that to a different situation.  > **telegramsam said:**
> Dude-

[www.getautomatix.com](www.getautomatix.com)

This HELPS.

Flash, Java, W32codecs, all of it is in there.  I would highly recommend getting it.

Thanks!

---

### Post by Brunellus on 2006-09-21
the shell is worth learning, because it saves you a LOT of time and aggravation.  Trust me.  

If the GUI works for you, that's great....but I find it's just an exercise in frustration giving GUI help over the internet.  

An example:

```

"OK.  Go to System>>Administration>>Synaptic Package Manager.  Type your password.  Now go to "search" and type "flashplayer-nonfree".  Tick the box, tell it to install, apply the changes.  When it's done, close synaptic."

```

Is a lot of bother to type.

```

sudo apt-get install flashplayer-nonfree
```

is terse, but it gets the job done.

---

### Post by brianC on 2006-09-21
I had trouble connecting , firefox stalls on some sites.
  After installing Firestarter everything worked. 
For terminal I found some sites to help me.
[www.ss64.com/bash/index.html]("www.ss64.com/bash/index.html")
[www.ubuntuforums.org/showthread.php?t=171507&highlight=terminal+commands]("www.ubuntuforums.org/showthread.php?t=171507&highlight=terminal+commands")
[monkeyblog.org/ubuntu/installing/]("monkeyblog.org/ubuntu/installing/")
[linuxcommand.org]("linuxcommand.org")
Seemed to work for me

---

### Post by blx_286 on 2006-09-21
Well I did have to wrestle with the USB WiFi, but it is a Netgear WG111. It is working now. Also having a bit of a problem with my HP 4M printer.

My laptop at work crashed due to a hard drive failure and I had to install Windows XP SP2 back on it. It didn't find drivers for 5 pieces of hardware :rolleyes: .

Can't beat the price of Ubuntu and this forum rocks. I'm also kinda old school, so that command line voodoo stuff is kinda cool too.

---

### Post by Mimsy on 2006-09-21
> **Scarlett said:**
> I think it comes down to, if I'm using a GUI, I can usually remember where I've gone and how to do it again or how it might apply in a similar situation.  With the command line I'm typing in things that I have no idea what it means or why it's doing whatever it's doing.  So it works for fixing an immediate problem but I'll never be able to apply that to a different situation.

That is *exactly* why the command lines frustrates me. I don't speak its language. I can communicate with the GUI though, and there I can remember what I did and where, and I can find it again easily.

From now on, whenever I need to install something, my first attempt will be through Synaptic. Amazing that it only took me six failed attempts to figure that out... :rolleyes: 

/Mimsy

---

### Post by telegramsam on 2006-09-22
> **Brunellus said:**
> Caution is a very very VERY important quality.  If you don't feel comfortable doing anything--don't do it.  Ask first, either on the forums or on IRC.  I think too many users go barrelling into tweaking their installations before they get a fair grasp of what might be involved....and end up getting so stuck, they feel like they have to reinstall.

Advice:  take it slow.  It's like learning to play the piano:  one finger first, one hand, two hands.


That's good advice.  Guess where I got the idea for Automatix, and how to network with the rest of my home machines which are all M$, and figured out how to update my install, the few terminal commands that I know and use frequently (It just takes some practice and it begins to make a little sense--it's another language)--I got all that right here on this forum.

One thing Ubuntu has that NOBODY else has is a support community like this one.  VERY patient and helpful people.  Once people get Ubuntu under control, I think a good number of them come back here and share that knowledge.  Pretty cool thing if you ask me.  (I know you didn't, but I'm talking here!![-X )

---

### Post by Brunellus on 2006-09-22
> **telegramsam said:**
> That's good advice.  Guess where I got the idea for Automatix, and how to network with the rest of my home machines which are all M$, and figured out how to update my install, the few terminal commands that I know and use frequently (It just takes some practice and it begins to make a little sense--it's another language)--I got all that right here on this forum.

One thing Ubuntu has that NOBODY else has is a support community like this one.  VERY patient and helpful people.  Once people get Ubuntu under control, I think a good number of them come back here and share that knowledge.  Pretty cool thing if you ask me.  (I know you didn't, but I'm talking here!![-X )
This community has been very helpful.  One other thing that I should add to this thread is that it's useful to buy a book on the subject.  Mine was "How Linux Works:  What Every Superuser Should Know" by Brian Ward (No Starch Press).  

I read it--at least once, maybe twice-- in bits and pieces on the train to & from work over a week or two.  After I'd done a bit of studying, many things became MUCH clearer to me.  It was helpful to have the more conceptual things--how Linux works, what various bits of the filesystem are, how the shell works, how networking works-- explained to me, so I could have a framework to understand specific things.  It also helps that I have to spend about an hour and a half a day on the train commuting.

---

### Post by zkaufman on 2006-09-22
I initiated this post with some serious venting but (and after sleeping on it) I do realize that the support you get from the Ubuntu forums is a major benefit to the product, i use it alot, but that is also part of the problem.

Thank you for the reponses. I will take the advice some of you have given for getting flash and firefox to work. And on a side note...I do recommend Ubuntu to everyone I know who I beleive has the skills to work through some of the issues I have experienced. Perhaps a little more development time and fine tuning of Ubuntu will take care of those issues and then I will be recommending Ubuntu to everyone i know.

Take care.

---

### Post by Brunellus on 2006-09-22
> **zkaufman said:**
> I initiated this post with some serious venting but (and after sleeping on it) I do realize that the support you get from the Ubuntu forums is a major benefit to the product, i use it alot, but that is also part of the problem.

Thank you for the reponses. I will take the advice some of you have given for getting flash and firefox to work. And on a side note...I do recommend Ubuntu to everyone I know who I beleive has the skills to work through some of the issues I have experienced. Perhaps a little more development time and fine tuning of Ubuntu will take care of those issues and then I will be recommending Ubuntu to everyone i know.

Take care.
....and for everybody else, there's MEPIS.  

Community hero **aysiu** has often opined that Ubuntu makes an excellent *second* distribution, and I have tended to agree.  MEPIS is a better *first* distribution...but ultimately more users are satisfied with Ubuntu.

---

### Post by javaJake on 2006-09-23
I thought I'd like to mention that I got Flash to work. If Flash is crashing Firefox, and Opera just shows a big grey square, then see my post here:
[http://www.ubuntuforums.org/showthread.php?p=1535147#post1535147](http://www.ubuntuforums.org/showthread.php?p=1535147#post1535147)

Hope this helps.

---

### Post by javaJake on 2006-09-23
> **Brunellus said:**
> ....and for everybody else, there's MEPIS.  

Community hero **aysiu** has often opined that Ubuntu makes an excellent *second* distribution, and I have tended to agree.  MEPIS is a better *first* distribution...but ultimately more users are satisfied with Ubuntu.

I was a MEPIS user! I found it annoying, however, that I'd have to reinstall my system every 3-2 months as a new version came out. If I apt-get upgraded then my system would become unstable.

Oh, and I'd try to compile anything, and POOF! Errors! Not just errors, either, but errors no one knew how to fix! I'd really want, say, the latest versions of so-and-so game, or so-and-so drivers, but oh no. I couldn't get one SINGLE thing to compile out of SIX compiles! Oh yes, I sure did count, because compiling was/is important for me!

This was all before MEPIS decided that they needed to upgrade to Ubuntu. Now, _doesn't the fact that MEPIS had to use Ubuntu's kernel to get a bit more stable say something to you?_ :D

I have had problems with Ubuntu, but they at least were figured out by a community of users using a standard forum (try MEPIS' forum). Try the #ubuntu IRC channel - it is extremely active nearly 24/7! And when I needed to compile ndiswrapper, or something else to get things working, at least it actually worked. Try that with MEPIS!

And all this on a solid suite of applications that make usually complicated stuff (upgrading, installing new programs) an easy-to-do process. MEPIS doesn't have anything like what Ubuntu has.

**Calms down**
I was close to flaming, and maybe I was overshooting how bad MEPIS is. But I hope you get why I switched, and why you should be really really careful with MEPIS - it isn't all it is cracked up to be.

---

### Post by xpod on 2006-09-23
> 3) Do you honestly think I am going to recommend Ubuntu for my family? No way. My brother, who is not computer savy at all, likes to watch videos online (YouTube) and likes to listen to music. Apparently this would be a major problem for him to do this with Ubuntu. I wouldn't even consider making the recommendation to him.

I only switched a pc on in march so neither am i pc savvy

> I would also like to add that I am a somewhat computer savy person

Mabey you should let HIM set it up:biggrin:

---

### Post by javaJake on 2006-09-23
> **Mimsy said:**
> That is *exactly* why the command lines frustrates me. I don't speak its language. I can communicate with the GUI though, and there I can remember what I did and where, and I can find it again easily.

From now on, whenever I need to install something, my first attempt will be through Synaptic. Amazing that it only took me six failed attempts to figure that out... :rolleyes: 

/Mimsy

The command-line is like school: you hate to learn it, you detest it, you kick and scream even. But then once in a while you are forced to use it, and once you start to get the hang of it, you end up using it more then you thought you would. I was JUST like you! I used to use Synaptic and other GUI stuff for everything for at least 2 years. But look at me now. I use the terminal really well, and even know some basic BASH scripting. :)

---

### Post by Mimsy on 2006-09-23
Okay, I'm looking at you, and it's not helping me a bit.

Instead of telling me that in two years I'll be just like you (a scary thought), if I just keep stumbling blindly through everything I come across, give me some help and pointers.

For example, 'cd' seems like it would mean Change Directory, because that's what it does, but beyond that, I'm lost. What is "aptitude", and why do I need to type it in before I install something? What is the difference between "upgrade" and "update"? How do I get a list of available options so I know what i have to work with?

I prefer the GUI because when I go to System -> Preferences -> Keyboard, I can see the options available to me, and I know that what I do there will affect only the keyboard settings. Until I have that level of understanding of the command line interface, I'll stick with the GUI. Whenever I use the command line, I most of the time don't even know whhat the command will do once I hit Enter, much less what it will do these things to.

Give me a tutorial that explains those thigns to me, and I'll start using it more. Until then I'll stick with the GUI, where I at least have a clue of what I am doing.

You probably meant well with your post, but save the bubbly enthusiasm for someone who shares it, and give me something concrete that will actually help me. That's all I want. Promises of what I will know in two years are useless to me now, and now is when I need help.

/Mimsy

---

### Post by DarkN00b on 2006-09-23
I grew up in the days before Windows and for years I never used anything but the command line (DOS).  I find that it helps to try and draw parallels between the Linux command line and the DOS command line.  Of course this may not help you at all if you never used DOS. ;)

---

### Post by xpod on 2006-09-23
> What is "aptitude", and why do I need to type it in before I install something?

[http://ubuntuforums.org/showthread.php?t=37736](http://ubuntuforums.org/showthread.php?t=37736)

---

### Post by aysiu on 2006-09-23
> **Mimsy said:**
> 
Instead of telling me that in two years I'll be just like you (a scary thought), if I just keep stumbling blindly through everything I come across, give me some help and pointers. One should not be *forced* to use the terminal. It can be scary if you're forced. I think if you use a Linux distro long enough (with perhaps the exception of Linspire), you will naturally start exploring the terminal more.

> For example, 'cd' seems like it would mean Change Directory, because that's what it does, but beyond that, I'm lost. It is Change Directory. If you do *cd directory* that changes to *directory* inside of the one you're in. If you do *cd /directory*, that assumes the directory is at the top level. 

> What is "aptitude", and why do I need to type it in before I install something?  Because when you later decide to remove whatever you're installing now, *aptitude* will remember all the dependencies that came along with it and then remove those, too. To see in action the difference between *aptitude* and *apt-get* (the latter of which seems to be what Adept and Synaptic use), go here:
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude) > What is the difference between "upgrade" and "update"? Update just checks what software is available. Upgrade actually installs newer versions of the packages (assuming there *are* newer versions. > How do I get a list of available options so I know what i have to work with? *man aptitude*

> I prefer the GUI because when I go to System -> Preferences -> Keyboard, I can see the options available to me, and I know that what I do there will affect only the keyboard settings. That's the reason most people prefer the GUI. > Until I have that level of understanding of the command line interface, I'll stick with the GUI. A good choice. > Whenever I use the command line, I most of the time don't even know whhat the command will do once I hit Enter, much less what it will do these things to. Paste in enough commands, and you slowly start to learn the gist.

---

### Post by Mimsy on 2006-09-23
I think I've read that article on the differences between aptitude and apt-get before, it looks very familiar. If Synaptic uses apt-get, is there a way to track down ununsed packages and remove them? I doubt they're very big, but I'm kind of obsessed about keeping unnecesary clutter off my hard drives.  I'm used to Windows and all the unnecessary things that came with it...

I'm going to assume "man" stands for "manual" sice that makes it easy to remember. 

I can see myself exploring and experimenting with the command line down the road, when I know more about ubuntu. Even without understanding how to  use it, can see that it has potential. However, until I know what I'm doing, that potential is limited to 'potential to seriously FUBAR things', and I'd rather not do that just yet.

Thanks for all the explanations! :)

/Mimsy

---

### Post by aysiu on 2006-09-23
> **Mimsy said:**
> If Synaptic uses apt-get, is there a way to track down ununsed packages and remove them? I doubt they're very big, but I'm kind of obsessed about keeping unnecesary clutter off my hard drives. Yes, there's a program called *gtk-orphan* that finds "orphaned" libraries and allows you to uninstall those.
> 
I'm going to assume "man" stands for "manual" sice that makes it easy to remember.  You're correct.

> However, until I know what I'm doing, that potential is limited to 'potential to seriously FUBAR things', and I'd rather not do that just yet. Good choice.

---

### Post by Mimsy on 2006-09-23
Thanks again. :) I'll go look for gtk-orphan next, and see what it can find to get rid of.

xpod, thanks for posting that link. (I was busy writing my previous post while you did.) I had no idea aptitude could run with a simple gui, but that actually makes it a lot easier to use. Funny how we come to depend on little things like drop-down menus...

/Mimsy

---

### Post by xpod on 2006-09-23
> I had no idea aptitude could run with a simple gui,

Thats ok...neither did i.
Other than using synaptic that is

---

### Post by Lakefall on 2006-09-24
> **Mimsy said:**
> If Synaptic uses apt-get, is there a way to track down ununsed packages and remove them?
Yes, if such a system has been programmed into synaptic. I don't actually know, as I've got used to the user interface of aptitude and use it. (As somebody probably doesn't know, you can see the interface by typing "aptitude". Pressing "q" and selecting yes with the arrow keys gets you out. You can also use mouse.)

> I'm going to assume "man" stands for "manual" sice that makes it easy to remember.

Type "man man" for more information. Man is a very useful command. It may be the command you are looking for.

Note that man pages tend to be rather technical. They are meant for people who already understand how things work and are looking for details. You don't need to understand everything on a page. 

The man command is simple to use. You usually just want to type "**man** [_section_] _page_" The square brackets mean you can leave that part out. You are meant to replace the underlined parts with the actual section number and page name you are looking for. You usually don't need to bother yourself with the section. The man pages use the same syntax I used.

I understand it can be distressing to see stuff like
> man  [-c|-w|-tZ]  [-H[browser]] [-T[device]] [-adhu7V] [-i|-I] [-m system[,...]] [-L locale] [-p string] [-C file] [-M path] [-P  pager]  [-r prompt] [-S list] [-e extension] [[section] page ...] ...
but once you understand the syntax, you realise you can just ignore most of it. If you need to understand it, it's explained in detail in the DESCRIPTION and OPTIONS parts of the man page.

---

### Post by javaJake on 2006-09-25
> **Mimsy said:**
> However, until I know what I'm doing, that potential is limited to 'potential to seriously FUBAR things', and I'd rather not do that just yet.Well, for one thing, if you backup documents, and you don't use sudo without really knowing what you are doing, then there shouldn't be any issues.

I keep my home directory copied and synchronized on two desktops. If I delete a file on one, I recover it from the other.

Really, the only reason why you wouldn't use the terminal now (if you've backed things up, and you aren't using sudo) is because it takes longer or is harder to remember and punch in commands then to go through GUI. For me, "apt-get install bzflag" is tons easier then "Applications -> Add/Remove -> " (wait for it to load) " -> Games -> Check BZFlag -> OK", but that's only because I know the command, how to use TAB to get a list of apps if I don't remember what it is called, and how to use other quick programs to get more information.

This is ligitimate reason! Not to be all teary-eyed, but I was there once, and know what it is like!

Actually, I don't even know why we are arguing - both methods are perfectly fine, since they get us where we want to go. Until, that is, you update xorg only to find out that the update crashes. Then you'll want to know that centericq is the Gaim equivilant for the terminal, and that lunx is a browser for the terminal, and that #ubuntu is where you get help. :D

One last comment before this post putters out: I'm not at all flaming. I'm discussing. Please don't take what I say the wrong way. [-o<

---

### Post by xpod on 2006-09-25
>  A post to vent your Ubuntu complaints

These forums breaking all the time is a pain...:-#

---

### Post by Mimsy on 2006-09-25
> **javaJake said:**
> 
Actually, I don't even know why we are arguing - both methods are perfectly fine, since they get us where we want to go. Until, that is, you update xorg only to find out that the update crashes. Then you'll want to know that centericq is the Gaim equivilant for the terminal, and that lunx is a browser for the terminal, and that #ubuntu is where you get help. :D

But I can just as well use my Windows PC for that. I'm a near-fanatical PC gamer (there's a reason I remain so poor), so there will alwas be a Windows in my house, and it can access these forums just as well as the laptop can. :) 

The reason I use the laptop for surfing and emails is that it's just faster. 

Yes, Ubuntu on a P3, 256 MB RAM laptop surfes the internet faster than my good gaming PC with WinXP does. There is either something highly ironic about that situation.

/Mimsy

---

### Post by pyman on 2006-09-25
Sorry to hear about anyone having with Ubuntu. It is nice that if you have problems with Ubuntu there is a place where you can rant that is hosted, maintained, and indeed allowed by the people that put so much into Ubuntu.
This is the best most supported community for any OS. IMHO.
So...
Rant away, I love Ubuntu and I am a Microsoft MCSD, MCP.

---

### Post by xpod on 2006-09-25
The more problems i had in my few months of windows the more i wanted to know what the other 10% used...

The more problems i have with this the more i enjoy it....weird:twisted:

---

### Post by javaJake on 2006-09-25
> **xpod said:**
> These forums breaking all the time is a pain...:-#

That's because they're doing major upgrades. This won't happen all the time. :p

---

### Post by Brunellus on 2006-09-25
> **javaJake said:**
> That's because they're doing major upgrades. This won't happen all the time. :p
Now is a good time to mention that YOU can do your part to alleviate strain on the forum servers.  Please, we BEG YOU, use the search function rather than posting new threads willy-nilly.  Odds are, your problem has already been solved many times over.

---

### Post by xpod on 2006-09-25
> That's because they're doing major upgrades. This won't happen all the time. 

:D I sort of tippled eventually.....It`s just that usually they go offline when they are doing something but this time it stayed up but just none of the posts were moving so it looked as though no-one had posted for an hour..

It went offline for a wee while eventually but it just seemed weird..

It`s only a pain when you dont realise why things aint moving...lol

---

### Post by xpod on 2006-09-25
> Now is a good time to mention that YOU can do your part to alleviate strain on the forum servers. Please, we BEG YOU, use the search function rather than posting new threads willy-nilly. Odds are, your problem has already been solved many times over.

:oops: 

IM getting better;) .....Not a lot of threads lately.
I seem to like a post to myself though so is THAT bad tooo?

Not as bad as the guy with over 2000 since august though....phew:mrgreen:

---

