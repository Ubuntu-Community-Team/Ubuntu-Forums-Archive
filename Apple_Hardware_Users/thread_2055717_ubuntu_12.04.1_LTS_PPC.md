---
title: "ubuntu 12.04.1 LTS PPC"
date: 2012-09-10
forum: Apple Hardware Users
---

### Post by drspaceman767 on 2012-09-10
Since 12.4.1 released I can see it on my update manager on my iBook G4 that runs 10.4 LTS. I tried doing the upgrade, but it couldn't "fetch the depositories" or something like that. Has anyone had any luck installing the new 12.4.1 LTS on a iBook G4 (or similar machine)?

Thanks,

Spaceman

---

### Post by 2blue on 2012-09-10
I haven`t tried Ubuntu with Gnome and Unity, thinking it was too heavy for the old hardware. It might have been a bit hasty, disregarding it with out even trying. It migt run fine, at least with higher spec G4 and G5s. 

I have lubuntu 12.04 with the lxde desktop running on my old iBook G4. I went straight for it having had very good experiences on low specs previously. There were a few issues booting the CD, but easily managed when you have them pointed out. There is a good ppc [faq]("https://wiki.ubuntu.com/PowerPCFAQ") page that helps ironing out issues. I have a few issues I am working on still.  

I don`t think you can jump from 10.04 to 12.04 upgrading via update 
manager, but you should easily install from CD better and more easily than the two individual upgrades up to 12.04. I assume you want the long term supported version, soon we are on to 12.10 ;- )

---

### Post by drspaceman767 on 2012-09-10
Yep,

Definitely want the LTS version, it's why I'm still on 10.4 on that computer. My desktop PC dual boots Windows 7 and Ubuntu 12.4 (or whatever is up to date at the moment), but I got to keep the lappy on LTS, and probably should switch to lubuntu or xubuntu.

I'll post findings soon once I attempt the upgrade.

---

### Post by drspaceman767 on 2012-09-15
SUCCESS!!!

After a little trial and error, I got 12.4 LTS to work on my iBook G4.
First I got the PPC 12.4.1 LTS live CD, booted and attempted to install. I got hung up when it tried to set up the wireless card. the error message was to the tune of "b43/ucode5.fw" not found. please go to blah blah blah website to get updated firmware. 
search google or this forum for plenty of articles about that issue.
then I got the alternate 12.4 ppc install cd from the website here:
[HTML]cdimage.ubuntu.com/releases/precise/release/[/HTML]that install process got me just a bit farther. I could install 12.4 LTS to the computer, but upon reboot, I got the same wireless card message above. 
further research was done and I found out about black listing

I put my 12.4.1 PPC live cd back in the computer and booted from it. then followed a process i found in the "where to find Ubuntu..." thread that is sticky'd in this forum.
2blue posted on page 22 this command

> I got some very good help with a bug in the boot up stage, that might  pop up. It turns out you need to run the command "live  b43.blacklist=yes" in the black screen, then after install "Linux  b43.blacklist=yes". 
Following that instruction I got 12.4 LTS running on my iBook, which I'm using right now. Next step is try to get the wireless card back online, but that shouldn't be hard. Hopefully 12.4 will not be to heavy duty for my OLD mac. otherwise I will have to go back to 10.4 LTS.

Thanks to 2blue and the forum for the help and resources.

Spaceman

---

### Post by djm02 on 2012-09-22
Hi Spaceman, and other,

