---
title: "Ubuntu 10.10 PPC - Mac Cube G4"
date: 2011-01-22
forum: Apple Hardware Users
---

### Post by BlastXng on 2011-01-22
Hello Folks
Maybe someone can help me out here..;)

I decided to give Ubuntu 10.10 a shot to see if it would display on my Mac Cube. 

I tried the LiveCD with no joy at all due to display issues where the display wouldn't work except for the initial boot. So I moved on to the alternate installer which I was able to install (since it's a real basic display) and to some extent get up and running. 

So here is my problem. I cannot at all run X-Windows on the Mac Cube I have. I have tried:
- Recreating the xorg.conf file - automatically from the menu in 10.10
- Recreating the xorg.conf file - via command line when I drop into "netroot" terminal

I have researched the various options that people have spoken about on these forums and other places. It seems like I am running out of options to be able to use Linux on my Cube. 

My present set-up from a hardware perspective is:
- Mac Cube G4 PPC 450
- 1 GB RAM
- 32 Mb Video Card (I don't remember which one)
- 17" Apple Display - using the ADC on my Cube

When attempting to get the display to work via reconfiguration on the command line for X, I get a bus error that comes back after the X-Org reconfigure attempts to run.. 

BTW I had thought about use the following xorg.conf file, but it's for a 15" display

[http://mac.linux.be/content/xorgconf-g4-cube-15-inch-apple-cinema-display](http://mac.linux.be/content/xorgconf-g4-cube-15-inch-apple-cinema-display)

So I downloaded it, installed it and tried to run it.. Black/Blank screen and I can't get back to the terminal without completely powering off my Cube.. 

What I figured is that the above file wasn't used originally by X when it tried to load... So... I rebooted the Cube and left the above mentioned xorg.conf file in /etc/X11/ and viola I have an actual display..

Unfortunately the display is pretty darn slow almost to the point that I don't know if I'll be able to use it well enough.. 

So I ran lspci which spit out the following:

@Cube:/etc/X11$ lspci
0000:00:0b.0 Host bridge: Apple Computer Inc. UniNorth AGP
0000:00:10.0 VGA compatible controller: ATI Technologies Inc Radeon RV200 QW [Radeon 7500]
0001:10:0b.0 Host bridge: Apple Computer Inc. UniNorth PCI
0001:10:17.0 Unassigned class [ff00]: Apple Computer Inc. KeyLargo Mac I/O (rev 03)
0001:10:18.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:19.0 USB Controller: Apple Computer Inc. KeyLargo USB
0001:10:1a.0 FireWire (IEEE 1394): Texas Instruments TSB12LV26 IEEE-1394 Controller (Link)
0002:20:0b.0 Host bridge: Apple Computer Inc. UniNorth Internal PCI
0002:20:0f.0 Ethernet controller: Apple Computer Inc. UniNorth GMAC (Sun GEM) (rev 01)

Is there a driver or setting in my xorg.conf file that would be able to take advantage of the 32Mb ATI Video card I have installed? I have started to poke around and thought about setting the drive to ATI, but last time I did that I got the above mentioned bus error.. 

**UPDATE**

Well the xorg.conf file referenced above, did work for one day. Unfortunately after I ran updates on the system, shut it down for the night my Mac Cube at boot kept having issues and constantly re-booting.. So now I am re-installing to see if this will fix anything.. which BTW I did try to get to and use "Linux 1" at yaboot but could never get that far without the rebooting occurring over and over. 

Any thoughts from anyone on the display issues and how I might be able to actually use a better X driver?

Much Obliged, 

Blast

---

### Post by linuxopjemac on 2011-01-23
try this:
[http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display](http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display)

---

### Post by BlastXng on 2011-01-23
> **linuxopjemac said:**
> try this:
[http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display](http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display)

I'll download it and will give it a shot.. BTW I did look through the other xorg.conf files on your site and didn't think about using this one, since the Video Card I have installed isn't the standard Rage 128 card, but is actually a 32Mb ATI card, which I believe is the 7500.. 

I'll let you know what happens..

---

### Post by BlastXng on 2011-01-23
> **linuxopjemac said:**
> try this:
[http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display](http://mac.linux.be/content/g4-ati-and-17-inch-apple-studio-display)

I tried this file out and unfortunately I ended up with a blank / black screen at boot time..

I am now working to get the xorg.conf active (referenced in my original post) to see if I can recover. 

Unfortunately, this didn't go well. When I booted back up and at yaboot put in "Linux 1" (then drop into NetRoot via the menu) which usually works without a problem, I ended up with a black/blank screen..  

Not sure what I can do at this time to correct this, but will try to get it back up and hopefully I don't have to re-install or move back to OSX 10.5.

** UPDATE **
Well I was finally able to boot into the text menu via Linux 1 at yaboot. I have replaced the G4_5 file with the G4_4 file and now have my display back.. Which is good for at least I now have a desktop I can see. :-)

I'm not sure what to try at this point and would really like to get this to work..

Would posting the information from Hardware Profiler for my G4 Cube maybe help?
 

Thanks

---

### Post by Jarbuntu on 2011-01-24
Hey i've been attempting to install a stable version of linux on my emac 1Ghz, with a radeon RV200 7500 videocard for a while now. my initial choice is ubuntu but after much trial and error and a nice stack of cd-r's ive started to settle into opensuse 11.1 but would still love to be running Ubuntu. Glad to see not everyone has given up on Powerpc. if you get this working id love to try it out.

---

### Post by BlastXng on 2011-01-24
> **Jarbuntu said:**
> Hey i've been attempting to install a stable version of linux on my emac 1Ghz, with a radeon RV200 7500 videocard for a while now. my initial choice is ubuntu but after much trial and error and a nice stack of cd-r's ive started to settle into opensuse 11.1 but would still love to be running Ubuntu. Glad to see not everyone has given up on Powerpc. if you get this working id love to try it out.

Jabuntu, I'm not sure what I am going to do next. I have tried Yellow Dog which installed the first time without any problems, but the Firefox and Thunderbird were so old that it wasn't funny.. 

In addition to the issues with the Video card, I also don't have any sound nor can I run the User & Groups Administration program to add my wife as a user on the cube. Thankfully she has a Powerbook 1.5Ghz G4 PPC that is running 10.5 and a laptop (x86) running LinuxMint 9.. 

If you have enough ram on your eMac you might want to go to 10.5 if at the end of the day you can't get the programs that you need.

Ciao

---

### Post by oswaldkelso on 2011-01-24
> **Jarbuntu said:**
> Hey i've been attempting to install a stable version of linux on my emac 1Ghz, with a radeon RV200 7500 videocard for a while now. my initial choice is ubuntu but after much trial and error and a nice stack of cd-r's ive started to settle into opensuse 11.1 but would still love to be running Ubuntu. Glad to see not everyone has given up on Powerpc. if you get this working id love to try it out.

Debian runs fine on PPC. Squeeze is more work if you don't install firmware-non-free but everything works. I run a G3 imac, G4 400, G4 800, G4 867, G4 emac 1ghz. 

Debian, Gentoo, Frugalware and Cruxppc seem to be the only distro's officially supporting PPC with current/latest software.

---

### Post by Jarbuntu on 2011-01-24
I wish I could be more help there blastx, I wouldn't say I'm a newbie...maybe a rookie.

..but this post  along with the inability to watch pulp fiction on dvd last night after much searching for the right file to install to opensuse,inspired me to give a fresh install of 10.04 a try (not 10.10 because the last try was quite laggy and slow with cd tray problems and no sound on top of the flash ports not working). 

I am as i type running the update manager on lynx. But havn't heard a single sound out of the machine since startup...and it seems to have the same cd tray issues (opens from keyboard, wich opensuse wouldn't do, but closes right away). 

Im running with 384mb of ram currently a little low but osx 10.4.11 kept up just fine. I tried a few old distros of ubuntu, debian, fedora, gentoo none of them liked the video card off the bat even with the vesa driver. And the ones that did run I had taken the same issue of them being thoroughly outdated (even having there repos entirely removed).

Im just glad at this point that I recently got a droidx so I can fix these issues with the help of you fine folk.

---

### Post by BlastXng on 2011-01-24
> **Jarbuntu said:**
> I wish I could be more help there blastx, I wouldn't say I'm a newbie...maybe a rookie.

..but this post  along with the inability to watch pulp fiction on dvd last night after much searching for the right file to install to opensuse,inspired me to give a fresh install of 10.04 a try (not 10.10 because the last try was quite laggy and slow with cd tray problems and no sound on top of the flash ports not working). 

I am as i type running the update manager on lynx. But havn't heard a single sound out of the machine since startup...and it seems to have the same cd tray issues (opens from keyboard, wich opensuse wouldn't do, but closes right away). 

