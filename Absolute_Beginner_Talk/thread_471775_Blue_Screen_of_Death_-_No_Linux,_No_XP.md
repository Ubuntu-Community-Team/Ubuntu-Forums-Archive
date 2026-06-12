---
title: "Blue Screen of Death - No Linux, No XP"
date: 2007-06-12
forum: Absolute Beginner Talk
---

### Post by viejo on 2007-06-12
I've been using Ubuntu now for at least a week with little problem. I tried to install NVIDIA and upon reboot Ubuntu freezes and I get BusyBox </bin/sh: can't access tty; job control turned off> Not knowing what this was, I tried to reboot this time to Windows in order to figure out the problem. This time XP wouldn't boot, always terminating at the blue death screen, regardless of type of bootup. Can anyone help me please!?! :(

---

### Post by dstew on 2007-06-12
What do you mean by "I tried to install NVIDIA"? Do you mean that you put new hardware in the machine, or that you installed some software? If software, tell us exactly what you did, if you remember.

---

### Post by viejo on 2007-06-12
I was installing the driver. Followed [http://ubuntuforums.org/showthread.php?t=432056]("http://ubuntuforums.org/showthread.php?t=432056") to install the correct driver. After I rebooted is when I encountered all the problems.

---

### Post by dstew on 2007-06-12
When you boot, do you get the grub menu? If so, try to boot using the recovery mode option. If it freezes, post the last page of errors to the forum if you can.

---

### Post by Kuoi on 2007-06-12
How old is the computer , and do you have a SATA drive.

Is time and date in your BIOS still correct ?

I can't see why XP gives the blue screen when you edit grub , but maybe someone can explain that to me.

I have the opinion that once your XP starts to boot (so grub is working) , that (maybe wrong) grub settings have nothing to do anymore with the further boot process of XP.
Am I wrong about this ?

So why the blue screen in XP ?

I am thinking about a BIOS setting , maybe you have a seperate  videocard , but somehow your "onboard" videochipset is enabled ?

Kuoi

---

### Post by viejo on 2007-06-12
I'm not sure what the grub menu is...sorry guys, very new...I thought I was good with computers ;)

I ran recovery mode on the most recent kernel (two listed...) and it did it's thing...last thing is...

```
Begin: Waiting for root file system... ...
Done.

          Check root= bootary cat /proc/cmdline
          or missing modules, devices: cat /proc/modules ls /dev
ALERT! does not exist. Dropping to shell!

BusyBox v1.1.3
Enter....

/bin/sh: can't access tty; job control turned off
```

---

### Post by MenZa on 2007-06-12
> **viejo said:**
> I'm not sure what the grub menu is...sorry guys, very new...

There's no reason to apologise; we all started out somewhere :)

The Grub menu is the boot loader for Ubuntu, which allows you to choose to boot Ubuntu on any kernel you may have installed, as well as Memtest86+. It looks like [this](http://www.omerique.net/twiki/pub/TIC/GrubStyleSuse/grub.png).

---

### Post by viejo on 2007-06-12
In windows, the blue screen tells me "unmountable boot volume"...

---

### Post by willl on 2007-06-12
Envy caused me problems at reboot when I tried it the other day. Rather than trying to fix things I just reinstalled Ubuntu and did the nvidia drivers by hand from their website. Some blue screen roughly equivalent to BSOD with scary errors about not starting something or other and no nvidia hardware being on the system.

---

### Post by viejo on 2007-06-13
So, used the live cd to recover my files, very handy. I then ran a scandisk type utility and low and behold, everything started again...windows and ubuntu. Well, actually, it said I had mismatching nvidia, which stopped me from logging into the x server. So, I reinstalled the matching driver, and we're up and running! 

It's been real!

---

