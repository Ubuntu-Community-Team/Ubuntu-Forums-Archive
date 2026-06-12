---
title: "Getting jaded...List o' Problems"
date: 2007-06-21
forum: Absolute Beginner Talk
---

### Post by whiskeysquared on 2007-06-21
Why is everything so complicated in Ubuntu?  After weeks, yes weeks, I finally got my resolution corrected on my monitor.  But I still have a whole host of other problems (2 very major problems, outlined below).  And no solution seems to be simple.  Everything seems to go by the same algorithm of:  

Find key to universe,
```
sudo gedit /etc/LIFE.conf
```
and retype the meaning of life,
promise first born son to Ubuntu
and etc.

But nothing is simple, like open this and click that.  That's not what I was sold on...  I was told Linux had made its way into being a usable-by-the-mainstream operating system.  I don't consider myself stupid, but spending weeks on getting my monitor to work right doesn't seem fun and finally getting it worked out didn't feel rewarding; especially when a windows machine would've just...worked.

I'm not trying to rant about Ubuntu, I want it to work for me.  But I'm investing so much time into getting it to just...function, enough for me to be able to use it as a production machine, that's it not worth it.  So, please if you can answer, simply, the following I would greatly appreciate it.

1.  I have a nice Brother DCP 7020 Copier/Printer/Scanner that's completely useless with Ubuntu, I've tried the app that supposedly gets most printers working, it doesn't work and the nearest driver prints WAY off.  Brother has a driver that allegedly works for linux for my printer, but I've yet to be able to get it working.

2.  I have a Windows laptop (luckily) and I would like to connect my external drive to the Ubuntu machine and easily share files back and forth from the laptop to the Ubuntu box.  Much like I would be able to do with two Windows boxes.  Everything seems to point to Samba, but Samba is like trying to decipher hieroglyphics without the Rosetta Stone; so any simple ways?

I completely expect a multitude of links to the forum entries I've already read, and I've read a lot that allegedly fix these problems, but they all go into some really complicated things.  I'm looking for simple solutions.  If there are none, just say there are no simple solutions and I'll go about my business and reinstall XP.  I really want to be able to use this, so I hope there are simple fixes.

---

### Post by Inxsible on 2007-06-21
I dont know nothing about the Brother copiers but for you second problem, if transferring files is your only objective, you can simply use a USB stick or an external drive to do it. I dont think it can get any simpler than that

---

