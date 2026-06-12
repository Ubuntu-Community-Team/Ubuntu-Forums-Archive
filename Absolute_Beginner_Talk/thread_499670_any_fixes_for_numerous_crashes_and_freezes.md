---
title: "any fixes for numerous crashes and freezes?"
date: 2007-07-12
forum: Absolute Beginner Talk
---

### Post by GMachine_24 on 2007-07-12
Ok so I am running a PIII 900 with 768 MB of SDRAM and Ubuntu 6.1 Edgy Eft is the OS and:

1. Computer crashes frequently when attempting to use Firefox, especially when attempting to minimize a browser page.

2. Having said that, the computer also crashes when using Open Office (2.0) typing program (yes by this I mean 'word processing'); Mozilla 1.7.13 browser; K3B (run under Gnome); Evolution Mail, etc.

This is a fairly recent install because I had to replace the main hard drive which (I concluded) got fried here in Florida with all the lightning strikes and because our power company is still in the dark ages when it comes to surge protection (I hear the transformer blow in the middle of a cloudless, beautiful day and a second or two later . . . no power). [Yes, all tech gadgets have numerous surge protectors/battery backu ups connected to them.)

I had read posts before doing this new install concerning how to conquer the freeze/crash problem. I am wondering if anything was compiled in one place and is there a consensus on what the problem(s) is / are? 

Thank you in advance.

gm

---

### Post by twiceasworn on 2007-07-13
Well it good be a good number of things to be honest. What have you installed since you did your fresh OS install?  Have you installed the graphics drivers for your card?  Also could you post the content of /var/log/messages?

---

### Post by wpshooter on 2007-07-13
Are you sure that you don't have a faulty power supply ?

---

### Post by alienexplorers on 2007-07-13
Sounds like the power supply or another part dying.  I had a simple fan going bad and my computer kept resetting.  Tell me thats not strange.

---

### Post by twiceasworn on 2007-07-13
> **alienexplorers said:**
> Sounds like the power supply or another part dying.  I had a simple fan going bad and my computer kept resetting.  Tell me thats not strange.

Its not strange.  If that fan was cooling something just enough to keep the machine from overheating then it is entirely understandable.

---

### Post by sailor2001 on 2007-07-13
also I think you could try a memtest to check your ram , etc.   Lightening strikes can really hurt in strange places.......another  thought.... run a telephone cable from your outside box (this is by-passing the surge protector) to your inside modem

---

### Post by GMachine_24 on 2007-07-13
hi: thanks for all your responses and input. i had just finished a reply about a minute ago when i clicked on the closer browser (x) button and..........crash. yes i know... but ... old habits die hard.

anyway, in response to your posts:

1. the power supply is a good one. this doesn't mean it hasn't been *compromised*. i have other new ones that i can use to see if that helps.

2. i believe i have the correct video driver:

Section "Device"
	Identifier	"S3 Inc. ProSavage PM133"
	Driver		"savage"
	BusID		"PCI:1:0:0"
EndSection

3.  i have attached the contents of the /var/log/messages file as it is quite long. UPDATE: Ok, I could neither attach the contents of the messages file nor could i pasted it into this post as it exceeds the size limitations.

twiceasworn: i was just thinking that i should swap the ram because i know when ram memory goes bad all sorts of flaky things can happen and you can chase your tail for hours if not days attempting to find the problem.

4. since the new install, i reinstalled all the files from my backup file. yes, i know this could have caused the problem.

i used to build/maintain/sell computers. i know how completely insanely difficult it can be to find the source of a problem - especially if you don't have, basically, another system to use to test parts, etc. i guess i was hoping for that 'magic bullet' .......

i had this system running for years without a hitch until december when problems occurred - computer wouldn't boot, nonsensical text spewed across the screen. anyway i won't go on any more.... i will try swapping parts to see if any new ones solve the problem. or, hey.... maybe i should just spring for all new hardware and save myself the aggravation. ....

