---
title: "Gigabyte P35C-DS3R -- I Simply have no clue anymore.. Please help?"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by giga_user_66 on 2008-02-26
Dear readers,

The last 5 days I've been endlessy trying to figure out why my ubuntu keeps randomly crashing.
Sometimes straight after the login screen and sometimes when i open just a random application or when i do multiple things at once (firefox + synaptic package manager + listen and mp3 for instance).
When I look back in kernel logs (because i write down when it crashes) there is no error to be found.
After some intensive googling I read that my motherboard gives the mem modules standard 1.8 V which is not enough. It requires 2.1 V
So i cranked up the voltage with 0.3 V
However I STILL get random crashes. It's making me deeply sad because I wanted this pc to solely be used for ubuntu.
I'm using Ubuntu 7.10 and all updates are installed.
Sometimes it crashes 2 times in an hour and sometimes its just once in 6 hours.
When it crashes the following happens: the monitor goes into power saving mode and all functionalities are gone. The only thing i see is a pc with running fans making noise but there is no way to do anything with it unless I take the power off and reboot it.
To make sure it's not my memory i decided to run memtest86+ v1.70 which a few passes and there were 0 errors. To be honest.. I simply dont know what to do anymore so I turn to the forums for my last piece of hope.
I hope someone out there can offer me help. It's making me depressed :(

My system specs:

Mem: 2x OCZ DDR2 PC6400 2048MB KIT, Spec Ops Ed ,w/two 1024MB PC6400 XTC, CL5-5-5-12 ===> total 4x1 GB
Mobo: Gigabyte P35C-DS3R
Cpu: Q6600
Harddisk: WD Raptor 74 Gb
PSU: OCZ StealthStream 600W

---

### Post by Kivech on 2008-02-26
Ok, this is just a guess based upon experiences I've read from others with your "type" of motherboard...

It seems that from Gygabite there is a series of motherboards who have problems that surface every now and then. One of them  being that they are really picky with memory. So you might want to run that memtest for an extended period of time (more than 4 hours for example).

