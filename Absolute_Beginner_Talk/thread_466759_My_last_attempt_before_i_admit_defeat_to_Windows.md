---
title: "My last attempt before i admit defeat to Windows"
date: 2007-06-07
forum: Absolute Beginner Talk
---

### Post by SimoG on 2007-06-07
First of all the background:

I think it is just over a month since I decided to dive in head first in Ubuntu and initially I had some success but recently it has been nothing short of a disaster.

I started off with an install of 6.06 (which took me 3 installs to get right with the partitioning and I still managed to corrupt my Windows install, but I have to take ownership for that one) and after doing a little bit of reading (I should have done more) I read that wireless networking is much easier on 7.04 so I did an upgrade install to 6.10 and finally another upgrade to 7.04 (yes I know and next time I will just do a straight install). After just under a month of happy computing and playing with Ubuntu it started to hang about 2 minutes after booting, which I couldn’t pin to any change I have made as I think I had tried every fix I found on the forums that remotely resembled my problems.

So I tried a complete reformat and reinstall of Ubuntu having a little more knowledge of Linux (which one month ago was absolutely nothing). Now with a clean install of Ubuntu with nothing but the standard repos, Nvidia Drivers (which I have since uninstalled), Swiftfox and Deluge Bittorrent.  

With the nvidia drivers and a clean install my computer was running for maybe 2 minutes (5-10 on a good day) and then hanging, the mouse was moving but not responding to any clicks and would stop about 1 – 2 centremetres before the cursor moves to the next screen.  Uninstalling the Nvidia Drivers has seemed to work but it is still hanging occasionally.

The other issue I am having is with the Synaptic Package Manager. Whenever I try to install any packages it returns as error saying the it has unresolvable dependencies (I’m at a work at the moment so cant get the exact wording of the error but I will post that as soon as I get home).

And the final issue I’m having is with the Wireless network, I have the RT61 chipset on the Linksys PCI card and no matter what I do and what guide I follow I cant get it to work, it can see the networks but not connect under WPA.

Anyway that is all the issues I have at this stage and any more I will post as I am being incredibly stubborn with this and I don’t want to go back to Windows.

Thank you in advance for your help

Simon

---

### Post by Catsworth on 2007-06-07
Ok, my suggestion (and it's by no means an 'expert' one) would be to go back to either 6.06 or 6.10.

I know that sounds like a daft suggestion, but 6.06 is the Long Term Support (LTS), and I've always found 6.10 to be very stable.

There are ways to get WPA working (I used WICD to get mine working, do a quick search of the forum and you should find a link to a site you can download it from).

I know it seems like a tough slog, but it really is worth it.  I've gone from knowing nothing about Linux/Ubuntu, to knowing enough to get most day to day tasks completed.  I'm still a far way from knowing everything, but every day I learn something new and love everything that I learn (how many people can say that about using Windows?).

Like I say, hang in there if you can.  Go back to a more 'stable' release and see if that helps.  You've obviously invested a lot of time (blood, sweat, and tears) in getting to where you are - it would be a shame to throw all that away now.

Good luck :)

---

### Post by Redbomber on 2007-06-07
Are you sure it is software and not a hardware problem?  Sometimes my PC resets on startup.  DId it with Vista and now Ubuntu.  I'm sure it's RAM, but it doesn't bother me much.

---

### Post by Inxsible on 2007-06-07
Simon,

Good to know that you want to stay back. We will try our darndest to help you out. Also post the configuration of your machine.

I am not too sure about your nvidia driver problem, but i think i can help out with the wireless card if give more info. I am sure there are others who can help you out too.

Lets get you all fixed up :D

---

### Post by Alterax on 2007-06-07
My own first experience with Ubuntu was, shall we say...less than satisfactory.  But don't let that discourage you; ever since I tried a fresh install of 6.10 and then from there to Feisty, it's actually been very rewarding.

According to your accounts, I think there are several problems that a fresh install of Feisty may cure.  The graphics drivers can be quirky, but NVidia does do a great job on them.  You may have better luck using the open-source drivers, even if it does mean having to cut out some of the eye candy in favor of performance.  (It can look great, but if it doesn't run your programs, it's worthless in my opinion).

The hardware lockups may possibly be due to overheating.  I don't know your hardware per se (post what you have and I can speculate a little further), but I am assuming that you are running this on a laptop.  If that is the case, it may be overheating.  Try checking to see if the system fans run a lot--or not nearly enough.  If the system is running hot, look for information on how to reconfigure the settings for the powernowd daemon.  You can configure  a processor to run at a lower rate, and paradoxically it can run better up to a degree because it can handle the heat a lot better.  Worked like a charm on my iBook G4, which is notorious for running hot and locking up from the heat.

