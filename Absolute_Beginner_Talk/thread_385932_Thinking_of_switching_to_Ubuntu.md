---
title: "Thinking of switching to Ubuntu"
date: 2007-03-16
forum: Absolute Beginner Talk
---

### Post by tbuss on 2007-03-16
I'm thinking about installing ubuntu on my computer but I'm unsure how everything will work. 

Dell Dimension 8200
Intel Pentium 4 1.79 GHz
512 RAM
2 HDD and 1 External 
--Maxtor 6Y120P0 [Hard drive] (122.94 GB) // Internal
--Maxtor OneTouch II Disk (300.08 GB) // External firewire connection
--ST340016A [Hard drive] (40.02 GB ) // Internal
ALL-IN-WONDER 9600 SERIES 
Creative SB Audigy 2 Platinum eX
Realtek RTL8139 Family PCI Fast Ethernet NIC
Canon i950 printer
 
I also 1 USB 2.0 PCI card installed and 1 Firewire PCI card installed. My keyboard and mouse are both Logitech wireless devices.

What I was wondering was will my sound card and video card work. I have read that ATI can be difficult to configure in Linux. I'm not sure about my sound card, from what I have read it will work but what about the software that loads with the card: EAX console, Surround Mixer, Speaker Settings etc. I'm concerend that my wireless keyboard and mouse will not be compatible as well. Also will my external HDD work with a firewire port, I now this basic but I don't know. I'm not looking for someone to answer all these questions for me (that would be nice however) but if you could simply direct me to some reliable sources that will give some useful info about these questions, that would be great.

---

### Post by Zzl1xndd on 2007-03-16
from what iv seen the only thing that might be an issue is the Video card ATI support is crap at best. Other then that I have seen people with very simalar set ups to yours get up and running in no time. But it would be worth downloading and running the live CD it'll give you a good idea oh what will work out of the box.

---

### Post by IcemanV9 on 2007-03-16
Try LiveCD on your Dell laptop. :D

There is a [[COLOR="Orange"]**wiki**[/COLOR]]("https://wiki.ubuntu.com/HardwareSupportMachinesLaptopsDell") on Dell laptops. Also, there are some threads on Dell laptops in Ubuntuforums.org.

---

### Post by Hendrixski on 2007-03-16
> **tweakedenigma said:**
> from what iv seen the only thing that might be an issue is the Video card ATI support is crap at best. Other then that I have seen people with very simalar set ups to yours get up and running in no time. But it would be worth downloading and running the live CD it'll give you a good idea oh what will work out of the box.

well hold on now.  There are binary drivers available from ATI for most of their cards.  The open source drivers for it work perfectly well as long as you're not trying to do anything like Beryl or Google Earth, etc.  The ATI drivers can be a pain to install, especially since there are 100 manuals out there, each one missing a piece.  I've never tried the all-in-wonder cards though, I've heard bad things.  But again, if you're not planning on dorking out with graphics intensive stuff like Beryl, you won't ever need to go through that.

If the liveCD runs on it then you will have no problem.  Check out how easy it is to install the printer!! in your browser type  localhost:631 and it detects all browsers on the network and has a one button install for any one of them.   Sound is almost never an issue, and ethernet works 99.9% of the time.... if not, just come back to the forums and someone will help you troubleshoot it.

---

### Post by darrenm on 2007-03-16
You will be fine with everything but the printer. There's no support from Canon for Linux.

---

### Post by Zzl1xndd on 2007-03-16
> **Hendrixski said:**
> well hold on now.  There are binary drivers available from ATI for most of their cards.  The open source drivers for it work perfectly well as long as you're not trying to do anything like Beryl or Google Earth, etc. 

Ok I will go rephrase, ATI will not give you the same options or Easy of use you would get out of a Nvidia Card So if you want to use a 3d desktop or things like that the ATI card maybe an issue.

---

