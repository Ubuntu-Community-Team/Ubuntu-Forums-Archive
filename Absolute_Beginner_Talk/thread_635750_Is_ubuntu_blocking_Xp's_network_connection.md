---
title: "Is ubuntu blocking Xp's network connection????"
date: 2007-12-09
forum: Absolute Beginner Talk
---

### Post by ThewhiteLynx on 2007-12-09
Well I got to say, I am utterly lost, I now have created a dual boot system, with windows XP professional, and Unbuntu 7.10, however I have nothing in my network connections area in windows XP but I can still access the internet in Ubuntu, I just now created both, and I have never had this problem before when it was just XP alone, so now I ask is Ubuntu somehow blocking XP???

---

### Post by kvorion on 2007-12-09
Are you sure that your ethernet drivers in XP are properly installed?

---

### Post by discoade on 2007-12-09
If you boot in to xp, ubuntu wont be running so how can it be blocking it?

boot into xp and

[COLOR=red][COLOR=Black] Click Start, Run and then type:

cmd

and click OK. 

At the command line, type:

ipconfig/all

and hit Enter.

Write down the DNS server IP addresses listed to the right of DNS.

Now click Start, Settings, Control Panel, Network Connections.

Right-click the icon for your connection and choose Properties, now click the Networking tab.

Click on Internet Protocol (TCP/IP) and then Properties.

On the General tab, click "Use the following DNS server addresses" and then type in the DNS server IP addresses. 

Click OK to get out of all of the windows and then reboot.[/COLOR] 

[COLOR=Black]try that!  it worked for me when i had a similar problem![/COLOR]
          
[/COLOR]

---

### Post by rkd on 2007-12-09
Hmmm. I'm surprised at discoade's suggestion.  As far as I know, ipconfig /all only reports the networking information that Windows has already set up, so if your network connection isn't working, copying what ipconfig /all reports shouldn't improve the situation.  Still, it seems to have worked for him, so it probably can't hurt to try it, although if your computer is supposed to get its settings via DHCP from your modem or router, they can change from time to time, so hard-wiring them into your windows configuration isn't such a good idea.

If his suggestion doesn't work, don't despair.  There are other things to try.

You didn't mention whether you added Ubuntu to a computer that had an already-working install of XP or it was a new install of XP on the computer.  If you had an already-working install of XP on the computer before installing Ubuntu, I would expect the networking in XP to continue to work after adding Ubuntu.  So I'll assume that you did a fresh install of XP onto the computer.

During the XP install, I believe it asks you about setting up the network and if you say you want to, it asks you some questions about how you connect to the internet.  Did you get that question?  Do you remember how you answered it?

If you don't remember, maybe that isn't important.  If you open the Network Connections control panel, there is a Network Setup Wizard.  Run that and it should lead you through the steps of getting your networking set up in XP.  I can't tell you exactly how to answer the questions because they depend on exactly how you are connected and there are too many combinations to try to lay them all out in this post. If you aren't sure how to answer a question, come back here, explain how your computer is connected to the internet and tell us the question you don't know how to answer and someone should be able to help you.  Or ask any of your friends who knows how to set up Windows to help you -- having Ubuntu on the computer as dual boot doesn't change anything about setting up Windows networking.

Just as a guess, your computer is probably directly connected to a cable modem or DSL modem, or to a router that is connected to the cable modem or DSL modem.  If that is the case, then you probably want to tell the wizard that you connect directly to the internet, not through another computer.  You probably want your computer to get its network settings from the router or modem via DHCP.  I don't remember how that question is worded.  I hope that when you see it, you'll be able to recognize what it is asking about and pick the correct answer.  And you probably don't want to use ICS (Internet Connection Sharing).  I hope those are all the hard questions to answer.  It has been a little while since I've done a Windows install, so it isn't fresh in my mind.  My guesses might not match your situation, so don't follow them if you know your setup is different.  Remember, if you have a friend who knows how to set up Windows, he should be able to help you past this problem, since Ubuntu doesn't enter into it at all.

