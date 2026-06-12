---
title: "last ditch cry for help before installing xp"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by daverich on 2007-05-19
ok.

My desktop computer just wont swallow ubuntu.

The vga card is a geforce2 mx400 - which I suspect is the heart of the trouble.

I have spent all afternoon playing around trying to get it working- reinstalled from the live cd 3 times - and the furthest i got was ubuntu working, but with no icons, and programs not loading - and ubuntu moaning about something called Gconf not working.

The laptop on the other hand works perfectly and caused me no trouble at all.

this is fiesty fawn.

Any ideas?

Kind regards

Dave Rich

---

### Post by halitech on 2007-05-19
I have a geforce2 mx400 and it works fine right from a fresh install. Have you tried running the mem test from the cd and are you using the live cd to install or an alt cd?

also, what are the specs of your computer?

---

### Post by daverich on 2007-05-19
i'm using the livecd for an install.

the ram is 1gig, athlon 2200, ecs k7s5a motherboard, sis735 chipset, 1 hard drive 180gig - brand new (bought it today to see if that was the problem)

I have a widescreen lcd monitor and when the video card does work, it won't do 1440x900 which i need it to.

I guess i could run memtest through a few times - but i did buy a new stick today as well.

thanks for replying :)

Kind regards

Dave Rich

---

### Post by halitech on 2007-05-19
ok, hardware should be nice to run it on.

maybe try the ubuntu alt install cd, I've never had much luck myself with installing from a live cd (just making a comment on my usage, not on the live cd installer on a whole)

---

### Post by daverich on 2007-05-19
i'll give that a go - 

where can i find the alt install cd download?

Kind regards

Dave Rich

---

### Post by aberadam on 2007-05-19
I'm about to go back to XP as well.  I've got Ubuntu installed OK it's just won't connect to the Internet.  They should really work on the 'just works' thing.  After getting on the Internet the next thing will be the grapics card... If I get that far. 

It's so frustrating.  Sadly, I'm coming to the conclusion that Ubuntu is just for those with in-depth computer knowledge or people who actually want to mess around with their computers all day for some reason.  I just want an efficient tool.  

