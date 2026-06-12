---
title: "Intel(R) 82865G"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by tompickles on 2007-06-13
Hi all,

Just bought a re-furbished pc (Dell) from the office. Though, it has Win 2k installed, which is just a tad unstable. Its a Pentium 4, 512 MB RAM, and from the Windows Device Manager, an Intel(R) 82865G Graphics Controller. When i tried to boot the Ubuntu CD, i selected 'Start or install' and was then presented with a Black Screen for 5 minutes before I rebooted back into Windows.


Any ideas?!

Thanks

---

### Post by infol on 2007-06-13
sounds like a bad cd.. did you check the MD5sum after download and after burning the iso?

---

### Post by Sparkster185 on 2007-06-13
You might want to "Check CD for Defects" and make sure the disc isn't corrupted.  I believe that system can handle Ubuntu, if it doesn't try Xubuntu.

BTW, I have an Intel graphics card (not nearly as old) and it works perfectly fine.

---

### Post by tompickles on 2007-06-13
I used a CD from ShipIt which has worked fine as a LiveCD on Laptops and other machines. Its a Pentium 4 3G Hz so, I should hope Ubuntu would work! Is it a problem with the default driver for Intel cards? Also, IF I get it to boot, with the Desktop Effects work or not?

---

### Post by infol on 2007-06-13
could be a compability issue between your BIOS and isolinux (the cd-bootloader). try upgrading to the latest bios (image files are available on dell's website) and then run the cd again.

---

### Post by tompickles on 2007-06-13
I don't really want to flash my BIOS! is this the only solution. Could I not force any boot parameters? And, people generally reccomend to start afresh, and reinstall windows - but - i don't actually have a windows install disk. Is it still 'safe'?!

---

### Post by infol on 2007-06-13
how far along in the boot-process do you get? does it blank out directly after POST, or do you get the ubuntu menu?

---

### Post by tompickles on 2007-06-13
Erm it boots the cd. And i did a Mem Check test and could see that fine - it passed that. Then I go back and hit enter on start or install ubuntu then you get the green dots at the top of the screen scrollin along
then it goes black. On other pcs when ive done this i get a screen full of white text loading up drivers and searching hardware etc.....but this doesnt happen. I just got bored and rebooted!

---

### Post by smartsaah on 2007-06-13
I am using Intel 865GBF with on board graphics card......as my cinfig is almost the same.....i did not have any prob.....as far as I can understand your CD is somewhat not OK, Burn it once more and see if anything improves

---

### Post by infol on 2007-06-13
the "green dots" on top of your screen is probably text...  try forcing another resolution before choosing live cd or install (by pressing F4 at the menu if i remember correctly).

---

### Post by tompickles on 2007-06-13
I'll try again later - it may have just been a fluke. And i'll try with another of the CDs that I ordered from ShipIt. Strange thing is this cd worked great on other machines!

---

### Post by tompickles on 2007-06-13
> **infol said:**
> the "green dots" on top of your screen is probably text...  try forcing another resolution before choosing live cd or install (by pressing F4 at the menu if i remember correctly).

The green dots appear as soon as you click on Start or Install Ubuntu, and say Loading vmlinux periodically

---

### Post by tompickles on 2007-06-13
Well, i rebooted using a new disk, and the same thing happened - though i did leave it longer. The next screen after the Start or install that i see is the GNOME splash, so all the pretty sliding orange loading bar i dont get to see. My monitor says im in 700x400 resolution, so, could this be the problem?!

---

### Post by camini on 2007-06-25
We have had exactly the same here on a Dell which we recuped and on which we tried to install Feisty.  The LiveCD is fine, yours probably too.
The solution was to install Edgy 6.10 and then upgrade to Feisty 7.04.
Now we have it working, but only in miserable 640x480 with the onboard 82865G onboard - I'm looking for a solution for this right now..

---

### Post by tompickles on 2007-08-06
My solution to this problem for all interessted was to migrate my Linux to openSUSE 10.2, which works a treat first and every time. It's a pity that Ubuntu and it's variesnt (Xubuntu etc) don'#t support Intel integrated graphics properly. I will be interessted to see if this happens with Gutsy.

---

### Post by Paulmd on 2007-08-07
> **tompickles said:**
> Hi all,

Just bought a re-furbished pc (Dell) from the office. Though, it has Win 2k installed, which is just a tad unstable. Its a Pentium 4, 512 MB RAM, and from the Windows Device Manager, an Intel(R) 82865G Graphics Controller. When i tried to boot the Ubuntu CD, i selected 'Start or install' and was then presented with a Black Screen for 5 minutes before I rebooted back into Windows.


Any ideas?!

Thanks

What model Dell is it?

Dell computers often benefit from bios upgrades. Check out support.dell.com, and see.

Also, win2k really is a stable OS, you may have hardware problems, run memtest (it should be an option on your Ubuntu boot CD)

---

### Post by tompickles on 2007-08-22
Got fed up of openSUSE! Ubuntu does seem to have the useability edge to it!

It is a Dell Optiplex GX270. Pentium 4 3.00GHz, 512MB RAM, Intel(R) 82865G Graphics Controller, 40GB HDD.

When I say green dots, for further claricification, when you select Start or Install Ubuntu, Green text appeasr at teh very top of the screen, [then this screen loads]("http://shots.osdir.com/slideshows/slideshow.php?release=790&slide=2"), except I cannot see this screen. The next one I see after about 10 minutes is the fully loaded Desktop. This is using the Live CD. The 6.06 Live CD works fine, but would rather use Feisty.

Any ideas?

---

### Post by Terl on 2007-08-22
If you go to the Dell site they will have the upgrades for you.  The BIOS updates are a breeze to do using their support system.  It is a fast download, you run it from windows, restart and all is done.  I really recommend you go to the dell site and get the bios updated.

---

### Post by tompickles on 2007-08-22
One step ahead. After posting the above, headed over to Dell. Downloaded the BIOS update. It was really easy - bene cautious of flashing my BIOS as I've heard horror stories of people having to buy new motherboards etc. Though, Im sure you can just flash it again with an older version?!

Anyway, updated from A02 to A07 - very out of date! So, will try again to see if Fiesty works. Will update later today.

The Uuntu forums is much faster/more helpfull/understanding than openSUSE's one! They just ignore some of the posts in there!

---

### Post by rrinker on 2007-08-22
I had been running an older Optiplex GX260 and it worked fine with Ubuntu. No graphics support problems at all with 7.04, I just booted from the CD and installed. The 'trick' with that machine was to make sure the video ram was set to 8MB in the bios and to get any sort of OpenGL acceleration working I had to turn on the VGA Snoop. It worked without doing that, but I couldn't run OpenGL programs like Tuxracer and TORCS. Not sure where the idea that Ubuntu doesn't support Intel Integrated video comes from, the driver is built in.
 The GX260 I have is the SFF box, and while it's a bit limited for expansion, it runs Ubuntu quite well, more than adequate for browsing, email, and office applications.

---

### Post by tompickles on 2007-08-22
> **rrinker said:**
> I had been running an older Optiplex GX260 and it worked fine with Ubuntu. No graphics support problems at all with 7.04, I just booted from the CD and installed. The 'trick' with that machine was to make sure the video ram was set to 8MB in the bios and to get any sort of OpenGL acceleration working I had to turn on the VGA Snoop. It worked without doing that, but I couldn't run OpenGL programs like Tuxracer and TORCS. Not sure where the idea that Ubuntu doesn't support Intel Integrated video comes from, the driver is built in.
 The GX260 I have is the SFF box, and while it's a bit limited for expansion, it runs Ubuntu quite well, more than adequate for browsing, email, and office applications.

Glad to hear that the Integrated Video is built in..... so why does it still not work after fashing my BIOS?! I get a black screen after hitting Start or Install. Please help?!

Don't understand what you said above about changing video ram.

---

### Post by rrinker on 2007-08-22
On boot, go into the setup. If the BIOS is similar, you press ENTER on the line for Memory. You can't change the item that shows the total RAM you have in the computer, but below that should be an option for Video Memory. The choices in the GX260 are 1MB and 8MB, not sure about the GX270. There should also be an option for AGP Aperature Size. I set that to 256MB.

---

### Post by tompickles on 2007-08-23
My Graphics are Integrated, so AGP is irrelevant?! I honestly don't know. I don't quite know why it doesn't work. Going to file a launchpad bug report as well.

---

### Post by tompickles on 2007-08-23
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/134237](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/134237) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				[Bug Report.]("https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.20/+bug/134237")