### Post by deadgobby on 2007-06-21
I understand your frustration with Linux and that is great that you are not given up easy. It is a lot different than windows and you need to throw out the windows way of thinking. I know all you want to do is print right now on your brother printer. I had a brother laser printer and it would print fine from the net, but big print from every thing els. So you'll need to play with your printer settings. You may need to get the cups driver from brother web site. 
[http://solutions.brother.com/linux/en_us/index.html](http://solutions.brother.com/linux/en_us/index.html)
 If you did that and you still are not happy. Email them. I did and they did help out. I cannot recall of top of my head what I did to fix the BIG print, yet it had to do with playing with the settings. After a year the printer went to crap and I picked up a nice HP instead. I love my HP laser jet 2100. Really HP printers work very well with Linux and Unix. 
Gobby

---

### Post by spartan777 on 2007-06-21
is the external drive formatted in ntfs? if you don't understand that, did you format it in windows? it is probably ntfs, and in that case, does the drive show up at all if you plug it in? is it usb or firewire or esata?

---

### Post by whiskeysquared on 2007-06-21
Okay, some elaboration.

Inxsible

> I dont know nothing about the Brother copiers but for you second problem, if transferring files is your only objective, you can simply use a USB stick or an external drive to do it. I dont think it can get any simpler than that

I might not have made it clear in my original post, I think I did, but maybe not.  The drive I'm looking to share IS an external drive.  I want to connect the drive (via USB spartan777, that is formatted in a way that is readable in Linux) TO the linux box, and through my home network, get onto my laptop (windows) and when needed, through the network, access my external drive (read and write) through the linux box in which it is connected to.  This is something that is super simple to do with two windows machines.

Deadgobby

Philosophically, I understand Linux is going to be a lot different than windows.  Really I do.  And I accept that I will have to sacrifice a certain way of Windows thinking; but that shouldn't mean that I need to sacrifice the ease of use way of thinking.  Really, the windows is demonic thing aside, when I plug something in, it works.  I couldn't even plug my monitor in and have it work.  I downloaded a driver made FOR linux for my printer and it doesn't work.  And maybe (and probably) it's user error; but why must it be that complicated.  And that's my point, if this is supposed to be so easy my mom could do it, I shouldn't have to open up the terminal or edit code at all when I'm trying to configure some of these basic things.

You mention my frustration and I do have some; but it's not toward Ubuntu specifically, it's toward Ubuntu's cumulative claim that it's the OS to switch to.  It should *at least* match the ease of configuration that commercial OS's provide.  And I do understand that a lot of blame goes to manufacturers for not having linux drivers, but a lot of the complication could be taken away by centralizing a lot of the apps that help out into the base install of Ubuntu.

---

### Post by bobfarrell on 2007-06-21
The reason things are so complicated in Linux distributions compared to Windows is, largely I think, due to the fact that there are so many more things to configure, and so many choices of how to do them. So once you get used to Linux the choice becomes a really positive thing - you get used to the idea of things taking a bit longer to set up because once you've done it, you can have everything tweaked and refined exactly how you want it, and that's one of the most important features of Linux and open source software in general.

In answer to your question about file sharing, I'd say Samba's the best way to go. You can install it from Synaptic, or from the terminal ```
sudo apt-get install samba
```

But, unfortunately, I wouldn't get my hopes up about it being a particularly easy install if Windows is your thing.

---

### Post by whiskeysquared on 2007-06-21
Bob, thanks for the reply.  I understand and welcome the control open source gives us.  I've embraced this for years with web apps, just not with Linux.  And I do enjoy having the control at my disposal, but think it should be an option, not a requirement in order to use it, even at a very basic level "out of the box".  

For example, I have downloaded Samba, that's why I mentioned it earlier as being as complicated as trying to read ancient symbols.  But, and herein lies a great problem with linux, to even get going in the right direction with Samba I had to look at, literally, 15 different posts/wikis from completely different websites.  All with different tutorials and difference advice.  So, even if you do have the patience to start fooling with linux and you seek any sort of guidance, good luck finding a centralized, up-to-date site that will have the information you seek.  I think it's impossible given the chaos that is open source development for documentation to be anywhere in the realm of organized.

So, thanks for the Samba recommendation, but I have tried it, without any luck.  And from what I found from descriptions in one of the 15 tutorials about how it works when you get it to work, it seems like the equivalent of duct tape and very rigged up.  I'm looking for usable, stable consistency and I'm not finding it.

But I'm not giving up, perhaps I should, but I know there must be an easy...to hell with easy because it isn't going to happen...  there must be a clear, somewhat manageable method of fixing my two primary problems.  I just know I can't bank on this machine being stable for production and I certainly can't recommend others attempt to do this and still expect to be instantly productive.

Ubuntu, at a glance now, seems to only work straight out of the box only if you groom your hardware to be completely compatible with linux.  From the monitor to the printer, to the GPU, etc.  This type of hardware requirement is very reminiscent of Vista.

Thanks again for the response.  And please, other readers, if you have an idea, let me in on it.  If you dispute anything I have to say, let me hear it too.

---

### Post by darren1270 on 2007-06-21
Wow that is such a rant!  LOL just kidding.  I understand that you have been trying to do things for weeks to get up and running.  Wouldn't it be nice to stick with ubuntu in let's say a dual boot environment so that when you do have time to learn you can do so at your own pace.  Remember switching to any flavor of linux involves learning to walk before you can run.  And I do think that in time you'll find that being able to have total control over your computer as apposed to your computer having control over you will be a great great step foreward for you.  Also remember....these are not problems....they are valuable learning experiences.  Sorry for my 2 cents worth but there you go!

Good Luck,
Darren

Ps... Remember this... Ubuntu just works for **ME** and if not that's ok to!

---

### Post by whiskeysquared on 2007-06-21
If it turned into a rant, I apologize, but I do hope it was well constructed, tame, gentlemanly rant.

The dual boot scenario, as outlined in another post on this forum turned into the first Ubuntu nightmare for me.  So I just went with a complete Ubuntu install.  I have my windows laptop for my production stuff so I can pay bills, but I want my desktop back and I want Ubuntu on it.  I just think I have a right for it to work before I drink the kool aid.

I'm well versed in Windows, yes, but I never really thought it had control over me...  I had access to everything that I needed and it worked.  If it was broke, it was easy to fix.  Ubuntu on the other had has it's control over me as I'm not at a point where I want to spend my days and nights becoming a linux expert; I just want to be a user.  But I get your closed architecture reference.

---

### Post by darren1270 on 2007-06-21
> **whiskeysquared said:**
> If it turned into a rant, I apologize, but I do hope it was well constructed, tame, gentlemanly rant.

The dual boot scenario, as outlined in another post on this forum turned into the first Ubuntu nightmare for me.  So I just went with a complete Ubuntu install.  I have my windows laptop for my production stuff so I can pay bills, but I want my desktop back and I want Ubuntu on it.

Not sure what approach you took to dual boot but here is what I did. (Wasn't concerned about loosing data as this was an old PC I picked up from work)

1.  Using killdisk I erased the entire hard drive.  You can get it here [http://www.killdisk.com/downloadfree.htm](http://www.killdisk.com/downloadfree.htm)  Burn the .iso and boot from the CD.  Free version only supports one pass but it works.

2.  Using A Windoze XP CD and installed it to the cleaned hard drive... When I got to the partitioning part of the install I made windows half of my 80 gig HD.

3. Set up windows with all the updates and made sure that worked fine.

4.  Put my fiesty cd in and restarted my computer making sure I would boot from the CD.

5.  Used the fiesty automatic method to install by telling it to use all continuous free space.

6. About 25 minutes later I was rebooting with the grub handling my boot options and what do you know I was now using fiesty on my dual boot pc that work was going to throw away!

If you follow the example I gave you shouldn't have any trouble.

Darren

No problem about the rant thing... I was just kidding around with you!

---

### Post by shearn89 on 2007-06-21
A lot of the problems with linux not being as easy to set up is that lots of companies don't make compatible hardware for it - its all windows-orientated. And sometimes, the combination of your hardware just doesn't work.

For example, i've tried repeatedly to try and get my Linksys wireless card working on my old laptop, which runs ubuntu fine; but the chipset my card is made with isn't natively supported by linux. So i installed ndiswrapper, and followed all the howtos i could find, but for some reason, anytime i connect to the network, my laptop freezes. Totally. There's not much i can do, as i never get any error messages - its probably just my laptop, and the specific hardware.

So i know its frustrating, and the terminal seems daunting, but more often than not the terminal is much easier to use than anything else, and not that hard to learn once you start using it.

---

### Post by carusoswi on 2007-06-23
If every single one of your initiatives in Ubuntu has been disasterous as you seem to indicate, then, either there is something wrong with your hardware setup or your approach is totally wrong (in reality, I'm guessing that your "rant" is a bit exaggerated and neither of my "eithers" applies).

You stated that setting up a dual boot was a disaster for you . . . did you ever succeed at that?  Sounds as though you gave up on it.  If you have wiped Windows off the machine for a full Ubuntu install, why not wipe the disc again and do a proper dual boot installation and prove for yourself that some things in Ubuntu really do work as described.

I would call myself pretty well versed in things Windows, and know well the feeling that came over me after I first installed Ubuntu.  I felt great that it worked, but, then was sort of stairing at the screen wondering to myself, "ok, so, now what can I do with it?"

I couldn't get any of the software to install because I had no idea how that is done in Ubuntu.

I have probably played with the program for six months now - and have not even attempted to install a printer.  But, I have managed to get a brand new N1 wireless router working, and I have successfully used both VMware and Virtual Box to install XP from within Ubuntu - and I do have my suite of core Windows products running under Crossover.

I have actually used Crossover to run MS Access to enter from home some of the office work I brought home with me - but I have not actually succeeded in making Ubuntu my only OS.

I would prefer it because it feels more stable than Windows.  You start your machine, it loads, and is there, ready for you to begin YOUR tasks, without constantly nagging you to check your security or running some AV routine without your permission or performing some atuomatic update that requests a reboot.  On my office machine, the most recent versin of Internet Explorer has taken to just opening up blank pages when i haven't even asked the machine to go online (it's always online as it is hooked to our T1).

To state that Ubuntu evokes feelings of Vista I think is a bit unfair.  Try running any non-windows software on a windows installation and see how far you get.  If you know Vista, you also know that it's all about monitoring your use and enforcing compliance with MS's view of fair use in all manner of intellectual property areas.  The underpinnings of the ap do not represent much in the way of enhanced computer use at all. and MS spent years and devoted millions (or billions) of dollars gleened from its user base to develop Vista.

I suggest you check into receiving via email a free subscription to Eweek.  They offer really good discussions about what is going on in the open source world and you may develop a healthier outlook on your frustrations with Ubuntu.

I remind you (even though you clearly already understand) that Ubuntu is entirely free, developed entirely by folks, most of whom, do this because they believe in open source (I won't say that none of them get paid - some clearly do - I don't quite understand the business infrastructure side of linux).  I have not tried other distros, but, suspect that Ubuntu is popular because, amongst what's available in linux, it is probably the easiest (or at least seems to enjoy that reputation).

But, most of us who approach Ubuntu as users (rather than trained computer programmers), do so from a Windows perspective that is long-engrained.  We are used to paying big money for applications and install them with high expectations that, given what we have invested, the thing had better darned be working right out of the box.

It's not really fair to view Ubuntu in that light.  Any "claims" you cite stating that Ubuntu is "so easy that . . ." were not made to promote the product to gain an advantage over some other distro.  Generally, you are reading statements made by folks who are using the OS.  Other than a deeply held belief in open source, developers of Ubuntu have no motive to grab your attention.  You won't find any cute commercials on TV knocking IBM or Apple.  You won't read any stories about how some Ubuntu exec strong-armed this or that or those companies to get them to use and develop for Ubuntu exclusively - no software rammed down your throat (like IE) that you cannot uninstall.  No automatic updates, no planned obsolescence (try purchasing a new XP box these days - there was about a two week span when big box computer stores would not even sell you a computer - their supplies of Vista machines were enroute, and they had finished selling anything XP).

So, it looks as though I've done a little ranting, myself, also trusting that I've done it in a polite manner.

I do understand your frustration . . . but, the nice thing about Ubuntu is that it is so easy to just scrap the installation and start over . . . you won't be sorting through any stacks of install discs - pretty much everything you need is either on the Live CD or in the repositories . . . and if not, you have this friendly community to which you can always return and, generally, find the solution (complete with copy/paste code) to most of your problems.

Take your time (oh, and, you will have to become somewhat expert - at least in locating solutions in threads on this board and copy/pasting into your terminal), continue to lean on Windows to get your work done, and enjoy this learning experience.

You have probably forgotten what most of us can probably look back on as days of frustration with Windows or Win-based applications - and we paid every step of the way.

[end of rant]

Good luck.

Caruso

---

### Post by shearn89 on 2007-06-23
> . . . but, the nice thing about Ubuntu is that it is so easy to just scrap the installation and start over . . .
That (i have to say) is one of the nicest things about ubuntu. Especially since if you install with a /home partition, it makes upgrading to a new distro much more hassle-free. As an example, my Feisty install disc arrived yesterday; as i was running dapper, and the corporate internet i'm connected to filters some of the upgraded packages due to combinations of letters like "boob", i had to upgrade to feisty via a disc, rather than using dist-upgrade. So i put in the disc, went through the (very nice!) graphical install, told it to use my current /home partition for my user, and rebooted. When i started up again, it had all my settings, all my THEMES, and everything else, exactly as it was. All i did was apt-get a few bits of software, and i was back where i was... Compared to the whole weekend you have to write off in order to reinstall windows, the hour it took to complete the whole process, from boot off live disc to updating the system, was much appreciated...

I guess what i'm trying to say is that it may be tricky at first, but persevere, and eventually its much easier than windows...

---

### Post by zipperback on 2007-07-14
> **whiskeysquared said:**
> Why is everything so complicated in Ubuntu?  

It isn't complicated. It is just different from what you are used to. And since you are coming from  a different operating system, there is going to be a learning curve for you.


> **whiskeysquared said:**
> 
After weeks, yes weeks, I finally got my resolution corrected on my monitor. 
 

Weeks? Oh come now. Did it seriously take you weeks to change the resolution?


> **whiskeysquared said:**
> 
But I still have a whole host of other problems (2 very major problems, outlined below).  And no solution seems to be simple.  Everything seems to go by the same algorithm of:  

Find key to universe,
```
sudo gedit /etc/LIFE.conf
```
and retype the meaning of life,
promise first born son to Ubuntu
and etc.


Linux has a security method using user level vs administrator level rights.

sudo allows a normal level user account to perform an administrative level common, IF they are  in the sudoers list.

Once you get familiar with how the user level vs administrator level rights work on your system, and the fact that they prevent normal user level accounts from making administrative level changes, it isn't difficult for most people.

> **whiskeysquared said:**
> 
But nothing is simple, like open this and click that.  


It depends on what you want to do. For example, package management with tools like synaptic, and all the various administrator tools available for system management, do in fact make it very much a few mouse clicks for certain things. Including changing your screen resolution, providing of course you are using the correct video drivers and such.


> **whiskeysquared said:**
> 
That's not what I was sold on...  I was told Linux had made its way into being a usable-by-the-mainstream operating system.  I don't consider myself stupid, but spending weeks on getting my monitor to work right doesn't seem fun and finally getting it worked out didn't feel rewarding; especially when a windows machine would've just...worked.


May I ask you please what video card and monitor it is that took you so long to configure?
Because it shouldn't take even a total beginner weeks to configure something like that.



> **whiskeysquared said:**
> 
I'm not trying to rant about Ubuntu, I want it to work for me.  But I'm investing so much time into getting it to just...function, enough for me to be able to use it as a production machine, that's it not worth it.  So, please if you can answer, simply, the following I would greatly appreciate it.

1.  I have a nice Brother DCP 7020 Copier/Printer/Scanner that's completely useless with Ubuntu, I've tried the app that supposedly gets most printers working, it doesn't work and the nearest driver prints WAY off.  Brother has a driver that allegedly works for linux for my printer, but I've yet to be able to get it working.


See the following link in regard to your printer.
http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020
Contact the manufacturer and tell them you want them to provide full linux supprt for it, if it isn't working correctly. By letting them know there is a serious demand for a viable driver for it, then you can help get it fully functional.


> **whiskeysquared said:**
> 
2.  I have a Windows laptop (luckily) and I would like to connect my external drive to the Ubuntu machine and easily share files back and forth from the laptop to the Ubuntu box.  Much like I would be able to do with two Windows boxes.  Everything seems to point to Samba, but Samba is like trying to decipher hieroglyphics without the Rosetta Stone; so any simple ways?



Click "Places" -> "Network" -> "Windows Network" should allow you to browse your windows network, (I think).

I don't use Windows on any of my computers. I honestly don't have any need whatsoever for windows.




> **whiskeysquared said:**
> 
I completely expect a multitude of links to the forum entries I've already read, and I've read a lot that allegedly fix these problems, but they all go into some really complicated things.  I'm looking for simple solutions.  If there are none, just say there are no simple solutions and I'll go about my business and reinstall XP.  I really want to be able to use this, so I hope there are simple fixes.


Simple solutions:
Item 1) Printer.
Read the link I gave you in regard to which printer driver to use.

Item 2) Windows network.
Click Places, Network, Windows networking.

It isn't complicated, it's just different.

- jack

---

### Post by whiskeysquared on 2007-07-15
> **zipperback said:**
> It isn't complicated. It is just different from what you are used to. And since you are coming from  a different operating system, there is going to be a learning curve for you.

Understood and is to be expected.  And there is a learning curve that I completely accept responsibility for.  And while my list of problems may illustrate me to be a complete fool when it comes to computers, I assure you that I am not.  I just look for the user friendliness of everything.  Usability is a very important ingredient in a platform that is looking to gain more ground.  And that's really why (other than to get answers) I even posted about this.
> **zipperback said:**
> 
Weeks? Oh come now. Did it seriously take you weeks to change the resolution?

Seriously.  And to answer your question further down, I'm on an NVIDIA card with a 1440 x 900 BenQ widescreen.  And, because it seems unbelievable, I'll tell you why.  Because, when you search for solutions with Linux you cant get one, clearly defined answer.  You find 100 different ways to do something.  And, while that may seem awesome, it's also very confusing on an alien platform to someone new.  But Ubuntu only registered one resolution "out of the box" and it was a VERY involved ordeal to fix it, and even now when an update is released, the GUI crashes and I need to start all over again.  And I can never remember what one solution fixed it.  And I guess that's the appeal for some people, but for me Ubuntu is like playing around with a chemistry set that came without a guidebook.
> **zipperback said:**
> 
Linux has a security method using user level vs administrator level rights.

sudo allows a normal level user account to perform an administrative level common, IF they are  in the sudoers list.

Once you get familiar with how the user level vs administrator level rights work on your system, and the fact that they prevent normal user level accounts from making administrative level changes, it isn't difficult for most people.



It depends on what you want to do. For example, package management with tools like synaptic, and all the various administrator tools available for system management, do in fact make it very much a few mouse clicks for certain things. Including changing your screen resolution, providing of course you are using the correct video drivers and such.


That really wasn't what I was referring to.  In fact, I find the things that ARE done with a simple point and click very exciting.  Now if everything was as centralized and easy to comprehend as the available software repositories, I wouldn't be voicing concern.  What I was talking about were all the solutions to problems, which always turn into this very daunting task.

> **zipperback said:**
> 
May I ask you please what video card and monitor it is that took you so long to configure?
Because it shouldn't take even a total beginner weeks to configure something like that.


I suppose, to elaborate on that a bit, I tried Envy first to get the NVIDIA card working.  Envy then crashed my GUI and since the fix for that seemed too difficult I just reinstalled Ubuntu.  So I stay away from Envy.  Then I went to Automatix, which again, didn't actually cause Ubuntu to add my resolution to the available list.  So I ended up editing my xorg file 200 different ways (exaggerating, but I edited a lot) because there were a LOT of recommendations from a lot of people that didn't work for me, until finally one did and then I stepped slowly away as to not disturb it and it worked until I updated Ubuntu on whim and then the whole thing crashed again...  Long story, but it's sort of working again now.  Fonts still look like crap, but I've come to expect that with Ubuntu now as I can't find a viable solution for that.

> **zipperback said:**
> 
See the following link in regard to your printer.
[http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020](http://openprinting.org/show_printer.cgi?recnum=Brother-DCP-7020)
Contact the manufacturer and tell them you want them to provide full linux supprt for it, if it isn't working correctly. By letting them know there is a serious demand for a viable driver for it, then you can help get it fully functional.



I finally figured this out on my own.  Luckily Brother had some clear documentation on how to use their drivers on Linux.  I'm still unable to share the printer with the windows network, but I'm afraid to mess with fate as (at least) my Ubuntu install seems to be very fragile.

> **zipperback said:**
> 
Click "Places" -> "Network" -> "Windows Network" should allow you to browse your windows network, (I think).

I don't use Windows on any of my computers. I honestly don't have any need whatsoever for windows.


Tried that and it doesn't work.  And I've set samba to share my external drive with ONE windows computer on the network, but only the one.  All the others can't access it.  So, partially resolved, through my own trial and error.

> **zipperback said:**
> 







Simple solutions:
Item 1) Printer.
Read the link I gave you in regard to which printer driver to use.

Item 2) Windows network.
Click Places, Network, Windows networking.

