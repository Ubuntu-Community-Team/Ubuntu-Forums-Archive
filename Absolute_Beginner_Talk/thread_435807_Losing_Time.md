---
title: "Losing Time"
date: 2007-05-07
forum: Absolute Beginner Talk
---

### Post by DaemonLee on 2007-05-07
Good Morning/Afternoon,


I run Ubuntu on a P4 2.4ghz 768mb of RAM, 160gb HDD, 1 Sony CDRW, Lite-on DVD, ATI 9600XT. 

Now, here's my issue. 

I'm running the NTP package, and it did this before I installed it, but I'll "lose" time. i'll sync it, because I know it's not right, and suddenly I'll get 30 minutes added onto the clock or some obscene number. 

No reboots occured, nor logging in or out. Just maybe idle times. 

My question is, why?

---

### Post by rich.bradshaw on 2007-05-07
Probably the CMOS battery is low on your motherboard. Almost definitely.

---

### Post by wpshooter on 2007-05-07
> **rich.bradshaw said:**
> Probably the CMOS battery is low on your motherboard. Almost definitely.

And if that is the case, which it probably is, then losing some time on the clock is probably just the start of your problems.  Might want to get a new battery in there ASAP.  Make sure you follow the motherboards instructions to the letter for replacing the battery.

Good luck.

---

### Post by JJNova on 2007-05-07
I want to point out that intensive demands on your machine will also cause the time to become incorrect. For instance, if you are a big user of Binary newsgroups, then you know what it mans to queue up a large amount of data and let that process. Well not only is your computer downloading, but it's also unpacking and compiling the contents that you are downloading. Prolonged high-demand activity causes time to be miscalculated while resources are being managed to other activities.

I just use newsgroups as an example, since it seems to happen quite often, but any intensive activity may have this effect. Specifically, if it's a prolonged activity. I assume this is the case, since you mentioned that the computer idles a lot. Which usually means it's doing so much work, you just walk away form it because trying to open another program takes 10 minutes ;)

---

### Post by Nythain on 2007-05-07
can you set the ntp daemon to update more frequently to make up for the "lost time" a bit quicker, so you arent gaining 30 minutes or so in one chunk???

---

### Post by Cypher on 2007-05-07
Sorry guys..first of all..the CMOS battery is to maintian the RTC (real-time clock) when the PC is powered off. When the PC is constantly running, the RTC has power and doesn't rely on the CMOS battery. However, if the CMOS battery dies, on a reboot, the RTC will have a wrong time.

Secondly, a high load on the machine will NOT affect the clock. All OS' implement a tick timer that is a hardware interrupt from the RTC in the system. This is a kernel level service that can and will easily interrupt ANY user-level action. So all your newsgroup browsing isn't going to affect the kernel threads.

If this is a multi-boot system, can you boot into your other OS (Windows perhaps) and see if you lose time there as well, if you don't. Then we can look at other Linux explanations, otherwise it's a hardware issue..

---

### Post by JJNova on 2007-05-07
> **Cypher said:**
> Sorry guys..first of all..the CMOS battery is to maintian the RTC (real-time clock) when the PC is powered off. When the PC is constantly running, the RTC has power and doesn't rely on the CMOS battery. However, if the CMOS battery dies, on a reboot, the RTC will have a wrong time.

Secondly, a high load on the machine will NOT affect the clock. All OS' implement a tick timer that is a hardware interrupt from the RTC in the system. This is a kernel level service that can and will easily interrupt ANY user-level action. So all your newsgroup browsing isn't going to affect the kernel threads.

If this is a multi-boot system, can you boot into your other OS (Windows perhaps) and see if you lose time there as well, if you don't. Then we can look at other Linux explanations, otherwise it's a hardware issue..

.....

Well, according to "computer clock loses time" searched through google, intense operations do affect the clock. So maybe you should write a webpage explaining why it doesn't and set the others straight. I will agree that they are probably written in regards to Microsoft Windows, but if you could explain to me how Ubuntu handles keeping track of time differently than MS Windows, then that would be really useful also. Since you said All OS', I assume you were including MS Windows in that statement. In which case, the Operating System maintains the time when the machine is powered on, and a heavy demand effects it's ability to do so. In windows, user-level actions interrupt the "kernel level service' of keeping time. 

I happily accept any lesson regarding Linux' time keeping function though.

---

### Post by DaemonLee on 2007-05-07
> **Cypher said:**
> Sorry guys..first of all..the CMOS battery is to maintian the RTC (real-time clock) when the PC is powered off. When the PC is constantly running, the RTC has power and doesn't rely on the CMOS battery. However, if the CMOS battery dies, on a reboot, the RTC will have a wrong time.

Secondly, a high load on the machine will NOT affect the clock. All OS' implement a tick timer that is a hardware interrupt from the RTC in the system. This is a kernel level service that can and will easily interrupt ANY user-level action. So all your newsgroup browsing isn't going to affect the kernel threads.

If this is a multi-boot system, can you boot into your other OS (Windows perhaps) and see if you lose time there as well, if you don't. Then we can look at other Linux explanations, otherwise it's a hardware issue..


It's a single boot, and also, I would not be surprised if the CMOS is failing on this board.

