---
title: "N00b intro thread"
date: 2008-02-08
forum: Absolute Beginner Talk
---

### Post by Ben_T_B on 2008-02-08
Hi guys, I thought I best introduce myself seeing as I will probably be posting a lot of questions on here.

I've been playing with Linux on and off for a few years; I'd install it and then get rid of it after a while because it wouldn't do what I wanted it to. I finally installed Ubuntu and bought myself Linux for Dummies and I'm determined to make it work this time.

As all newbie intro's go, I already have some questions for you, most knowledgeable users of Linux (bit of flattery there):

1. I have a pretty standard PC yet in the Add/Remove section it says that most of the apps cannot be installed on my PC. Even the NVIDIA drivers which I find a little distressing when I have one of their cards. Anyone know why?

2. I'm dual booting with Windows currently. Is there away of getting rid of Windows and re-sizing the disc so that Linux is using it all?

3. Has anyone ever used Sonicstage in Linux?

I really appreciate any help you can give and look forward to the new world of Linux.

---

### Post by jhenager on 2008-02-08
I'll take Question 2.
Get GPartEd.
Gnu Partition Editor.
Just be careful, because when you remove a partition, that data is gone.

---

### Post by Ben_T_B on 2008-02-08
Thanks jhenager, I actually didn't want Windows to remain when I installed Ubuntu as this is my test PC before I release Linux in the wild

---

### Post by nynoah on 2008-02-08
for question #1, you need to be more specific about the hardware you are talking about.  Why is it not supported?  It makes me wonder what it is?  Could be old, could be new?  Tell us more.

and for #3 never heard of the program.

---

### Post by Sidewinder1 on 2008-02-08
Welcome Ben_T_B !!!!
I'm not sure that I understand question 1. Please list the specifications of your pc.
2. Yes you can certainly resize your partitions if you wish to eliminate Windoze; but I wouldn't even think of that just yet. It's always nice to have another os to boot to in the event of a problem, even with a live CD.
3. Never used Sonicstage

---

### Post by Ben_T_B on 2008-02-08
It's an AMD Duron (I think) 2.4ghz processor with just over a gig of SDRAM. The graphics card is a Geforce 6600.