Good luck.  This should be a simple problem to get past.  The fact that Ubuntu can use the network means that everything in the PC and your network is working fine, so you just have to give the right answers to Windows' network setup questions and all should be well.

---

### Post by discoade on 2007-12-09
rkd

you have a point there reading back it looks like its a new install mine was working then just stopped after a system crash.  the information i posted was passed to me by tech support it worked in my case and i haven't had any problems since.

---

### Post by ThewhiteLynx on 2007-12-09
> **rkd said:**
> Hmmm. I'm surprised at discoade's suggestion.  As far as I know, ipconfig /all only reports the networking information that Windows has already set up, so if your network connection isn't working, copying what ipconfig /all reports shouldn't improve the situation.  Still, it seems to have worked for him, so it probably can't hurt to try it, although if your computer is supposed to get its settings via DHCP from your modem or router, they can change from time to time, so hard-wiring them into your windows configuration isn't such a good idea.

If his suggestion doesn't work, don't despair.  There are other things to try.

You didn't mention whether you added Ubuntu to a computer that had an already-working install of XP or it was a new install of XP on the computer.  If you had an already-working install of XP on the computer before installing Ubuntu, I would expect the networking in XP to continue to work after adding Ubuntu.  So I'll assume that you did a fresh install of XP onto the computer.

During the XP install, I believe it asks you about setting up the network and if you say you want to, it asks you some questions about how you connect to the internet.  Did you get that question?  Do you remember how you answered it?

If you don't remember, maybe that isn't important.  If you open the Network Connections control panel, there is a Network Setup Wizard.  Run that and it should lead you through the steps of getting your networking set up in XP.  I can't tell you exactly how to answer the questions because they depend on exactly how you are connected and there are too many combinations to try to lay them all out in this post. If you aren't sure how to answer a question, come back here, explain how your computer is connected to the internet and tell us the question you don't know how to answer and someone should be able to help you.  Or ask any of your friends who knows how to set up Windows to help you -- having Ubuntu on the computer as dual boot doesn't change anything about setting up Windows networking.

Just as a guess, your computer is probably directly connected to a cable modem or DSL modem, or to a router that is connected to the cable modem or DSL modem.  If that is the case, then you probably want to tell the wizard that you connect directly to the internet, not through another computer.  You probably want your computer to get its network settings from the router or modem via DHCP.  I don't remember how that question is worded.  I hope that when you see it, you'll be able to recognize what it is asking about and pick the correct answer.  And you probably don't want to use ICS (Internet Connection Sharing).  I hope those are all the hard questions to answer.  It has been a little while since I've done a Windows install, so it isn't fresh in my mind.  My guesses might not match your situation, so don't follow them if you know your setup is different.  Remember, if you have a friend who knows how to set up Windows, he should be able to help you past this problem, since Ubuntu doesn't enter into it at all.

Good luck.  This should be a simple problem to get past.  The fact that Ubuntu can use the network means that everything in the PC and your network is working fine, so you just have to give the right answers to Windows' network setup questions and all should be well.
I am directly connected to a cable mode, or so I believe.  I use to have XP on this PC it worked fine, then I deleted it to install unbunt which worked fine, then I deleted ubuntu to spilt the hard drive for both XP and unbuntu, XP first, then unbuntu.  I already did try though to go ahead and set up a network connection, but XP is not detecting any network devices, as I belive it thought so during the installation as well, therefore I suppose it shouldn't have anything to do with unbuntu:)  though now Im lost, the PC is detecting nothing in my network, How do I get it to see it????

---

### Post by ThewhiteLynx on 2007-12-09
> **discoade said:**
> rkd

you have a point there reading back it looks like its a new install mine was working then just stopped after a system crash.  the information i posted was passed to me by tech support it worked in my case and i haven't had any problems since.

