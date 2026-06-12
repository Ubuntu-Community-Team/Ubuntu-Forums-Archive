---
title: "i think my hard drive is going bad. not sure."
date: 2007-09-14
forum: Absolute Beginner Talk
---

### Post by graigsmith on 2007-09-14
so, i think my hard drive is going bad. lately i think it has been making wierd noises.

in my messages log. theres a thing that looks like this.
```
Sep 14 12:32:30 Graig kernel: [  201.028724] hda: dma_intr: status=0x51 { DriveReady SeekComplete Error }
Sep 14 12:32:30 Graig kernel: [  201.028733] hda: dma_intr: error=0x40 { UncorrectableError }, LBAsect=450152891, high=26, low=13945275, sector=450152890
Sep 14 12:32:30 Graig kernel: [  201.028746] ide: failed opcode was: unknown
Sep 14 12:32:30 Graig kernel: [  201.028752] end_request: I/O error, dev hda, sector 450152890
```

the thing that has me stumped is WHY, it's practically brand new...  did ubuntu kill my hard drive?  or did i just get a bad drive?

---

### Post by w4ett on 2007-09-14
There is a long thread in the Laptop and Hardware sub-forum for possible solutions:

[http://ubuntuforums.org/showthread.php?t=508576&highlight=is+ubuntu+killing+harddrive](http://ubuntuforums.org/showthread.php?t=508576&highlight=is+ubuntu+killing+harddrive)

---

### Post by CaptainInsaneO on 2007-09-14
If it's make "weird" noises, that could mean any number of things. If it's clicking, the servos that move the drive head (the "laser" *makes Dr. Evil quote signs*) are going bad. If that's a new drive, I've seen this problem the most in new Maxtor drives.

If it's grinding, that is a very, very serious problem that could result in complete and total data loss. (The drive head is crashing against the platters and possibly scratching them up.)

Either way, if I were you I would back up all my data on that drive ASAP and send it back for a refund/replacement, because it's most definitely a bad drive, not a problem with Ubuntu.

---

### Post by graigsmith on 2007-09-14
so, this sucks.  makes me wonder if i should go back to using windows.  did they fix this bug? or what?  or should i use an older version of ubuntu? or go use debian stable?

---

### Post by w4ett on 2007-09-14
Here is the actual Bug Report fix:

[https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.17/+bug/67810/comments/60)

Apparently it has been fixed in Gutsy too, and it is due out the 19th of next month as a stable release....SO........

Apply the patch now, upgrade to the Gutsy Beta, or wait a month. :)

---

### Post by graigsmith on 2007-09-14
so, wait, it has NOT been fixed in feisty? thru updates or anything?   so every time my computer reboots or shuts down.  ubuntu has smacked the hard drive heads around?  :confused:

---

### Post by graigsmith on 2007-09-14
it's a desktop, and i leave it running all the time. and  therefore it shouldn't have done any damage to my hard drive. cause really i only reboot it. or reset it occasionally.   and the bug only happens when you shutdown the system, and i rarely do that.

---

### Post by ev5unleash1 on 2007-09-15
If you keep it on alot i don't really see the problem. It could be your hdd going bad but on the machine what is teh position of the HDD if it's lop sided or something there are numbers of things that could happen.

---

### Post by ramjet_1953 on 2007-09-15
It certainly sounds like you should seriously consider backing-up at least your /home directory.

As far as the issue of Linux not parking the heads correctly on your HDD, it was basically FUD.

Yes, there was a problem, but it was fixed with a kernel update in Feisty. Even if it had not been fixed, the claims of it killing your HDD were not valid. Someone did the numbers and it worked out that even with forced parks, it would take years to exceed the maximum specified by the manufacturers.

So no, if your HDD is failing, it was not caused by Linux, or any other OS, for that matter.

I suggest that you go onto the website of your HDD manufacturer and download the diagnostic software that most of them provide. It is sometimes available as an iso image that you burn to a CD and then you boot from this CD and run the diagnostics.

Regards,
Roger :cool:

---