It isn't complicated, it's just different.

- jack

In the end, it feels like some new problem comes up every time I turn it on.  Especially with firefox.  Every time I open firefox, another one of my extensions isn't working.  So far I've lost functionality with the eyedropper, google sync and the gmail checker.  There were others but I sacrificed them a long time ago.  I can see the potential, but I stand by my original statement that while it's made great strides, it's still not user friendly when problems come up.

---

### Post by zipperback on 2007-07-15
> 
That really wasn't what I was referring to.  In fact, I find the things that ARE done with a simple point and click very exciting.  Now if everything was as centralized and easy to comprehend as the available software repositories, I wouldn't be voicing concern.  What I was talking about were all the solutions to problems, which always turn into this very daunting task.



I do agree with you. There are some things which can seem quite overwhelming to people when they first start using Linux and find that they need to go manually edit a configuration file by hand and such.



> 
I suppose, to elaborate on that a bit, I tried Envy first to get the NVIDIA card working.  Envy then crashed my GUI and since the fix for that seemed too difficult I just reinstalled Ubuntu.  So I stay away from Envy.  Then I went to Automatix, which again, didn't actually cause Ubuntu to add my resolution to the available list.  So I ended up editing my xorg file 200 different ways (exaggerating, but I edited a lot) because there were a LOT of recommendations from a lot of people that didn't work for me, until finally one did and then I stepped slowly away as to not disturb it and it worked until I updated Ubuntu on whim and then the whole thing crashed again...  Long story, but it's sort of working again now.  Fonts still look like crap, but I've come to expect that with Ubuntu now as I can't find a viable solution for that. 