I think I got somthing simalar to work a year or two ago when I had a simalar problem, but alas this time it didn't, alas far as my computer is concerned it thinks it is the lone computer in the universe

---

### Post by kvorion on 2007-12-09
> **ThewhiteLynx said:**
> I am directly connected to a cable mode, or so I believe.  I use to have XP on this PC it worked fine, then I deleted it to install unbunt which worked fine, then I deleted ubuntu to spilt the hard drive for both XP and unbuntu, XP first, then unbuntu.  I already did try though to go ahead and set up a network connection, but XP is not detecting any network devices, as I belive it thought so during the installation as well, therefore I suppose it shouldn't have anything to do with unbuntu:)  though now Im lost, the PC is detecting nothing in my network, How do I get it to see it????

I ask again....have you installed your motherboard drivers on windows XP? Looks like your WinXp is a fresh installation. WinXP certainly will not detect your network card if you dont install the drivers; and this certainly has nothing to do with Ubuntu.

---

### Post by spamzilla on 2007-12-09
I bet that your ethernet drivers aren't installed. Go to:

right click my computer > properties > hardware > device manager

under network adapters is your ethernet card listed? If not, install the drivers and it should work.

---

### Post by tall8 on 2007-12-09
I have 7.10 dual booted with Windows XP and have never had a problem connecting in either, one after another too. When in Windows why not turn off the power to your modem first, and then to your router (if you're using one) and let them reset themselves. This usually solves the problem.

---

### Post by bsell on 2007-12-09
If you have an Internet connection in Ubuntu, but not in XP then it is a driver issue. Ubuntu is using the NIC through the card's MAC (physical) address because it has a driver for the card. They are usually Plug and Play.

---

### Post by Myglaren on 2007-12-09
Xp should detect and use the network card by default, as Ubuntu does.  Never yet had an XP install that failed to do that, never had to resort to installing drivers although windows update has sometimes installed updated drivers specific to that network card.
I suspect that the network drivers have been corrupted somewhere along the way.  Ubuntu would not do this under normal circumstances.  The only way I can imagine this happening is if you failed to clean up and run defrag before partitioning for and installing Ubuntu where Windows system files may have been moved and lost or become corrupt somehow.

---

### Post by thelatinist on 2007-12-09
> **Myglaren said:**
> Xp should detect and use the network card by default, as Ubuntu does.  Never yet had an XP install that failed to do that, never had to resort to installing drivers although windows update has sometimes installed updated drivers specific to that network card.

There are some older network cards which XP will *not* detect automatically.  I have an older 3Com card which Ubuntu detects and uses perfectly but for which I have to download Windows 2000 drivers from the 3Com site to get it working in XP.

I second the suggestion of checking the hardware manager.  If the network card is not listed (or, more likely, is listed but marked as not working), then it's clearly a driver issue.  And it almost certainly has nothing to do with Ubuntu.

---

### Post by Myglaren on 2007-12-09
> There are some older network cards which XP will not detect automatically. I have an older 3Com card which Ubuntu detects and uses perfectly but for which I have to download Windows 2000 drivers from the 3Com site to get it working in XP.

I stand corrected.  Apologies for being misleading.  I will repeat though that is has never happened in my experience and some of the cards have been pretty ancient, even second hand ones discovered in boxes of oddments.
I made the probably eroneous presumption that there were a set of 'global' default drivers that would wotk with anything that then got updated to a more specific version once online.

After all the talk of hardware problems with Linux I have always been very pleasantly surprised at how well it detects and installs everything I have thrown at it (with only one exception)*

On my first install of Ubuntu and expecting it to be like Windows but worse, I was knocked sideways when after only a few lines od the installation process it went straight online and compared the packages on the CD with the ones in the repositories and said stuff like "Skipping this package - installing more recent one from Ubuntu repository"  It all went like silk and was unbelievably quick.  I was seriously impressed before even ever using it and have been more and more impressed the more I use it.

* A fairly ancient USB scanner, worked with Dapper but not any more, won't work with Vista either - surprise, surprise!

---

### Post by rkd on 2007-12-09
If you don't know how to get Windows to reinstall the drivers, it is pretty easy. 

Get into the Device Manager, as spamzilla mentioned: 

  right click my computer > properties > hardware > device manager

Look through the list in the right side of the display until you see Network Adapters.  Click on the + to the left of Network Adapters.  That should open to show the name of your network adapter (or adapters if you have more than one).  Right click on the name of your ethernet adapter and choose Uninstall from the menu that pops up.  Click Ok when it asks whether you really want to uninstall it.  Reboot.  Windows should find and reinstall the network drivers during the reboot.  I'm not sure whether it will automatically do the network setup at that point.  If your network access from Windows doesn't start working at that point, go to the Network Connections control panel and run the setup wizard.  Write down each question and your answer, in case things still don't work, so you can tell us each step.

When you open the Device Manager, if you find that Network Adapters is already open with a yellow or red warning symbol by the network card name, that indicates that Windows has found some problem with the network adapter.  After uninstalling it and rebooting, check in the Device Manager again to be sure the yellow or red warning is gone.  If it is not gone, then perhaps the driver file has been corrupted and you'll have to get windows to replace it from the Windows CD (or download the appropriate driver for the card from the internet, which you can do from another Windows computer or from the Ubuntu side  of this one, and move over to the Windows side via a floppy or thumb drive or something).

If that doesn't get your Windows networking up, you might have to get a friend who knows Windows to help you figure out what is wrong with your Windows installation.  You could try describing what you found out here, and one of us might be able to figure it out, but a local person probably could solve the problem quicker.

---

### Post by ThewhiteLynx on 2007-12-09
> **spamzilla said:**
> I bet that your ethernet drivers aren't installed. Go to:

right click my computer > properties > hardware > device manager

under network adapters is your ethernet card listed? If not, install the drivers and it should work.

Ok, well after extensive looking around I have decided that indeed I do need to install new drivers for XP however, how the heck do I???? I got into task manager and try'd to reinstall my ethernet controller, but it would appear that I need a disk which I know I dont, or a internet connection to get proper drivers, which again, kinda hard when thats what im tyring to get working in the first place.  how in the owrld am I to go about getting the proper drivers????

---

### Post by rkd on 2007-12-09
I think my previous post (the one just before yours) answers some of your questions.

I assume you meant Device Manager rather than Task Manager.  Did you try my suggestion to right click on the ethernet adapter in the Device Manager, select Uninstall, then reboot?  Did that not work?

Perhaps it would be helpful to explain exactly what you found that told you that you need new drivers.  More details might or might not help us tell you exactly what to do.  (And that is why I said that a local friend who knows how to configure Windows might be your best bet, but we will try to help online.)

If you need the drivers off of the Windows installation CD, you'll be able to put it into the CD drive when Windows asks for the driver disk.  If you know you need drivers that are not on the Windows installation CD (and know where to find them on the internet), you can download them when booted into Ubuntu, then copy the driver files to a floppy or thumb drive (flash drive), then boot Windows and install them from the floppy or thumb drive.

We can probably tell you more if you give us more details about what you see.

---

### Post by rkd on 2007-12-09
Sorry, I'm going to be away for 6 or 7 hours.  I hope others will be able to help you get the driver straightened out.

---

### Post by discoade on 2007-12-09
i may have missed something here!

is your eithernet card onboard ie; your modem/router plugs in in the back panel near your usb ports mouse etc or is it a pci card ie you modem plugs in lower down in the horizontal slots at the back of your tower?

If you need to download drivers, download them in ubuntu save them to your desktop and stick em on a flash drive of burn them to a cd and when you boot back to xp you will have them ready for when xp asks for them!

rkd beat me to it on that last bit!  

Floppy drive rkd? have you still got one? takes up valuable hdd installation space! :)

---