It could also be a defect on your motherboard. Here, check out these forums, they have quite some posts about Gygabite boards (I have one myself): [http://forums.overclockers.co.uk/forumdisplay.php?f=2](http://forums.overclockers.co.uk/forumdisplay.php?f=2)

It's an overclocker's forum, which I prefer since they are more likely to run into problems/limits of hardware than others.

Post your problem there and see if maybe they come up with something useful. To me it really sounds like a potential hardware problem. If Ubuntu worked first and now it goes like this, it would be rather weird to think Ubuntu is the culprit, unless something changed in the configuration of course.

Did you ever have another OS on this PC of yours, and was that more stable? Just to rule out that maybe it could be Ubuntu for whatever reason.

Let us know how things work out in the end. Good luck.

Kivech

---

### Post by Iceni on 2008-02-26
I do get the feeling your motherboard is the bad boy here. There are a number of things you can do to check this:

- boot into livecd and leave it on for a day or so, see if it crashes
- boot ubuntu, kill X and leave it in command line

Also monitor your temps.

Is this a new system now, or have you been running windows on it before? Is it overclocked?

---

### Post by giga_user_66 on 2008-02-26
Big thx for you reply.
I had my old OS Win XP Pro on the harddisk. Which booted up fine again with the new motherboard and specifications (that was before i wiped that partition and used it for ubuntu). It was stable and it did not crash like ubuntu does.
Ill let memtest run for 4 hours, which should be enough I think. I will let you know what the results are.
I just wish I knew what it was.
Btw its the 2nd new mobo i got cos the previous P35C had to be RMA-ed (it did not POST at all)
This one seems fine but has issues with Ubuntu (or even windows too, i dunno).

---

### Post by giga_user_66 on 2008-02-26
> **Iceni said:**
> I do get the feeling your motherboard is the bad boy here. There are a number of things you can do to check this:

- boot into livecd and leave it on for a day or so, see if it crashes
- boot ubuntu, kill X and leave it in command line

Also monitor your temps.

Is this a new system now, or have you been running windows on it before? Is it overclocked?

Hi!

Ive let Ubuntu run for 1.5 day, worked fine. If I don't do anything it doesnt crash for some reason.
The temps are ok, it has 3 case fans and a nice zalman cooler. Its a brand new system (apart from the fact that its my 2nd P35 mobo, previous one never showed POST, got RMA-ed). Its not overclocked.
The hd from the old windows system i simply placed over. Before i installed ubuntu it automatically booted from that and i used that system for a day or two to copy over and backup some files. It never acted up in that time. (while using windows)


Forgot to reply on that X thing. How do I do that?

---

### Post by jhenager on 2008-02-26
I agree with those looking at the motherboard and/or memory itself.
I don't see a Gigabyte diagnostics disc available, but that would be the direction I would go.
I have 7.10 running on an older GA-6IEML, and it is solid as a rock, if that helps.

---

### Post by mikebravo on 2008-02-26
I have been running a GA-P35-DS3R (rev 2) for five months now and could not be happier.  Am using two sticks of 512 Meg Kingston Value RAM DDR2 800 for total cost of $57 at Newegg (N82E16820134116).  These are 1.8 volt chips.  If you are really up against the wall you might want to go with Gigabyte's specs.

---

### Post by giga_user_66 on 2008-02-27
Update: I just let it on for the night copying over files from ext3 partition to ntfs partitions.
It crashed somewhere this morning. No traces in the logs again. Just when i went back to the pc the monitor was in power saving mode and all functions were disabled, no way on earth to get it back. Had to hold down the power button to  turn it off.
I'm also starting to think this is not an OS issue anymore. Therefore I will install windows on the disk again and let that run for a day or more. If this crashes too I know something is wrong with the hardware.
It can either be 3 things. The motherboard, the memory or the power supply!
However I dont hope it ends up being a conflict with my nvidia 6600GT card. But we will see what windows does. 
On another note : the memtest86+ If windows crashes too ill let that run for 6 hours and see what happens. Thx for all ur replies. Ull see a post back here soon.

---

### Post by Duck2006 on 2008-02-27
I run a Gigabyte GA-7IXE4 Mother Board. (Early board i know) On windoze it crashed and on ubuntu, fedora it crashed until i got the configuration right, ie video, sound card. now it runs very good. Good luck

---

### Post by giga_user_66 on 2008-02-27
> **Duck2006 said:**
> I run a Gigabyte GA-7IXE4 Mother Board. (Early board i know) On windoze it crashed and on ubuntu, fedora it crashed until i got the configuration right, ie video, sound card. now it runs very good. Good luck

Ok. Well I dont have a soundcard. (its integrated on the mobo)
And about the videocard, what do you mean with getting the configuration right?

---

### Post by Duck2006 on 2008-02-27
> **giga_user_66 said:**
> Ok. Well I dont have a soundcard. (its integrated on the mobo)
And about the videocard, what do you mean with getting the configuration right?

I run a ATI card and it never worked well in win and linux. I ended up with a PCI Geforce card and never looked back. Now these thinks may not work for you but, it worked for me. Did you check what your IRQS and DMA are set for?

---

### Post by giga_user_66 on 2008-02-27
> **Duck2006 said:**
> I run a ATI card and it never worked well in win and linux. I ended up with a PCI Geforce card and never looked back. Now these thinks may not work for you but, it worked for me. Did you check what your IRQS and DMA are set for?

I did not check the IRQ and DMA, where can i do that and what do i need to look for?

---

### Post by Duck2006 on 2008-02-27
Not sure where in ubuntu you would find that. I check in win and got that running ok then i installed linux and it worked good. If i went back to the ati card in linux i had problems. The sound card was a sound blaster card.

---

### Post by giga_user_66 on 2008-02-29
Update:

So I installed windows back again. The x64 edition so all my memory can be used.
Even disabled pagefile use to increase chance of crashing if it would be the memory.
Funny thing is, it's stable. Ive browsed, listened some music, moved files. And it's working for 2.5 day now. No more weird random crashes like on Ubuntu.
I guess me and Ubuntu dont go together.
Seems in my case that new hardware + ubuntu = pain
I rest my case. Thanks for the ones that provided help. Windows prevailed in this case im afraid.

---

### Post by Duck2006 on 2008-02-29
Maybe 8.04 will be better for your hard ware.

---

### Post by giga_user_66 on 2008-02-29
I knew you were gonna say that. :) I tried the latest Hardy Heron Alpha. It had the same thing :)
I havent tried the server edition of Ubuntu. But i think its something in the desktop environment that doesnt like my hardware. If I wanted to be sure I would have tried the server edition too.
But I want to use this computer and not trial/error for weeks and weeks. I was hoping it would install just as fine as on my old laptop. I was terribly wrong. :(
Maybe another pc someday, sometime...

---

### Post by Duck2006 on 2008-02-29
Good luck.

---

### Post by mangoes on 2008-03-01
I have the same mobo,  rev 2.1x . It kept crashing in the same way you described a couple of times a day, but 2 days ago I flashed the BIOS to F10  and it has not crashed since.  What surprised me is that during flashing I found out that the current bios was F8,  but rev 2.1  is supposed to have  F9 and F10 only.

  I'm still jittery and holding breath everytime I start the box. Will update you in a couple of days about the stability but if you have not flashed your bios it's worth a try. Just make sure which revision you have.  

One thing is that I could not use Q-flash because it did not recognize the F10 bios that I put in my flash drive,  so I had to use @bios in XP.  

Another thing is that on rebooting after flashing, I had to disable the usb legacy and usb keyboard & mouse support in the bios menu, otherwise the computer keeps rebooting upon loading Gutsy.  Someone else in another thread had the same problem.  

This is a bit of a pain because that means if I want to boot into the windows partition,  I had to get into bios first to enable the usb keyboard support in order to scroll down to xp during grub, but I only ever have to use xp in strange circumstances(like this one).

Now I'm a noob knows very little about mother boards, so not sure if the following is relevant,  but also read in other forums that this mobo needs at least 500W psu.  I had a cheapie 600w on paper but in reality hover around 450W and one time during a crash, it died. I also had to replace this motherboard once (under warranty) because it was toasted and the techie suspected the psu was the problem.  Now I have a better quality 800W psu. 

hope that helps
ps: needless to say, don't forget to load optimized defaults after flashing the bios.
=============
p35cds3r
Quad 6600
Nv Geforce 6400 (restr drive disable at the moment)
4Gb Ram
Logitech usb keyboard & mouse w/ receiver station

Hope that helps.

---

### Post by mangoes on 2008-03-01
I have the same mobo,  rev 2.1x . It kept crashing in the same way you described a couple of times a day, but 2 days ago I flashed the BIOS to F10  and it has not crashed since.  What surprised me is that during flashing I found out that the current bios was F8,  but rev 2.1  is supposed to have  F9 and F10 only.

  I'm still jittery and holding breath everytime I start the box. Will update you in a couple of days about the stability but if you have not flashed your bios it's worth a try. Just make sure which revision you have.  

One thing is that I could not use Q-flash because it did not recognize the F10 bios that I put in my flash drive,  so I had to use @bios in XP.  

Another thing is that on rebooting after flashing, I had to disable the usb legacy and usb keyboard & mouse support in the bios menu, otherwise the computer keeps rebooting upon loading Gutsy.  Someone else in another thread had the same problem.  

This is a bit of a pain because that means if I want to boot into the windows partition,  I had to get into bios first to enable the usb keyboard support in order to scroll down to xp during grub, but I only ever have to use xp in strange circumstances(like this one).

Now I'm a noob knows very little about mother boards, so not sure if the following is relevant,  but also read in other forums that this mobo needs at least 500W psu.  I had a cheapie 600w on paper but in reality hover around 450W and one time during a crash, it died. I also had to replace this motherboard once (under warranty) because it was toasted and the techie suspected the psu was the problem.  Now I have a better quality 800W psu. 

hope that helps
ps: needless to say, don't forget to load optimized defaults after flashing the bios.
=============
p35cds3r
Quad 6600
Nv Geforce 6400 (restr drive disable at the moment)
4Gb Ram
Logitech usb keyboard & mouse w/ receiver station

Hope that helps.

---

### Post by tgalati4 on 2008-03-02
I was also going to suggest changing the power supply.  Your Raptor, Quad Core, 4 GB monster will use a lot of power.  Try reducing RAM to 2 GB.  Try declocking--try half speed.  See if Live CD of Ubuntu will last for more than a couple of days in this configuration.

It's possible that Windows 64-bit has better power throttling so the CPU's aren't eating as much power.  With Ubuntu, it's full bore until you go into power settings and start changing things and turning "On-demand" power rules.

Normally these kind of problems are sorted out in the lab before the machine is sent out for retail.  When you build it yourself, you get the honor of testing and validating the system.

---

### Post by giga_user_66 on 2008-03-02
Hmm.
Alot of replies :) Thanks!
Well if the PSU would be the problem I would have noticed it during my use of win x64 already. Since it still runs fine. 
The only weird thing I still have is that when my system is under alot of stress (multiple threads of moving files etc) it will give a random beep from time to time.
I read somewhere that this is from the overtemp-failure-sensors.. Ill have to check what to turn off in the BIOS for that..
As for flashing.. I'm not planning on flashing anything if the motherboard boots just fine and does not give me any POST errors. I am not planning to overclock this motherboard, I seek stability.
About the revision and current bios I have. Ill look that up later today when I reboot.

