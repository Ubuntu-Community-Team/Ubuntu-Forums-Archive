---
title: "Wireless, ndiswrapper, Netgear wg511v2"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by alabasterjones on 2007-07-03
Hi!
So, I just installed the newest feisty fawn Ubuntu last night with the text installer. I think it's cool, the GNOME thing reminds me of Mac OS, the color scheme is cool, everything seems to run.

But...

I have been trying to get my NETGEAR Wg511v2 wireless card to work with linux for weeks now and I can't!

I've been reading all kinds of posts online about it and it seems like it always needs a manual setup on any distro, but everyone seems to do it a different way!

First problem:
I have ndiswrapper but I can't even install it. 

I extracted it from the tar.gz, followed the installation instructions in Terminal to the letter, but when I try to run it with "ndiswrapper -i" or "ndiswrapper -i driver.inf" as instructed, it says ndiswrapper is not installed. Then it says "try: sudo apt-get install ndiswrapper..." or something like that, and I do that, then try to run it again and it still says it's not installed.

Second problem:
I have all the files I'm supposed to need: the .sys and .inf files from the install cd, a .arm file from prism54.org, but I don't really know where they are all supposed to go. (I tried installing the .arm on Linspire in usr/lib/drivers/hotplug or whatnot as I read somewhere that that worked right away for someone, but it didn't work when I did it)

Another problem: 
My ubuntu has setup modules for "wired" and dial-up connections (near the top right corner) but not one for wireless. Is that right?

When I run iwconfig it says 

eth0: not detected (I'm working from memory on all these printouts)

(something else)0: not detected

I'm running dual boot with windows just to have the internet, but this is really weird and frustrating.

Let's make this easy for people! That way linux can get popular and bill gates won't get anymore of our money. The world will be a better place

---

### Post by userundefine on 2007-07-04
I have the same dongle and used [this thread]("http://ubuntuforums.org/showthread.php?t=329299") to get it working flawlessly.  It tells you how to install ndiswrapper and everything you need.

---

### Post by lintoon on 2007-07-04
This probably isn't much use to you but I thought I would say it anyway because you have a new install of Ubuntu and may not have much to lose.

I have a netgear WG511T and it worked immediatley.  All I done was insert the card and then install Ubuntu.  Luckily it was recognised was installed for me during installation.  The only thing I had to do was install knetwork manager to allow me to use WPA encryption.  

Like I said, probably not much use to you because the other posts seem to be pointing towards ndiswrapper.

---

### Post by panther_sn on 2007-07-04
I also have the wg111v2 and all i did was install the ndiswrapper, i think (cant remember now)
[PHP]sudo apt-get install ndiswrapper[/PHP]

then logged into my router , speedstream 6520 if any1 needs help with that modem/router,  got all the settings I needed then opened network settings clicked on wlan0 then properties, then I put in my ESSID and key which I had copied from my router made sure I had clicked WEP Key under password type, and pressed enter then enabled it in network settings, restarted computer and all worked fine.

Hope that helps, as I am also a newbie and no the troubles that sometimes happen, all I can say is thankgod for the community here

---