That's kind of strange that you're having so many problems.

Could you post up a screen shot so I can see what you are dealing with in regard to "Fonts still look like crap.". Perhaps I might be able to asssist you in fixing that issue.



> 
Tried that and it doesn't work.  And I've set samba to share my external drive with ONE windows computer on the network, but only the one.  All the others can't access it.  So, partially resolved, through my own trial and error.


Perhaps you could type up a How-To of what you did and others might be able to learn from it, and help you resolve any issue that might be still causing you problems with it.



> 
In the end, it feels like some new problem comes up every time I turn it on.  Especially with firefox.  Every time I open firefox, another one of my extensions isn't working.  So far I've lost functionality with the eyedropper, google sync and the gmail checker.  There were others but I sacrificed them a long time ago.  I can see the potential, but I stand by my original statement that while it's made great strides, it's still not user friendly when problems come up.

I haven't used any of those extensions. I pretty much just run Firefox with a few multimedia plugins and thats about it. 

- Jack
- zipperback :popcorn:

---

### Post by whiskeysquared on 2007-07-20
> **zipperback said:**
> 

That's kind of strange that you're having so many problems.

Could you post up a screen shot so I can see what you are dealing with in regard to "Fonts still look like crap.". Perhaps I might be able to asssist you in fixing that issue.