---

### Post by giga_user_66 on 2008-03-02
> **tgalati4 said:**
> I was also going to suggest changing the power supply.  Your Raptor, Quad Core, 4 GB monster will use a lot of power.  Try reducing RAM to 2 GB.  Try declocking--try half speed.  See if Live CD of Ubuntu will last for more than a couple of days in this configuration.

It's possible that Windows 64-bit has better power throttling so the CPU's aren't eating as much power.  With Ubuntu, **it's full bore until you go into power settings and start changing things and turning "On-demand" power rules**.

Normally these kind of problems are sorted out in the lab before the machine is sent out for retail.  When you build it yourself, you get the honor of testing and validating the system.

I had absolutely no clue about that on-demand thing :?
That is something I should have known before... Thanks though!

---

### Post by Cybie257 on 2008-03-03
New to the forums and find it inviting to at least share some thoughts. 

I have the same motherboard with 3gigs of RAM. Mixed (2gigs one brand, 1 gig other brand). I will say, from experience, change out your RAM. Windows has always been unstable by trying to hard to be stable at times. Meaning, it will crash less with hardware issues. Linux is a very stable OS and if it finds something out of whack, such as bad RAM, then it will crash. Only had that happen once. Replaced the RAM in the problem computer and wholla! It's been stable ever since. 