as an aside, .... my computer crashed at least four times while i attempted to finish this post.....word processor, browser, no rhyme or reason (to me)

---

### Post by twiceasworn on 2007-07-13
Ok, I would agree that it is a hardware problem most likely.  Especially since you have lightening strikes regularly.  We have power outages here in St. Louis ALOT and my system has been screwed because of them at least 2 or 3 times.  One of the times completely frying the 5volt power bus on my Mother Board.  I would suggest doing the memtest as someone above mentioned.

---

### Post by GMachine_24 on 2007-07-13
Thanks again for your help.

As I had to replace hardware on three other computers already - which all began having problems at the same time - I think trying new hardware, including a mb and cpu if necessary - is my next best step.

Everyone here hates the local power company because they fry home appliances, computers, etc. all the time. They have a surge protector they can put on the outside of my building which will  (supposedly) reduce surges to minimal levels . . . . but they won't install one unless the owner of the building asks them to do so. (I live in an apartment.) Just how stupid can you get?

---

### Post by wpshooter on 2007-07-13
If it's a PIII, then you need a new computer anyway.  Get yourself a good APC ups of sufficient wattage, IMO need more than surge suppressor.

Good luck.

---

### Post by mgmiller on 2007-07-13
Have you had a good close look at the capicitors on your mobo?  There is a "capacitor plague" that affected many brands of mobos and other hardware over the last few years.  I recently discovered one of my machines had this problem, random reboots and finally no boot at all till I put in a larger PSU.  That's when I noticed my caps were leaking and did a google search on capitor plague.  Amazing story by the way!  A new mobo did the trick for me.

---

### Post by GMachine_24 on 2007-07-13
Hello again. This is just too perfect . . . 


So .. I have to admit I had no idea how to run the memtest until I remembered seeing it as a boot option on my laptop (dual boot win and lin) . . 

Anyway . . . I started the memtest on this comp, the dreaded PIII, and .... things were going along fine so I lay down on my futon to relax and watch TV and . . . sure enough ..... click.... squeal ... buzz... the power died and then came right back . . . i could here the usb devices reloading (or whatever) on windows ....the surge screwed up this computer... again.... and on reboot there were numerous errors and I got a msg saying I needed to run a manual fsck on /dev/shm/root

which I did... chose 'y' at each prompt to fix the errors and now here I am ready to reboot the computer and try the memory test again . . . Progress Energy willing...

I am going to install new surge protectors tomorrow and I'm going to see about building my own as all the retail ones are either too weak or too expensive and I .... as I used to work in an electronics plant doing everything from assembly to testing I think I can probably build my own . . . perhaps I will sell them or design them.... who knows. Can't be that hard.

And... the PIII 900 is decidedly not too slow or old or whatever for what I use it for . . . which includes complete back ups of my Win**** machines; various programs; I also use it for Gnucash (which I am still trying to figure out) and ripping DVDs and I have Open Office to take care of all that stuff . . .and email. So.... it has been a great computer.

All that off a main drive that uses less than 1GB of space for the OS, all the programs, etc.

Thanks again to everyone for your help.

gm

---

### Post by GMachine_24 on 2007-07-14
12:30 a.m. Saturday the 14th

Memtest did its thing and detected . . . errors? There were three memory sticks and at least one has problems so I removed them all and installed a new 256MB PC-133 SDRAM module (yes I will run memtest on it).

Anyway..... I also started memtest on two other Linux boxes I have and they so far have reported no errors.

I will let this configuration run for a couple days to see if any problems emerge - I also will check the motherboard for leaking capacitors and if I run into more trouble replace the power supply.

As I believe it's important for people to post their 'how I fixed it" lessons, I will update this thread as is called for (i.e. if I run into more problems). If I don't have any problems in a month or so I will report that back and consider this issue SOLVED!!

Thanks again to everyone for your time and trouble.

gm

And yes I still plan on replacing the UPS device ASAP today.

---

