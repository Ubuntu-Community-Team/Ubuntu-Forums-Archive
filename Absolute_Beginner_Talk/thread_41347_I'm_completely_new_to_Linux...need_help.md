---
title: "I'm completely new to Linux...need help"
date: 2005-06-13
forum: Absolute Beginner Talk
---

### Post by darkbane on 2005-06-13
Help me please...somebody.

As my subject states, I am completely new to Linux.  First things first, I'm trying to get my wifi card to work.  I have the D-Link dwl-g630.  I know it has some issues and I've been reading the instructions that other people have posted as to how to get it to work, but I'm just not figuring it out for some reason.  

Is there anybody out there that would be able to give me some very detailed step-by-step instructions as to what to do to get this card to work.  I would be very very gratefull.  I'm not new to computers by any manys, so it's not like you'd be trying to explain it to some 80 yr old lady.  I know my stuff, but I'm new to Linux and I'm trying to catch on.

thanx for your time,

DB

---

### Post by darkbane on 2005-06-13
Anybody?    Please.!!

---

### Post by poofyhairguy on 2005-06-13
Hello. I'm not the best at explaining things, so I'll leave the best guide we have as a link and ask you waht you don't understand:

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper)

Start at the part called:

"Installing the Windows Drivers"

---

### Post by darkbane on 2005-06-15
OK.  So I followed that tutorial, which were the same steps that I had taken before.  When I do the "modprobe ndiswrapper"  I get a return saying "operation not permitted.  When I do "-L" to list.  I get a return saying "net5211 invalid driver"

I'm using the D-Link Dwl-g630 rev: C2  I'm using the driver that came off of the CD.  The driver is "net5211.inf".  

Should I be using another version of this driver, maybe the win2k or win98 driver?  

Does anybody have any other suggestions.  


Thanks for the link "Poofyhairguy"

---

### Post by ltmon on 2005-06-15
[QUOTE=darkbane]OK.  So I followed that tutorial, which were the same steps that I had taken before.  When I do the "modprobe ndiswrapper"  I get a return saying "operation not permitted.  When I do "-L" to list.  I get a return saying "net5211 invalid driver"[/QUOTE]

Hi,

I don't use wifi at all but from the looks of it the tutorial may have a mistake.

instead of 

> modprobe ndiswrapper

try

> sudo modprobe ndiswrapper

and enter your password when prompted.

---

### Post by darkbane on 2005-06-15
I tried that as well, but return the same results.  

One thing I did notice though when reading the tutorial stated earlier.  It says this:
*"simply install the ndiswrapper-modules and ndiswrapper-utils packages from the Synaptic Package Manager"*  

When I search for ndiswrapper in the Package Manager I only find "ndiswrapper-utils"  I don't see any other package referring to ndiswrapper-modules.  Could this be my problem?  If so, how do I get this ndiswrapper-modules package"

---

### Post by ltmon on 2005-06-15
Try adding the extra repositories (sorry, as I said I don't use wifi so I'm not sure about any of this).

