---
title: "Dual AMD socket A"
date: 2006-09-17
forum: Absolute Beginner Talk
---

### Post by buffy^ on 2006-09-17
I have just installed ubuntu to my server, then thought hang on its a bit slow atm.

check the system settings a noticed that It was only using 1 processer.

Please let me know what infomaiton you need to help me reslove this problem.

At the moment I am at work so I will check again when I get home.

Thanks in advance for any suggestions.

---

### Post by pistcivet on 2006-09-17
What do you get from:
```
uname -r
```
If you see 386 at the end, you need the K7 kernel.

---

### Post by buffy^ on 2006-09-17
I will check the second that I get home.
Thanks

---

### Post by David Corrales on 2006-09-17
Just let me add that you need the K7 (Athlon optimized), because it has SMP (symmetric multi processing) built in. That's the feature that enables multiple processor/cores.

---

### Post by buffy^ on 2006-09-17
how do i get the k7 kernal?

---

### Post by mixmaster on 2006-09-17
Use the package manager of your choice to install linux-k7-smp and then reboot to activate the new kernel.  I think this probably resolves to the same files as linux-k7 nowadays but it is labelled as the kernel for duron/athelon processors with SMP.

---

### Post by bulldog on 2006-09-17
Take a look here,

[http://ubuntuforums.org/showthread.php?t=85917](http://ubuntuforums.org/showthread.php?t=85917)

---

### Post by Kilz on 2006-09-17
> **buffy^ said:**
> I have just installed ubuntu to my server, then thought hang on its a bit slow atm.

check the system settings a noticed that It was only using 1 processer.

Please let me know what infomaiton you need to help me reslove this problem.

At the moment I am at work so I will check again when I get home.

Thanks in advance for any suggestions.

Yes if its a server and your not running a amd64 version try it. There is no reason not to run a amd64 version on a server. Im guessing your not because all 64bit kernels are smp enabled and you only see one processor.

---

### Post by buffy^ on 2006-09-17
I am not running 64bit because the 2 processers are 2x AMD1000+ socket a, so they only have 32bit arc.

---

### Post by buffy^ on 2006-09-17
right just ran the command on the server and there was a little flutter in my hard as my hart skipped a bead, things in ub are so beautifully easy when you know how. I am very quickly falling in love with this community, thanks for all your help and I believe that this is now gonna be reslove.  <3

---

### Post by buffy^ on 2006-09-17
nope i think there was a problem as the 2 processers are 2 seperate  physical entities, and not 1. k7 smp killed it. any other ideas?

---

### Post by buffy^ on 2006-09-18
Right i have looked around to see if anyone else has been suffering from a simular problem and I am not finding anying that quite matches.

Please could some one tell me what the command is to show how many processers have been detected, as it could just be that both are being used but UB isnt optimised for this old machine.

Again any help is most appreicated

---

### Post by David Corrales on 2006-09-18
If you're using a graphical interface, you can go to the sytem monitor and in Resources you'll see how many processors are being detected.
You can also get some more info about your processor by typing
**cat /proc/cpuinfo**

---

### Post by buffy^ on 2006-09-18
Ok under the GUI i can only see one CPU being shown, unless both devices are exactly matching the same graph patten. I am not able to run that command until I get home and will do it as soon as I get there, lets say for arguments sake that its only showing 1 cpu what would you advise would be the best course of action?

---

### Post by David Corrales on 2006-09-18
Only 1 processor is being detected then. Let's make sure you're running the SMP kernel. Type **uname -r**. You should get: 2.6.15-26-k7

If you don't, type in the terminal **sudo apt-get install linux-k7** and after it's done, reboot.

---

### Post by buffy^ on 2006-09-18
I am have run the K7 kernal and it wont load the kernal, it uncompresses it and then hangs.

processor       : 0
vendor_id       : GenuineIntel
cpu family      : 6
model           : 8
model name      : Bentium III (Coppermine)
stepping        : 10
cpu MHz         : 997.798
cache size      : 256 KB
fdiv_bug        : no
hlt_bug         : no
f00f_bug        : no
coma_bug        : no
fpu             : yes
fpu_exception   : yes
cpuid level     : 2
wp              : yes
flags           : fpu vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 mmx fxsr sse
bogomips        : 1978.36

---

### Post by David Corrales on 2006-09-18
Well, it looks like you could try the 686 kernel then.
**sudo apt-get install linux-686** and try it out :)

By the way, your processors are Pentium III, not AMD.

---

### Post by buffy^ on 2006-09-19
/me looks like he might have to hide under a big rock.

I have not as yet checked under the heatsinks to verify the make and model but was told at time of purchase 1 year ago that it was a dual 1 Ghz AMD athalon, although after checking on tinternet and the coppermind would appear to fit the board the same ways as an AMD with a simular socket to the socket A.

If this is the case I think i will simpley pack up and find a rock to crawl under.

---

### Post by David Corrales on 2006-09-19
Hahaha, those are the funny moments to remember :)
Again, the 686 kernel will get you up with SMP in no time ;)

---

### Post by buffy^ on 2006-09-19
Ok so what do you do after you have installed the 686 and then it say uncompressing kernal ok, loading kernal.... and hangs.

---

### Post by David Corrales on 2006-09-19
Looks like there's a bug somewhere that's not allowing your system to boot properly when using SMP.
Use the 386 for now and submit a bug with your problem plus complete hardware configuration. I'm not a kernel expert so I can't help you further if it's an exotic bug :( There's probably a kernel boot parameter that might help you but you'll have to dig it out a bit more.
You might try some options like disabling APIC and local APIC. Those gave me troubles long ago while I was using mandrake and caused hangs. To try this LONG SHOT haha do the following:
When the computer's booting up and Grub appears, select the 686 kernel and press **E**
Then move to the *kernel* line and press **E** to edit it. Add **noapic nolapic** after splash and press **Enter**.
Press **Esc** to get back to the main menu and press **Enter** to boot.

It's good to know how to add those kernel boot time parameters because like I said before, those might help you :) good luck!

---