Im running with 384mb of ram currently a little low but osx 10.4.11 kept up just fine. I tried a few old distros of ubuntu, debian, fedora, gentoo none of them liked the video card off the bat even with the vesa driver. And the ones that did run I had taken the same issue of them being thoroughly outdated (even having there repos entirely removed).

Im just glad at this point that I recently got a droidx so I can fix these issues with the help of you fine folk.

Jabuntu,

Over 10 years ago I ran Suse Linux on a 7500 with an upgraded G3 card (really? I'd have to double check) anyway and it ran pretty darn good all things considered.. So did YDL.. 

I have been basically staying away form running Linux (any variant) on PPC due to the ability to use OSX and all of the NIX tools that are available via the various CVS repo's. 

I have been doing some research and now I am thinking about installing Debian and then updating it to MintPPC for I figured I haven't got much to loose at this point. If things go haywire then I'll just re-install OSX 10.5 (Yes I use a hack to install 10.5 on a non-supported Mac) back onto my Cube. 

So unless I get things sorted on this Cube with Ubuntu, I'll be making a switch to Debain (Lenny I think?) version 5.08 and see what happens. Hell I might even try out MintPPC on top of Debian which is what one needs to do anyway when using Mint. 

Quite frankly I am wondering, quite hard that is, whether to abandon using Linux at all on my Cube.. While Yellow Dog Linux did boot up with it's GUI after installing it, the use of the the Frame-buffer in the xorg.conf file really made it run horribly and the distro was so old that getting updates wouldn't happen. 

The thing is, is that I really want to run Linux on my Mac Cube.. MintPPC, Debian or Ubuntu, but it's getting very difficult to get things to work, which I am more than willing to try. If this goes on much longer, I'll be back to OSX 10.5 on my Cube cause my wife would like to use it from time to time.. :-)