---

### Post by tompickles on 2007-08-23
Downloading Gusty Tribe 4 to see if this solves problem.

---

### Post by tompickles on 2007-08-23
Ok, after some initial fd0 read error warning, the Live Desktop Loaded. Slowly to be fair. Wireless works out of the box, unlike openSUSE where I had to ndiswrapper it.

Graphics problem solved too.

How safe is Gutsy yet? No desktop effects on live cd?!:icon_frown:

Recommend I wait until October?

---

### Post by andrew.46 on 2007-10-01
Hi,

 Saw my computer mentioned:

> **rrinker said:**
> I had been running an older Optiplex GX260 and it worked fine with Ubuntu. No graphics support problems at all with 7.04, I just booted from the CD and installed. The 'trick' with that machine was to make sure the video ram was set to 8MB in the bios and to get any sort of OpenGL acceleration working I had to turn on the VGA Snoop. It worked without doing that, but I couldn't run OpenGL programs like Tuxracer and TORCS. Not sure where the idea that Ubuntu doesn't support Intel Integrated video comes from, the driver is built in.
 The GX260 I have is the SFF box, and while it's a bit limited for expansion, it runs Ubuntu quite well, more than adequate for browsing, email, and office applications.

 Same experience with mine: a solid, dependable computer with good results from the onboard graphics. Like you I changed the video ram in the bios to 8. I also changed to 1 gig ram which made a considerable difference and I am halfway through buying a second hand 120 gig drive to replace the 40 gig incumbent.

 I have found the i810 driver delivers better results than the intel driver, you?

                   Andrew

