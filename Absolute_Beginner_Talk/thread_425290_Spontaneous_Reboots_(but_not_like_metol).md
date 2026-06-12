---
title: "Spontaneous Reboots (but not like metol)"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by hlynna on 2007-04-27
OS and Hardware Info:  (most of my hardware is less than a year old)

RAM: Kingston ValueRAM 1GB (2 x 512MB) 240-Pin DDR2 SDRAM DDR2 400 (PC2 3200) Dual Channel Kit System Memory Model KVR400D2N3K2/1G

Video: Leadtek PX6600TD-256 GeForce 6600 256MB DDR PCI Express x16 Video Card - Retail

HDD: Western Digital Caviar RE WD1600YD 160GB 7200 RPM Serial ATA150 Hard Drive - OEM

CPU: AMD Athlon 64 3200+ Orleans 2.0GHz Socket AM2 Processor Model ADA3200CNBOX

PSU: Thermaltake TR2 W0070RUC ATX 430W Power Supply

Output of 'uname -a': Linux oscar 2.6.15-28-amd64-generic #1 SMP PREEMPT Tue Mar 13 20:51:52 UTC 2007 x86_64 GNU/Linux

GIGABYTE GA-M55SLI-S4 Socket AM2 NVIDIA nForce4 SLI ATX AMD Motherboard

Dual-boot using GRUB with Windows XP Pro (which appears stable but I'm never there longer than it takes to feed the Sims addiction).

Having read through metol's post, I am thinking that I need a new motherboard too.

HOWEVER, my reboots occur when I'm idle, which is a significant difference from that poster, who experienced reboots while he was working.

When I've looked at /var/log/messages and /sys/log/messages, I found nothing amiss.  The machine did not appear to go through a normal shutdown and restart process; it appeared to be a hard reset.

Please note:  I say "I" but I mean a combination of my much more geekly husband and me (who just needs more time to understand things, but it's MY computer.)

Appreciate any help you can give.

---

### Post by Seisen on 2007-04-27
Your computer could be overheating or it could be a faulty power supply. It could be a number of things. Does this happen in Windows at all or just Ubuntu?

---

### Post by hlynna on 2007-04-27
As I don't leave Windows up like I do Linux, I don't know if it's happening in Windows.

Regarding overheating and power supply, I will ask my husband if he's investiogated those (I assume he has though b/c those would have been the first thing I thought of and I'm not the computer guy).

---

### Post by johnny4north on 2007-04-27
i had the same power supply[great power supply], til my gaming box out grew it.  have your husband test the power supply by unpluging cd/dvd drive, floppy, zip, other harddrives and replug the main fan to one of the freed plug-ins[not the motherboard].  the power supply has only one rail and i believe that your current hardware config has out grown your once great power supply.  also try cleanup the wires by zip tie them together and improve air flow.

---

### Post by hlynna on 2007-04-27
johnny4north:

my husband is not sure what you mean by main fan?

---

### Post by johnny4north on 2007-04-27
cpu or cpu duct fan out the back[some systems have only one fan] you may need an adapter to do this, for the 3 pin to 4 pin reg. plug in.   by unpluging all the other devices and moving the cpu plug in.  you will be giving the cpu and mother board[videocard] more power.  this is could be your main problem. check for  heat problems.  if this improve the computer preformance you will need  a new power supply [PSU: Thermaltake TR2 W0070RUC ATX 430W Power Supply] i upgraded my Thermaltake Power Supply to 580or600 watts, which solved my random boot problem.

---

### Post by Seisen on 2007-04-27
You mean the case fan, don't you?

---

### Post by johnny4north on 2007-04-27
the power supply is fine i believe, but the motherboard power draw is greater then the power supplys one rail can handle.  by removing the cd/dvd, floppy etc.... and repluging all the fans plugged into the motherboard to the reg 4plugs.  this will give the motherboard more power.  i had  similar setup with the same random reboot problem. my system is same except 200gb hd and ati pcix x800pro 256mb.  i replugged in the one dvd burner in my game box, and used it well my ordered power supply took it sweet time coming to ak[two weeks].

---

### Post by johnny4north on 2007-04-27
i do alot of upgrading for friends and most of them forget to upgrade their power supplies [newegg.com has side bars of there users reviews, great help] and another note- heat is bad, very bad, because heat creates resistance, which lowers power for your system[dont go nuts and put a million fans which uses power as well, just cleanup and organize the system with zip-ties]. got 2 go.  hope this helps you out:)

---

### Post by popefelix on 2007-04-28
Husband in question here.  :)

What I've done:

Blown the dust out of Hlynna's machine with compressed gas inna can.  There was a lot.  I blame the cats.  :)

Slot fan below her video card was already on a connection coming out of the PS, rather than the mobo.

Zip-tied her power cables together and moved them out of the way.  There's a lot of space now between the whole mobo and the side of the case.

