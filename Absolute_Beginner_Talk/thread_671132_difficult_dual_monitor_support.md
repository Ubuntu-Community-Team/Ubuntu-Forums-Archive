---
title: "difficult dual monitor support?"
date: 2008-01-18
forum: Absolute Beginner Talk
---

### Post by KezzerDrix on 2008-01-18
wow, this is the first thing I not seen ubuntu 7.10 pick up and run with, I have an IBM t61 laptop mounted to a dock with one dvi and one vga port on the back of it.  On XP I connected one monitor to each port and blamo I had dual monitor support.  I did a search but did not find anything like my setup.  Most were ATI issues, well this laptop has an INTEL graphics card.  When I click on screen and graphics in the system directory.  I get this driver info INTEL - Experimental modesetting driver, on the screen tab the second monitor tab is greyed out and alas my monitor is black. 

Help please, I really need dual monitor support, and I kind of have a lot of people looking at me as I am the only person using Linux in the company.  I told them that I had used it in the past and they want to see it up and running.  So I kind of need to make it "show" good.

Please help

Kezz

ps. it will also not allow me to turn up the Eyecandy. :(

---

### Post by KezzerDrix on 2008-01-18
hmm, no answers, probably shouldn't have asked at 6am :)

---

### Post by KezzerDrix on 2008-01-21
Graphics: Intel GMA X3100 is this chipset supported, I am having lots of problems, no 3d, no compiz, no dual monitors.  EtC

Do I need to download a prop driver or something?

Kezz

---

### Post by Golem XIV on 2008-01-21
Yeah, I'm in the same boat with a Dell Vostro 1400.

[Here]("http://www.thinkwiki.org/wiki/Installing_Ubuntu_7.10_(Gutsy_Gibbon)_on_a_ThinkPad_T61#Introduction") are some instructions on the setup for your Thinkpad. 

You can enable compiz using [this information]("http://linux.dell.com/wiki/index.php/Ubuntu_7.10/Issues/Compiz_Fusion_965GM_Incompatibility") (it's for my Dell, but it should work on any i965/X3100 system), but this will kill your video playback.  You can work around the video playback problem by opening the Multimedia Systems Selector (if it's not in the System->Preferences menu either enable it first by right-clicking on the start menu and selecting "Edit Menus", find the entry under Preferences and enable it or type "gstreamer-properties" in a terminal) and select the Video tab and under Default Output select "X Window System (NoXV)".  this will give you movie playing capabilities but performance will be lower.  Also, Skype Beta video (and other XV dependent stuff) will NOT work.

Let's hope Intel releases a fixed driver for this chipset soon.

---

### Post by KezzerDrix on 2008-01-21
I have an ibm t61 with intel x3100 graphics, which I can not get to work.  No 3d, no dual monitors, no compiz, etc, etc, etc.

I have an ibm t60 with ati x1300, does it have better support?

---

### Post by Thingymebob on 2008-01-21
I have an acer with a mobility x1300 inside. Proprietry ATI drivers install fine using [Envy]("http://albertomilone.com/nvidia_scripts1.html") compiz, dual monitors all work

---

### Post by KezzerDrix on 2008-01-21
OK, I have figured out that dual monitors works for me just not the two monitors that I want it to use.

I have 2 dell 1908fp attached to a docking station for my t61, no matter what I do, Ubuntu wants to use the laptop monitor and one of the dell's.

What I want is for it to use the two dells attached to the docking station.  I have one attached to the dvi and one attached to the vga.  

the video card is integrated 965gm chipset

Please help.

Kezz

---

### Post by KezzerDrix on 2008-01-22
I cannot get dual monitors working.  This seems as though it should be an easy issue.  

I tried an ibm t61 with an intel 965 integrated graphics card.  I messed with it for days, I then decided to downgrade to an IBM t60 with ati x1300.  I installed ENVY and installed the graphics drivers.   Everything works except this dual monitor issue.

I do have dual monitors but not the two that I want.  I have two 19" monitors attached to my docking station, one to the vga port and one to the dvi port, and it is using the dvi port and the laptop screen. 

The annoying thing is that it sees my two 19" because when I boot it starts on one and then when I log in it switches to the other 19" and the laptop screen, and yes the laptop lid is closed the entire time.



HELP please

---

### Post by spiderbatdad on 2008-01-22
displayconf-gtk might be for you...in synaptic, installs under system>>administration>>screens and graphics

---

### Post by KezzerDrix on 2008-01-22
Yes, I know of that, the problem is that it shows one external monitor and one laptop monitor.  This works, the problem is that I have two external monitors, and want to use those.  

I can not get it to use my two external 19" monitors it wants to use, 1 external monitor and the laptop screen that is 14" 

Please help

---

### Post by smurphy_it on 2008-01-22
Sounds like you haven't exported your video off of the laptop screen to the external monitor.  Usually on laptops this is done with a function key combination.  Most laptops is Fn + F4, or Fn + F8.  First time you press it, it should be the laptop screen, 2nd time it is the external monitor, third time is both laptop screen and external screen.  This process keeps looping BTW.

Usually the Function Key it is will have an icon of a display screen on it.  Could be F3, F4, F5, F8 etc...

Give that a shot.

---

### Post by KezzerDrix on 2008-01-22
Hello,

I have an IBM t60 laptop with a radeon x1300 video card.  This laptop is attached to a docking station, the docking station has a dvi port and a vga port on the back on it.  On the dvi port I have an external monitor attached a dell fp1908(digital) and on the vga port I have an external monitor attached a dell fp1908(analog). I cannot get Ubuntu to use the two 19" monitors, it wants to use the 14" laptop monitor and one of the 19" monitors.  The 19" monitor that it chooses it assigns some kind of wacky scrollable resolution.  Basically making it unusable.   I have been trying to rectify the situation for days.  

I would like to have both 19" monitors working.  I could survive with the laptop and one functional external monitor.

I have installed all updates, and installed envy to correctly configure the ati x1300.

PLEASE help

---

### Post by sandr- on 2008-01-22
Maybe you should look up about xrandr. I use that command to switch between my notebook and my external monitor on my laptop !

Here is the link to the tutorial I used: [http://www.thinkwiki.org/wiki/Xorg_RandR_1.2](http://www.thinkwiki.org/wiki/Xorg_RandR_1.2) , I hope it helps. I am no expert in this matter, but this gets my job done, hopefully yours too.

---

### Post by smurphy_it on 2008-01-23
For this setup sounds like you need to modify the xorg.conf file and add an option for adding the dvi support.

Don't know how to do this off hand, but should be some tutorials on this.

---

### Post by KezzerDrix on 2008-01-23
having trouble finding anything on it.  The strange thing is that the laptop with the lid closed, boots off the vga then once booted switches to the to secondary dvi and resumes use of the laptop monitor.  

The second problem is that it makes the secondary monitor some wacky resolution that is scrollable and huge.

---

### Post by bwtranch on 2008-01-23
Did you try the OEM website? Believe it or not some have great support for their products now.

---

### Post by KezzerDrix on 2008-01-24
thank you all for your assistance, I wound up reinstalling and now it works.  That is like the 5th time I reinstalled.  I about kissed the computer when it worked :)

---

### Post by caligari2k on 2008-06-06
Now that you have your Dual Monitor working, I have few questions and requests.

1.  are you still using a T60 or T61?

2.  Is this an Intel Graphics systems?

3.  do you think you can post a copy of your xorg.conf file for us to see.  

I fought with a new T61 for several hours and went back to my T43/ati system.  I could never get dual monitors work (both external).  And when I tried to use the intel driver at anytime, the system wouldn't even let me log on graphically.  It complained about a pam_smb module missing.  Don't ask me why, I have no idea.  But that is what it said.  This is 8.04 BTW.  With the number of updates I have seen every day, perhaps I should go back to 7.10?

---