Did you end up with 12.04 or 12.04.1?
Because I thought that 12.04 is the latest version for PPC so far.
Maybe that's why at first it would not work.
I've installed 12.04 also on my Powerbook g4 using the Live CD and did a clean install without any problem.
[U]
Problems I encountered were;[/U]
No wifi at first, this is the page that helped me..
[http://linuxwireless.org/en/users/Drivers/b43](http://linuxwireless.org/en/users/Drivers/b43)
I installed without doing any updates or third party stuff.
Right after updating I used this page above.

Also I had no sound, this is what helped me...
[http://www.linux-radar.net/linux-ubuntu-1204-ppc-mac-mini-dummy-output-sound-card.html](http://www.linux-radar.net/linux-ubuntu-1204-ppc-mac-mini-dummy-output-sound-card.html)

The only thing I have not solved yet is the fact that I am not able to watch video's online, or stream video's online.  :( And that's what I use the laptop mostly for.

So I'm hoping that someone comes up with a solution for this.
I've followed every instruction I could find so far on the internet, 
but nothing so far.
These are the links I've tried in this matter;
[http://www.noobslab.com/2012/02/no-adobe-flash-on-linux-except-chrome.html](http://www.noobslab.com/2012/02/no-adobe-flash-on-linux-except-chrome.html)

[https://wiki.edubuntu.org/PowerPCFAQ#Flash.2C_Flash_video.2C_Gnash_and_Lightspark](https://wiki.edubuntu.org/PowerPCFAQ#Flash.2C_Flash_video.2C_Gnash_and_Lightspark)

Also I tried installing the flashaid-addon.
I've tried every option with help of this addon, but no result.

Did anyone have more succes / luck?

Hopefully we can all remain to enjoy our PPC machines.
Thought that Mac was the BOM, never had one, but I did not know that older Mac where sort of discriminated in the online world by shutting out support.

greeting DjM

---

### Post by 2blue on 2012-09-22
I don`t know about any 12.4.1 iso, but when you do updates you will end up with the latest. I have tried all mozilla browser plugin packages for Lightspark and Gnash, unfortunately all broken for ppc. So far I have never been able to make Lightspark stream, but Gnash streams all right in Midori. Probably because Midori is non-mozilla, there are probably others too. The lower specs CPUs will hardly stream flash well, I think minimum will be around 1.5GHz, but that is only a loosely made estimation by me. 

There are a few workrounds for video streams like minitube for Youtube, Gnome mplayer used to work fine with Flash Video Replacer plugin in Firefox, but it hasn`t been available the last few weeks (will it ever return?). 

Video streams are the largest challenge for ppc, and you have to search for workarounds for the site you use. Totem Player has different plugin packages for Firefox and is worth a try.

---

### Post by rick1959 on 2012-09-23
Hi,
Just been reading up on this thread and wanted to ask a few questions, if you could bear with me?

I have a clean iBook G4 1.42Ghz, 14 inch screen. last of the iBook series. So far, I've been running into the road block of the B43 issue when trying to install Lubuntu 12.04 PPC.....

So, my question is if this is worth doing to be able to use Ubuntu for PPC?

I would be doing this for an improvement over OS X 10.4.11, from a practical use perspective. Being familiar with Ubuntu and various flavors on Intel based PC's (NOT Mac's!!), I wanted to try this before going to another Linux distro or making do with OS X, "as is". 

I need a working computer at this time, not an experiment. If it were an experiment, I'd eBay this off and get a used Intel PC and load Ubuntu that way......

Any thought's?

Many Thanks, Rick

---

### Post by 2blue on 2012-09-24
I don`t know if there would be much of an improvement over Tiger or Leopard. You will need to work a bit to find solutions for some applications like media streams in browser. You will be able to have latest Firefox if that matters; Gnash flash player (works in Midori at least). Flash will always be an issue if there are no other alternatives. 

In Tiger you can have Tenfourfox, Camino which is not available for Ubuntu. Tenfourfox is listed as open source, there might be a way if you can build packages. 

The b43-hault is easy to fix on the iBook. You will be able to have a stable system, booting fine and running fine. You will be able to use your online bank, have a fully working office (libre or open office among them), watch youtube, facebook, email. Your Wireless, CD/DVD player will work fine once you have drivers installed. 

It`s sort of a toss really, it depens upon what you want. Either Tiger or Ubuntu (I chose lubuntu) you will have to struggle a bit on ppc.

---

