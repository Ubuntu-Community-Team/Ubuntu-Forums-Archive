---
title: "Poor system performance"
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by Marc Hoffman on 2007-10-08
I have found system performance has been getting very slow recently, for example when searching in banshee the application will fade to grey for a while then return to colour and will resume letting me type into the field. The same would happen with other programs. Now Opera is the worst affected and wont even start.

I am running 7.04 for a few months now with no problems until now on a Dell Inspiron 6000 Celeron 1.30ghz with 512mb ram. Other than the standard updates I have not installed any extras recently. Desktop effects are turned on.

Any advice on where to start?

---

### Post by macogw on 2007-10-08
Turn off desktop effects.

---

### Post by Jeroen Vernooij on 2007-10-08
Does this also happen with desktop effects turned off?
There are many things that can cause poor performance. You can analyse what's going on with System monitor or by typing **top** in a Terminal. What's your system load? Is there a process which take 100% CPU? Is your RAM all filled?

---

### Post by peterbrewer on 2007-10-08
Were desktop effects on all the time?  How long have you had issues?  Did it come after a specific update?  Is it generally slow or just in banshee?

---

### Post by macogw on 2007-10-08
> **Jeroen Vernooij said:**
>  Is your RAM all filled?

```
free -m
``` to check that, by the way

---

### Post by Marc Hoffman on 2007-10-08
Thanks for the replies so far. In answer to the questions;

1. There is no difference if desktop effects are on or off.
2. Banshee has always played up from time to time but i put this down to have 10gig of music
3.CPU usage is erratic ranging from 7% to 98%. Opera caused the most problems and makes the system hang until I force quit it.
4. System load is - Load averages for the last 1,5,15 minutes: 1.22 1.78 2.27
5. results for free m as follows
6. system is generally slow, not just banshee

marc@Oberon:~$ free -m
                                 total       used       free     shared    buffers     cached
Mem:                          495        421         74          0          5        129
-/+ buffers/cache:                     286        209
Swap:                          478        179        298

---

### Post by Jeroen Vernooij on 2007-10-08
Strange,
CPU is oke, enough RAM free, everything seems ok.
Sorry can't help you, maybe some base packages or libs are slowing stuff down, don't know.

---

### Post by Marc Hoffman on 2007-10-08
I have rebooted my machine and run free -m again

Results are:
marc@Oberon:~$ free -m
             total       used       free     shared    buffers     cached
Mem:           495        489          6          0          8        185
-/+ buffers/cache:        295        200
Swap:          478          0        478
marc@Oberon:~$ 


i can see that I have only 6mb of free ram left and the whole swap file. Could i have a hardware problem with slow access to the swap file? ( just clutching at straws)

---

### Post by HermanAB on 2007-10-08
Run 'top' and see what is eating things.  The culprit will be at the top:
$ sudo top

Once you found it - kill it.

Otherwise, if the trouble seems to be network related, check your DNS response times with 'dig'.  Look in '/etc/resolv.conf' and test all the DNS listed.  Put the fastest one at the top of the list:
$ sudo dig @w.x.y.z [www.yahoo.com](www.yahoo.com)

Cheers,

H.

---

### Post by bluenova on 2007-10-08
It's normal in Linux that it will use all your RAM before it starts using SWAP.

---

### Post by skymera on 2007-10-08
yeah but i use 200megs of RAM and NO swap

thats with evertything running.#

something dosent seem right

i agrree with

sudo top

then kill the juicy beast :lol:

---

### Post by Marc Hoffman on 2007-10-08
running sudo top gives me a fairly dynamic list msotly populated with processes owned by root with a haldeamo appearing now and then. There is no real one process that seems to be taking that much cpu, the highest is root Xorg with a figure between 5 and 13%.

Opera is now working but really slow.

---

### Post by philinux on 2007-10-08
Give system monitor a try its quite user friendly.

---

### Post by Marc Hoffman on 2007-10-08
Still no real clear culprit using system monitor. Opera sometimes spikes high then calms down again.

---

### Post by philinux on 2007-10-08
Just for comparison here's a screenshot of mine with firefox, kopete and system monitor the only user apps. You can clearly see that the system is only using 57.7% of hardware memory.
The processor is on about 14% cos of system monitor being the only active app. Have a look at the other tabs in sys mon too.

---

### Post by Marc Hoffman on 2007-10-08
My CPU usage looks like a critical patient chart. Banshee is surging up to 98% on occasion- this is when the application turns grey.

With just opera and system monitor running my cpu usage is at 68%

---

### Post by philinux on 2007-10-08
What is opera up to then?

My spec is well old and I only run into trouble with firefox and multiple tabs if a script gets stuck on a certain page. The screenshot I took was when firefox had about 4 tabs open but was not actively doing anything

Is there anything other than banshee to test out your system

---