The apt-get/software dependencies issue (and add/remove programs, Synaptic Package Manager, and Automatixx are all just front-ends for apt) seems to indicate that your software repository lists are incomplete.  This can be handled by a fresh install and then adding the Universe repositories from the System Menu.

Finally, there's WPA.  I have been using WPA_GUI (apt-get install wpa_gui) to handle WPA on my own wireless card (Broadcom 4306 series chipset using the bcm-43xx drivers).  It has done well, but I've noticed when I suspend my laptop, I have to reapply for a DHCP lease by running sudo /etc/init.d/networking restart .  

My mate seems to swear by KNetworkManager (apt-get install knetworkmanager) for using WPA on the other laptop (IBM/Lenovo ThinkPad), and says it works great.  It has a nicer interface than WPA_GUI, and it will run on the standard Gnome interface for Ubuntu.  Network Manager didn't get nearly as good reviews from either of us.

I hope this helps, but if you'd be so kind as to post what kind of hardware you are using, I may be able to get more information that'll help for your specific situation.

--Alterax

---

### Post by floke on 2007-06-07
Don't know about the lock-ups - that must be bloody annoying (do they happen on LiveCD?) - but for wireless you could try wifi-radar (the first thing I install on fresh ubuntu's - network manager has a habit of crapping out on me when it wants to).

---

### Post by khardbored on 2007-06-07
Do you have your CPU overclocked? I know that Linux can be sensitive to it as well. I had my P4 3.0 pushed to 3.9 and she would crash. It took me about 2 hours to find the right OC...just a quick suggestion.

---

### Post by SimoG on 2007-06-07
Thanks for the quick replies.  it is a desktop PC (but this is also a trial run to see if i install Ubuntu on a laptop which will be purchased in the next month or two)

intel 64bit 3.0G processor
1G ram
160G Western Digital Sata HDD (45G OS Partition, 5G Swap File Drive, 100Gish media partitian
300G sata HDD
330G Sata HDD
Nvidia 6200TC graphics card

asus Motherboard P5GD1-PRo

i hope this can help

and this is the error i am getting with the package manager

gtkpod:
 Depends: libid3tag0 (>=0.15.1b) but it is not installable


thank you again for your help

Simon

---

### Post by SimoG on 2007-06-07
And i'm not overclocking the CPU

S

---

### Post by Alterax on 2007-06-07
Ah.  Gotcha.

I'm willing to bet that it could be the 64-bit version of Ubuntu that is causing the problem.  Some 32-bit apps and libraries don't work all that well with the 64-bit optimized kernel.  The library that you just mentioned that goes with GTKpod may not be available for the 64-bit repositories.

That leaves you with two options.  The first is to try to install GTKpod from source.  You'll need to hunt down it and its dependencies, run sudo apt-get install build-essential to get your compilers and all, then do the ./configure && make && sudo make install dance.  But it should work.

The video troubles are the other problem, and they may be solvable by using a slightly less compatible version of Ubuntu.  The drivers aren't built from source, so it's probably trying to use a 32-bit proprietary driver on a kernel optimized for the 64-bit processor.  (I found out to my regret that the x86 32-bit version seems to be the most popular for video drivers.  Since I run with a PowerPC processor, I'm stuck with the open-source drivers).  Since you've considered blowing your hard drive away and going (reluctantly)back to Windows, could you try using the regular 32-bit (x86) Ubuntu install CD for a fresh installation?  It may work out better in your situation, though it won't take full advantage of your processor's capabilities.  On the other hand, your video should work much better and you'll have better luck getting your software dependencies met (since the x86/32-bit repository has more software written natively for that kernel than the 64.)  Later releases may be able to handle 64-bit kernels better.

Best of luck!

--Alterax

---

### Post by SimoG on 2007-06-07
Sorry i should have clarified ... it is a 64bit chipset but 32bit OS (i learnt that lesson when i tried 64bit windows shortly after it came out and said goodbye to all my devices.

S

---

### Post by Alterax on 2007-06-07
The converse can hold true here, too.  Try the 64-bit version, see if it helps. 

--Alterax

---

### Post by SimoG on 2007-06-07
Ok so i'm going to go back and reinstall Feisty, hopefully see you guys on the other side.

I'll report back on how i go with the issues i am having

Simon

---

### Post by Alterax on 2007-06-07
Excellent.  Best of luck!

-A

---

