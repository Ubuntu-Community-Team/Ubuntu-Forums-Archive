---
title: "Xserver issues with Ubuntu Studio - very frustrated"
date: 2007-07-03
forum: Absolute Beginner Talk
---

### Post by Alex Madsen on 2007-07-03
I don't know what exactly happened, but when I tried to update to Ubuntu Studio (I had Ubuntu Feisty 7.0.4 and loved it) now I can't get my damn Acer Aspire 5570Z to work.

I get the dreaded "screen not found"  xserver warning.

I've tried literally for three days to get Ubuntu Studio to work on my system, to no avail. 

As far as I can tell (Acer's website is useless) I have an Nvidia card. 

Now I'm stuck with a laptop that's goin' nowhere fast.

I've tried adding that "nvidia" to the list of stuff but as a noobie, I'm very, VERY confused by the technical-speak that's used on the forums here.

I guess all I can do here is humbly ask for some help ... step by step...in the simplest, layman's terms you guys can muster. 

I really, REALLY don't want to use windows again, so if anyone can help, god bless!

---

### Post by Alex Madsen on 2007-07-03
Darn - I hope *someone* out there can help!

---

### Post by Alex Madsen on 2007-07-03
I believe there are quite a few "newbies" out there who, like I have, went from traditional Ubuntu 7.0.4 to Ubuntu Studio and have had the same problem - just regular guys who would really like to do recording work on laptops but would really, REALLY like to stick it to microsoft and Pro Tools -- both NOTORIOUS for constantly trying to pilfer your pockets with update after useless and costly update.

So please...help us laptop recording guys out!

---

### Post by Alex Madsen on 2007-07-03
Sorry guys - I just gotta keep bumping this because I know there's a bunch of us out there who could really use a step-by-step to fix the xserver problem.

Any other Acer laptop users with this issue?

---

### Post by vexorian on 2007-07-03
12 hours is not really that much time...

However, I guess you can boot from live-cd, save your files somewhere and then do a clean ubuntu studio install. Upgrades of this kind sometimes fail... 

But I am not sure why you had to upgrade to studio, why not just get the packages for the tools studio uses? I got synaptic to download inkscape and agave...

---

### Post by Alex Madsen on 2007-07-03
Well, I'm a total idjit when it comes to this stuff, so I'm not surprised at all that I managed to find the wrong way to do it, heheh.

Could you walk me through the "live cd" process? I'm really THAT bad at this...but I want to learn the wonderful world of linux. You guys really have the right idea and I'd really like to walk away from microsoft for good!

---

### Post by Alex Madsen on 2007-07-03
Thanks for the reply - I think I understand what to do now; basically, I'm going to reinstall ubuntu feisty 7.0.4 and add ubuntu studio stuff after the fact. Could you give me a basic rundown on how to do that?

---

### Post by franck3d on 2007-07-03
Why not do a full install of ubuntu studio?

although you may find that your x problem follows you.
but nvidia usually plays nice with ubuntu.

I have found that dist upgrades are more trouble than they are worth.
If you keep your personal files on a seperate hard drive or partition, then a clean install is not so frightening.

good luck!

---

### Post by ellgor on 2007-07-04
Hi,

If you are still having problems then you might want to check out a program called envy (just google envy) it is a program by an italian guy in conjunction with Nvidia to make easy access in setting up your scren etc, hope this helps.

Regards, Ellgor.

---

### Post by Alex Madsen on 2007-09-09
Hi Guys,

Well, I'm back to running Ubuntu's Fiesty version, but I'm gonna give another shot at dropping Ubuntu Studio on a partition. I've figured out a bit more since last time, so I'm hoping for the best!

---

### Post by urangela on 2007-09-11
I think that (I am hoping) that it is a configuration issue. I am also using an acer : aspire 5570z, I have cut it into 2 70 gig main partitions, with 1 gig of swap. I have the same problem, the installation runs fine, but when I try to boot, Xserver crashes. I know that according to acer's site; the 5570 series comes with an nvidia Geforce Go 7300 However I don't think that this is the case with the _5570z_. The only display hardware that I can see listed is " Mobile Intel(R) 945GM Express Chipset Family " 
The first error message I recieved was "fatal error, caught signal 11". 
I tried to fix it using dpkg-reconfigure Xserver-xorg . I then tried to start the Xserver again and recieved this error mesage:
Fatal error no screens detected

Any and all assitance and advice is greatly appreciated; This is my first time with linux, and I am not going to quit until I have ubuntustudio running on this machine!!!!!! 

PS If the Xserver log file would be helpfull, I can try to post it.

---

### Post by simon303 on 2007-09-11
I recently booted my computer to find Xserver wouldn't start. So I pressed Ctrl+Alt+F1 to get to a command line where I logged in and did some searching in manual pages, etc. In xorg.conf I found a command to automatically update xorg.conf
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
it asks acouple of questions like card make and prefered resolutions. When it was finished I rebooted and Xserver worked fine.
I have also found the following usefull for upgrading Ubuntu Feisty Fawn to Ubuntu Studio
[https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromFeisty")
I just downloaded the script at the bottom and ran it in the install I wanted to upgrade to studio (important: right click on the script and go to properties-->permissions and make sure the check box with "Allow executing file as program" before running the script in a terminal)
Hope this helps

---

### Post by urangela on 2007-09-11
Thank you simon for the dpkg hint, It was the key to this mess!!!!
Ok, this is actually simple to fix, First off I would like to clarify that the acer aspire 5570z does NOT have an Nvidia card, but the Intel Graphics Media Accelerator 950, thus it needs the intel driver.
 
To fix this problem I took the following steps:
1 selected the low latency recovery mode kernel from the Grub loader
2 Ran the code that simon posted above from the shell: 

sudo dpkg-reconfigure -phigh xserver-xorg.

This loads a text based configuration program for the Xserver.
The first dialog box that comes up asks you which driver to use, Select i810 from the list.
The next dialog box asks you what resolutions you would like to use. I selected everything from the bottom three up to 1280 X 1024. I then rebooted, into ubuntustudio, and the GUI has loaded perfectly. I am actually posting this from studio right now.

---

### Post by simon303 on 2007-09-12
It's nice to know I helped someone, I hope this thread will be just as usefull to others

---

