---
title: "just installed.. won't boot."
date: 2009-04-01
forum: Apple Hardware Users
---

### Post by swiftnomad on 2009-04-01
IDE1 master partitioning

IDE master hda 41.0GB
#1 32.3 kb             Apple
#2 1.0 MB B K boot
#3 40.2 GB    ext3
#4 765.5 MB F swap     swap


The first time booting up it says Welcome to yaboot version 1.3.13

So anything I type. boot. etc etc. It says: 

Please wait, loading kernal...
/pci@f20000000/mac-io@17/ata-4@qf000/disk@0:3,\\1: No such file or directory.

The machine. Some old iMac.  Its white and blue. I think its a g3. I installed 8.04 alt powerpc and it went through.. no errors. 

If you need to know anything else.. let me know. but I would like to boot into linux. xD

---

### Post by swiftnomad on 2009-04-01
So- bumb? does anyone know how to fix this? I'm sure it's an easy fix??

---

### Post by genal on 2009-04-01
have you added the "acpi=off" option to your kernel-line?

---

### Post by swiftnomad on 2009-04-01
I haven't ever been able to boot into it. I just installed it.

---

### Post by stream303 on 2009-04-03
Some B&W PowerMacs have multiple drive-controllers which can make installation a bit more difficult.

You may have to manually edit your /etc/yaboot.conf with a corrected openfirmware path to get it to boot properly.

Be sure to see the B&W threads for more info - especially in the forum archives for ppc as well.

It is frustrating to be sure.

---

### Post by swiftnomad on 2009-04-03
How do I edit it and which one do I change it to? the swap or the boot one? I'm totally lost here.

---

### Post by stream303 on 2009-04-04
The first thing to do is help us identify your machine.  Take a look here and see if you can spot which one it is:

[http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html](http://www.everymac.com/systems/apple/powermac_g3/index-powermac-g3.html)

I notice you have a 40gb hard disk, which makes me think that it was installed as a replacement for the original?

If so, in addition to the multiple drive-controller issue, you'll most likely need to manually partition the drive yourself to keep the root / partition under 128gb, typically 125gb and then partition the rest of the drive as to how you want it.

Plus, in the end, if you only have 128mb of memory on board, will that be enough to do what you want to do with it?  Most recommend at least 256 or 512mb to be minimally useful with a normal desktop environment.

Throw in the fact that you won't have any 3D video, nor any 100% usable flash replacement, you may want to rethink how you use this box.

These are just some things to think about with that specific box, that may make this whole trip a lot more trouble than it is worth.

I'm not trying to put you off, but I don't know your personal frustration limit as a newcomer to linux.  Unfortunately with all the above, it isn't going to be as easy as just changing one or two config file lines.

Just trying to be honest and save a lot of possible time and frustration. :)

---

### Post by swiftnomad on 2009-04-04
Hello,

thanks for the reply. To be honest I'm not sure if the hdd was replaced or not. What I do know is that it does have 256mb of ram and I guess the hard drive was replaced.

That site didnt have my model number but I googled it and here it is:

[iMac g3]("http://www.dealtime.com/xPF-Apple-APPLE-IMAC-G3POWERPC-G3400-400-128-10-DVD-SND-NC-MAC-OS-9-2-BLEU-Apple")

I want to use it for my wife. Something I can have firefox on and a chat for her to use. That is basically going to be the essence of the use. 

I used the powerpc alternate install. (text) and the install went through good.

So, now. What exactly do I need to do?

---

### Post by swiftnomad on 2009-04-08
So, what do I do? I'm basically stuck? no one can help?

---

### Post by tiresia on 2009-04-08
You can try to reboot from the alternate CD in rescue mode. It looks like the open firmware path of the root partition is not correct in your yaboot.conf file.
Try to reconfigure your yaboot file starting in rescue mode and rebinding your partions.

Anyway if you don't have enough RAM, I would suggest you to install xubuntu (or Debian with Xfce). PPC-users have now the chance to use also a Xubuntu Live-CD (> 128MB RAM). I haven't tried it on such machines as your, but if you have time, I would be interested to know how it works
[http://ubuntuforums.org/showthread.php?t=1117130](http://ubuntuforums.org/showthread.php?t=1117130)
And maybe, using even ext4 for root partition (?)

---

### Post by swiftnomad on 2009-04-10
> **tiresia said:**
> You can try to reboot from the alternate CD in rescue mode. It looks like the open firmware path of the root partition is not correct in your yaboot.conf file.
Try to reconfigure your yaboot file starting in rescue mode and rebinding your partions.

Anyway if you don't have enough RAM, I would suggest you to install xubuntu (or Debian with Xfce). PPC-users have now the chance to use also a Xubuntu Live-CD (> 128MB RAM). I haven't tried it on such machines as your, but if you have time, I would be interested to know how it works
[http://ubuntuforums.org/showthread.php?t=1117130](http://ubuntuforums.org/showthread.php?t=1117130)
And maybe, using even ext4 for root partition (?)

so, I installed ubuntu with the alt dvd.. so, how do I change the yaboot file?

---