### Post by mgmiller on 2007-07-14
You said:
> I am going to install new surge protectors tomorrow

and then in your last post you said you were going to replace the UPS as soon as possible.

Based on your statement:
> Anyway . . . I started the memtest on this comp, the dreaded PIII, and .... things were going along fine so I lay down on my futon to relax and watch TV and . . . sure enough ..... click.... squeal ... buzz... the power died and then came right back

You are not using a UPS. (unless it's battery has died).  You seem to be using surge protectors which do not help if the power goes out.  From what you say, your electricity is wildly unreliable.  You should get  a nice UPS (uninterruptible power supply) that has a battery so if the power goes out, your computer keeps humming along without missing a beat.  The better ones also help with brown outs (low voltage) and have much better surge protection than the average stand alone surge protector.  If there is a Costco (Price club) near you, they have a great deal ($99) on a Tripplite 1000 or 1100 watt unit that I have in use in multiple locations for my home theater system, my office file server, cable modem, router, switches, even my office phone system has one.  It even has a nice LCD display showing you the current voltage and the state of the internal batteries charge.  During recent blackouts, my entire office computer and phone systems stayed up for about an hour while I took care of business and gracefully turned things off as needed.

I think one of these units would help you a lot.

---

### Post by GMachine_24 on 2007-07-14
MG:

Hi. Thanks for your comments.

I did some research last night after making the post about getting a new surge protector and realized that - as you suggest - what I really need are some new UPS units.  I do have UPS devices - I think I mistakenly used the terms interchangeably. Anyway,  I think you are right that the batteries have died on some units. I appreciate the info you gave me re: the Tripplite unit. We don't have Costco but we do have Sam's Club so I will check that out.

I, too, have a UPS unit for my cable modem and Lingo (VOIP) modem (?) so when the power goes I still have phone service.

I usually keep up much better --- ok there right now as I was typing this there was a power surge/spike/drop (lights dimmed, UPS units beeped)  but everything remained running. I really cannot believe the third-world quality of the local power grid. And I am sick of dealing with it. But until I move, I will have to. 

gm

---

### Post by mgmiller on 2007-07-14
I know what you mean.  I was just in Florida visiting my mom for a week and the power would flicker often.  She also lost her cable tv signal a lot.  A very different experience from what I'm used to.  The power failures in my office I mentioned above were the first in 2-3 years that I can remember.  We had 2 a few days apart.  During the first, my whole office was unusable.  I got the UPS's and during the second it was almost a non-event.

Anyway,  here is a link to the Costco store finder.  If you scroll down a bit to Florida, you will see there are  quite a few in your state.  Click on the one nearest your home for more info.  They are a great place to shop with a very liberal return policy and high quality products.  (No, I don't work there or own stock in the company)

Good luck...

[http://www.costco.com/Warehouse/Location.aspx?country=United%20States&lang=en-US]("http://www.costco.com/Warehouse/Location.aspx?country=United%20States&lang=en-US")

---

### Post by GMachine_24 on 2007-07-17
Thanks again for your continuing posts.

Ok, so.... just to bring people up on my fascinating modern-power-grid-vs-computer saga:

1. I might as well get the embarassing one out of the way first: When I went to replace the UPS for this system I *discovered* it has two sets of plugs - three plugs are just surge protection, three are surge protection and battery back up. Guess which one the computer genius had plugged the PC box into? Right - the side without battery back up. So, I moved the plug to battery back up and despite a hellish thunder storm yesterday the computer has been running through steadily.

2. I have three Linux computers - 3.5 if you count one of my laptops which is dual boot - and I did memtest's on the memory in the other two. Everything was fine. So, I took a 500 MB module from one of those and put it into this computer - the PIII which had all the trouble - and everything has been fine. (More on this in a minute.) Also, I took the modules from this computer - which tested bad - and retested them on the other Linux boxes and .... voile.... no errors. On either machine. Which lead me to . . . 

3. Even though the 500 MB module tested good in this PIII computer, I figured there had to be another problem; I checked the CPU/fan for dirt/dust/circulation, check the CPU temp - all of this was fine. So, I installed a new power supply. It is a *generic* one but one that came in the computer cases I previously used to build computers I sold online - they had a zero percent return rate. Now it has been 3/4 days and, even though the computer is running a little slower (500 MB vs 768MB SDRAM before) other than that, no problems. No crashes; no freezes. I ran everything I could remember that previously caused the computer to crash or freeze and all is well. So far.

I am still concerned about the MB and CPU as, if it was the power surges that did in my previous power supply, obviously the damage could have extended to the MB and CPU. I am waiting to see what happens.

This situation reminds me a lot of the toughest part of PC trouble shooting when I was *in the business*: bad memory can cause many different errors and it's difficult to pin down a problem when you keep getting mixed signals. Same for a bad/overheating CPU - crashes, crazy activity by a previously solid program. And, add in a possible bad power supply and the potential problems are almost endless. And, almost impossible to identify unless you have many desktop analyzers (which I don't) or other computers you can use to test components. Many people do not have the latter - which can make troubleshooting and fixing a real drag.

I write all this only because this post is in the *absolute beginner talk* and, perhaps, someone with similar problems and not much experience troubleshooting his/her computer will find the information useful.

As far as the PIII computer here, it's running this week on the 500 MB stick and then, if all continues to go well, this weekend I will add back memory to bring it up to 1 GB. Yes, I know it's an old CPU, etc. But, as I  said in a previous post, it does what I need it to do and Linux is not the hog that other unmentionable OS is.

Cheers everyone.

gm

---

### Post by mgmiller on 2007-07-17
> three plugs are just surge protection, three are surge protection and battery back up. Guess which one the computer genius had plugged the PC box into?

I'm sorry, but as a fellow 'puter geek, I have to laugh at that....:lolflag:

Your memory inconsistency, reminds me of a similar problem I had a while back.  Memory sticks were causing crashes and bad mem test results in one machine, but when I moved them to another, they mysteriously tested good and ran fine, for a while, then, same problem.  

What I discovered and what has kept the problem fixed for over a year now is that the memory sockets and pins on the memory had both developed an _invisible film_ of oxidation.  When I took the memory out of the socket and plugged it back in again, some of it wore off and good contact was made, for a while, till it oxidized again.  I know, they are gold plated and are not supposed to oxidize, but I live on an island, surrounded by salt water and EVERYTHING oxidizes here.  

I went to Radio Shack and bought a Deoxit Pro Gold Kit (Radio Shack part number 640-4338 ) consisting of 2 sprays, one is a cleaner and the other is a protector.  This has fixed many many intermittent electronic problems for me.  

I have used it on the PCI slots and memory slots on my mobos, on telephone and network cable connectors, charging cradles for cordless phones, and the most interesting was the plug for the keyboard inside my laptop computer.  The keyboard was going crazy, intermittently losing keys, I traced it down to the internal ribbon connector plug by unplugging and plugging it in a half dozen times to clean it, but that would only work for a few days till the problem would come back.  One shot with the progold kit and it has been flawless for over a year now.  

I highly recommend this product!

---

### Post by GMachine_24 on 2007-07-19
Hey: 

Thanks for your latest post. All continues to go well with all computers - despite a few spikes/disruption. All computers keep running now.

Reminds me of the time a friend of mine, then a financial adviser with Raymond James, bought a new computer from HP. Couldn't connect to the Internet (this was back in the 56K modem days). She or her assistant spent hours on the phone trying to solve the problem. Of course, everyone blamed the other parties. To come to a conclusion here, I got on the phone with her assistant and after talking to her for 10 minutes, suggested she move the telephone plug going into her modem from one jack to another. She said she'd already done that numerous times - I asked her to do it one more time, to humor me if nothing else. Of course, problem solved. Go figure.

Anyway, the oxidation suggestion is a good/interesting one. Especially since:

a) I live in St. Petersburg, Fla.
b) my home is less than half a mile from the bay
c) I run into the same problems - e.g. these speakers I really like ... whenever I adjust the volume I get static-static-static. Remembering a suggestion from a stereo fix-it guy many years ago, I whirl the on/off knob back and forth until some of the static disappears - but it never completely goes away. This kind of thing has been driving me crazy and I will give your suggestion a go - with that spray.  I figured it was oxidation on the control knob leads/brushes inside the speakers  (if they even have brushes any more) but I didn't know what to do other than the bit where you try to wear off the oxidation with repetitive motion/pressure.
d) Some of the hardware I use is considered ancient in the computing industry . . . allowing for enough time for some good oxidation build up.

