---
title: "RAM Upgrade went wrong, so wrong"
date: 2006-04-22
forum: Absolute Beginner Talk
---

### Post by legolas on 2006-04-22
I have an MSI 875p Neo motherboard, and I had 4 512RAM for a total of 2Gigs, and I upgraded to 4 1Gig sticks from Corsair(TwinX2048-3200), so a total of 4 Gigs.  I would think this would improve my systems performance dramatically but it actually got about 10-15 times slower!  It takes forever to boot up and then it is just slower than molassass.   I am dual booted with Windows XP and it doesn't seem to slow Windows down too much.  I checked with the Corsair web site and it should be compatable with my motherboard.  Do I need to configure it in some way?  I thought I could just stick them in there and let the magic begin!   Please don't tell me I have to send the memory back.  I live in Japan and it would be a HUGE pain in the Royal Rectum!  ](*,)  Any help would be greatly appreciated.

---

### Post by Mustard on 2006-04-22
Just guessing here, but I'm thinking you might need to change to a different kernel if you are using that much RAM.  Which kernel version I am not sure though. Depending on which kernel you need, it could be pretty straightforward to change it (if it is necessary at all that is)

Can you give the output of this command so we can see your current kernel version?

```
uname -r
```

What type of CPU are you using?

---

### Post by legolas on 2006-04-23
Thank you for the quick reply.

$ uname -r
2.6.12-10-686

---

### Post by legolas on 2006-04-23
Oh, my cpu is an Intell 2.66 GHz

---

### Post by Mustard on 2006-04-23
[QUOTE=legolas]Thank you for the quick reply.

$ uname -r
2.6.12-10-686[/QUOTE]
Well, your kernel is the already the one I thought it should be ie 686 kernel.  So I guess that option is down the drain. :)

My experience with installing RAM is pretty limited, so I'm not sure where to go from here.

---

### Post by syg00 on 2006-04-23
Looks like that kernel comes with highmem turned on by default. Try the following> grep -i highmem /boot/config-2.6.12-10-686Check "CONFIG_HIGHMEM=y"  is set.

---

### Post by Jason_25 on 2006-04-23
Did you run memtest after you installed the ram?  It also shows memory bandwidth so maybe you could compare bandwidth between 2 gigs and 4 gigs.  It's not surprising to me that your system got slower.  Generally, as you add memory your system loses bandwidth and gains latency because it has to deal with the overhead of the extra modules.  Often, the system will have to increase latency timings and command rate (or the intel equivalent) which together are IMO, a huge hit on performance.  On most lntel systems these things are taken care of automatically as you add the memory.

---

### Post by legolas on 2006-04-23
Thanks guys, I really appreciate your help!
However, I don't even know what a memtest is!  I am in a little bit over my head, here.  
Here is the out come of the command, syg00:

grep -i highmem /boot/config-2.6.12-10-686
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HIGHMEM=y
# CONFIG_DEBUG_HIGHMEM is not set

Jason 25, I don't even know what a memtest is yet.  Talking about that 'latency timings' and 'command rate', can I adjust those or, is there something that I can do to make the RAM I bought work, or am I up the river without a boat?

---

### Post by Bartender on 2006-04-23
I'm somewhat familiar w/ memtest in Windows, not Linux.  Memtest is a simple program that runs before your OS starts.  It'll put your RAM thru various tests, cycling over and over until you ask it to stop.  Some folks run it overnite and check in the morning to see if they got any faults.  
I'm not sure what Jason meant by checking bandwidth.  
Memtest can be run in Ubuntu from the grub menu.  You'll see it as one of the options when grub comes up asking which OS you want to run.
As an option, you can d/l memtest, follow the instructions to make a bootable floppy from the d/l, tell your BIOS to boot 1st from A drive, then restart the machine with the floppy inserted.
What, 2 gig's wasn't enuf?  :rolleyes:

---

### Post by InterNut on 2006-04-23
if im not mistaking (wich i am verry often) i think you can press ESC just when you boot up (after POST) when grub is loading, there i think you can select "memtest"....

but dont bet any money on my tip.... im a newbie...

