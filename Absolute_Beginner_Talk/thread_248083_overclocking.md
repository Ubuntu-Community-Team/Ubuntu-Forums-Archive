---
title: "overclocking"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by mr_tubaman2002 on 2006-08-31
Im running an old computer with a pentium II and even know ubuntu runs alot faster than when i had windows XP installed i would really like to know how i can overclock the processor to get it to run a little faster.  The computer was given to me by a friend and right now im not sure what kind of motherborad i have but i can find out if needbe.

Thanks

---

### Post by ehonda on 2006-08-31
I have a decent laptop, and mine seems to run faster with ubuntu as opposed to win-ders.

---

### Post by b_martinez on 2006-08-31
Go to the manufacturers site and look up the specs. There may be a way to overclock the cpu with jumper settings. Other than this, you may be outta luck.
Bill

---

### Post by mr_tubaman2002 on 2006-08-31
I know that in windows you can use the bios, is ther a simular way in ubuntu.

---

### Post by kinematic on 2006-08-31
yes....the bios ;)

---

### Post by mr_tubaman2002 on 2006-08-31
ok if feel stupid asking a question like that (aobut the bios).  really the problem is i dont konw how to get to or use the bios if some one could help me of give me a link to a webpage that can geve me some step by step.

---

### Post by mysticrider92 on 2006-08-31
To open your BIOS, press the Delete button while your PC is in the first part of the boot process (before it says loading Ubuntu). You may have to boot up then restart to get to it. I wouldn't advise doing this unless you are sure that you know how. Messing up the BIOS can destroy your PC, forcing you to get a new motherboard, and overclocking voids any warranty, and can fry your system (literally), so be careful.

---

### Post by wpshooter on 2006-08-31
Don't try to overclock.  And I don't think you would be able to on that old of a machine anyway.

If it is stable, use it like it is or get yourself a better, faster machine.

Good luck.

---

### Post by Metacarpal on 2006-08-31
I second that.  Here's a little bit of hardware insight into why overclocking is possible:

When a processor manufacturer produces the chip, they test it at higher and higher clock speeds until it basically melts.  Then they set the processors to run at a clock speed somewhat lower than the last good speed before it burned out.  This ensures that any minor variations in the printing of each chip won't cause any given chip to fry.

Overclocking basically tells the processor to ignore that limit and go faster.  The only problem is, you can't really know how much faster a chip can go without burning out.  Even if someone else says, "I have the same chip and it can do 200MHz more" - he might have gotten a lucky chip, or you might have gotten a slightly flawed one, and pushing yours could cook it.

Also, a faster clock speed means more heat.  If you don't upgrade your cooling system too, it increases the chances of cooking your hardware.  All around, it's better to avoid it unless you really know what you're doing.

---

### Post by Gerg on 2006-09-10
I'm 16 and have been using Windows all my life and decided to try linux, I also obtained an overclockable computer at the same time so I figured why not. Now I know the basics of overclocking but I'm wondering are there any stress testing programs out there for linux so I can make sure my computer is stable at my new speeds. And is there a way I can check to make sure it is actually booting at those speeds?

---

### Post by Klaidas on 2006-09-10
Unless you REALLY know what your're doing, you might better want to just upgrade your hardware. Overcloaking is evil :evil:

---

### Post by Coolit on 2006-09-10
I'm all for overclocking, but I would do some reading into the subject first. 

There is a lot to be gained from overclocking if done correctly, myself I have a 2.2ghz AMD64 3700+ running rock solid at 2970mhz, faster than an FX chip :) for 1/4 the cost. 

It's true what the guys have said earlier though, this will put extra strain on the cpu and it will die earlier than it would have under normal load but I suspect you would upgrade long before the cpu fails. The key to good overclocking is to keep the heat under control :)

---

### Post by Gerg on 2006-09-10
Bump!

I found a program that displays the CPU speed but I'm still looking for a stress testing program. Does anyone know of one?

---

### Post by Thomas,Bakker on 2006-11-13
im also overclocking a bit and had found a very nice howto only i lost the link. i would say google it up.
make sure to whatch the temp.
about the stress test i havent found one for linux but you could use F@H it
lets your cpu run at 100% (of the bios clock speed so if you clocked it at 2.0ghz than the program uses that full 2.0ghz) our anywhere lower whitch is a bit scalable to about 50% cpu usage.
In the meantime the program is designed to help in the research for curing disseases like cancer. take a look at there site  [http://folding.stanford.edu](http://folding.stanford.edu)

so it aint designed as an stress test program but you could try to use it for that pupose. other thing you could trie to do is looking for SuperPi for Linux.

---

### Post by autocrosser on 2006-11-13
You can also run SETI@home--My dual 3.2 runs at a 5% OC (3360mhz)--You should have a system monitor (I use Gkrellm & lm-sensors) to keep a very close eye on temp--AND Make sure you upgrade your CPU cooling system.

---

### Post by Malta paul on 2006-11-14
Hi,
Welcome to Ubuntu. Do be very carefull if you overclock, it is inportant to overclock in small stages and monitor your CPU temp. also check that your system remains stable. [CPU cooling is very Inportant].
My computer has been overclocked from 3GB to 3.33GB for the past 2 years runs great.When I get home from work I could list some temp. monitioring programmes for you, BUT the problem is that with an old motherboard it not likely to have temp. sensors.:( 
My advice to you is to stay with your system the way it is till you upgrade your computer. Good luck.:)

---

### Post by runefreak on 2006-12-16
i must agree take great caution when overclocking  do your homework 
 if you don't you may do what i did the first time i overclocked and burn out the mobo
 i recently overclocked a compaq presario that i was told could not be overclocked lol
 i love th when people tell you that somthing can't be done then you do it
 anyway took a amd k2-6 475 mhz and overclocked it to 528 mhz  runs just peachy
 i benchmarked it with sandra on xp the clock speed is indeed 528 mhz cooling was not an issue
 as i had a larger heat sink and fan laying around i slaped in it 
 all in all it took about half an hour to find the dip switch settings  which was the hardest part 
  evidently there is no way to up the fsb so i had to overclock via motherboard jumpers 
  but reguardless of what anyone says all mobo's can be overclocked to some extent 
   just have to dig around and find the info

---

### Post by tophatandy on 2006-12-20
can you even overclock the pII..


thought it was the only cartrige pentium processor..

if you make it work.. post..

---

### Post by mcduck on 2006-12-20
There is no CPU that you couldn't overclock :D

486/33 was the best one, you could easily make it run over twice it's default speed. Oh, all the good memories ;)

Check the BIOS for FSB or multiplier settings, and it the BIOS doesn't give you those options you may be able to find jumpers on motherboard to change the settings. If neither of these is possible overclocking will be much harder and require some soldering, probably not worth the trouble..

For performance testing I recommend SuperPi, there's a Linux version available. And for stability testing try cpuburn, it's in the repositories.

---

### Post by loopjeremyloop on 2006-12-20
> **tophatandy said:**
> can you even overclock the pII..


thought it was the only cartrige pentium processor..

if you make it work.. post..



the P2 oc'd fairly well - in fact, my first CPU that I bought with my own money was the P2-based Celeron 300a, which was the #1 overclocker at the time.

When I bought it, the 300a cost around 100 dollars, and a simple tweak in the Abit BX-6 changed the bus from 66 to 100mhz... without any effort, that 100 dollar processor outperformed the (then) flagship P2-450, a 700 dollar processor.


I would REALLY recommend heavily against overclocking UNLESS you know what you're doing.

---