### Post by Hendrixski on 2007-03-16
When you run the liveCD, you can open a terminal, and type "lspci" and it will list your hardware.  :)

Ubuntu is really an operating system for human beings.  I always carry a liveCD with me to give it to new people.  Because I love it so much.  It's like a good book that you want to share with all of your friends.  How often do you find a product like that?

If you have kids, try edubuntu, it's Linux for Little Human Beings.  And has tons of educational software.  Kids love it.

If you don't want to bother with installing drivers, try Sabayon or Mandriva.  They're different, oftentimes can be harder to use, but they're still great!  You can also buy an edition of Linux, like Linspire, which comes with all of the codecs and DVD software already installed (Ubuntu can't offer a lot of that for legal reasons). or Suse Enterprise.  :) 

Enjoy :)

---

### Post by jhenager on 2007-03-16
Yeah - Live CD.

I have used Red Hat and SuSE for years. Ubuntu is awesome.
If I ever run into Hendrixski in New York, I will report back on whether or not he actually had a CD with him. Just kidding. Good for you man.

---

### Post by tbuss on 2007-03-16
To everyone who has replied, thank you very much. I'm downloading a LiveCD right now and will post back with results.

---

### Post by silkstone on 2007-03-16
Look at TurboPrint - it's not free (although there's a trial) but it supports most printers including the i9xxx.

---

### Post by Zzl1xndd on 2007-03-16
> **jhenager said:**
> Yeah - Live CD.

I have used Red Hat and SuSE for years. Ubuntu is awesome.
If I ever run into Hendrixski in New York, I will report back on whether or not he actually had a CD with him. Just kidding. Good for you man.

LOL I can't speak for Hendrixski but I do carry some on me most of the time if you know anyone In the Fredericton Are that wants one :).

---

### Post by Moeru on 2007-03-16
I'm running a Dell Dimension and everything just detected fine. Long as you aren't aiming to play heavy duty games (i.e. World of Warcraft and such), it should work directly out of the box

---

### Post by tbuss on 2007-03-16
Okay, ran LiveCD and everything seemed to work. Video/Audio did not work for some media (I understand that this is an encryption/codec issue) My external HDD was available and my wireless keyboard and mouse worked fine. Audio seemed to only work through center channel (5.1 setup) Is there an application I can use in Linux that is similar to the EAX console for my SB card; to adjust audio settings, equalizer and adjust output settings (5.1 4.1...) With my windows machine there is an application called Catalyst for my ATI card. Is there something similar in Linux that will allow me to adjust my video settings? My sound card also has an external module for input/output devices. It came with its own software for configuration. I know I'm asking a lot of questions. I am currently researching these issues but it seems there is definitely more than one way to skin a cat. I did not attempt to connect to printer.

I was going to post my lspci result but apparently the text file I saved didn't save to my external drive. However, I did see my video, LAN, audio, and all other connected devices listed correctly.

If everything will run the way it did in Live Mode, and I can resolve some of my audio and video questions, looks like I will be making the switch.

---

### Post by jhenager on 2007-03-16
tbuss, this might be a longshot, but once you do the install, and are running off your hard disk instead of the CD, you might want to see if you can install the Creative software through wine.
I have been surprised by some of the packages that will run under Linux. It never hurts to try.
Welcome to the best OS money can't buy.

---

### Post by esaym on 2007-03-16
> **tbuss said:**
> I'm thinking about installing ubuntu on my computer but I'm unsure how everything will work. 

Dell Dimension 8200
Intel Pentium 4 1.79 GHz
512 RAM
2 HDD and 1 External 
--Maxtor 6Y120P0 [Hard drive] (122.94 GB) // Internal
--Maxtor OneTouch II Disk (300.08 GB) // External firewire connection
--ST340016A [Hard drive] (40.02 GB ) // Internal
ALL-IN-WONDER 9600 SERIES 
Creative SB Audigy 2 Platinum eX
Realtek RTL8139 Family PCI Fast Ethernet NIC
Canon i950 printer
 