Another scenario... I recently bought a laptop from eBay that needed a simple repair. The laptop was shipped with a kingston 512MB DDR chip. Since it was suspected to be bad, I bought a patriot chip and got the puter running with Kubuntu (Believe it or not, this laptop would not run Ubuntu, while every other computer I've had accepted Ubuntu so much easier). 

I sent the suspect chip back to Kingston and they sent me a new one (Kingston rocks with their warranty policy - I wasn't the original purchaser, no reciept required). I installed it with the same results.Sometimes it would boot, then crash, others it would cause the video on the BIOS Bootup to go crazy. 

Okay, now back to the Gigabyte MOBO and other thoughts. I would recommend getting some cheap RAM (2qty 512MB) of 1.8V standard DDR2 that you can get for about $20 these days. Try that and see how that works for you and Ubuntu. I installed Ubuntu on my system and never had a problem except for my ATI video card. I love ATI cards, but if they don't put more effort into Linux support, they are history for me. 

As for the power supply, I give that a BIG maybe, but not likely. A motherboard should never require a certain wattage to be run (above the normal 350W+). If you have a power-sucking Video card and lots of hard drives and other add on cards, then you'd want to upgrade. I run a 400Watt with 4 Hard Drives, Dual-Head ATI video X1300, 7 USB Devices, PS2 Keyboard, 2 Case fans. Never a glitch at all. 

Probably a little more detail than I needed to go into, but wanted to give you an idea of my experience with the motherboards, RAM, and OS's. So, try the quick, cheap route of replacing the RAM and see if that helps. It's always good to have some extra RAM laying around to test with. Has saved me many times from sudden issues, such as unknown crashes. 

Hope this helps. :)

-Cybie

PS. I wanted to add (as an edit), that I'm not knocking any ideas whatsoever about possible issues mentioned, like power supply and such. Just telling my experiences and hoping that they will help you in your Linux adventures! :)

---

### Post by mangoes on 2008-03-04
> **giga_user_66 said:**
> Hmm.
Alot of replies :) Thanks!
Well if the PSU would be the problem I would have noticed it during my use of win x64 already. Since it still runs fine. 
The only weird thing I still have is that when my system is under alot of stress (multiple threads of moving files etc) it will give a random beep from time to time.
I read somewhere that this is from the overtemp-failure-sensors.. Ill have to check what to turn off in the BIOS for that..
As for flashing.. I'm not planning on flashing anything if the motherboard boots just fine and does not give me any POST errors. I am not planning to overclock this motherboard, I seek stability.
About the revision and current bios I have. Ill look that up later today when I reboot.

My motherboard also booted fine and there was no POST errors. I do not overclock nor have nvidia restricted driver on, because I need to box to be stable enough to run long numerical models while I'm doing post processing and writing up reports.  But it kept on crashing a couple of times a day.

Now it's almost a week with no single crash since I've updated the bios.  Still nervous though. I'm going to run a couple of heavy fortran programs simulltaneously in the next couple of days and will update you on whether the box will crash again. :)

---