SonicStage is the software for Sony MP3 players. Load of crap but you HAVE to use it ;(

---

### Post by Jon Monreal on 2008-02-08
For question #3, I looked into the WINE (a Windows Emulator for Linux) Application Database, and I found this: [http://appdb.winehq.org/appview.php?iAppId=1701&sRating=Bronze](http://appdb.winehq.org/appview.php?iAppId=1701&sRating=Bronze)

It appears that people have not had much success with installing Sonicstage.

As for question #1, I'm not exactly sure what your problem is. Could you tell us more?

Hope this helps you.

---

### Post by kostkon on 2008-02-08
> **Ben_T_B said:**
> 1. I have a pretty standard PC yet in the Add/Remove section it says that most of the apps cannot be installed on my PC. Even the NVIDIA drivers which I find a little distressing when I have one of their cards. Anyone know why?
Could you please be more specific. It would be better if you could paste here the exact message that Add/Remove gives you.
> **Ben_T_B said:**
> 3. Has anyone ever used Sonicstage in Linux?
I don't think you will be able to make it to work with Wine. Although, I think there is a program for Linux that will allow you to transfer music to your Sony mp3 player. A good idea would be to search the forum here. What model do you have?

---

### Post by Ben_T_B on 2008-02-08
Thanks Jon, I suspected that might be the case. I'll probably end up using some kind of Virtual Machine for my music. Do they have a VMWare for Linux?

Here's the message I get when clicking on the NVIDID Driver:

Canonical Ltd. provides technical support and security updates for NVidia binary X.Org driver
NVidia binary X.Org driver cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

---

### Post by Ben_T_B on 2008-02-08
It's the E-Series:

[IMG]http://www.cnet.co.uk/i/c/blg/cat/digitalmusic/handson_sony_eseries_crave.jpg[/IMG]

---

### Post by nynoah on 2008-02-08
it should work with your PC (question #1)  does it say that you need to down load some other program from synaptic to get it to work.  I know for me, there was something (can't remember specifically all) about downloading package.  1.2.22-12 rt (something) in order to get my nvidia drivers to work.

---

### Post by Jon Monreal on 2008-02-08
> **Ben_T_B said:**
> Thanks Jon, I suspected that might be the case. I'll probably end up using some kind of Virtual Machine for my music. Do they have a VMWare for Linux?

Here's the message I get when clicking on the NVIDID Driver:

Canonical Ltd. provides technical support and security updates for NVidia binary X.Org driver
NVidia binary X.Org driver cannot be installed on your computer type (i386). Either the application requires special hardware features or the vendor decided to not support your computer type.

You should be able to use VMWare, QEMU, Virtualbox or something of the sort to run Windows XP. I use both Virtualbox and QEMU personally.

It may be that no driver exists for your video card. It may also be that you might have to manually download a driver. It would help if you could post what video card you have. If you need help finding this information, feel free to ask.

---

### Post by forrestcupp on 2008-02-08
What version of Ubuntu did you install?  It almost sounds like you installed a version that uses an old i386 kernel rather than the newer generic kernel.  Maybe you see if you can install the latest generic kernel if that is the problem.  Search for linux-generic in Synaptic, and if it's not installed, install it.  Maybe that will help.

If not, try using [Envy](http://albertomilone.com/nvidia_scripts1.html) to install your nvidia drivers.  It automatically installs the very latest drivers for you.  Maybe that will work.

---

### Post by Ben_T_B on 2008-02-08
I appreciate all the help so far. It appears to be some kind of crappy OEM card. The box reads:

Sparkle 256MB DDR2 6200 High Performance 3D VGA Accelerator

---

### Post by klemens on 2008-02-08
might be an older version of ubuntu, while gutsy should install it without any probs

---

### Post by Ben_T_B on 2008-02-08
I only downloaded it yesterday. 7.10 Gutsy Gibbon I believe

Now it won't let me change the resolution after restarting. Starting to suspect the Graphics Card doesn't like Linux very much

---

### Post by lswest on 2008-02-08
could you post the output of ```
lspci
``` (run it in the terminal)?

---

### Post by Ben_T_B on 2008-02-08
01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)

---

### Post by klemens on 2008-02-08
envy seems like a good thing to try, for new people.

i got the newest drivers from nvidia site and installed those, wasn't really though but might be hard for someone new to linux

---

### Post by lswest on 2008-02-08
yeah, envy might actually be good to try (i just used it this afternoon to install ATI drivers for my RADEON 9600SE) and it seems to work better than it used to.

---

### Post by Ben_T_B on 2008-02-08
Ok, sorry to sound like a dullard but what's envy?

---

### Post by nynoah on 2008-02-08
There are never dumb questions when you are trying to learn.  Everyone had to learn everything for the first time, at some point.

Envy is an ouside of the normal distros release that compiles/installs video card plugins.  I personally do not like Envy.  It has never worked for me correctly.  When you tried to install your Nvidia plugin, did it ask you to install anything else?  Also, turn off your restricted drivers for now and revert back to the basic ones.  Then try to reinstall them.  Does it then ask you to download another dependency from snyaptic?

---

### Post by Ben_T_B on 2008-02-08
The saga goes on...

I managed to download the NVIDIA Drivers and kill X as they requested (This took an hour btw!") but when they try to install it gives me a message saying that it needs to compile a Kernel interface but then errors saying i need to install some Libc development stuff???

---

### Post by Ben_T_B on 2008-02-08
Ok, found the restricted drivers and they're not on. Tried to turn them on and it says:

"The software source for the package nvidia-glx-new is not enabled"

---

### Post by nynoah on 2008-02-08
remember what it asked you to install and go to synaptic package manager and search for those in there.   *System/administration/snyaptic package manager*

---

### Post by nynoah on 2008-02-08
Ben your problem might be that you do not have all the repositories you need enabled.   Example go to*** System/administration/software sources***.  Open that and see if you have (main), (restricted), (multiverse) and (universe) checked off  after that is changed, hit reload to update your packages.
 
Also  I have these repositories in my computer too.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

---

### Post by Ben_T_B on 2008-02-08
I try to run Envy and it says:

Error: Dependency is not satisfiable: xserver-xorg-dev

Frustrating but fun

---

### Post by Ben_T_B on 2008-02-08
> **nynoah said:**
> Ben your problem might be that you do not have all the repositories you need enabled.   Example go to*** System/administration/software sources***.  Open that and see if you have (main), (restricted), (multiverse) and (universe) checked off  after that is changed, hit reload to update your packages.
 
Also  I have these repositories in my computer too.

[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

That has at least got me to the installing stage of Envy.

I'd be quite happy tinkering with this all night but I've got to fly out to the states tomorrow morning for work.

I really appreciate all your help mate and I'm sure I'll be back on here very soon.

Take care

---

### Post by Jon Monreal on 2008-02-08
> **Ben_T_B said:**
> That has at least got me to the installing stage of Envy.

I'd be quite happy tinkering with this all night but I've got to fly out to the states tomorrow morning for work.

I really appreciate all your help mate and I'm sure I'll be back on here very soon.

Take care

Feel free to send me a PM when you get back for help. Also, remember that you can still come back and start a new thread asking for help or bookmark this one.

Using Linux for the first time can be frustrating. But I have found that once you get used to it, Ubuntu is incredibly easy to use.

I hope that one way or another your problem gets resolved.

---

### Post by Ben_T_B on 2008-02-11
Thanks Jon. After installing and running Envy it would appear that my Graphics Card was working. Sadly I was just getting into tinkering with Linux when I had to leave for work but I'll be back on it soon.

Appreciate your help mate and here's to me not going crawling back to Windows again

---

### Post by ubuntu-freak on 2008-02-11
If anyone else needs info on Envy, try [this sticky](http://ubuntuforums.org/showthread.php?t=301499).
 
The restricted-extras package doesn't install everything you may need. Check out my own newbie friendly [how-to](http://ubuntuforums.org/showthread.php?t=661833). All you have to do is cut & paste really.
 
Nathan

---