:(

---

### Post by daverich on 2007-05-19
yeah i hear ya.

it's wierd though- like i said - the laptop just worked  (but then it is intel)

Kind regards

Dave Rich

---

### Post by Zyphrexi on 2007-05-19
most of the time, the defaults ubuntu wants to use are annoying. As far as screen resolution, I would just edit the /etc/X11/xorg.conf file.

That's the file that controls the display properties of the X server. (which is the graphical part of linux)

I'd install using the highest options without problems, and work on configuring it later. Admittedly I have not used the live cd to install. I think I installed from breezy or dapper, and dist-upgraded from there.

---

### Post by richaoj on 2007-05-19
good luck re-installing xp.  it is (to me) much more difficult than installing ubuntu.  be sure you have your driver disks handy, because xp will not come close to installing all of the drivers you need to run your system properly.   

for the graphics, have you tried the "restricted drivers management"?  it makes things quite easy if you have a graphics card that does not have an open-source driver.  

as far as the internet connection goes, if you post some more information, we could probably help you here.

---

### Post by halitech on 2007-05-19
> **daverich said:**
> i'll give that a go - 

where can i find the alt install cd download?

Kind regards

Dave Rich

try this link

[http://mirrors.gigenet.com/ubuntu/7.04/ubuntu-7.04-alternate-i386.iso](http://mirrors.gigenet.com/ubuntu/7.04/ubuntu-7.04-alternate-i386.iso)

thats assuming you are in the US, if not, check here [http://www.ubuntu.com/getubuntu/downloadmirrors](http://www.ubuntu.com/getubuntu/downloadmirrors) and select one closer to you.

---

### Post by halitech on 2007-05-19
> **aberadam said:**
> I'm about to go back to XP as well.  I've got Ubuntu installed OK it's just won't connect to the Internet.  They should really work on the 'just works' thing.  After getting on the Internet the next thing will be the grapics card... If I get that far. 

It's so frustrating.  Sadly, I'm coming to the conclusion that Ubuntu is just for those with in-depth computer knowledge or people who actually want to mess around with their computers all day for some reason.  I just want an efficient tool.  

:(

I'll admit I was what I thought of as a "Windows power user" but I'll be honest, Linux has really humbled me and made me realize just how little I actually know about computers but I'm enjoying every minute of it :)

---

### Post by daverich on 2007-05-19
thanks -

can you tell me what the difference between the ALT version and the DESKTOP versions are?

Kind regards

Dave Rich

---

### Post by halitech on 2007-05-19
the alt cd is going to install only, will not take you to a desktop first but they are the same other then that.

---

### Post by daverich on 2007-05-19
thanks - i'll give the desktop version a go.

memtest is running as i type this and it seems ok so far.

Kind regards

Dave Rich

---

### Post by maniacmusician on 2007-05-19
> **halitech said:**
> the alt cd is going to install only, will not take you to a desktop first but they are the same other then that.
Yes, and it is text based. There's an ncurses GUI, but it's not like actual windows or anything. You'll see when you boot it up. It's usable, but you may have to get used to it a little. 

If you've ever installed XP, it's a littl ebit like the XP install is at first. With th eblue blackground and white, blocky text.

---

### Post by maniacmusician on 2007-05-19
> **daverich said:**
> thanks - i'll give the desktop version a go.

memtest is running as i type this and it seems ok so far.

Kind regards

Dave Rich
The desktop version is the LiveCD, which you've already tried. You want to try the Alternate CD

---

### Post by halitech on 2007-05-19
the desktop is the live cd, if you want to install, go for the alt cd instead.

---

### Post by daverich on 2007-05-19
> **maniacmusician said:**
> The desktop version is the LiveCD, which you've already tried. You want to try the Alternate CD

thanks for letting me know ;)

Kind regards

Dave Rich

---

### Post by darkworld on 2007-05-19
> **aberadam said:**
> I'm about to go back to XP as well.  I've got Ubuntu installed OK it's just won't connect to the Internet.  They should really work on the 'just works' thing.  After getting on the Internet the next thing will be the grapics card... If I get that far. 

It's so frustrating.  Sadly, I'm coming to the conclusion that Ubuntu is just for those with in-depth computer knowledge or people who actually want to mess around with their computers all day for some reason.  I just want an efficient tool.  

:(

Im lucky then because my net connection just runs straight out of the box on Ubuntu, mandriva and dsl. What exactly is going wrong. Open another thread on it. It could be a firmware problem in cable modem if thats what your running. A guy who i work with wanted to run Linux but ran into a problem with the cable modem virgin media supplied him with. Needed a firm change.

---

### Post by daverich on 2007-05-19
yeah my lan just works - very well in fact, ever since i got a router.

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-19
hmm- 

text mode - *sigh* - I've a feeling this is going to be more hassle.

or is there an easy way with the alt installer to do a normal/simple install?


Kind regards

Dave Rich

---

### Post by woland on 2007-05-19
> text mode - *sigh* - I've a feeling this is going to be more hassle.
Actually no, it quite strait forward, unless you stray into some advanced options.

The main difference between the Live/Install CD and the Alternate Install CD is that the first one is more for evaluation and then an easy install, without too many options, while the latter is designed for a more advances uses, like upgrading a distribution without internet access, making a complex disk arrangement (lvm) or using kernel based virtualization (XEN or KVM).

---

### Post by daverich on 2007-05-19
ok-

we're getting there!!

i now have an ubuntu which boots up and works - however,

the first time it said it couldn't open the normal login screen so used a more basic looking one - now it's fine though.

I did edit the xorg.conf file to make sure it uses the correct res - which it now does, 1440x900.

one last problem though is that on loading the ubuntu logo is trying to display at a higher res than my monitor can manage - how do you stop that?

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-19
hmm, also still getting hangs - first when i ran the gimp, and 2nd when opening the desktop backround pref app

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-19
hmm and then on reboot it doesn't manage to get as far as the gui.

BAH.

Kind regards

DAve Rich

---

### Post by daverich on 2007-05-19
and now it will get to the gui but keeps saying your session lasted less than 10 seconds, and then returning to the login prompt.

one wonders would a sledgehammer help?

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-19
the error reported by xsession-errors file is
y
Inconsistency detected by ld.so: ../sysdeps/i386/dl-machine.h: 554: elf_machine_rel_relative: Assertion '((reloc->r_info) & 0xff) == 8' failed!

Hopefully that means something to someone?

Kind regards

Dave Rich

---

### Post by daverich on 2007-05-22
OK.

Just bought an intel motherboard with built in video.

I expect zero problems.

I really hope all these driver problems get sorted out.

Kind regards

Dave Rich

---

