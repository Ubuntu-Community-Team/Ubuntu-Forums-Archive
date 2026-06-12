---
title: "First impressions &amp; some basic questions"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by arphaus on 2007-04-23
Yesterday, Ubuntu was my first ever successful install of a non-MS operating system.  After I cleared space on the hard drive and deleted an existing partition, it was easy.  Disturbingly easy.  I'm not used to needing to answer only 7 questions for the install.  This was definitely a change for the better.

RAM usage seems a bit lighter, but I'm not running as much as I do with XP, where I usually have ~639mb free after booting & loading the system tray with stuff like Skype, Nod32, etc.  Even so, it seems more responsive overall and (with fewer apps in the tray) takes about 100mb less RAM.

Q1: Does Ubuntu tend to be easier on resources?

[Kidders]("http://ubuntuforums.org/showpost.php?p=1481075&postcount=5") states the following in another thread:
[QUOTE=kidder]# Say goodbye to fragmentation
# Say goodbye to disks slowing down as they fill up
# Linux doesn't slow down or misbehave if you don't reboot it every now and then.[/QUOTE]

Q2: Is that accurate?  The way Windows degrades in performance over time is one thing that's bothered me over the years.  Does Ubuntu constantly defragment like OS X?  How is disk fragmentation prevented?

I've installed a number of programs already, tho I haven't used them yet (basically getting all the options for replicating my needs.  I like how there are repositories.

Q3.  I guess you can check to see if your installed programs have updates?
Q4. Does all this installation (or uninstallation) have the ability to affect system stability like in XP (aside from some specific conflict between 2 apps).

Q5.  What is a 'session?'  That's a tough one to search on the forums as that pulls a wide range of responses.  Is it possible to have different setups with various running applications & desktop arrangements?  Is it possible to have the pc boot and have it automagically start some specific programs?

Thanks - this has been quite the revelations so far!

Next on the agenda:
[LIST=1]
[*]Figure out vpn.  One network I access requires the Cisco VPN client, and my attempted install yesterday was fruitless.  However, on the same network Macs can connect via LEAP, so I'm curious if that's possible with Ubuntu.
[*]Setting up Thunderbird so I can use it in both Ubuntu & XP until I decide whether I'm going to use Ubuntu fulltime.
[*]Figuring out WINE, starting with Photoshop, Illustrator & other Adobe/Macromedia products.  Then move to playing a bit with adding other apps (FL Studio?) for the hell of it.
[/LIST]

---

### Post by Cypher on 2007-04-23
A1. The Linux Kernel has been said to be more robust than the Windows Kernel. So you will find Linux running perfectly fine on PCs with much more limited resources than Windows. Having said that, if Linux needs to use more of your PC to perform a function, it will do so.

A2. I'm not really sure about fragmentation, so I'm not going to say one way or another. As far as slow downs go, right you will not notice any if you start putting more stuff on there and lastly yes a properly configured/maintained Linux machine can stay up for months, if not, years without any problems.

A3. Any program installed through Synaptic will be checked and udpated when a new one is available. You can also install application entirely seperately and manually and in that case you will have to do the work yourself.

A4. The installation/un-installation will not mess anything up. Unlike Windows programs that just clutter up the Registry with all sorts of stuff, you don't have that here.

A5. I am a recent re-convert to Ubuntu and as of yet don't feel like I know everything about the desktop environment to adequetly answer this question.

Regards

---

### Post by igknighted on 2007-04-23
> **arphaus said:**
> Yesterday, Ubuntu was my first ever successful install of a non-MS operating system.  After I cleared space on the hard drive and deleted an existing partition, it was easy.  Disturbingly easy.  I'm not used to needing to answer only 7 questions for the install.  This was definitely a change for the better.

RAM usage seems a bit lighter, but I'm not running as much as I do with XP, where I usually have ~639mb free after booting & loading the system tray with stuff like Skype, Nod32, etc.  Even so, it seems more responsive overall and (with fewer apps in the tray) takes about 100mb less RAM.

Q1: Does Ubuntu tend to be easier on resources?

[Kidders]("http://ubuntuforums.org/showpost.php?p=1481075&postcount=5") states the following in another thread:


Q2: Is that accurate?  The way Windows degrades in performance over time is one thing that's bothered me over the years.  Does Ubuntu constantly defragment like OS X?  How is disk fragmentation prevented?

I've installed a number of programs already, tho I haven't used them yet (basically getting all the options for replicating my needs.  I like how there are repositories.

Q3.  I guess you can check to see if your installed programs have updates?
Q4. Does all this installation (or uninstallation) have the ability to affect system stability like in XP (aside from some specific conflict between 2 apps).

Q5.  What is a 'session?'  That's a tough one to search on the forums as that pulls a wide range of responses.  Is it possible to have different setups with various running applications & desktop arrangements?  Is it possible to have the pc boot and have it automagically start some specific programs?

Thanks - this has been quite the revelations so far!

Next on the agenda:
[LIST=1]
[*]Figure out vpn.  One network I access requires the Cisco VPN client, and my attempted install yesterday was fruitless.  However, on the same network Macs can connect via LEAP, so I'm curious if that's possible with Ubuntu.
[*]Setting up Thunderbird so I can use it in both Ubuntu & XP until I decide whether I'm going to use Ubuntu fulltime.
[*]Figuring out WINE, starting with Photoshop, Illustrator & other Adobe/Macromedia products.  Then move to playing a bit with adding other apps (FL Studio?) for the hell of it.
[/LIST]

1) Linux will report to use more RAM than windows, because the philosophy is "unused ram is wasted ram".  Anything not in use for applications will be used by the OS for caching to speed stuff up.  This doesn't interfere with applications, because the system will allocate them ram with top priority, so they will take the ram needed and caching will stop if theres no space.

2) Yes, linux won't degrade (at least in an appreciable way like windows).  This is over the long run of an install, but also during a single uptime (my computer can stay on for months with no issues... which is much nicer for your hardware).

