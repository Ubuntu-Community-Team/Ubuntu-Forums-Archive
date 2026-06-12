---
title: "memory leaks..."
date: 2006-04-27
forum: Absolute Beginner Talk
---

### Post by Caligula on 2006-04-27
What can I do against them?
I heard that there is a program for windows against them, is there such a thing for linux?

I've got a big problem with those...
After I use some "big" programs(firefox, thunderbird, openoffice and a few more), I close them, but it doesn't get much better...
And yes, I'm using the new firefox...
anything I can do?

thanks:)

---

### Post by oldmanstan on 2006-04-27
what are the symptoms?

someone more knowledgeable might tell me i'm wrong, but in my experience problems that seem like memory leaks can sometimes be caused by problems with the physical memory. if you have problems with the system crashing randomly and what not you might try taking one DIMM (or whatever you have) out at a time and running the computer without it to see if you still encounter problems, if your problems go away with one of them missing then you know which one had the error.

i don't know, but i had this problem once and that's how i solved it. although this wouldn't explain a general slowdown of the computer (which is maybe more commonly associated with a memory leak)

that's why i asked what the symptoms are.

---

### Post by Caligula on 2006-04-27
aha!
I do have crashes as well...
I'll explain it from the beggining, long story...

About four months ago, I was still using windows, and I had problems with my virtual memory, meaning I got a BSOD and the computer restarted. 
I added a bit of RAM, formatted, and reinstalled windows.

The problem was solved for a short period of time, but then the computer started freezing, absolutely not responding, it there was music on it just turned into a long drrrrrr...

That stopped some time ago, and I started having another problem, the computer just randomly switched of, no error messages or anything, just as if I took the power out.

Now, I then tried system restore and it broke my windows install, I then decided to install Ubuntu, as I wanted to do for a long time...

Everything in Ubuntu worked great for a few days, and then the computer crashed. In the same way as in windows, just as if I took the power out. 
It's not happened for a few days now.

Now the notes...
I'm using a laptop, compaq Evo-N115, 384 RAM.
Sometimes I get a sudden "Beep" out of nowhere... I started refering to it as an indicator for coming trouble...lol

Battery- I  keep having weird things with my battery...
Sometimes it shows as if it's charging but the percentage is actually going down, and all that kind... weird.

I though about two options, RAM or power supply, or just my cable...

But the original message didn't have a lot to do with this...
I was talking about that that even when I leave "big" programs, the performance doesn't get much better, as if the memory is still used, but nothing is running.

Thanks:D 

and yeah, I know, complicated stuff...

---

### Post by Caligula on 2006-04-27
oh! and by the way...
you told me exactly the same as the guy from HP, to take out the DIMMs, whatever they are...

The trouble is that I don't know how to do it, AND I'm using a laptop, witch really complicates things...

---

### Post by cwaldbieser on 2006-04-27
[QUOTE=Caligula]aha!
I do have crashes as well...
I'll explain it from the beggining, long story...

About four months ago, I was still using windows, and I had problems with my virtual memory, meaning I got a BSOD and the computer restarted. 
I added a bit of RAM, formatted, and reinstalled windows.

The problem was solved for a short period of time, but then the computer started freezing, absolutely not responding, it there was music on it just turned into a long drrrrrr...

That stopped some time ago, and I started having another problem, the computer just randomly switched of, no error messages or anything, just as if I took the power out.

Now, I then tried system restore and it broke my windows install, I then decided to install Ubuntu, as I wanted to do for a long time...

Everything in Ubuntu worked great for a few days, and then the computer crashed. In the same way as in windows, just as if I took the power out. 
It's not happened for a few days now.

Now the notes...
I'm using a laptop, compaq Evo-N115, 384 RAM.
Sometimes I get a sudden "Beep" out of nowhere... I started refering to it as an indicator for coming trouble...lol

Battery- I  keep having weird things with my battery...
Sometimes it shows as if it's charging but the percentage is actually going down, and all that kind... weird.

I though about two options, RAM or power supply, or just my cable...

But the original message didn't have a lot to do with this...
I was talking about that that even when I leave "big" programs, the performance doesn't get much better, as if the memory is still used, but nothing is running.

Thanks:D 

and yeah, I know, complicated stuff...[/QUOTE]

Does you PC seem more sluggish as a result of the memory being utilized?

---

### Post by Caligula on 2006-04-27
What do you mean?
The performance is worse, it's slow...
It's supposed to get better, say, when I close openoffice, but it doesn't...

---

### Post by oldmanstan on 2006-04-30
[QUOTE=Caligula]oh! and by the way...
you told me exactly the same as the guy from HP, to take out the DIMMs, whatever they are...

The trouble is that I don't know how to do it, AND I'm using a laptop, witch really complicates things...[/QUOTE]

check your manual, or just do a google search. changing DIMMs on a laptop is sort of tricky since the space is so confined but you should be able to do it without too much trouble if you find some directions. basically they're just little things about the size and shape of wafer cookies (thinner) and you just have to wiggle them out.

as for your other stuff, i would really recommend checking out the memory because a busted DIMM can really wreak havoc on the computer, one symptom could be a slowdown, depending on what exactly the problem is.

also, you might want to check your bios and see how much memory the computer is recognizing. if you added RAM to it you might have added the wrong type and if you just added a DIMM board the computer might only be recognizing one of the ones in your computer, in other words your computer is only actually using a fraction of what you think you have. i dunno, something to check out.

---

