---
title: "PowerPC low-latency kernel?"
date: 2013-11-22
forum: Apple Hardware Users
---

### Post by jsedwards on 2013-11-22
How hard would it be to build a low-latency kernel for PowerPC (g4)?  I haven't build a kernel for 10 years.

Last year I was using this PowerMac g4 to record audio with 12.04.  I could never get it to record at 192 KHz (my post from last year: [http://ubuntuforums.org/showthread.php?t=2085988]("http://ubuntuforums.org/showthread.php?t=2085988")).   I did find that it would record at 176 KHz fairly reliably, only getting an overrun every now and then.

A few weeks ago, I had a brain cramp and decided to upgrade it to a newer release (this turned out to be a case of "if it ain't broke don't fix it").  But I upgraded it all the way to 13.10 and then discovered it will no longer record reliably record at 176 KHz, it gets overruns every few seconds.  I tried the kernels from 12.10 (3.5.0-43), 13.04 (3.8.0-17), and 13.10 (3.11.0-3) and all of the kernels after 12.04 are nasty as far as overruns go, getting 5 or 6 overruns in less than 3 minutes of recording.

I re-installed 12.04 in a different partition and it was better, only getting one overrun in about 3 minutes of recording.  Which is still worse than I remember it being last year, when it would usually record 10 or 15 minutes before getting an overrun.  I disabled Xorg and found that it would record without an overrun, but the audio had pops and clicks in it anyway.

I then installed Ubuntu-server 12.10 in another partition to see if having minimal stuff running would improve it, but the overruns are still very bad and happen every few seconds.

The hardware has not been changed since last year, so I am assuming this must be caused by software?

I have also observed on both the PowerPC machines I have strange pauses that I don't see on any of the x86 machines I have.  Like sometimes while typing on the command line there is 2 or 3 second pause between typing a character and it appearing on the screen.  And when the desktop is running, I often click on something and there is a delay of several seconds before anything happens.  I was telling my son about it a few days ago and he said that when he had some PowerPC machines years ago, he saw the same thing.  I believe he said he saw it on G5 machines.

Is it possible to build a low latency kernel for PowerPC, or is there some other issue that is causing this?

Thanks!!

---

### Post by tgalati4 on 2013-11-23
Real-time and low-latency kernels will cause pauses to user input--also using recording hardware with hardware interrupts will slow down user input response--this is normal.

Are you using the on-board sound hardware to record or a firewire rack?  Unless you are doing studio recordings, 24-bit, 96 kHz is overkill because you will normally mix down to 16-bit, 44.1 kHz (CD quality).  I challenge you to hear the difference unless you have $100,000 in microphones, monitors, and mix boards.  The fact that you could only get up to 176 kHz shows that the hardware is running at its limits.  You could try running a stripped down version of linux (like [dynebolic]("http://www.dynebolic.org/")), but I don't know if a PPC version exists.

---

### Post by jsedwards on 2013-11-23
Hi tgalati4,

Thanks for your reply!

> **tgalati4 said:**
> Real-time and low-latency kernels will cause pauses to user input--also using recording hardware with hardware interrupts will slow down user input response--this is normal.

Sorry I should have explained that better.  These weird pauses happen even when there are no programs (other than the normal OS stuff) running.  I did real-time programming for over 30 years and taught real-time classes at a college, so I understand that when real-time processes are running all bets are off.  These weird pauses happen all the time, when there are few or even no other things running.  They even happen when no GUI is running at all. 

> **tgalati4 said:**
> Are you using the on-board sound hardware to record or a firewire rack?

It's an ESI Juli@ card: [http://www.esi-audio.com/products/julia/](http://www.esi-audio.com/products/julia/)

> **tgalati4 said:**
> Unless you are doing studio recordings, 24-bit, 96 kHz is overkill because you will normally mix down to 16-bit, 44.1 kHz (CD quality).  I challenge you to hear the difference unless you have $100,000 in microphones, monitors, and mix boards.

I want to archive this stuff so I want the best recording I can make.  If I thought there was a snowball's chance in hell of it being supported on Linux I would have liked some Direct Streaming Digital recording device ([http://dsd-guide.com/](http://dsd-guide.com/)) for the best future proof recordings.  But I have been Microsoft free for 15 years so the only way I would use Windows if someone was holding a gun to my head.  I suppose OS-X is okay, but I am much more comfortable with Linux, and prefer to use it for everything I can.  I don't have $100,000 worth of equipment, but I do have a studio mixer and studio microphones that were expensive for me, so I am loathe to record at 44.1 KHz.

If it comes down to it I will move the card to an Intel box, but I was always a huge fan of the PowerPC and I have five or six PPC machines that are just sitting around now.  It would just be so cool if I could still feel like I was getting some use out of one of them.

> **tgalati4 said:**
> The fact that you could only get up to 176 kHz shows that the hardware is running at its limits.

If the machine didn't have all these weird pauses when it was just sitting there idle, I could maybe buy that.  Also there is an order of magnitude difference between 12.04 and the later versions in the number of overruns.  I'm going to go back and see if I can recreate the situation as it was before.  I'm so pissed off at myself for updating it when it was working well enough before and making it unusable now.

> **tgalati4 said:**
> You could try running a stripped down version of linux (like [dynebolic]("http://www.dynebolic.org/")), but I don't know if a PPC version exists.

I'd forgotten all about Dynebolic, I doubt they have a PPC version, but I will go look.  You just gave me an idea, I should probably try Yellow Dog Linux just to see what that does.  I don't know if it is around anymore either...

Thanks again!
  -scott

---

### Post by jsedwards on 2013-11-24
> **jsedwards said:**
> 
I'd forgotten all about Dynebolic, I doubt they have a PPC version, but I will go look.  You just gave me an idea, I should probably try Yellow Dog Linux just to see what that does.  I don't know if it is around anymore either...


Yellow Dog Linux appears to be defunct.  I installed an old version and did not see any weird pauses.  I suspect it was too old to recognize the sound card so I could not test recording.

I then installed Debian PowerPC.  I ran it from the command line there were no weird pauses that I observed.  It exhibited the same overruns as Ubuntu.

> **jsedwards said:**
> 
If the machine didn't have all these weird pauses when it was just sitting there idle, I could maybe buy that.  Also there is an order of magnitude difference between 12.04 and the later versions in the number of overruns.  I'm going to go back and see if I can recreate the situation as it was before.  I'm so pissed off at myself for updating it when it was working well enough before and making it unusable now.


Today, from the command line, I have not noticed any weird pauses on Ubuntu either.  I have no idea what was causing them before.  Since Debian exhibits the same overruns and i cannot seem to reproduce the way it ran last year (far fewer overruns) i am going to agree that the hardware is just not fast enough.  i am going to give up on the PowerPC machine and just move the sound card to an Intel box and see if I can get better results.

Thanks again for the comments!
  -scott

---

### Post by jsedwards on 2013-11-24
Follow up (in case anybody wonders how this turned out):

I moved the audio card to a Dual Pentium 4 machine with SATA drives.  If I remember correctly the PowerPC machine had 49 Bogomips, the P4's both say 5586 Bogomips, so more than 100 times more processing speed?

I could not get Ubuntu to recognize the sound card at all.  I finally gave up and installed Debian 7.2 with a real-time prempt kernel.  And guess what... arecord still overruns.  I can't really tell if it is any better than the PowerPC was.

---

