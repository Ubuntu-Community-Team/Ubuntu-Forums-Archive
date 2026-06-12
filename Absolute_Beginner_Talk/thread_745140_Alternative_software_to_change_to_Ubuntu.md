---
title: "Alternative software to change to Ubuntu"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by eagle6 on 2008-04-04
I'm seriously looking at changing from Windows.
My obvious options are Mac or Linux. With Mac it's a straightforward system swap. With Linux it's a complete change for me and I've no experience whatsoever.

For Linux to be viable I need alternatives to 2 pieces of software, Dreamweaver and Fireworks. Not some homebrew alternatives, but real functionally similar alternatives. The rest of my software/utilities requirements are not rigid so I'll play around and find my own alternatives.

So what's out there?

TIA

---

### Post by piousp on 2008-04-04
You can try to run Dreamweaver and Fireworks under linux using wine.

---

### Post by DGortze380 on 2008-04-04
Not familiar with Dreamweaver and Fireworks, but I do have some general solutions for you.

You can burn a live CD and try Ubuntu that way (you can do most things on a live CD that you can on a full install).  Or you can run a virtual machine on a 30 day trial of VMware to try out Ubuntu.  Once you decide it's right for you (and you will if you give yourself enough time to learn about it), you can either install it for a single boot; or if you don't find alternatives for those programs, you can dual boot Ubuntu with either OS X or Windows.

---

### Post by eagle6 on 2008-04-04
> **piousp said:**
> You can try to run Dreamweaver and Fireworks under linux using wine.

This is why I'm dubious about changing to Linux. I'm not a "geek". If I want to edit an image I want to open a program and edit.
I don't want to have to try and run a program on some sort of emulator.

I was warned that moving to Linux was not easy for "normal users" but I'm prepared to give it a try.

---