I also took a DMM and measured the voltage across her various power connectors with the PS connected to the mobo (standard ATX and 4-pin connectors) and the CPU fan connected to the mobo.  12.05-12.06 and 5.14-5.15 volts on each connector, and this voltage did not appreciably drop after I measured it again with all fans (1 case fan, 1 slot fan, 1 CPU fan), DVD-RW, and floppy connected.  I didn't connect her HDD because I didn't want the thing to boot, and didn't want to cause any potential damage should I cause a short or something.

I'm going to power up her box here in a moment, and then I'm going out for the day.  We'll see if it's rebooted by the time I get home.

---

### Post by popefelix on 2007-04-28
No reboot since I last posted.  *fingers crossed*

---

### Post by popefelix on 2007-04-28
Also - she has a pair of 512MB DDRII DIMMs.  They were in slots 3 & 4.  I relocated them to slots 1 & 2.  Just in case something that trivial might cause such a problem.

---

### Post by croxi on 2007-04-28
I had a few teething troubles with UBUNTU 7.06 on my laptop because it wouldn't stop crashing on me, I had to install the video codecs and sound drivers thingy and its been better since then but its not done anything for my email connections with Evolution...proves my theory that evolution doesn't work, at least for now anyway.

---

### Post by popefelix on 2007-04-28
In case this doesn't work, I'm going to set up a custom kernel for her as well, just in case this is something in software.

---

### Post by popefelix on 2007-04-28
OK.  Doing all that **** I just did wasn't it.  The machine just rebooted.

---

### Post by metol on 2007-05-01
Hello Hlynna & Popefelix,

Well, I certainly understand how frustrating it is to diagnose such a problem.  I’m happy to report that since I replaced my MB I have not had any problems whatsoever.

I doubt your issue is with cooling since it is happening while your system is idle.  I eliminated this possibility by removing the side of the case and blasting it with air from a simple desk fan.  

So, you have cats and this happens while you are away from your computer?  Could the cats be rubbing against a loose power cable or something similar while you are away?  Or could you be getting power surges or brown-outs?  I’m just tossing out ideas.  I tried to exhaust every possible problem before I started replacing hardware.  Although if your PS seems fine, I would start with the MB... but I could be biased.

Best of luck,
Metol

---

### Post by popefelix on 2007-05-01
I don't think power surges or brown-outs are likely - Hlynna's machine is connected to a dedicated UPS.

I don't think it's the cats rubbing up against a loose power cable - I've seen the reboot happen, and there were no cats in the vicinity at the time.

I'm starting to think it may be time to replace the mobo.

---

### Post by SycloneMedia on 2007-05-03
I'm really curious with this thread... I have the same problem: random reboots when idle.
However, I have a 15" Al Powerbook 1.25 with 2 GB ram, dual-booting Mac OSX and Kubuntu Feisty.

As far as "potential" causes to help diagnose, I submit the following problems that I know of with my computer...

- Could my ram have anything to do with it? I get a string of random kernel panics occassionally when I try starting up in Kubuntu. I have heard that this may be a sign of a bad module? Would that somehow effect the random reboots?

- My power plug (the male piece) that connects into the laptop is damaged, or the carriage inside the laptop is slightly damaged since it stays in but wobbles and definitely doesn't sit completely in. The funny thing is, in Mac OSX, a few times when I've disconnected the power plug from the laptop while it's running will cause a complete freeze/hard panic.

- I have read (as I have a problem with) screensavers not working right in Feisty. It seems a coincidence that after idle for a certain time (just like how the screensaver waits a certain period of time) it reboots. I don't even have a screensaver set, but then again, Kubuntu has the base Ubuntu under it, and the gnome screensaver could be causing a conflict???

I have no clue.

:confused: :(

---

### Post by popefelix on 2007-05-03
Well, I know that my laptop will periodically lock up, I think because I have non-OEM memory in there.  Are you running any non-OEM RAM?  Seems that IBM laptops are more particular about their RAM than desktops, so maybe that applies to your Powerbook too.

Is there a version of Memtest86+ that will run on your hardware?  That's the de facto standard for testing RAM, I think.

As for your power plug, do the spontaneous reboots happen when the machine is on battery?

Maybe it's something with your machine trying to turn off your display via DPMS?

> **SycloneMedia said:**
> I have the same problem: random reboots when idle.
However, I have a 15" Al Powerbook 1.25 with 2 GB ram, dual-booting Mac OSX and Kubuntu Feisty.
<snip>

- Could my ram have anything to do with it? I get a string of random kernel panics occassionally when I try starting up in Kubuntu. I have heard that this may be a sign of a bad module? 

- My power plug (the male piece) that connects into the laptop is damaged, or the carriage inside the laptop is slightly damaged since it stays in but wobbles and definitely doesn't sit completely in.

<snip>

- I have read (as I have a problem with) screensavers not working right in Feisty.


---

