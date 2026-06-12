---
title: "Why does Ubuntu have a Slow Kernel Timer?"
date: 2008-02-12
forum: Absolute Beginner Talk
---

### Post by jasonhaley on 2008-02-12
I recently installed Rosewater, a music maker, and it gives me this error message:

System timer resolution is too low
Rosegarden was unable to find a high-resolution timing source for MIDI performance.
This may mean you are using a Linux system with the kernel timer resolution set too low. Please contact your Linux distributor for more information.

Is there a better program to use for Gnome? Will the low timer resolution be fixed in Hardy? What happens if I try to adjust it myself?

The best solution seems to be to choose a lowlatency kernel from the repository (search for it with synaptic or your favorite tool). Install the new kernel and reboot. This will solve the problem and remove the lag.

---

### Post by njparton on 2008-02-12
I think it's about 200 MHz by default but if you compile your own kernel you can select up to 1000 MHz.

It's not really that hard a job, even I managed it first time :)

---

### Post by jasonhaley on 2008-02-12
Are there any drawbacks to doing this? If not, then why doesn't Ubuntu do this by default? I guess what I'm asking is what's the main pro and con?

---

### Post by shae on 2008-02-12
Yes using a higher timer number causes more power use and CPU wake-ups.

---

### Post by karlo on 2008-02-12
> **shae said:**
> Yes using a higher timer number causes more power use and CPU wake-ups.

Which means more chances to overheat?

I decided to be happy with Ubuntu after all, after not using all of my speed. Tried using Performance, 1.70GHz, but my laptop would turn off then goes back to the login window of Ubuntu.

Now I tried Dynamic, nothing happened but the speed is fluctuating.

Now I am using userspace, minimun speed is 600 MHZ, maximum is 1.40GHz out of 1.70GHZ, is my configuration correct?

Also, what is consider_nice? By the way my performance increased without making the laptop turn off automatically just by changing the performance ac to 95. I think it's the performance of your pc in percentage, if you put it on low, your pc will slow a little, and you'll see the cpu frequency monitor fluctuates more to a lower value.

am I corrent? haven't tried ubuntu on batteries yet..

---

### Post by misfitpierce on 2008-02-12
If you are referring to CPU then mine is on Performance and works fine on constant 1.8 ghz

---

### Post by karlo on 2008-02-12
> **misfitpierce said:**
> If you are referring to CPU then mine is on Performance and works fine on constant 1.8 ghz

probably your place is cold and your fans are working and cold...

probably windows xp experience or does not all the time experience that thing it's because it's uses something like ubuntu's dynamic frequency thingy... agree?:confused:

---

### Post by jasonhaley on 2008-02-12
I'm using a laptop that I doubt could risk getting any hotter than it already gets.. perhaps I'll just use Synaptic to find a lowlatency kernel from the repository ...would that create a chance to overheat too? ..Anyone know of any reasons not to do this?

---

### Post by Whiffle on 2008-02-12
> **karlo said:**
> Which means more chances to overheat?

I decided to be happy with Ubuntu after all, after not using all of my speed. Tried using Performance, 1.70GHz, but my laptop would turn off then goes back to the login window of Ubuntu.

Now I tried Dynamic, nothing happened but the speed is fluctuating.

Now I am using userspace, minimun speed is 600 MHZ, maximum is 1.40GHz out of 1.70GHZ, is my configuration correct?

Also, what is consider_nice? By the way my performance increased without making the laptop turn off automatically just by changing the performance ac to 95. I think it's the performance of your pc in percentage, if you put it on low, your pc will slow a little, and you'll see the cpu frequency monitor fluctuates more to a lower value.

am I corrent? haven't tried ubuntu on batteries yet..

I use "ondemand" on my Pentium M 1.86 GHz, it spends 99% of its time at 800MHz but jumps up to 1.86GHz in no time.  


The timer the OP is referring to isn't related to processor speed though (or overheating).  I believe the error in the OP is referring to [http://lwn.net/Articles/145973/](http://lwn.net/Articles/145973/) .  The stock Ubuntu kernel has it at 250Hz I believe,  it can go up to 1000Hz, but that can hurt battery life.

---

### Post by karlo on 2008-02-12
> **jasonhaley said:**
> I'm using a laptop that I doubt could risk getting any hotter than it already gets.. perhaps I'll just use Synaptic to find a lowlatency kernel from the repository ...would that create a chance to overheat too? ..Anyone know of any reasons not to do this?

I see... the laptopmode tools or utils and cpufreqdyn thing or cpudyn, something that is not built-in, in the default installation of Ubuntu, it does not work on my laptop.

For example, when I install cpudyn, I am always on performance mode.

---

### Post by karlo on 2008-02-12
> **Whiffle said:**
> I use "ondemand" on my Pentium M 1.86 GHz, it spends 99% of its time at 800MHz but jumps up to 1.86GHz in no time.  


The timer the OP is referring to isn't related to processor speed though (or overheating).  I believe the error in the OP is referring to [http://lwn.net/Articles/145973/](http://lwn.net/Articles/145973/) .  The stock Ubuntu kernel has it at 250Hz I believe,  it can go up to 1000Hz, but that can hurt battery life.

I see... well anyway OP, can I lower it to prevent huting the battery life? By the way according to majority of the tips here, they all suggested to remove the battery.

Normally the battery on your laptop can be a ups or a backup power, specially when the lights went out...:)

---

