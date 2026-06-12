---
title: "did windows mess up my pc?"
date: 2008-01-01
forum: Absolute Beginner Talk
---

### Post by lunamystry on 2008-01-01
i installed windows on my system last year and two days later i left it with my sister who was not willing to even try ubuntu and thus used windows. i got back a few days back to my pc and use ubuntu. I installed windows on a 80gig hard drive that has bad blocks. i have ubuntu on a 160gig hard drive and i switch using bios. i have intel p4 and 512mb ram and a asus phoenix motherboard. the hard drives both use sata cables. i am buying more 1gig ram soon as i get money and a graphics card.  the problem now is that everytime i use windows my pc does not start up. i used ubuntu all the time and never had an over heating problem except when re-installing. my pc does not boot right now and i have disconnected the 80gig hard drive. what happens is grub loads and when its about to start up the pc shuts down. why would that happen?

---

### Post by scopo on 2008-01-01
Don't know if this is your problem or not, but is your fan over your processor still turning ?

Some MBs have a protection system built in that when they get too hot they simply shut down to protect the processor.

---

### Post by kerry_s on 2008-01-01
when the pc shuts off like that it points to a hardware issue of some sort. try checking all your connections are plugged in firmly. since you pulled the drive, if it was the master, make sure you change the jumper from slave to master on the drive you have. leave the side open so you can see if things look like there working, all fans turning, etc...

---

### Post by LowSky on 2008-01-01
well there could be a few things.

First thing I would check is the hard drive,  could you reinstall windows? How old is the hard drive? has your sister beeen using it since you were away. It could have picked up a virus. Will it run in safe mode? If you disconnect the ubuntu drive and reinstall windows onto the 80 gig drive you wont loose your grub settings.

---

### Post by bigken on 2008-01-01
could be a bad psu

---

### Post by JuiceBoxHero on 2008-01-01
Definitely could be a hardware issue, but try everything else before you consider buying anything. Windows wouldn't mess anything up, particularly if you already pulled the drive it was on. If at any point you changed your bios settings, you may want to reset to defaults and make any necessary changes from there. Check for any fan settings in the bios, and try turning the system on with the case open and verify every fan is working. If they're all on, it's not likely an overheating issue. Was the ubuntu OS installed using this exact system? If not, it may be configured for the wrong hardware.

---

### Post by lunamystry on 2008-01-01
it was a hardware problem. i had connected the hard drive in the wrong slot, but there is still the problem when i use windows. if i restart the problem comes back but leaving the pc for a while like 5min or so ubuntu can boot again but windows i have to wait a looong while. ubuntu works fine but i think windows is over heating my cpu or something. is that possible?

---

### Post by JuiceBoxHero on 2008-01-01
Not likely. If they're on the same hardware, the fans/cooling system either work or they don't. If you're not changing your bios or anything, there shouldn't be any hardware difference. My guess is that there's something corrupt on your windows install. Next time you get the windows portion running, you may want to consider extracting the files you want from it and reinstalling from a freshly reformatted HD.

---

### Post by kerry_s on 2008-01-01
> **lunamystry said:**
> it was a hardware problem. i had connected the hard drive in the wrong slot, but there is still the problem when i use windows. if i restart the problem comes back but leaving the pc for a while like 5min or so ubuntu can boot again but windows i have to wait a looong while. ubuntu works fine but i think windows is over heating my cpu or something. is that possible?

the best thing to do would be to wipe the 80gig drive and start over with a clean install, a bad install could get stuck holding the cpu at 100% and that will overheat the cpu and cause a shutdown. if there are to many bad blocks you should discard the drive all together and get a new one. if the bad blocks are towards the front or the back you can partion around the bad area, leaving the bad area unformatted still making the drive usable.

---

### Post by bigken on 2008-01-01
Personally I would bin the 80gig if it has bad sectors and buy a new one save yourself from having more problems in the future it could be a bad sector stopping windows from booting

---

### Post by lunamystry on 2008-01-01
> **kerry_s said:**
> the best thing to do would be to wipe the 80gig drive and start over with a clean install, a bad install could get stuck holding the cpu at 100% and that will overheat the cpu and cause a shutdown. if there are to many bad blocks you should discard the drive all together and get a new one. if the bad blocks are towards the front or the back you can partion around the bad area, leaving the bad area unformatted still making the drive usable.
 how would i kn
ow where the b
ad blocks are?and how i partition around them?

---

### Post by kerry_s on 2008-01-01
> **lunamystry said:**
> how would i kn
ow where the b
ad blocks are?and how i partition around them?

 i think for you just do a low level format it might be able to fix the bad blocks.
i believe i used a boot disk, when i had to do it.
i googled-> [http://www.ariolic.com/activesmart/low-level-format.html](http://www.ariolic.com/activesmart/low-level-format.html)

good luck

---