[howto add new repositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by poofyhairguy on 2005-06-15
[QUOTE=darkbane]OK.  So I followed that tutorial, which were the same steps that I had taken before.  When I do the "modprobe ndiswrapper"  I get a return saying "operation not permitted.  When I do "-L" to list.  I get a return saying "net5211 invalid driver"
[/QUOTE]

That means you have the wrong *.inf file. Can you find the Windows 200 drivers by any chance?

---

### Post by darkbane on 2005-06-15
I've tried the win98, win2k, and winXP drivers and still have had no luck

---

### Post by darkbane on 2005-06-15
I'm still trying my butt off to get this to work.  If I'm not providing enough information, please let me know.  I've tried all of the Revision C drivers for my card and I've even tried the Revision B drivers as well.  Still nothing.  

Everything seems to be going ok up untill I do the "modprobe ndiswrapper".  I get an error return saying:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation no permitted"

Can anyone tell me what this error is and what I can do about it?

I read online somewhere that other people tried using the "TNET1130.inf" driver instead of the "Net5211.inf" driver.  What are most people using with this card.

I'm about ready to give up on Ubuntu if I can't get this to work.  I don't want to do that, because I already like the feel of it, but if I can't get internet access on it, then all of this is pointless.

Please somebody help me.

---

### Post by Kyral on 2005-06-15
[QUOTE=darkbane]I'm still trying my butt off to get this to work.  If I'm not providing enough information, please let me know.  I've tried all of the Revision C drivers for my card and I've even tried the Revision B drivers as well.  Still nothing.  

Everything seems to be going ok up untill I do the "modprobe ndiswrapper".  I get an error return saying:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation no permitted"

Can anyone tell me what this error is and what I can do about it?

I read online somewhere that other people tried using the "TNET1130.inf" driver instead of the "Net5211.inf" driver.  What are most people using with this card.

I'm about ready to give up on Ubuntu if I can't get this to work.  I don't want to do that, because I already like the feel of it, but if I can't get internet access on it, then all of this is pointless.

Please somebody help me.[/QUOTE]
 Operation Not Permitted usually means you don't have permissions for that command. when working with Modules (modprobe) always sudo it :D

---

### Post by darkbane on 2005-06-15
Whether I "sudo" or not, I'm still getting the same error:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation no permitted"

Also when I list (-L) the drivers, I get:

Installed ndis drivers:
net5211 invalid driver!
tnet1130        invalid driver!


I'm starting to think that maybe there is something wrong with my card, but the light blinks on it and in the device manager it recognizes that there is a D-Link device there.

---

### Post by wowbuntu on 2005-06-16
[QUOTE=darkbane]Whether I "sudo" or not, I'm still getting the same error:

"FATAL: Error inserting ndiswrapper (/lib/modules/2.6.10-5-386/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Operation no permitted"

Also when I list (-L) the drivers, I get:

Installed ndis drivers:
net5211 invalid driver!
tnet1130        invalid driver!


I'm starting to think that maybe there is something wrong with my card, but the light blinks on it and in the device manager it recognizes that there is a D-Link device there.[/QUOTE]
 Hey try SimplyMEPIS or PCLinuxOS.....these EXCELLENT newbie-oriented distros and I hope u'll be able to get ur wifi working with them.

Or try Xandros...which is considered THE BEST for total newbies and has THE BEST driver support....but since its a commercial distro theres a disadvantage to it....the FREE version of this distro has this limitation that u can't burn CDs at speeds greater than 4x..
But Xandros will give u THE BEST out-of-the-box experience. 

but still try it out...u can do ur cd-burning in windows right!

hope this helps.

Newbie

---

### Post by Gerjan on 2005-06-16
I had some problems with my Dlink DWL-G650+ but now it is working and with WPA encryption. Have you tried the latest Ndiswrapper version? I have used de 1.2rc version and I used the XP drivers from the CD. Did you copy all the files in de driver directory to your computer or only the inf file? For me it worked when I moved all the files in the XP driver dir.
You can also search for the harware comp. list and look for your card, it has a link to working drivers for you card.

---

### Post by jsuen on 2005-06-16
you can try searching for ndiswrapper-modules via apt-cache... something like
bash$ apt-cache search ndiswrapper 
should show you results? (sorry, i've only learnt the merits of apt recently :P )

---

### Post by desdinova on 2005-06-16
[QUOTE=wowbuntu]Hey try SimplyMEPIS or PCLinuxOS.....these EXCELLENT newbie-oriented distros and I hope u'll be able to get ur wifi working with them.

Or try Xandros...which is considered THE BEST for total newbies and has THE BEST driver support....but since its a commercial distro theres a disadvantage to it....the FREE version of this distro has this limitation that u can't burn CDs at speeds greater than 4x..
But Xandros will give u THE BEST out-of-the-box experience. 

but still try it out...u can do ur cd-burning in windows right!

hope this helps.

Newbie[/QUOTE]

And this helps with Ubuntu how, exactly? If you want to discourage the accusation of trolling, it helps to be consistent in which alternative distro you proleytize. Fedora, Xandros, Mepis, Ark...

---

### Post by darkbane on 2005-06-16
Ubuntu's hardware list doesn't give any listings for my specific card.  I have tried copying the whole xp drivers directory, but that doesn't help either.  

Is the fact that I don't have the "ndiswrapper-module" my problem, do you think.  It would be nice to get all of the software and support I need onto cd instead of having to download from the internet the packages I need and/or want.  Oh well I can't complain.  I really like Ubuntu so far, except for this major detail I'm having issues with.  I'm not ready to switch to a different Distro yet.  Maybe if I stop getting replies and help from the wonderfull people hear, then maybe I'll consider switching.  I know the answer to my problem is out there, so I'm not going to jump ship that easily.  

Thanks for the suggestions though.  

I'm going to search and see what I can do about finding the "ndiswrapper module" and I'm gonna try the newest version of ndiswrapper.

Thanks for the help... Keep the suggestions coming if you can think of anything else that might help.  Much appreciated.


DB

---

### Post by firecat53 on 2005-08-06
If you're still looking for help with the dwl-g630(C2) under Hoary, I've got it working (WEP too) with the madwifi drivers. I had to grab the most recent version and build from the source. There's a couple of how-to's that cover that. Just haven't got WPA to work yet.....

---

### Post by aris on 2005-09-15
darkbane, I am having the EXACT same problems as you and I am trying to install the exact same card and I get the exact same responses.

Actually, I have the exact same feelings, that Ubuntu seems great but I am bloody annoyed that this wifi card doesn't work with it.

It's so frustrating!

Have you found out anything new?

---

### Post by Nequeo on 2005-09-15
One thing I do know is that if you're getting an 'Error: Operation Not Permitted' sort of error when you try to 'sudo modprobe ndiswrapper', it usually means you've buggered up the NDIS-wrapper install. This is easy to do when trying to follow several different guides written by several different people.

I cannot help in the case of that particular card - but as a general tip for NDIS wrapper, you need Windows XP drivers, and XP drivers ONLY. 

If the drivers on your CD don't work, try downloading the latest version from the website. 

And there is, somewhere out there on Google, a list of what driver to use for which card. I can't for the life of my seem to find it... But it is out there, hiding... hiding...

And if you do end up giving up and going back to Windows, make sure you send D-link a nasty letter saying that the next wireless card you buy *won't* be D-link, because they refuse to support your OS of choice - Linux. :) Otherwise, nothing will ever improve. The problem is not that people *haven't* written drivers for Linux. The problem is that they *can't*, because companies like Broadcom refuse to release the information we'd need to create them. But if enough people complain... *shrug* who knows? Something might happen...

---

### Post by npaladin2000 on 2005-09-15
[QUOTE=darkbane]Ubuntu's hardware list doesn't give any listings for my specific card.  I have tried copying the whole xp drivers directory, but that doesn't help either.  

Is the fact that I don't have the "ndiswrapper-module" my problem, do you think.  It would be nice to get all of the software and support I need onto cd instead of having to download from the internet the packages I need and/or want.  Oh well I can't complain.  I really like Ubuntu so far, except for this major detail I'm having issues with.  I'm not ready to switch to a different Distro yet.  Maybe if I stop getting replies and help from the wonderfull people hear, then maybe I'll consider switching.  I know the answer to my problem is out there, so I'm not going to jump ship that easily.  

Thanks for the suggestions though.  

I'm going to search and see what I can do about finding the "ndiswrapper module" and I'm gonna try the newest version of ndiswrapper.

Thanks for the help... Keep the suggestions coming if you can think of anything else that might help.  Much appreciated.


DB[/QUOTE]


Your problem is that you have invalid drivers installed into ndiswrapper, like the thing says.  Remove them

Net5211...ins't that an Aethros driver??

---