3) Updates should come up on their own as a taskbar icon.  You can run the commands "sudo apt-get update" and "sudo apt-get upgrade" from the terminal to do it yourself.

4) In linux (typically) when a non-critical app crashes, the rest of the system is unaffected.  No "oh crap, konqueror crashed... gotta reboot".  Force quit the app and keep going like nothing happened.

5) A "session" is on user's login.  You can add programs to start by going to System->preferences->Sessions, then the autostarted applications tab, and entering the command to start the application on the list.

Others:
1) before you try to force photoshop onto linux, please try the equally capable (and free) linux alternatives.  There is the GIMP and Inkscape, which are great apps.  I love Inkscape for vector graphics (illustrator), but don't care for gimp as much (though many love it).  I use Krita, it does true CMYK unlike GIMP.  Also if you don't like Inkscape, try Karbon.

---

### Post by sailor2001 on 2007-04-23
#6 sessions......you have gnome and kde sessions...........Go to synaptics, check repositories to see if all are ready for you, and download kde if you are in gnome.....many packages there.....now you can ctrl/alt backspace and switch between sessions....... maybe you would like one better than the other so you can make that default

---

### Post by Arjunus on 2007-04-23
Hi, 

about sessions. I got it to open firefox on start up but I cant seem to get it to open anything else. I found the command line for fifrefox in the /bin folder. is this the folder I should be looking in to find program files that can be opened in a session?

---

### Post by igknighted on 2007-04-23
Hmm, usually its the title in all lower case... the commands should all be listed in /usr/bin, so try looking there.  Also, if a command is in /usr/bin, for example firefox is /usr/bin/firefox,  you don't need to name the whole path, just the command (ie, firefox).  If you are running, say, swiftfox from /opt, you need to include the whole path (ie, /opt/swiftfox/swiftfox).

---

### Post by Talon2 on 2007-04-23
> **arphaus said:**
> 
[*]Setting up Thunderbird so I can use it in both Ubuntu & XP until I decide whether I'm going to use Ubuntu fulltime.
[/LIST]

You could just set up Gmail then it would not matter if you are using Ubuntu, Windows, OSX or OS/2.

mail.google.com

---

### Post by arphaus on 2007-04-23
I love the community around open source apps - thanks to everyone who's chimed in so far.

I did read a comment in another forum describing someone's Ubunut laptop as being overkill spec-wise, as well as someone in the forums here saying their next laptop was going have some simpler specs.  That makes linux sound pretty good from the performance standpoint.  And I look forward to not having performance bog down over time.  Even so, when reinstall time comes along I'm guessing it's more painless than the MS way?