It's just a ASUS P4S800, and I've had it for a little while. I'd be really interested on how to make the NTP daemon update more often.

---

### Post by DaemonLee on 2007-05-08
Also, the BIOS clock is not losing time. It is accurate.

---

### Post by compmodder26 on 2007-05-08
Perhaps the clock on the time server you are syncing with is off by 30 minutes?

---

### Post by DaemonLee on 2007-05-08
I disagree. Everything else in my room is set on the correct time, and my PC slowly loses Minute-by-minute, if not set by Automatic Sync. 

If I fall asleep, over a 8 hour span, it'll lose 30 minutes. I doubt it's the NTP servers, as I also have four in my Time Zone, and region selected.

---

### Post by RedACE on 2007-05-17
I'm having the same problem. I'm losing about 10 minutes per hour. This is on a brand new machine so I doubt the battery needs replacing. Did the original poster find a solution? If so, can you please share it.

---

### Post by Thelasko on 2007-08-27
I too am having the same problem.  I'm on a brand new Dell with an Intel Core II duo.  However, I am running a dual boot with Vista.  Once I set the clock on Vista it keeps perfect time.  Feisty is losing about 40 minutes every hour.

---

### Post by bannerman9 on 2007-09-27
I have the same problem. My /proc/cpunfo reports that my processor is an Intel(R) Core(TM)2 Duo CPU     E4500  @ 2.20GHz. This is a really big deal for me. Please help! #ubuntu and #debian were unable to assist me.

hwclock stays relatively accurate
date loses 30 seconds over 10 minutes.

I'm more than happy to provide any other information about my system if it will help!

---

### Post by bhaverkamp on 2007-11-02
I too am seeing this. Watching the seconds roll by on my clock the second count very slowly on the order of about 1/2 or 1/3 of real time against my watch. I have only noticed this in the last week

model name      : Intel(R) Core(TM)2 CPU          6700  @ 2.66GHz
Dell 390

---

### Post by hotspoons on 2007-11-08
I'm having the same exact issue on a fresh install of Gutsy on a 1st gen 15" MacBook Pro. I had Feisty on this machine for 6 months before reloading it, and never experienced any issues related to time. It is dual booted with OS X/Tiger, and I never lose time while running in Mac. Any ideas? I found this: [http://blogs.sun.com/richb/entry/losing_time](http://blogs.sun.com/richb/entry/losing_time), and there wasn't a fix that worked for him.

---

### Post by JillSwift on 2007-11-13
"Mee tew!"

Ubuntu Gutsy
Intel Pentium D 2.8Ghz
2 gig RAM (DDR2 PC2-4200)
(HP Media Center PC m7250n)

Dual boot with Win XP MCE, and no time drift under Windows.

---

### Post by talcite on 2007-11-16
Chalk one more up on the tally.

Gutsy 64bit.
e6300
D975XBX

Single boot

---

### Post by steveneddy on 2007-11-23
OK - I'm having trouble with this, too.

Intel Core 2 Duo @ 2 Ghz
2 Gig RAM
nVidia graphics
Gutsy 64 bit

I installed some things from Ubuntu Studio for sound recording and sound in general, including the RT kernel.

Anyone thing that this would have an effect on the hwclock?

---

### Post by JillSwift on 2007-11-30
*bump* Any ideas dear folks?

---

### Post by dvdhldn on 2007-12-13
Same problem here, worked fined under feisty.

---

### Post by steveneddy on 2008-01-01
My hwclock issues were related to a bug in the 64 bit OS.

I installed the 32 bit version is util-linux and all is well.

---

### Post by Thelasko on 2008-01-03
My machine doesn't always do this.  Sometimes it had a good boot and the clock is fine and others it's slow.  I know that AMD machines used to have the opposite problems under Feisty and I think the fix for that is causing the problems under Gusty.  I applied the [same fix as the AMD users did under Feisty]("http://ubuntuforums.org/showthread.php?t=53094&highlight=clock+double+speed") and it appears that as long as I only do cold boots I don't have a problem with the clock.

Does this work for anyone else?

---

### Post by goulo on 2008-02-11
I am also seeing this problem; my clock is losing many minutes per hour, and I keep having to fix it, even after setting it up to use ntp.  It was not doing this until recently, after a recent Ubuntu update a couple days ago.  64-bit Ubuntu 7.10.  Rather frustrating!

---

### Post by Thelasko on 2008-02-11
I have been using the fix I posted above for quite a while now and haven't had any problems.  I recommend trying it.  You can edit the GRUB menu without making it a permanent change by hitting the "e" key when the GRUB menu appears on bootup.  Once you make your changes you hit "b" to boot.  This way you don't have to worry about breaking your GRUB.

---

### Post by sillymrman on 2008-03-30
@Thelasko:
Thanks for posting that link!  I've got an Ubuntu 7.10 x86-64 box (Intel Quad Core, Core 2 Duo) and had to run a cron job every fifteen minutes to force the time to stay fixed.  It was slipping 25 seconds every fifteen minutes.  Setting the no_timer_check kernel option did the trick!  Everything's right on track now!

Anyone suffering this issue [on a 64-bit install of Ubuntu, at least] should try this fix!

---

### Post by Thelasko on 2008-03-31
Good to hear!  I have yet to have a problem since implementing this fix.

---

