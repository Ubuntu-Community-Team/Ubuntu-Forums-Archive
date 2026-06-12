---
title: "Why so slow? (Both at boot and in general.)"
date: 2007-03-03
forum: Absolute Beginner Talk
---

### Post by Raavea on 2007-03-03
My computer died last week. It just stopped working - it got to where it tries to load the kernel and stuck. I got a message that I have since forgotten, but which basically said that the hard-drive didn't seem to exist and thus could not be booted. I had to leave the computer for around an hour and a half for the boot to get that far. 

 I thought it was dead for good - hard drive died and needing replaced. But if it remembered which kernel I had, and had grub there, surely the hard disk must just be a bit sick? So I played about with my liveCD. Memtest fine - nothing wrong with my RAM. (256 DDR) Boot from hard drive got the same hour of nothing followed by the error. I decided I couldn't really be bothered to fiddle with it, so I just on a hunch tried wiping it and re-installing Ubuntu.

 It's slow as hell. It was never this slow before! What could be causing it? My little graphs say that I have the following in use, all I have open is this FF window;
 Processor: 16% in use
 Memory: 27% cache, 66% programs
 Network: Zilch
 Swap: 22% in use
 Load Average: Zilch
 Disk: 0%

 What can be causing my issues? This is so slow it's maddening. Even for this thing with it's sucky RAMs, it's slow... And don't get me started on the boot time. 


 What can I do to find the problems, and fix them?

 Thanks in advance! :]

---

### Post by kerry_s on 2007-03-03
With that much ram you should switch to xubuntu, which would run much lighter.

-> [http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso](http://archive.ubuntu.com/ubuntu/dists/edgy/main/installer-i386/current/images/netboot/mini.iso)

---

### Post by konungursvia on 2007-03-03
Is it a laptop? I had the same thing. Had to install Debian Sarge to fix it, though Dapper is fine on my bigger machine.

---

### Post by laidback on 2007-03-03
I'd start by going into the Bios and getting it to find hd's again, Mine has an option to do this, also I'd check that the CPU is running at best possible speed. On odd occassions my BIOS resets itself which means that it looses the hd config and sets the cpu speed to minimum! It's old so I forgive it.

---

### Post by Raavea on 2007-03-04
**Kerry_S** - I have tried using just XFCE, it is no faster. Same with fluxbox which I am currently using. The only difference is that menus display a little bit quicker in flux.
**Konungursvia** - Yah, it's a laptop. It was fine a little while back with Ubuntu, so it shouldn't be playing up like this.
**Laidback** - How do I do that? My bios don't have much in the way of options. I didn't see anything for finding it's hd, or working with the other settings my old PC had in bios. It just has boot order, system time, alarm time, and some other useless things.

---

### Post by konungursvia on 2007-03-04
Same here with my Acer laptop. Ubuntu ran fine for a week or two, then after one of the updates or installs, I had exactly your problem, and tried re-installing dapper and edgy several times -- the thing slowed to a crawl after a random period of time, usually ten minutes of apparently perfect operation. I think Ubuntu couldn't recognize and communicate with the laptop hardware too well. Like I said, Debian 3.0 now runs on it solid as a rock.

---

### Post by mcduck on 2007-03-04
> **laidback said:**
> I'd start by going into the Bios and getting it to find hd's again, Mine has an option to do this, also I'd check that the CPU is running at best possible speed. On odd occassions my BIOS resets itself which means that it looses the hd config and sets the cpu speed to minimum! It's old so I forgive it.

That sounds like your CMOS battery needs to be replaced. It's a small battery, usually located around lower right corner of the motherboard, and it's used to provide enough power to store you BIOS settings when the machine is powered off.

---

### Post by laidback on 2007-03-05
mcduck,
I agree, so I changed it a week or so back. Some improvement but not completely solved.

---

### Post by laidback on 2007-03-05
Raavea,
Goodness me, I've never come across a BIOS like that, so little control. Guess your stuck on that front then.

Sorry

---

### Post by Raavea on 2007-03-06
No probs laidback - it is a lended laptop 'cuz I kinda blew my PC up a while back and my mother couldn't stand the idea of not having me around to enslave into free webdesign. :lol:

It's a Toshiba Satellite Pro.. If I am correct, the bios is reached by hitting esc during the first few moments of bootup, when it flashes the Toshiba splash. This takes me to something with virtually no control compared to the screen the same proceedure got me on my old bit of kit.

I just don't understand why it is so slow.. I even wiped and rebooted. Perhaps the HD is a bit corrupt or something.. o.O? 
I will make do.. Fluxbox is nice and fast but programs are still slow to load. Firefox takes around a minute and a half to pop open... Oy vay, as they say, and life is life and will go on.



...I'm sure it'd go on better if I had a decent rig though. :lol:

---