---

### Post by nowshining on 2007-10-02
have any of u tried updating to the latest bios, if the Computer is like mine - which it sound like it is, then the latest Biso is A12 and when I did use the onboard intel card 82865G it worked fine for me in Feisty 7.04.

---

### Post by angelman99 on 2007-12-13
I scored an ex lease Dell GX270 the only problem I've had with it was the CD/DVD ROM drive was stuffed :(, worked intermittantly and slowely, 10 minutes to boot the Live CD :( . Replaced it with a newer DVD burner, loaded 7.04 rocking :) Took ram up to 1Gb that helped :) Currently running A6 BIOS no troubles.

---

### Post by ncgater on 2007-12-25
I have an HP/Compaq with an 82865G and am stuck with 800x600 resolution. I need to go up to 1280x1024 for Ubuntu to work. I previously had Centos working at 1280x1024 so I know it is possible.

If I do System->Preferences->Screen resolution, I get no choices. With System->Administration->Screens and Graphics, I get nothing at all. I have tried a few of the more commonly offered fixed for the 82865G but they do not work. Any Ideas folks?

David

---

### Post by tgalati4 on 2007-12-26
Here's something that worked for me.  Load SLED10 and grab the modlines from /etc/X11/xorg.conf.  Then transfer them to your Ubuntu xorg.conf.  Opensuse 10.3 might work as well if it uses a similar graphics card detection as SLED10.

I was able to get all kinds of strange resolution and refresh rates and they all worked!

---

### Post by ncgater on 2007-12-26
Okay, I got this working but I am not super confident in the solution. The key was to change the driver from "intel" to "i810". I then added a number of display subsections with various depths and modes. Kind of a kludge but at least I have choices now when I do System->Preferences->Screen Resolution and I can set it to 1280x1024.

While I can now do System->Administration->Screens and Graphics, I dare not. Every time I do it it messes up my xorg.conf with the result being I only get 640x480. So while it is sorta' working like I want, I don't feel it is stable.

From my xorg.conf

[INDENT][I]Section "Device"
[INDENT]        Identifier      "Intel Corporation 82865G Integrated Graphics Controller"
#       Driver          "intel"
        Driver          "i810"
        BusID           "PCI:0:2:0"
[/INDENT]EndSection

Section "Monitor"
[INDENT]        Identifier      "IBM G96"
        Option          "DPMS"
        HorizSync       30-75
        VertRefresh     50-85
[/INDENT]EndSection