As an aside . . . I broke down and bought a Compaq notebook with Vista Home Premium. Curiosity got the best of me - its' a Pentium dual core with 1 GB of memory (another GB is on its way from New Egg); 80 GB HD; dual-layer CD/DVD writer; and a nice screen . . . $450. I figured it wasn't going to get much better than that for awhile - but I'm probably wrong. Except for a shameless amount of advertising built in to the start-up process, all has gone well so far - but it definitely needs the extra GB of DDR2 (which is amazingly cheap - like $40).

I will install Linux on the new laptop as soon as I figure out how to get the Broadcom wireless card on my old XP laptop working. It is driving me crazy.

Ok so this is way more than anyone should post at one time - it's just that I was going to the Devil Rays baseball game but my frriend called to inform me that - surprise - today's game was a 12:15 start and seeing as how we were planning on getting there at 6:00 . . . well ... I'm sure you can see the problem.

Take care. Thanks for your ongoing tips. Do you run just Linux boxes or do you have Apple, Windows, etc?

gm

---

### Post by mgmiller on 2007-07-20
> Take care. Thanks for your ongoing tips. Do you run just Linux boxes or do you have Apple, Windows, etc?

I own a total of 11 computers.  10 are desktop machines and one laptop.  5 of the desktops and the laptop are in my office and they all run XP exclusively, due to the mix of special software my business uses.  These machines are all connected to the internet via a shared broadband connection with 30 mbit down and 5mbit up capability.  I have never had any problems with virus/spyware, etc and they are all very reliable because I never install anything they don't absolutely need for their jobs.  They also get defragged regularly and run antivirus and multiple antisypware utilities.  For me, XP has been an acceptable, but expensive sollution in my office.  