I had my first automatic update notification earlier - much better than seeing a notice telling more windows updates are waiting to slower my puter :) 

The session thing sounds really cool - would be great to have a 'surfing & chatting' session vs a 'serious web dev' session.

@sailor2001: is the concept of a desktop environment similar to shell replacement in windows?  Or is it more than surface changes?  I dig gnome so far, but I haven't looked at KDE to see what's different.  Is one more resourcee-intensive than the other without any extraneous apps/features running?

@igknighted: I need to be able to exchange .psd & .ai files with others.  How good is the interoperability of such files between linux apps & adobe products?  I'm not averse to checking out what's available, of course, but my guess is that I will either
[LIST=1]
[*]Always keep a stripped down install of XP for Adobe apps & some specific audio production tools
[*]Look seriously into Parallels or VMWare after I get a new puter
[*]Eventually get lucky with WINE (not holding my breath)
[/LIST]

Thanks again to all!

---

### Post by arphaus on 2007-04-23
Actually, I do use Gmail and pop it to Tbird.  I prefer using T-bird for having more control over signatures and the like.  And to avoid the 'sent on behalf of' crap that broadcasts my Gmail addy.  The Google Calendar integration with Tbird 2 is the bomb as well.

> **Talon2 said:**
> You could just set up Gmail then it would not matter if you are using Ubuntu, Windows, OSX or OS/2.

mail.google.com

---

### Post by igknighted on 2007-04-23
> **arphaus said:**
> I love the community around open source apps - thanks to everyone who's chimed in so far.

I did read a comment in another forum describing someone's Ubunut laptop as being overkill spec-wise, as well as someone in the forums here saying their next laptop was going have some simpler specs.  That makes linux sound pretty good from the performance standpoint.  And I look forward to not having performance bog down over time.  Even so, when reinstall time comes along I'm guessing it's more painless than the MS way?

I had my first automatic update notification earlier - much better than seeing a notice telling more windows updates are waiting to slower my puter :) 

The session thing sounds really cool - would be great to have a 'surfing & chatting' session vs a 'serious web dev' session.

@sailor2001: is the concept of a desktop environment similar to shell replacement in windows?  Or is it more than surface changes?  I dig gnome so far, but I haven't looked at KDE to see what's different.  Is one more resourcee-intensive than the other without any extraneous apps/features running?

@igknighted: I need to be able to exchange .psd & .ai files with others.  How good is the interoperability of such files between linux apps & adobe products?  I'm not averse to checking out what's available, of course, but my guess is that I will either
[LIST=1]
[*]Always keep a stripped down install of XP for Adobe apps & some specific audio production tools
[*]Look seriously into Parallels or VMWare after I get a new puter
[*]Eventually get lucky with WINE (not holding my breath)
[/LIST]

Thanks again to all!

I can't comment on the file types... perhaps if you have both you could test it?  I see that inkscape and Karbon will save as illustrator files but see no .psd in Krita (i don't use GIMP)

As for what a DE is, it is more than a shell.  There are graphical libraries that drive different default apps.  The goal of each DE is to create a full working environment (apps, looks, etc.), but they do things a little differently.  KDE and Gnome are the major ones, it is definitely worth taking a look at both to see which you like.  Apps from one DE will work in the other, however they won't be rendered visually as well as they would in their native DE usually.  Also, there is a slight performance tax for loading a bunch of extra libraries (usually negligent unless you are on a rather old computer).

---

### Post by arphaus on 2007-04-23
I will check out the DEs.  My machine's not that old (just added info to sig), so I'm curious about what's available.  The concept itself is really interesting - I'm always looking for better ways of doing things.  Or sometimes just different cuz I get bored :-P

---

### Post by igknighted on 2007-04-23
> **arphaus said:**
> I will check out the DEs.  My machine's not that old (just added info to sig), so I'm curious about what's available.  The concept itself is really interesting - I'm always looking for better ways of doing things.  Or sometimes just different cuz I get bored :-P

If you have a good internet connection, "sudo aptitude install kubuntu-desktop" will install the KDE setup for you.

---

### Post by arphaus on 2007-04-23
thanks - i'll do that when i get a chance.

---

