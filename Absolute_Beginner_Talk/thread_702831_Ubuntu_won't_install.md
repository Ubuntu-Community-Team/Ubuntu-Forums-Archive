---
title: "Ubuntu won't install?"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by nclester on 2008-02-20
Hey, it's my first post on these forums and it's a desperate one, so. I'll get right to the point. 

I am attempting to set up a dual-boot (xp pro sp3 and ubuntu) machine and am having trouble booting Ubuntu. 

I've installed and loaded up SP3 with no problems; installed the required graphics and audio drivers and now Windows works fine. I set aside 95GB of space on my 160GB drive for Windows. 

I then downloaded the Ubuntu 7.10 Live CD and burnt it to a disk then rebooted my PC. The PC boots from the Ubuntu disk and things seem to look good, I select to install Ubuntu the regular way. The first option. 

I get the Ubuntu logo and a orange sliding bar, then it jumps right into a CLI and freezes. 

[412.801924] --------------

That's the last line of code on my screen, and it doesn't move at all. I have to manually power down, which I hate to do, and then boot in XP. I don't understand what I could be doing wrong? I've been working on my own PC's for years, and consider myself to be pretty tech savvy... but I'm stumped. 

I burnt the disk a 4x, and verified it's contents. 

Can someone please give me a direction to head in? I'm not lazy, I'll read if it pertains to my topic. I've searched everywhere... It's just I really have no idea what to search for.

Thanks for any help!

Glad to be a member of the forum and hope to learn a ********!

---

### Post by jcitguy78 on 2008-02-20
there is a program called infra recorder on the ubuntu site that you can use to burn a clean copy of the ISO. 