### Post by tgalati4 on 2007-09-15
I think it's a normal part of bootup as the hardware detection algorithm tries different modes of addressing the hard disk.  The modes that don't work will give an error.  As long as you don't see a continuous stream of these errors, I think it's OK.


Besides, if your machine works, then don't worry about it.  When your machine freezes and then you start getting disk read errors (they are obvious in the log files) then you need a plan B.

---

### Post by graigsmith on 2007-09-15
so, i grabbed a new hard drive. and ubuntu cant even see it, most of the time.. it's a 500 gig hard drive. my old one was a 300 gig.  i think my motherboard went bad.  which is wierd because i ran a test for 8 hours or so using the memory tester on ubuntu and it didn't get any errors.  so i guess the connector went bad on my motherboard.   or mabey the power supply went bad.  but i figure if the power supply was bad i wouldn't get a good memory test after 8 hours.  besides some of the connectors on the back of my motherboard went bad. so it's likely the motherboard.  (gonna test the powersupply just to be certain)   :(

on the bright side, i get to order some new hardware....what's a good motherboard to get that's well supported in ubuntu?  my current processor is an athlon 2800+  and i'm thinking of just buying a replacement motherboard... but i might upgrade to a better chip and ram.  mabey i should get one of the new nforce boards a dual core cpu.   or perhaps a new intel board with intels onboard video?  which works better in ubuntu??  i play wow in wine. so i know nvidia's drivers work for this. but how about intels onboard graphics? do they work well in compiz and 3d games played thru wine?   i am highly tempted to go intel because of the open source videocard drivers.  

anyone got any hardware suggestions then?

---

### Post by CaptainInsaneO on 2007-09-16
I used to use an ASUS intel board, before I had an nVidia graphics card. The onboard video works fine in linux, but Compiz with a lot of eye candy turned on tends to lag and after awhile, windows go black because I was running out of video memory. And good luck playing a game like Nexuiz.

I switched out my old mobo a couple months ago for one of [these]("http://www.newegg.com/product/product.asp?item=N82E16813188019") and it went way smooth. Linux didn't even hiccup (like windows did). I haven't tried to run SLI on this board in ubuntu yet because I can't afford another 8800gtx yet, but I assure you that my video card was a breeze to set up and it works great!

Also, I commend you on thinking about going intel... just like nvidia is bashing ATI (amd), intel is now doing the same. I've seen the actual numbers (look to MaximumPC) and intels are actually faster now than AMD is. But it's up to you what you go with, of course.

Hope this helps.

---

### Post by graigsmith on 2007-09-17
so, i was at best buy and saw an acer computer for sale. so i grabbed it.  seems to support ubuntu from the live cd.. but it came with vista home premium. so i am playing with it for the time being.  got lazy and decided not to build my own computer, since this is about the same price. and i diddn't have to put it together.  

But, vista is actually pretty nice. all i have heard is horror stories from it.  but it's actually not that bad. and it seems more organised how i like it. though explorer is annoying compared to the user friendlyness of nautilus.  plus the thing about it not being free software.   it's missing alot of functionality that i had with ubuntu.  in the end i'll probably format it. but it's nice to experiment with it.

---

### Post by CaptainInsaneO on 2007-09-17
Vista has already had a service pack (of sorts) released, I've heard a lot of the annoyances that were intially there on release have been fixed. Keep in mind that a lot of people are having trouble dual-booting Ubuntu and Vista, because Vista doesn't like to play well with grub.

Edit: Here's a link for some more information: [http://www.pro-networks.org/forum/about78184.html](http://www.pro-networks.org/forum/about78184.html)

---

### Post by graigsmith on 2007-09-17
eh too late, i formatted vista. it was fun to play with for a day or so. but i couldn't read my camera raw files.  without buying some 60 dollar program. f that lol.  anyways, i called acer, and they will send me the software for free. < i payed for it with the computer so i should have it on disk, thats my opinion.

got ubuntu working. and booted, and i have both hard drives connected, copying my home folder over now.  Yeah, the old hard drive from my old computer seems to be working great in this new computer. had to remove the cd rom to connect it.   thankfully ubuntu is so easy to restore. copy the files and it's done.  and hey. the video works great with this new onboard nvidia card :)

---