I also 1 USB 2.0 PCI card installed and 1 Firewire PCI card installed. My keyboard and mouse are both Logitech wireless devices.

What I was wondering was will my sound card and video card work. I have read that ATI can be difficult to configure in Linux. I'm not sure about my sound card, from what I have read it will work but what about the software that loads with the card: EAX console, Surround Mixer, Speaker Settings etc. I'm concerend that my wireless keyboard and mouse will not be compatible as well. Also will my external HDD work with a firewire port, I now this basic but I don't know. I'm not looking for someone to answer all these questions for me (that would be nice however) but if you could simply direct me to some reliable sources that will give some useful info about these questions, that would be great.

Oh my, that's an old cpu, upgrades are [cheap]("http://cgi.ebay.com/Used-Pentium-4-2-4GHz-CPU_W0QQitemZ160094240299QQcategoryZ14293QQrdZ1QQcmdZViewItem") right now!  Sound should work.  I have an Audigy 2 zs and I don't have any problems.  The ati card will work as some people have said.  You might run into a few glitches with it, like having to boot the live cd using the "safe video" option.  However you will not be able to play any games with that card.  That is probably ok with you since that is a very sub-par card for gaming.  I certainly hope you were not trying to use it for gaming in windows :neutral: 

However if you do want the best and want to game some or just want a better experience, the nvidia 6 series are all good card.  The geforce 6200, 6600, and 6800 can all be bought used for UNDER $50.  Just check ebay and classifieds ads on forums.  Even the geforce 6200 will be way faster then the ati 9600 in gaming.

---

### Post by wxnker on 2007-03-16
According to their website Canon have linux drivers for a few printers like: IP2200-IP4200, IP1000-IP1500.

Anyone who has a different model should fill out this form:
[http://www.canon-europe.com/Support/Software/Linux/registration.asp](http://www.canon-europe.com/Support/Software/Linux/registration.asp)
and ask Canon to make those damn Linux drivers. I am hoping for IP4300 drivers to be developed myself. 

There is also links to the supported models on that site.

Turboprint works fine but I'm not going to pay for a driver. 
Make Canon provide those. Sign up.

Regards
wxnker

---

### Post by tbuss on 2007-03-16
**esaym,**

I purchased the card because of it's built in tv tuner, as long as I can configure a tv signal and have decent graphics I'm okay, I have considered switching to nvidia and purchasing a seperate tv tuner pci card (some research indicates Hauppauge would be best choice?) Also, the link was helpful, I'm definitly not a hardware guy so I would have never known what to look for as far as a cpu upgrade.

**jhenager**

I forgot a detail in my initial post. I also have a small home network installed. The computer I'm thinking about switching OS's on is connected to my wireless router (Miscrosoft :( MN-700 Wireless Base Station). Now, this WINE program, will I need to use this to run the network utility program for my wireless router? If not, how will I access the router and configure the security, essid, moniter network taffic, etc.

---

### Post by vree13 on 2007-04-06
> **tbuss said:**
> I forgot a detail in my initial post. I also have a small home network installed. The computer I'm thinking about switching OS's on is connected to my wireless router (Miscrosoft :( MN-700 Wireless Base Station). Now, this WINE program, will I need to use this to run the network utility program for my wireless router? If not, how will I access the router and configure the security, essid, moniter network taffic, etc.

I don't know if you've resolved this question yet, but according to the manual for the MN-700, which I found [here]("http://download.microsoft.com/download/b/6/9/b69c956c-85d9-4641-aa6f-1548391e0967/mn700_usersguide.pdf"), you can connect via web browser and make changes with no problem. Instructions on how to connect start around page 15 of the .pdf file. Good luck!

---

### Post by tbuss on 2007-04-08
vree13

Thanks for the reply, I figured out that I could type the IP of the router in the address bar and I'm able to login to the managment tool, wish you had posted sooner :)

---