[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by Het Irv on 2008-02-20
You can try that, but I don't think that is his problem.  The best way to test it is when the CD first starts up select Test CD for Defects.  

What are the specs on your computer.  You *might* have a hardware issue.

---

### Post by S15_88 on 2008-02-20
can you give us some specs of your machine?  what program did you use to burn the image? 

Thanks, Alain

---

### Post by nclester on 2008-02-20
jcitguy78, I downloaded a clean .iso directly from Ubuntu and had the same issue. 

Het Irv, I haven't tested the CD yet, at least not at the Ubuntu screen. 

I used PowerISO to burn the image and it worked fine, I always burn bootable .iso files with PowerISo, unless it's .uif... that's fit for MagicISO. 

The machine is about 3-4 years old, upgraded RAM and GPU and Sound about a year ago. My specs are as follows. 

Pentium 4 2.93GHz CPU / 1GB DDR2 / NVIDIA GeForce 6200 GPU / Creative SB Audigy 4 Sound Card / 160 GB HD / Windows XP Pro SP3 - fresh install

I snapped a few pics of the CLI I see with my iPhone and finally figured out how to get them from the phone to my computer. 

[[IMG]http://img213.imageshack.us/img213/8817/img0029yw8.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=img0029yw8.jpg)

Thanks again guys/gals!

*edit*
Sorry for imageshack non-sense, it was quick and easy. I'll upload next time!

---

### Post by jan quark on 2008-02-20
there is always the option to install via the alternate CD using the text mode
which is more stable than the live cd

here you can download it
[http://releases.ubuntu.com/gutsy/](http://releases.ubuntu.com/gutsy/)

and here is an excellent guide
[http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)

---

### Post by nclester on 2008-02-20
jan quark, I thought about that. I'm not a very proficient coder, meaning I want the GUI version of Ubuntu for that reason, it's GUI. Will that option still let Ubuntu run regularly? Is the alternate CD just another way to install the same package? 

Thanks for your reply!

---

### Post by nclester on 2008-02-20
Also, I'm beginning to think my GPU might have something to do with my problem.

---

### Post by supertails on 2008-02-20
> **nclester said:**
> jcitguy78, I downloaded a clean .iso directly from Ubuntu and had the same issue. 

Het Irv, I haven't tested the CD yet, at least not at the Ubuntu screen. 

I used PowerISO to burn the image and it worked fine, I always burn bootable .iso files with PowerISo, unless it's .uif... that's fit for MagicISO. 

The machine is about 3-4 years old, upgraded RAM and GPU and Sound about a year ago. My specs are as follows. 

Pentium 4 2.93GHz CPU / 1GB DDR2 / NVIDIA GeForce 6200 GPU / Creative SB Audigy 4 Sound Card / 160 GB HD / Windows XP Pro SP3 - fresh install

I snapped a few pics of the CLI I see with my iPhone and finally figured out how to get them from the phone to my computer. 

[[IMG]http://img213.imageshack.us/img213/8817/img0029yw8.th.jpg[/IMG]](http://img213.imageshack.us/my.php?image=img0029yw8.jpg)

Thanks again guys/gals!

*edit*
Sorry for imageshack non-sense, it was quick and easy. I'll upload next time!

Maybe it's best to buy it. That's what I did. Sometimes ISOs don't burn that well with Windows. I've never got it to work with windows but it's easy with Linux so buy it. It cost $13 on Amazon so it could be worth it.

---

### Post by jan quark on 2008-02-20
with the alternate cd you will install the same desktop environment as with the live cd

just read through the guide posted above

it is very similar to the graphical installation but without... the graphic

the steps are the same
do not worry it is not more difficult

---

### Post by spiderbatdad on 2008-02-20
it may be as simple as setting some parameters at the grub screen for how your hardware is polled.
Press f6 at the grub screen and delete the end of the kernel line up to and including ro --quiet splash.
type in noapic nolapic vga=771

---

### Post by jcitguy78 on 2008-02-20
> **supertails said:**
> Maybe it's best to buy it. That's what I did. Sometimes ISOs don't burn that well with Windows. I've never got it to work with windows but it's easy with Linux so buy it. It cost $13 on Amazon so it could be worth it.

I'm not sure what you are referring to as the cost of $13. Ubuntu is free???

---

### Post by nclester on 2008-02-20
supertails, I'm not sure what your talking about? Buy what? PowerISO? Waste of $13 dollars if you ask me, I've burned .iso's for years now on Windows. 

jan quark, thanks for the help. I'm going to go ahead and give the alternate CD route a try. I'll let you know how I make out. I appreciate the heads up!

---

### Post by nclester on 2008-02-20
spiderbatdad, I'm a Ubuntu and actually, a code noobie. At the GRUB screen I pressed F6 and then I got a command line like this. 

Boot Options  file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz quiet splash--

That's exactly what I see after pressing F6, and that's directly underneath the installation options. 

I have no idea what to delete or replace, even though you tried to show me. 

Could you write what should be there? And maybe even what I'm changing so I can actually learn what I'm doing? 

Thanks dudeeeee!

---

### Post by spiderbatdad on 2008-02-20
not exactly what I'm used to seeing there. I expected "ro --quiet splash" at the end of the line. This only useful for getting the cd to install. Afterward you will need to edit the kernel line in /boot/grub/menu.lst  to reflect the same changes.  in your example, I would delete "quiet splash --"
and replace with "noapic nolapic vga=771" (no quotes). From that same screen, if you press F1 you will get some explanation, and f6 again for more possible parameters. esc to return to boot screen.

---

### Post by nclester on 2008-02-20
Alright, so I deleted "quiet splash--" and replaced it with "noapic nolapic vga=771" without the quotes obviously. I pressed F1 for an explanation and then hit F1 again on accident and it brought me to a CLI like this.

boot

Nothing else anywhere on the screen, so I pressed RETURN. It then ran off a few more lines of code and I ended up at the ubuntu loading screen, orange bar going left to right, then about 5 minutes later it went to a blinking underscore on a blank CLI. 

What now?

It's been like 5 minutes

---

### Post by uberlube on 2008-02-20
try adding 'irqpoll' to the boot procedure and also the 'vga=? (i use 791)'

---

### Post by spiderbatdad on 2008-02-20
sounds like some other parameters might serve you better. you might try noapic nolapic noirqpoll

sorry I can't give you the exact parameters. I've done this by trial and error on a couple of difficult machines. Generally Ubuntu installs for me with no options needed.

---

### Post by nclester on 2008-02-20
After giving it a minute it produced a screen close to that of my first post. Damn close actually, just different content. The screen has a flashing underscore at the bottom of the code and isn't responsive.

---

### Post by spiderbatdad on 2008-02-20
did you try uberlube's suggestion? noapic irqpoll vga=791

---

### Post by nclester on 2008-02-20
I'm working on it as I type. I tried "noapic nolapic irqpoll vga=795" I hit enter and it brought up a black screen and nothing else. I'll try vga=791 and it might work. 

I have a question, what am I adding or subtracting to the boot order? Like, what does noapic stand for? nolapic and irqpoll? I know what VGA is, but what are the associated numbers? 

I had no idea Ubuntu was this difficult. I won't give up on it, give me a few more minutes to try a few other options. 

I sincerely appreciate the time and effort that other Ubuntu user's are giving me. Nice to find a forum that's not full of BS!

---

### Post by nclester on 2008-02-20
I tried noapic irqpoll vga=791 and it prompted me to leave the GUI and go to CLI. I agreed. I'm staring at a screen like this. 

boot:_

and thats it.

What do I do? I feel like a freaking moron.

---

### Post by spiderbatdad on 2008-02-20
I'm at least half BS but I do the best I can. ACPI= advanced configuration and power interface. My limited understanding is, it tells hal or some other daemon, during the boot, not to look for (or try to configure) certain hardware.

---

### Post by nclester on 2008-02-20
Haha. Your best is good enough dude, thanks again! 

Still no idea what I should do, I'm no command line interface guru. I still see...

boot:_

Any suggestions?

*update*

I tried it again and clicked RETURN, it once again loaded a few commands and sent me to the Ubuntu loading screen, orange bar sh*t. I'll give it a while and perhaps it will work. 

I wonder what could be causing my PC not to boot into Ubuntu? It's kind of a bummer, but I love fixing sh*t.

---

### Post by spiderbatdad on 2008-02-20
maybe some config setting in your bios for the display...analog vga is what I have mine set to.
Other than that, you may be stuck with having to try the alternate cd, unless you can fiddle with the parameters until you find the trick.

---

### Post by nclester on 2008-02-20
Agh, forget it. I'll try the alternate CD and see where I come out. I have no experience fooling with boot parameters, I'll probably f*ck something up. 

I'll be back to let you know how the alternate install went! 

Thanks, spiderbatdad!

---

### Post by nclester on 2008-02-20
jan quark, thanks for the alternate CD download. Your Ubuntu Alternate CD guide is a bit outdated, so I tried this one! 

[http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2](http://screencasts.ubuntu.com/MoS2007/10_Installing_Ubuntu_Part_2)

It's a Ubuntu Screencast and it's pretty through for a beginner. My only question is, when I get the "Is the clock set to UTC?", what do I enter? Yes or No?

I'm running Windows XP Pro and always have, this is my first Linux Distro ever.

---

### Post by ve9gj on 2008-02-20
Answer no if your PC is set to local time.  Most are.

---

### Post by nclester on 2008-02-20
Thanks ve9gj

---

### Post by nclester on 2008-02-20
Alright, I downloaded and burned the Ubuntu Alternate CD and it's worked flawlessly so far. 

One question, I'm manually partitioning my drive and have one partition showing 100GB for Windows . So I created another partition for swap, 512MB, but I don't know if a swap partition is Primary or Logical? 

I'll have like 60GB left over for the Ubuntu partition and I'd be happy : ) ---->wait... what about this partition here, is it logical or primary? 

Thanks again!

*edit* 

Waste of a post, Google did it. Sorry

---

### Post by nclester on 2008-02-20
After the install and reboot, grub worked fine. I selected to boot into ubuntu str8 up and the ubuntu loading page popped up, you know, the logo and the orange bar. It started to load perfectly but stopped when the bar was like a quarter full and froze. Like, nothing changed for a good 8 minutes. I shut it down and tried it two more times and got the same response. 

So having no idea what to do I tried to boot into recovery mode and it couldn't. Stopped to an error message. Check the pic. 

[[IMG]http://img66.imageshack.us/img66/9427/img0030uf8.th.jpg[/IMG]](http://img66.imageshack.us/my.php?image=img0030uf8.jpg)

So I still can't boot Ubuntu on my machine. 

Suggestions? :(

---

### Post by ve9gj on 2008-02-21
I wonder if possibly you might have some bad RAM.   What you are experiencing is not normal.  To check your ram choose the program memtest from the boot menu when booting from the Ubuntu install CD.  Let it run for awhile, (30 mins or an hour) If it has any errors (shows up as red lines on the bottom) you have a RAM problem.

Another thought might be to try booting a knoppix cd 
[http://www.knopper.net/](http://www.knopper.net/)
or an INSERT CD
[http://www.inside-security.de/insert_en.html](http://www.inside-security.de/insert_en.html)
and see what happens.

---

### Post by gianchi on 2008-02-21
For Spiderbatdad.

Hello there.

I had trouble starting the LiveCD myself, when I stumbled across the "vga=771" screen. Suspecting a video-card/monitor issue I tried that and got to install Gutsy on my pc, in dual boot.

Now, the problem is, when I try to boot from HD, the same thing happens and I don't know how to prevent it... can you help me? I guess once I get to log and set the right resolution, it won't happen again (and I'll be able to look at all the other issues I'll surely find! :D)

Thank you, anyway. :)

---

### Post by nclester on 2008-02-21
ve9gj, I'm running a memtest right now. Although I don't think I have any bad RAM, or at least I hope not. I'll post results when it's finished. 

I'm still unable to boot into Ubuntu, but Windows XP Pro SP3 works fine and GRUB works fine. 

After I select Ubuntu 7.10 - generic from the GRUB menu and hit RETURN, I get stuck at the next loading screen, my orange bar doesn't ever make it past 1/4 full. 

To recap what I've done up until this point, first I attempted to install with Live CD... no dice. 

Then finally got Ubuntu to install from the Alternate CD. After install, I began to experience the freezing up at the loading screen. 

I have 3 partitions on one 160 GB HD. 

100GB - Windows - bootable
1GB - Swap - non-bootable
59GB - Ubuntu - bootable

If the memtest comes out clean, what other options do I have? What can I try? I mean, I have Ubuntu installed on my machine, but I can't even boot it up?

Thanks in advance!

*edit*
Oh and I tried to boot into recovery mode with little luck. Check picture in last post!

---

### Post by Shadonova on 2008-02-21
I feel bad for ya man. Wish I could help. Ive been trying to install this for like 12 hours now....its CRAP lol...



I just cant wait for it to work. Wanna have a laugh, go look at my post lol

---

### Post by spiderbatdad on 2008-02-21
> **gianchi said:**
> For Spiderbatdad.

Hello there.

I had trouble starting the LiveCD myself, when I stumbled across the "vga=771" screen. Suspecting a video-card/monitor issue I tried that and got to install Gutsy on my pc, in dual boot.

Now, the problem is, when I try to boot from HD, the same thing happens and I don't know how to prevent it... can you help me? I guess once I get to log and set the right resolution, it won't happen again (and I'll be able to look at all the other issues I'll surely find! :D)

Thank you, anyway. :)

The thing to do now is edit /boot/grub/menu.lst (small "L" not .1st) to reflect the working parameters.```
gksu gedit /boot/grub/menu.lst
``` scroll down to ####END DEFAULT OPTIONS####
and look at the first block of text. This describes your linux kernel. On the kernel line...at the end of the line, replace/input the same parameters you used to boot the livecd. Save the file by clicking the floppy disk icon at the top of the window.

---

### Post by Sceiron on 2008-02-21
Hello,
have you tried installing ubuntu from the live CD in the "Safe Grafics mode" ?

---

### Post by nclester on 2008-02-21
Sceiron, no I haven't tried that. I guess I'll give that a shot once this memtest is finished running.

---

### Post by nclester on 2008-02-21
I ran the memtest for a little over 2 hours, just to be sure. No error logs or anything. Perfectly normal. 

Now do I try the Live CD, and just install over what I already have?

---

### Post by gianchi on 2008-02-21
> **spiderbatdad said:**
> The thing to do now is edit /boot/grub/menu.lst (small "L" not .1st) to reflect the working parameters.```
gksu gedit /boot/grub/menu.lst
``` scroll down to ####END DEFAULT OPTIONS####
and look at the first block of text. This describes your linux kernel. On the kernel line...at the end of the line, replace/input the same parameters you used to boot the livecd. Save the file by clicking the floppy disk icon at the top of the window.

Yep, but.... how can I edit the file, if I can't boot the system? Must I do that from the CLI of the recovery mode? Can I do it from a Live session or from Windows?

---

### Post by nclester on 2008-02-21
gianchi, thanks for jacking my thread bro

---

### Post by spiderbatdad on 2008-02-21
start a new thread, bro, with where you are now...using the alternate cd...what you've tried...and what is happening. If you get resolution, come back here and link the new thread. I know this is frowned on, but your issue has gotten diluted and you've changed installation disks...etc...etc.
Sorry this is has been so difficult for you. I really hope you get a successful installation.  Maybe post in the installations forum.

---

### Post by nclester on 2008-02-21
nough said'

---

### Post by gianchi on 2008-02-21
Ok, sorry for "hijacking": I posted here just because you were already talking about that vga string... I'll start a new topic.

EDIT: Ok, I got it, spiderbatdad, just had to edit the menu.lst with vi, in recovery mode. Thank you for your help.

---

### Post by ve9gj on 2008-02-21
> **nclester said:**
> I ran the memtest for a little over 2 hours, just to be sure. No error logs or anything. Perfectly normal. 

Now do I try the Live CD, and just install over what I already have?

Well that's good in the fact that your RAM is fine.  It was worth checking to eliminate that.  I am not sure if you have tried reinstalling or still have your alternate install which won't boot.  When you get to the grub boot prompt you can type e to get to edit mode.  Use arrow keys to move to the line that starts with kernel and type e for edit again.  Try adding this to the end of the line:
```
 noapic nolapic acpi=off 
```

Hit enter when done and b to boot.  

Other things to try might be to disable on board modems and possibly ACPI in your PCs bios. Take note of what you change so you can set them back later.
These are just ideas to try, they might not help at all but it can't hurt to try.  There is something that the kernel is tripping over while booting it seems.  

If you have a chance try booting with a Knoppix or INSERT live cd. 

Good Luck.

---

