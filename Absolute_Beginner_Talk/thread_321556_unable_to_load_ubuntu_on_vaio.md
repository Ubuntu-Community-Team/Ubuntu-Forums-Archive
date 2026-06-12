---
title: "unable to load ubuntu on vaio"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2006-12-19
[FONT="Comic Sans MS"]Hello and help! My wifes Sony Vaio was attacked and stuffed late last year, adware, viruses, hijackers, whatever.

The local Sony shop said the main drive was dead and they would have to replace at a cost of 10,000rmb, about $1200us. So we bought an entirely new laptop.

I've just got a new seagate disc drive to fit in the sony and tried to load Ubuntu on to it.
It loads the kernel after the initial splash screen and then I get an error that says > Kernel panic - not syncing; attempted to kill init. at the end of a whole bunch of hexadecimal code

I turned it off and tried again with basically the same result > Kernal panic - not syncing; attempted to kill the idle task.

What the heck is wrong? How do I fix it?:confused: [/FONT]

---

### Post by Sef on 2006-12-19
1) Did you md5sum the download?

2) Did you burn the iso at 4x or less?

3) Are you installing Dapper or Edgy?

4) Are you installing via the Live CD or alternate cd?

---

### Post by carloslosgrande on 2006-12-19
Ok, sorry about the lack of details.
I'm using the live cd that I've used twice on my own machine, Both times its worked perfectly.
Dapper 6.06. Don't know what speed I burned it at!

The sony vaio is a model from the states, bought in 2000, called a sr17k.
Are you saying I should burn another live cd at a slower speed?

I've just tried again and prior to ubuntu loading the initial cmos screen tells me this (among other things) - Warning 0251; system cmos chechsum bad - default config used
and also - Error 0280; previous boot incomplete - default config used

So I've continued to ubuntu startup screen and selected memtest which is running thru right now. Its showing LOTS of errors, heading up towards a million so far. 
Obviously there is something seriously wrong or I'm reading this entirely backwards. Don't know which.

---

### Post by Ashrael on 2006-12-19
Your memory might be busted....

---

### Post by carloslosgrande on 2006-12-19
Ok, so what does that mean in terms of fixing the thing? It is a new board needed? I've no idea what to do with this. I can probably get parts if thats whats needed. Its interpreting the errors that I can't follow.
Thanks

---

### Post by Ashrael on 2006-12-19
Well the machine is prob. out of waranty? If you have no exp. in laptoprepair, i would bring it to someone that does....and let them check whats wrong (I could be wrong too)... Cost you a bit more than doing it yourself but gives more result too.. and no funny surprises (financialy) if you scr*w it up even more...

keep me posted...

---

### Post by carloslosgrande on 2006-12-19
[I]Hi Ashrael, I wanted to run this new hard drive as Ubuntu only but out of desperation I'm now trying to reload the 'system recovery' discs that came with the machine. So far so good, I'm at 85% complete without any errors showing!! Even though this will put windoze back on at least if I can get the original setup going I can hopefully stick Ubuntu on and then resize windows down to negligible wasted space.
I'll let you know the outcome.
Thanks.[/I]

---

### Post by Ashrael on 2006-12-20
Thx! and good luck! If you get w*nd*ws up and running, download " everest free" and do a scan and test of your hardware, print out the results, come in handy later on! 
Also download a memorytest util...like: [www.memtest86.com](www.memtest86.com)... and any other testutil you might think of...there must be a reason for the failure...And yes, it could be that M$ works on shoddy memory (i've seen it happen before) and linux crashing (it's a bit more critical, and that's a good thing, mostly). It could also be an unsupported chipset for one of your devices...But my first guess is that it's memory related...Also possibly a good tip: turn off all possible hardware (in the BIOS) when you start the install proces, if it works then it must be one of those devices, after you install, you can start enabling them one by one...and see how far you get....

once again: good luck...

greets.

---

### Post by carloslosgrande on 2006-12-20
Hi Ashrael, Windows didn't load on reboot after system recovery setup. It seems its completely cactus. I guess I'll have to see about replacing the memory.
Thanks for your help.:)

---

### Post by Ashrael on 2006-12-21
Glad to help!......good luck in fixing it...

K.U.P.

---

### Post by Sef on 2006-12-21
> Are you saying I should burn another live cd at a slower speed?


Yes.  Burning at faster than 4x can corrupt the iso burn.  Just need to reburn a new disk at 4x.  

Also if you have had problems with the live cd, use the alternate cd.   Have to type in a few things, but mostly common sense.  If you want to read about installing from the alternate cd, read the [Illustrated Dual Boot]("http://www.users.bigpond.net.au/hermanzone/").  Just skip the install sections where it talks about a FAT32 file and windows.  The rest applies.

If you have any more questions, please post them.

---