**Edit: i didnt see that Bartender already answerd that... *crap* (:

---

### Post by YuHoo on 2006-04-23
This may mean nothing, but it could be of added comfort. I searched for incompatabilities in the ram/motherboard and came up with this [http://www.msi.com.tw/program/newsrelease/news_page.php?UID=191](http://www.msi.com.tw/program/newsrelease/news_page.php?UID=191) . Seeing as MSI launched this with TwinX ram, you might feel better about finding some other path than returning it. Also, you might want to check the bios settings for the ram. When I tried corsair my bios misread it (that's partly why I only buy Geil:mrgreen:)

The misread timings actually seems to be a possible problem [http://memtest.corsairmemory.com/print_report.aspx?model=K8N+Diamond+Plus&pn=TWINX2048-3200C2&id=5099](http://memtest.corsairmemory.com/print_report.aspx?model=K8N+Diamond+Plus&pn=TWINX2048-3200C2&id=5099)
It is advertised at 2.3.3.6 but read at 3.3.3.8 (check out [http://www.tomshardware.com/2004/01/19/ups_and_downs/](http://www.tomshardware.com/2004/01/19/ups_and_downs/) for a nice guide to how to understand ram timings) and if it is lower than or sometimes just plain wrong it can cause some really nasty problems. I hope this helps, but hang in there, RAM is a finicky thing that I have thrown out windows before.

---

### Post by legolas on 2006-05-08
Weird thing is that windows read it alright, but Ubuntu really slowed down-if I were to round down, I would stay 'stopped'.

---

### Post by legolas on 2006-05-18
Ok, I did the memtest and it said:
memory 3711m     1743mb/s

That doesn't make any sense does it?!  I should have 4 gigs of memory not 3177megabytes!  or am I reading that wrong?   It really gets me because Windoze handles the new ram fine.  

What about this?

grep -i highmem /boot/config-2.6.12-10-686
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HIGHMEM=y
# CONFIG_DEBUG_HIGHMEM is not set

This says highmem is ON right?

Also I set the CAS to 2.5, 3, 3, 7,  like the ram gurus' said to on their RAM forum.  The memtest also did not give me any errors so I am assuming that this must be a kernel problem.  Which makes me wonder: 

Am I using the right kernel?

Please linux know-it-alls!  Help me!
Thanks

---

### Post by pbaehr on 2006-05-18
The amount of RAM you're showing is fine. One would expect 4 gigabytes to be 4000 megabytes but in the real world that's not the case. There is a technical explanation for this but I can't remember it. Perhaps someone else can go into more detail but as a general rule the exact number will always be lower than the nice round number we expect. Same goes for hard drive capacities and processor speeds.

The rest of your problem is completely beyond me, so all I can do is wish you luck!

---

### Post by syg00 on 2006-05-18
I'd be inclined to pull out all the memory and start playing - each stick by itself, then add another, ...
See where it starts playing up, and see if you can isolate (hopefully) one stick.

Not very scientific, but might help.
As an aside, Windows seems *much* more tolerant of timing issues.

---

### Post by legolas on 2006-05-18
It doesn't seem to be any bad sticks because, I got no errors from the memtest and like I said there is no problem with Windoze.  If I just put in half(2 of the 1 gig sticks) and use 2 of my old 512's, there is no problem.  But when I go to all 4,  the computer goes into Million Dollar Man speed. (Very, very slow)
What about that HIghmem setting, does it look ok?

---

### Post by macdo on 2006-05-18
The size problem is just maths.

Somebody who wants to sell memory counts in decimal:1000 (10^3) = 1 kilo, 1000 kilo = 1 mega, 1000 mega = 1 giga. 
Computers count differently (in binary) : 1024 (2^10) =1 kilo, 1024 kilo = 1 mega, 1024 mega = 1 giga
So when you bought your RAM, you bought 4,000,000,000 bytes of RAM. That means 3.72 gigabytes (binary) or 4 gigabytes (Decimal). I'm told that we should actually be calling the binary version kibibytes, mebibytes and gibibytes, but that hasn't really caught on. 
It could be worse - if you had bought a 4TB hard drive, you'd only get 3.6TB on your computer...

---

### Post by apollyonis on 2006-05-18
If I'm not mistakened, there's something wrong with one of the two 1 Gig modules that you didn't test last. The memtest is supposed to show the correct amount of 4096mb; the lesser amounts apply to hard disks (I.E. 1gig is less than 1024mb). - the fact that it shows 3711mb implies that either it isn't being allocated correctly or quite simply...you have one bad Corsair module. I'd take out each and test them one by one. It may be a pain, but at least it'd show whether it really is a bad memory module or not.

---

### Post by macdo on 2006-05-18
[QUOTE=apollyonis]If I'm not mistakened, there's something wrong with one of the two 1 Gig modules that you didn't test last. The memtest is supposed to show the correct amount of 4096mb; the lesser amounts apply to hard disks (I.E. 1gig is less than 1024mb). - the fact that it shows 3711mb implies that either it isn't being allocated correctly or quite simply...you have one bad Corsair module..[/QUOTE]

you're right - but not when the big G is hit, it appears: the maths work...

---

### Post by apollyonis on 2006-05-18
Odd, because I just ran the memtest option from GRUB and the gigabyte shows up as 1024mb. :???:

---

### Post by macdo on 2006-05-19
My guess is that your RAM is from a different manufacturer - or that you have two 512 MB sticks...

---

### Post by legolas on 2006-05-19
I talked to 3 Ram professionals and they all said it was the right kind.  Memtest said no errors.  They are definately 1 gig sticks, and they work fine in Windows so it to be a Ubuntu/linux setting problem, or a kernel thing I think.

---

### Post by Jason_25 on 2006-05-19
So what kernel are you using?  You will surely need something other than the default kernel for that much ram.

---

### Post by aaarg on 2006-05-19
i read an article recently (i am sorry i can not find the link yet, when i find i will submit here) that based on performance tests suggested that more than 1 gig was actually slower and 2 was an absolute waste and you are using 4.

why not just remove some and put it in another machine?

---

### Post by legolas on 2006-05-20
Is this the way it should be?

$ grep -i highmem /boot/config-2.6.12-10-686
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HIGHMEM=y
# CONFIG_DEBUG_HIGHMEM is not set

---

### Post by legolas on 2006-05-24
C'mon guys, "throw me a freaking bone, here."
-Dr. Evil
Isn't there some RAM wizard out there who knows what the heck I should do?  Is the 686 kernel the one I should have at least?  It really gets to me because my Windoze handles the 4 gigs just fine.

---

### Post by nanotube on 2006-05-24
[QUOTE=legolas]Is this the way it should be?

$ grep -i highmem /boot/config-2.6.12-10-686
# CONFIG_NOHIGHMEM is not set
CONFIG_HIGHMEM4G=y
# CONFIG_HIGHMEM64G is not set
CONFIG_HIGHMEM=y
# CONFIG_DEBUG_HIGHMEM is not set[/QUOTE]

yes, this looks right, highmem is configured...
i am not sure what the problem is, though.
you could always just stick with 3g of ram (2x1g + 2x512m) if nobody comes up with a solution...

---

### Post by legolas on 2006-05-24
Yeah, that is what I am doing, but that is like flushing $100 bucks down the toilet!  Anyways, I read that linux can handle HUGE amounts of RAM and I can't even get it to handle 4??!  Big bummer.

---

### Post by user1397 on 2006-05-24
I don't think that your system would ever chew up 4 GiB of RAM, even if you had some intensive application.  srry if i sound rude, but can you sell your ram? (perhaps ebay?)

---

### Post by nanotube on 2006-05-24
another thing i can suggest - download a livecd of dapper, boot it, and see if that works ok. if it's ok, you can just upgrade to dapper. :)

---

### Post by legolas on 2006-05-26
[QUOTE=nanotube]another thing i can suggest - download a livecd of dapper, boot it, and see if that works ok. if it's ok, you can just upgrade to dapper. :)[/QUOTE]

I just tried Dapper Live.  It did alright- I mean it was slow, but I think that was just normal CD speed- same as when I use any other live cd.  I guess the next thing to do is to check the speed of a different live cd with the 4 gigs to compare to the Dapper live cd speed.  If the other live slows down like my system does when I stick in the 4 gigs of RAM, I can assume that the Dapper will work with the 4 gigs right?  I know, I know, "when you 'ASSUME' you make an '***' out of 'U' and 'ME' ":-#   
By the way everyone,  Dapper looks good!  I can't wait to see the new release next month!"

---

### Post by legolas on 2006-05-26
[QUOTE=nanotube]another thing i can suggest - download a livecd of dapper, boot it, and see if that works ok. if it's ok, you can just upgrade to dapper. :)[/QUOTE]

Ok, I am a moron.  I forgot to put in all the RAM when I tried the Dapper live.  It is such a pain in the rectum to put in take out and put in again.  I would just like to leave it in but it is TOO DANG SLOW!  Unfortunately, when I put in the 4gigs of RAM the Dapper live  was just as slow as Breezy.  However, the live cd is the 386kernel right?  So maybe I need to install the 686 on the Dapper too.  (It will probably be just as dissapointing as the 686 on Breezy).  I will be switching to Dapper for the Japanese support anyway.  There has got to be a way.  This is crazy.](*,)

---

### Post by nanotube on 2006-05-28
[QUOTE=legolas]Ok, I am a moron.  I forgot to put in all the RAM when I tried the Dapper live.  It is such a pain in the rectum to put in take out and put in again.  I would just like to leave it in but it is TOO DANG SLOW!  Unfortunately, when I put in the 4gigs of RAM the Dapper live  was just as slow as Breezy.  However, the live cd is the 386kernel right?  So maybe I need to install the 686 on the Dapper too.  (It will probably be just as dissapointing as the 686 on Breezy).  I will be switching to Dapper for the Japanese support anyway.  There has got to be a way.  This is crazy.](*,)[/QUOTE]
heh, crazy indeed. 
you should try posting your problem on the dapper section as well. maybe someone on there will have some ideas for you.

---

### Post by legolas on 2006-05-29
Ok, I upgraded to dapper, but no good.  Slow slow, real slow.

---