I will as soon as I encounter a GOOD example again.  For example, my screen now, I know is off on text sizes and such, but there are more extreme examples on other pages that I will grab for you.  It's mainly a firefox issue.  Other issues are just my own dislike of the linux sans font.  I've tried changing it but MS fonts do not render correctly.
> **zipperback said:**
> 
Perhaps you could type up a How-To of what you did and others might be able to learn from it, and help you resolve any issue that might be still causing you problems with it.

I absolutely would if I had any idea how I came to my solution.  Seriously, I follow EVERY tutorial I find to the letter and it doesn't work out for me.  Most issues have multiple posts for the same thing describing different routes on how to do something, which leads me down this path that I don't know how to get out of and eventually I do something accidentally and it fixes it.  The only tutorials that seem to work are those written by manufacturers that have some semblance of linux support; like Brother for my printer.  
> **zipperback said:**
> 
I haven't used any of those extensions. I pretty much just run Firefox with a few multimedia plugins and thats about it. 

See, I'm used to those extensions and firefox is pretty much useless to me without its ability to have operable extensions.  Does your flash plugin routinely go crazy and give some weird reverb/echo noise, or if you right click over the flash area, does it crash firefox completely?

I think i'm a couple of frustrations away from busting out my windows disc, this is taking up way too much time.  I do appreciate your help though.

---

### Post by mlentink on 2007-07-20
> **whiskeysquared said:**
> I think i'm a couple of frustrations away from busting out my windows disc, this is taking up way too much time.  I do appreciate your help though.

This is what I don't understand. If Windows works for you, why not simply use it, especially if your income depends on it? Why put so much effort in something you cannot get to work easily?
 I have a business to run. I don't have much time to play around with stuff. My mailserver is Ubuntu 6.06, my desktop is feisty, my notebook is Feisty, my wife's desktop is fesity, the only Windows machine left in the house is my son's for gaming. I chose Ubuntu because it works for me (OOo for most activities, Bluefish for webwork), in fact turned out to be rock-solid.

Ubuntu is about choice. Even the choice not to use it if it doesn't work for you

---

### Post by whiskeysquared on 2007-07-20
mlentink you're completely right and I understand your statement.  The only reason I've been working with it so long is because of the hype.  I honestly am not a complete idiot and I wanted to get the system working and experience what the hype was all about, but it's evading me altogether.  I've consistently found nothing just works in ubuntu and it kills me.  But there's a time when you just have to accept defeat, and I think I'm there.  I think if I can't figure out this firefox issue and get my scanner working, I'll throw in the towel.

---

