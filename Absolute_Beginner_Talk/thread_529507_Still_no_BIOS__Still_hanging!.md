---
title: "Still no BIOS / Still hanging!"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by jankind on 2007-08-19
I have had some trouble the past few days and still can't get it figured out.
First off, I'm new to Linux and Ubuntu so take into consideration I might not know the obvious...

My problem is that I can't get into the bios and after several tries, all of a sudden now, simply starting up the machine stalls for 3 - 4 minutes and the bios screen doesn't even flash up for a second like it normally does. 

When I go to start up, the monitor sits blank (with the little indicator light at orange, not green)
for 3-4 minutes and then finally goes directly to the Ubuntu sign in screen.
This happens no matter if I try to start up normally, boot into a Live CD, or enter the bios.


This is all new since I started messing around trying to get into the bios. This thing normally fires up in about 40 seconds it seemed.

Any thoughts? Thanks all!

---

### Post by Steve1961 on 2007-08-19
Can you reset the CMOS?  Alternatively try taking the CMOS battery out for 5 minutes.  This often sorts problems out.

---

### Post by Jimmyfj on 2007-08-19
If you have the documentation for your motherboard you'll se a jumper close to the bios chip. This can bee moved to force bios reset. Try moving the bios jumper and then start the computer. After a few seconds, not more that 10 - 15 you shut down the Pc and moves the jumper back and tunr on the computer. Your bios should be reset by then.

---

### Post by jankind on 2007-08-19
Thanks, I'll look at both solutions and see if I can get this figured out. 
:KS Thanks!

---

### Post by jankind on 2007-08-19
Ok..

I tried both and still no dice.
I removed the CMOS battery for a little over 5-6 minutes and then replaced it.
Then I moved the BIOS jumper from pins 1-2 to pins 2-3 and it wouldn't even power on until I switched them back...

The way we're looking right now, it's not even booting up AT ALL. So hanging for 3 minutes  and mising the bios is no longer the problem. It powers on and then...nothing.

This actually started as a completely different issue and I think I keep tugging at this thread and making it worse.

Any other thoughts???

---

### Post by Steve1961 on 2007-08-19
OK, the first thing that comes to mind is faulty hardware - could be your memory, graphics card, or even your mobo.  Make sure you unplug all peripherals and and try and track down the faulty component. First step, reseat your ram and graphics card   Next, if you have two ram sticks, boot with a single stick, and then swap them over.  Next, if you have one, try a different graphics card.  Sorry I can't be of more help, but I've seen this a few times and whenever resetting the bios didn't work it was usually a memory or graphics card fault.

---

### Post by jankind on 2007-08-19
Thanks again, This might be a little beyond my reach but I'll at least try...

---

### Post by jankind on 2007-08-19
OK without doing any of that, I did manage to get into the bios one time. There was something on there that said the CMOS settings were wrong and then I chose  F2 / reset defaults and continue. Now it's back to how it was, eventually getting to the login screen.

ugh.

---

### Post by jankind on 2007-08-27
OK quick update and one more question...

I tried everything here. 
I toggled the bios jumper as mentioned above.
Put in a new battery.
Reseated my RAM a few times.
Stripped down  to bare bones.

Still not booting at all. 
At least when I started this thread, I could get through the post and eventually boot.
No more of that. No beep codes even.  
Is it safe to say that at this point it's most likely the motherboard?
Maybe I possibly damaged something with all my tinkering around?

Thanks for listening!

---

### Post by armandh on 2007-08-27
after trying questionable memory i got  only one line 
Bios check sum error
then
A:\
I was able to boot to dos on the a drive and re flash the bios.
then the reload
really starting from ground zero
UGLY but successful

your bios may be toast and past easy help
I have never done a jtag loading

---

### Post by the.phantom on 2007-08-27
when you kill the bios with the jumper or removing the battery it will not have "the correct checksum" when it first powers up !
that is why you got that message ( it is normal) 
and i think it was telling you that tapping the F2 key is how you can get into the bios and change it 

had you made any changes in the bios since you had it ? ( the time will be off for sure)

and i do know that on windows it would freak out if the time was before a file was written ( say the time came back with a year of 2002 and you had updated a file in 2007!

so i would say get back in the bios and change times or at least correct the system time !

---

