---
title: "can't get 7.04 on my pismo"
date: 2007-04-22
forum: Apple PPC Users
---

### Post by iamdigitalman on 2007-04-22
ok, this is being typed under 7.04 on my B&W G3, off the live CD. i'm not installing it on here, just wanted to make sure my burn was OK. So, I popped the CD in my pismo, and let it boot. after the splash screen, I got a loading bar, and it was wierd colors on the unloaded bit. on the loaded part, it was orange as it should be. Then, when it got fully booted, I had nothing but rolling lines on the screen. it sounded like it booted OK, as it made the login sound, and the CD kept being accessed. So, I rebooted, and popped it in my G3. it booted right up, no rolling lines or anything.

the only diffrences between the two machines (besides one being a laptop and one a desktop) is the pismo uses an ATI Rage on an AGP bus with 8mb of VRAM, and the B&W has a ATI Rage 128 in the PCI 66 slot with 16mb VRAM.

any ideas?

oh, and hello again. it's been a while.

now back to OS X.

-digital ;)

---

### Post by dpny on 2007-04-24
Trying to boot my Pismo off the Fesity Live CD and I it won't boot. I get the following:

```
[117.963537] RAMDISK: ran out of compressed data
[117.963761] invalid compressed format (err=1)
[117.965886] Kernel palic - not syncing: VFS: Unable to mount foor fs on unknown-block(1,0)
```

Does Feisty not like the Pismo?

edit: It worked when I rebooted for the fourth time. Weird.
edit again: lots more errors: SQUASHFS errors. Won't boot the live CD.

---

### Post by iamdigitalman on 2007-04-24
well, I know it's not the AGP video, as I booted the Live CD on a Sawtooth G4, a indigo slot load iMac, and a tangerine iMac. I'll try it on a friend's clamshell indigo iBook, maybe it just doesnt like the older portables.

it sucks the PPC build in unoffical. Was the decision made because there is no shipping consumer machine that uses a PowerPC chip? if so, the [new amiga owners](http://www.engadget.com/2007/04/24/amiga-returns-to-the-hardware-game-promises-two-new-ppc-desktop/) will be disappointed in not having an alternitive OS, but then again, AmigaOS 4.0 is really nice.

-digital ;)

---

### Post by dpny on 2007-04-24
Just tried with the Feisty alternate CD. Got through the partitioning process, but couldn't get packages from the CD because they were "corrupt". Has anyone been able to install on a Pismo from the Fesity CDs?

---

### Post by godsbane on 2007-04-24
I used the alternate CD and it installed just fine. I didn't even try the normal disc. I am now however having issues with the thing rolling the video as if the refresh rate is too high.

---

### Post by godsbane on 2007-04-24
Solved the Rolling screen issues.. had to set up the proper modeline.
I found this post

[http://lists.debian.org/debian-powerpc/2002/05/msg00269.html]("http://lists.debian.org/debian-powerpc/2002/05/msg00269.html")

And if you scroll down to the monitor section, his values work fine. 

Modeline "1024x768"  78.741  1024 1058 1154 1312  768 769 772 800 +HSync +VSync

thats the line i used to get it to work properly. 

Start the pismo, and when it gets to the rolling lines, hit ctrl option f1.
login, and type sudo pico /etc/X11/xorg.conf and add the modeline to the monitor section. hit Ctrl+X , y , enter to save the newly modified file, and reboot.

---

### Post by iamdigitalman on 2007-04-24
ah yes, that did it. I just wanted to boot the live CD, as I just needed tol test a few pieces of hardware and do a few demos for some clients.

thanks.

-digital ;)

---

### Post by dpny on 2007-04-27
Finally got Feisty up and running on my Pismo. I had to install Edgy, download all the upgrades, and then do a distribution upgrade from inside Edgy. For some reason my machine absolutely would not successfully install from the Feisty CDs.

---

### Post by didg on 2007-04-27
Hi,

Can you post your Xorg.0.log?

Thanks

---

### Post by hinanzo on 2007-07-03
one thing i dont understand is (sorry i am a newb) how can you see the terminal when your screen is rolling. I have this problem with my Pismo. I installed xubuntu 7...but the screen rolls.

---

### Post by iamdigitalman on 2007-07-03
Actually, when the screen is rolling, xserver has started. I think you just press alt+F2 or something to quit xserver and get back to the command line.

correct me if i'm wrong.

oh, the pismo died. I have a 500mhz dual USB icebook in the mail, gonna try ubuntu on that, see if it's the early AGP portable machines (AGP 2x) that has the problem, or just the pismo.

-digital ;)

---

### Post by joninkrakow on 2007-07-03
> **dpny said:**
> Just tried with the Feisty alternate CD. Got through the partitioning process, but couldn't get packages from the CD because they were "corrupt". Has anyone been able to install on a Pismo from the Fesity CDs?

I've only had minor, niggling issues with Feisty on my Pismo (w/ Daystar G4 processor upgrade), namely, when I boot from the live CD, it boots to 800x600 resolution. Calling up a terminal, and running dpkg fixes that. 

I've tried to think what could be wrong in your situations, and the only thing I can think is that I cannot boot _any__ form of Linux while my external Firewire HD is plugged in. I have to unplug it, or weird things happen. I sometimes get weird screen, but typically, it just sits there and does nothing. If you have a FW hard drive, try unplugging it, and see if that gets you a boot.

-Jon

---