The remaining 5 machines are on my home network.  3 are XP and 2 are Ubuntu.  Of the 3 XP machines, 1 needs to maintain compatibility with my office software to run backups, 1 is in my daughters bedroom and is almost never used since she moved out and the 3rd is part of my home theater system.  This 3rd machine is the next one I will convert to Ubuntu, when I don't feel so lazy.  

The 2 Current Ubuntu boxes are what I consider my "main computers".  Most of my home computing time is spent on these 2 machines. The one I am using to send this post also functions as my home file server and contains music, family pictures and videos, etc.  It is networked to all the others and I can watch things on the big TV in my home theater system or on the 37" LCD in my bedroom via the "bedroom Ubuntu" box.  All very great fun and impresses the neighbors, etc..

With the exception of the Dell laptop, I built all the other machines, which I have been doing since the days of DOS 3.something.  I believe, as long as you pick the right hardware, installing Ubuntu (or a few other Linux distros) is the easiest, fastest OS install.  I have gone from a freshly built "pile of parts" to a totally working internet connected computer is as little as 15 mins.

Just for fun, one time I did a quick demo for a friend where I took a bunch of spare parts I had laying around and just plugged everything together on my desk.  No case, just bare parts laying around, cables going every which way, no hard drive, just an old CD-rom drive attached and booted it off an Ubuntu Live CD.  Within 2 mins, I was surfing the internet, to his total amazment.

Well, I'd love to stay and chat some more, but I need to get to work. 

Good Luck with the Radio Shack Progold spray.

---