### Post by linuxlizard on 2008-04-04
strictly speaking, wine isn't an emulator, but it does take a little effort to set it up. Once set up, if your programs are compatible (and I don't know- you might google wine dreamweaver and wine fireworks and find out) then they run in linux, not on an emulator but you click and run like anything else (sort of- that's the hype anyway).

If you are bound to a program like dreamweaver and are unwilling or unable to try an alternative (kompozer?), linux probably isn't a good fit for you. Use whatever OS the programs you must have run on and do us all a favor and e-mail a complaint to the company for not providing a linux version.

---

### Post by eagle6 on 2008-04-04
> **linuxlizard said:**
> 

If you are bound to a program .......

No, I'm not bound to these programs, but would need something comparable. I'm looking for alternatives as the title says. I appreciate that I can't run the ones I'm currently using.
What are people using for web design/image manipulation on Linux?

---

### Post by OrneryGuy on 2008-04-04
You could go here Eagle, they tell you how to install Dreamweaver with wine.
[http://ubuntuforums.org/showthread.php?t=200305]("http://ubuntuforums.org/showthread.php?t=200305")

---

### Post by Mauler5858 on 2008-04-04
Fireworks will run fairly well in wine.  It recieves a gold rating from the app database.  Setting up wine is very simple.
1. Go to the Synaptic package manager (Administration>Synaptic Package Manager).
2. Search for and install wine.
3. Go to a terminal.(Alt+F2) and type in winecfg.
4. Then google how to install fireworks using wine (usually gives some very easy to follow tweaks).

Dreamweaver would run not so well:
Check this site for alternatives. [http://www.osalt.com/dreamweaver](http://www.osalt.com/dreamweaver)

also [www.linuxalt.com](www.linuxalt.com) gives some very good lists of Open Source replacements for commercial products.

---

### Post by bumanie on 2008-04-04
Have a look at this site. There are direct software comparisons/alternatives available in linux.
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

---

### Post by eagle6 on 2008-04-04
Thanks "Orneryguy", but I really don't want to get involved in any command line stuff.

I think I must ask you all the deal breaker question.

Is Linux a viable desktop system for the average user?
I class myself as above average purely on the fact that I've been using computers since the early '80's.

---

### Post by eagle6 on 2008-04-04
> **bumanie said:**
> Have a look at this site. There are direct software comparisons/alternatives available in linux.
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

Thanks, very good link!

---

### Post by piousp on 2008-04-04
> **eagle6 said:**
> This is why I'm dubious about changing to Linux. I'm not a "geek". If I want to edit an image I want to open a program and edit.
I don't want to have to try and run a program on some sort of emulator.

I was warned that moving to Linux was not easy for "normal users" but I'm prepared to give it a try.
Sometimes we geeks forget how to comunicate with people :lolflag:
By "normal users" you mean "people used to windows" ??

Anyways, I found this options for you,
For Dreamweaver:
Quanta Plus
Nvu
bluefish
Amaya

For Fireworks:
The Gimp

Alright, now, how can you try them out before moving out of windows?
Some steps to make life easy for you ;) :

1. [Install VirtualBox]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI")

2. If you have never used a virtual machine, ask here for some help.

3. Install Ubuntu in the virtual machine (it runs under windows, so dont worry about anything).

4. Once you hae Ubuntu, under the "Applications menu", select Add/Remove Programs"

5. Search for all those apps, and try them out!!!

---

### Post by linuxlizard on 2008-04-04
> I think I must ask you all the deal breaker question.

Is Linux a viable desktop system for the average user?
I class myself as above average purely on the fact that I've been using computers since the early '80's.

Well, It depends. My parents are in their 70s and have used ubuntu for a few years now and never used a computer until they were in their 60s. I had to set it up for them, but after that they have had no problems actually using the machine. I would have had to install windows for them too, and with windows they were constantly on the phone with me with fear in their voices asking questions or needing help (usually the printer or wondering if they should click to update windows and stuff).

I've been using computers about the same time as you. But really, it depends on what you want to do and if you expect it to be exactly like windows. 

Command line isn't to be feared by someone using as long as you have- just take your mind back to msdos days, no difference.

I'm a "normal" user myself- command line can be limited to simply cutting and pasting commands from here to your terminal and hitting return and letting the computer do it's thing without worrying much about what it's doing. Once stuff is set up, you can just point and click day to day and never go into the command line unless you are doing something very special, like installing dreamweaver with wine for example. Actually running it can be done from the desktop once set up.

I do a little web work myself- check out kompozer. It's probably the best of the what you see is what you get editors. Then bluefish if you do a lot of hand coding. Graphics, look into the gimp.

That will get you started anyway, the links others gave are excellent.

---

### Post by eagle6 on 2008-04-04
> **piousp said:**
> 
By "normal users" you mean "people used to windows" ??

Love it or hate it, it represents 90%+ of desktop users.

The frightening fact is that I'm just into my 60th year and of those I've been a Windows user for 21 years!

---

### Post by piousp on 2008-04-04
Again, "is linux for the average users?" is kinda hard to say.
I'll asume that for "average user" you mean "people used to windows".

> **eagle6 said:**
> Love it or hate it, it represents 90%+ of desktop users.

The frightening fact is that I'm just into my 60th year and of those I've been a Windows user for 21 years!
I dont want to sound rude, but its for adjusting my mental image of what your are referring to "average user".
Same goes to a all-time-mac-os guy. His "average user" will be someone used to mac os.

In that case, they'll have a more-less hard time moving to another OS (windows, mac os, linux, unix or any other )

In this case, Ubuntu is very good for "average users" if everything works out-of-the box with your hardware. If it does, you'll have a system so incredible easy to use, that you'll wonder why you didn't change before.

If it doesn't, expect to use the command line.

So, that means linux is harder? Not at all. The problem lies in the huge ammount of hardware that exist out there, which by default, DON'T support linux, and then we have to somehow make it work.

So, again, my advice, try the virtual machine solution i posted so you can try out the apps.
If you are happy with the apps, just burn the .iso onto the cd and use it on your "real" computer. The wonderful thing of a live-cd, its that you can try them out, before "touching" your hard drive.

---

### Post by linuxlizard on 2008-04-04
On further thought- if you find gimp and kompozer or the other linux alternatives work fine for you, you would probably never need to do anything in the command line. And installing these and thousands of other apps is much simpler than in windows- you just go to applications, add/remove programs and then select them and they are downloaded and automatically installed and ready to go for you. In many ways, linux is much simpler to operate now than windows. And usually to install as well.

---

### Post by eagle6 on 2008-04-04
One last question.
How do I get my photo files, etc., from Windows to Ubuntu? Currently all stored on a USB remote 500Gb HD.

---

### Post by NR1224 on 2008-04-04
yes, it is an alternative for the avg. user. But, if you want to do anything complicated, be warned it is very different from windows. Not harder, just VERY different

---

### Post by NR1224 on 2008-04-04
oh, linux can probably read your hard drive as well, minimal or no set upo required

---

### Post by PantsMan on 2008-04-04
> **piousp said:**
> You can try to run Dreamweaver and Fireworks under linux using wine.

On similar lines, you could always continue to run Dreamweaver and Fireworks, only in a virtual machine session... personally, I'm really liking VirtualBox OSE to let me run Zend Studio in a 32-bit VM on my X64 laptop (even though running Ubuntu inside Ubuntu is mad... Oh, Zend, when will you make ZDE natively support X64?) It's even happy to mount my htdocs folder so I can directly work against my development Zend Core installation in X64 Heron without having to faff around with FTPing things from one bit of the file system to another.

As long as you have a recent processor, you will also benefit from hardware virtualization support as well. Worth a think, surely...

---

### Post by piousp on 2008-04-04
> **eagle6 said:**
> One last question.
How do I get my photo files, etc., from Windows to Ubuntu? Currently all stored on a USB remote 500Gb HD.

I have an external USB hard dirve (250 GB). I just have to connect it and thats it. I just then click on the icon it generates on my desktop.
:KS

---

### Post by eagle6 on 2008-04-04
> **PantsMan said:**
> On similar lines, you could always continue to run Dreamweaver and Fireworks, only in a virtual machine session... personally, I'm really liking VirtualBox OSE to let me run Zend Studio in a 32-bit VM on my X64 laptop (even though running Ubuntu inside Ubuntu is mad... Oh, Zend, when will you make ZDE natively support X64?) It's even happy to mount my htdocs folder so I can directly work against my development Zend Core installation in X64 Heron without having to faff around with FTPing things from one bit of the file system to another.

I'll respond later when my universal geek translator comes back online! :lolflag:

---

### Post by hyper_ch on 2008-04-04
for virtualization you should not have a too old machine.... loading a clean win xp into it and then running only necessary applications will impact your overal performance not all too much. That might be a viable alternative for you.

---

### Post by piousp on 2008-04-04
So, after all this geeky rambling, eagle6, what are you gonna do?

---

### Post by eagle6 on 2008-04-04
> **piousp said:**
> So, after all this geeky rambling, eagle6, what are you gonna do?

I'm an impetuous old git! so I'll probably just archive off anything of importance, download Ubuntu, do the install, and worry about the consequences later.

Oh, and in a couple of days I'll have to RTFM

Thanks to all for the assistance.
You seem to have the basis of a good system here, but just remember that when talking to the "Jack O'Neils" of this world (like me), some of you shoot yourselves in the foot with your abundance of knowledge and can frighten people away. You need to "dumb down" a little.

---

### Post by The Titan on 2008-04-04
> **piousp said:**
> Sometimes we geeks forget how to comunicate with people :lolflag:
By "normal users" you mean "people used to windows" ??

Anyways, I found this options for you,
For Dreamweaver:
Quanta Plus
Nvu
bluefish
Amaya

For Fireworks:
The Gimp

Alright, now, how can you try them out before moving out of windows?
Some steps to make life easy for you ;) :

1. [Install VirtualBox]("https://cds.sun.com/is-bin/INTERSHOP.enfinity/WFS/CDS-CDS_SMI-Site/en_US/-/USD/ViewProductDetail-Start?ProductRef=innotek-1.5.6-G-F@CDS-CDS_SMI")

2. If you have never used a virtual machine, ask here for some help.

3. Install Ubuntu in the virtual machine (it runs under windows, so dont worry about anything).

4. Once you hae Ubuntu, under the "Applications menu", select Add/Remove Programs"

5. Search for all those apps, and try them out!!!
I think quanta is better than dreamweaver but the gimp replacing fireworks.. thats a stretch, i haven't found anything to replace fireworks for me =/

---

### Post by Gommo on 2008-04-04
Hi Eagle

I was in the same situation as you I wanted to change to Ubuntu but was worried about programs I rely on in Windows- Itunes etc. In the space of a few days and the help of the internet I had everything I needed in ubuntu set up and will never go back to Windows (my main problems were getting wireless internet to work and installing morrowind).

I installed ubuntu on a seperate partition and dual booted with windows for a few days to try it out and then removed windows. I have used Ubuntu for about three months and can't believe I didn't switch sooner. I do think Ubuntu is a viable alternative to windows for the average user and it seems to get better and better unlike windows. I have been using PC's since my ZX81 in the early 80's, but wouldn't say I was particularly savvy particularly when it comes to non-windows environments.
For an above average computer user it would not take much to change - I don't think ubuntu is as steep a learning curve as it is often made out. I spent hours reading about how to install my printer in Linux and needn't have bothered as I just plugged it in 'duh' and it worked no need for driver installation as it did in XP. The only users who would have a major problem with linux, in my opinion, are people who use computers but know nothing about them and would probably get into difficulty in windows anyway.
If you don't want to use the Terminal/Command line then you don't have to. Installing wine (or any ubuntu program) and then installing a windows program can be done without using the command line quite easily (whether dreamweaver or fireworks will work or not I don't know). But you will find you will use the command line after a while as it is so easy to use to install and uninstall things.
I would recommend giving it a go.

---

### Post by eagle6 on 2008-04-04
@Gommo

iTunes was one program I'd completely fogotten about. Can you download and sync as with windows? I use my iPod mainly for podcasts BOL, TWIT, etc

---

### Post by Gommo on 2008-04-06
@eagle
I never use podcasts I just use my Ipod for my music. I have just discovered Amarok which seems to be able to do everything gtkpod does but looks way better. Apparently it can sync podcasts I am not sure about downloading them though.

---