Cheers

---

### Post by BlastXng on 2011-01-24
> **oswaldkelso said:**
> Debian runs fine on PPC. Squeeze is more work if you don't install firmware-non-free but everything works. I run a G3 imac, G4 400, G4 800, G4 867, G4 emac 1ghz. 

Debian, Gentoo, Frugalware and Cruxppc seem to be the only distro's officially supporting PPC with current/latest software.

How has the Debian been working for you? I was thinking about Gentoo, but I noticed that they are usually a bit behind in updates for PPC. 

I'm looking for something that not only I can use, but also my wife (got to keep her happy!) who isn't a tech-head.. That's why I was thinking about Debian and then maybe putting MintPPC on top of it..

---

### Post by Duo Maxwell on 2011-02-21
Tried Debia Squeeze on my 800Mhz Quicksilver w/ Radeon 7500 and 1.5Gb of ram, was a mass of headaches with it refusing to recognise the sound chip, constantly losing the mouse if it didn't like what I clicked on till I replugged it in, after reboot would always lose DNS settings...

So far Ubuntu works pretty well, but I can't get 3D acceleration and video playback looks more pixelated then it should be in Totem and Mplayer, but looks fine in VLC.

---

### Post by rsavage on 2011-02-23
I don't have your machine and I don't know much, so the following is a guess!

Before I disabled KMS the video playback on my iBook was strangely pixelated/very poor quality.  There are quite a few posts on how to do this.  Some recent ones are:

[http://ubuntuforums.org/showthread.php?t=1691511](http://ubuntuforums.org/showthread.php?t=1691511)

and 

[http://ubuntuforums.org/showthread.php?t=1691981](http://ubuntuforums.org/showthread.php?t=1691981)

but there are more detailed instructions if you do a search.  This should hopefully sort our your 3d acceleration too.

---

### Post by oswaldkelso on 2011-02-24
Duo the sound issue is well known about. 

[http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html](http://oswaldkelso.blogspot.com/2010/10/how-to-fix-no-sound-on-debian-powerpc.html)

---

### Post by MisterGaribaldi on 2011-02-26
Well, here's what I can tell you...

I have run Debian on both an OldWorldROM PowerMac G3 and a G4 Mac mini, and in both cases it ran just fine, no display issues whatsoever. The G4 Cube sits between those two computers (much closer to the Mac Mini, of course) and so it should support your hardware without any problems.

Now, don't go expecting the world from it (like 3D acceleration, full sound support, etc.) but for just a nice solid basic workstation (or, as in my case, a server) it should be solid.

---