Section "Screen"
 [INDENT]       Identifier      "Default Screen"
        Device          "Intel Corporation 82865G Integrated Graphics Controller"
        Monitor         "IBM G96"
        DefaultDepth    24
        SubSection "Display"
[INDENT]        Depth       1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
[/INDENT]        EndSubSection
        SubSection "Display"
[INDENT]        Depth       8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
[/INDENT]        EndSubSection
        SubSection "Display"
 [INDENT]       Depth       15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
[/INDENT]        EndSubSection
        SubSection "Display"
[INDENT]        Depth       16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
[/INDENT]        EndSubSection
        SubSection "Display"
 [INDENT]       Depth       24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
[/INDENT]        EndSubSection
[/INDENT]EndSection
[/I][/INDENT]

---

### Post by tgalati4 on 2007-12-27
Remove the lower resolutions from your xorg.conf file (800x600 and 640x480) and make a backup of your xorg.conf.  

Don't use the system, admin, graphics resolution tool.  It will write it's own, crappy xorg.

Try control-alt-backspace a few times to test for xserver stability.  If it keeps returning to the same, desired resolution without messed up fonts and icons, then it should be OK.

Also, try increasing the frequency range of your display a little:

Identifier "IBM G96"
Option "DPMS"
HorizSync 30-75
VertRefresh 50-85

Here's what I grabbed from SLED10:

snip

+vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync 
+vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync 
+vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync
 +vsync
        Gamma   1.0
  VertRefresh 48-170
  HorizSync   30-107
  DisplaySize 350 260
  UseModes    "Modes[0]"
EndSection

Section "Modes"
  Identifier   "Modes[0]"
  Modeline      "1280x1024" 188.88 1280 1376 1520 1760 1024 1025 1028 1084
  Modeline      "1024x768" 150.39 1024 1104 1216 1408 768 769 772 828
  Modeline      "1024x768" 149.05 1024 1104 1216 1408 768 769 772 827
  Modeline      "1024x768" 147.88 1024 1104 1216 1408 768 769 772 827
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82945G/GZ Integrated Graphics Control
ler"
        Monitor         "DELL P992"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 2048    1536
                Modes           "1280x1024@99" "1280x1024@75" "1280x1024@85"
"1024x768@60"   "1280x1024@60"  "1024x768@70"   "1024x768@75"   "1024x768@85"
"1600x1200@65"  "1600x1200@60"  "1600x1200@75"  "800x600@75"    "1600x1200@70"
"1600x1200@85"
        EndSubSection
EndSection

--------------------------------------------

I have no clue what the modline numbers mean, but I get a boatload of resolutions to choose from.  This works on Linux Mint 4 XFCE (Gutsy-based).  The XFCE resolution tool doesn't seem to rewrite the xorg.conf file so no problems there.  This is probably a Gnome tool issue.

---

### Post by penman242 on 2007-12-30
Thank you ncgater!  Your suggestion fixed my problem on a GX280 with the intel 82915G/GV/910GL Integrated Graphics Controller.  I have a custom e17 system I set up using the gutsy mini-iso and I could not get  my desired screen resolution (1280x1024) either from within e17 or by modifying xorg.conf.  Now everything works perfectly.  

As to your fears about it being stable, I think it is.  Just don't do System -> Administration -> Screens and Graphics.  In my case, I sure won't do Configuration -> Configuration Panel -> Screen -> Screen Resolution.  I have rebooted several times and restarted X several times with no sign of instability.

Thanks again.

---

### Post by ncgater on 2008-01-01
You are very welcome penman. It's good when we can help each other.:-)

Unfortunately I replaced my Ubuntu install with Fedora 8. Ubuntu was just not going to give me what I needed on this system. It is interesting that I ran into the same problem with the Fedora install but I guess not so surprising. 

FWIW, I fixed it pretty much the same way.

David

---

### Post by nofal on 2008-02-25
> **tompickles said:**
> Hi all,

Just bought a re-furbished pc (Dell) from the office. Though, it has Win 2k installed, which is just a tad unstable. Its a Pentium 4, 512 MB RAM, and from the Windows Device Manager, an Intel(R) 82865G Graphics Controller. When i tried to boot the Ubuntu CD, i selected 'Start or install' and was then presented with a Black Screen for 5 minutes before I rebooted back into Windows.


Any ideas?!

Thanks

100                                               100

---

