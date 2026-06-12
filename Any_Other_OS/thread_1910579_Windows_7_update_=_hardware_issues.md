---
title: "Windows 7 update = hardware issues"
date: 2012-01-17
forum: Any Other OS
---

### Post by sabatron on 2012-01-17
Sorry to bug you guys on the linux forums about this but I don't know where else to turn and people here seem to be more competent than other forums I've tried.  I bought Windows 7 pro a couple years ago for $30 when they were offering a student special.  I had always used linux up until that point but I figured it would make my life a lot easier if I just sucked it up and got Windows 7 in order to use school software and play games easier.  Now I have no use of my computer because a windows update went wrong.  Here's the story..

I went to shut down my computer and Windows started to do an update.  I went to bed and then the next day I go to turn my computer on and everything seemed fine.  the mobo startup screen was shown and the windows start-up screen came up... only it looked a bit different than usual... I snapped a quick picture of it on my phone that you can look at here [http://a4.sphotos.ak.fbcdn.net/hphotos-ak-ash4/402989_3110278840650_1374726964_3256260_1448357778_n.jpg](http://a4.sphotos.ak.fbcdn.net/hphotos-ak-ash4/402989_3110278840650_1374726964_3256260_1448357778_n.jpg)

it said "Applying update operation 13601 of 13601 (\Registry\Mach..)"

and then the screen went black and windows 7 never booted up.  I looked down at my tower and I noticed my cousin's portable external hard drive was plugged in.  I had no idea it was there when I shut it down the night before.  I've left my external in my computer dozens of times though and never had any issues with microsoft updates.  I took his external out and plugged it into my laptop.  there was a very strange folder on it named with a bunch of letters and numbers and i could not open it and the capacity was 0 megs.  i looked at when it was last modified and it was the night before right after i had shut my computer down and when it started to install the update.  AWESOME.  the only conclusion i was able to come up with is that the update started to install on the hard drive for some reason (maybe my cousin's external was larger than my computer's hd and it defaulted to it?).  So anyways i was able to delete the file off of his external and then I manually shut down my computer because the screen was still black from bootup.  I wait a few minutes and then turn it back on.... i get nothing.  even the mobo start up screen does not boot up and the computer boots up really fast as if there is no hard drive.  I assume that my hard drive is corrupted and that i have to re-install windows 7 on it.  that wouldn't be such a big problem except I can't even get into my mobo's bios to change the boot sequence to something besides the hard drive (like a cd rom with win7 pro).  the weird thing is, if the hard drive is corrupted why is my mobo not booting up?  i hear the beeps but i get nothing.  this also leads me to think what if it's my graphics card... I mean it would make NO sense that my graphics card somehow stopped working over something like this considering it was just working minutes before when windows was started up with that funny message.  but the fact that i'm not getting anything on my screen leads me to suspect that.  so basically i can't use my computer because when i go to start it I get a black screen... my monitor is working fine but nothing comes up on it... not even the mobo startup screen so i can't even reformat the drive... any ideas about how I can fix this?  did my pc just break or something?  why am i having hardware issues like this because of a microsoft update that went wrong?  Do I need to buy a new mobo/hd/graphics card?

thanks for any help on this and i tried to supply as much info as i could about the whole situation so sorry if this was a very long drawn out post

---

### Post by pricetech on 2012-01-17
sevenforums.com

---

### Post by xyzzyman on 2012-01-17
Some questions:

Do you have experience working inside your computer tower?

Does your motherboard have an onboard video card to fall back to if you were to remove the video card you have installed.

Is it the normal beeps from booting or are they different than normal?

---

### Post by JonUK76 on 2012-01-18
Windows updates can't cause hardware problems like a failed graphics card. They also won't install to an external drive (they need to be installed to your main drive to replace the files they are supposed to be updating).

It could be the graphics card, but the only way to really test that out is to either test your card in another machine to see if it causes a problem, or use another card in your PC (or switch to onboard graphics if available).

I had a graphics card fail last week actually.  I too thought it was some software issue at first because Windows was extremely unstable, with the mouse pointer skipping about slowly, but Linux appeared to be booting and working OK. But it got worse rapidly...  Soon I was getting artefacts on all the screen output (in Linux too).  A few hours later there was no output at all from the card.

---

### Post by sabatron on 2012-01-18
Thanks for all the ideas guys.  so i am starting to think it may be the graphics card as well.  i have a moderate understanding of what is inside my tower because i chose all of the hardware and a friend helped me assemble it together.  this is what my machine looks like:

OS
    win 7 pro x64
CPU
    intel pentium duo-core e-5800
Motherboard
    gigabyte GA-EP45-UD3P
Memory
    g-skill 2gig sticks ddr2 x2
Graphics Card(s)
    ati radeon hd 4870
Sound Card
    n/a (on board sound)
Monitor(s) Displays
    acer
Hard Drives
    500 gb western digital caviar blue
PSU
    ocz 600w
Case
    cooler master

and the motherboard i am using unfortunately does not have onboard video.  and the other graphics card i have will not fit the slot because it is from an older computer. also the beeps from the mobo sound normal.  i did do research last night and i found this:

[http://news.softpedia.com/news/Windows-7-Black-Screens-of-Death-for-Some-AMD-ATI-GPUs-132913.shtml](http://news.softpedia.com/news/Windows-7-Black-Screens-of-Death-for-Some-AMD-ATI-GPUs-132913.shtml)

i am using an ati radeon hd 4870 which is on this list. i dont know why i never had issues installing win 7 the first time but maybe this has something to do with it? 

and i know something went wrong with the update because why would the external have that weird folder in it from the update?  apparently if i use another monitor i can see whats happening?  the graphics card has 2 dvi ports so im going to try connecting another monitor to it but im a bit skeptical about whether itll work.  do you think it would matter if i used a vga chord with a vga to dvi adapter on it?  for some reason i am only finding vga chords laying around but my graphics card is dual dvi.  

i have also been meaning it upgrade my graphics card but it seems that ati has issues with win 7... should i try an nvidia card instead?

---

### Post by xyzzyman on 2012-01-18
The VGA-DVI adapter will be fine. That's why those cards usually came with 1 or 2 of 'em. Looks like you also have a good PSU in there also.

One of the updates used the external as a temp folder and personally I wouldn't worry about that file as it's not that uncommon to happen, even from installing regular programs.

Your link also has nothing to do with your card. Those are the mobile laptop versions and it only happens when using a specific type of internal connection inside the laptop. When it comes to compatability with Windows 7 you are pretty evenly matched between Nvidia and ATI and will wind up finding people on both sides that hate the other. On the linux side it's generally understood that especially on desktops nvidia provides much better drivers at the moment and are much more proactive at releasing new drivers to keep up with new xorg changes, etc...

We're all assuming that it seems like the hard drive is actually booting? That there is activity after post? If so then either the card or PCI express slot on the motherboard died (Unless the power connector to the card (if equipped) or the 4-pin connector to the mobo is loose/disconnected.) If you aren't getting hard drive activity then you need to try resetting the ram, trying the ram sticks individually, etc... Although you would most likely be getting POST error codes through the beeps from the mobo.

EDIT: Once this issue is resolved we are going to come to your house if you don't dual-boot with Ubuntu. :) We won't require you to go back to just linux, but you're partitioning that hard drive!

---

