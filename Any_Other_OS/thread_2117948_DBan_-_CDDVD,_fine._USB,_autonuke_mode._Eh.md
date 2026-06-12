---
title: "DBan - CD/DVD, fine. USB, autonuke mode. Eh?"
date: 2013-02-19
forum: Any Other OS
---

### Post by Roasted on 2013-02-19
I frequently repurpose old computers by putting Xubuntu on them and handing them out to people who have no computer but could use them. As a result, Clonezilla Live, GParted, and DBan are helpful utilities. 

DBan to nuke the drives prior to imaging for a better sense of data security, Clonezilla Live to pull the image I already built and have saved on my Samba file server, and GParted to expand that partition to take 100% of the disk when completed (image was built on a 40GB HDD, the smallest I'd ever consider handing out for light duty use).

I used MultiBoot to put all 3 ISO's on my flash drive. When I boot to DBan, it seems to automatically go into autonuke mode and nuke everything attached to the system. Thankfully, I have a dedicated computer JUST for this purpose, but it nukes my flash drive in the process. If I put it on a CD/DVD, it of course doesn't do this since optical drives are read only.

For greater confirmation, I totally redid the flash drive. It had no partition table when I plugged it back into my desktop. I booted back up to it via USB and sure enough, it began wiping everything, including the flash drive. I had no prompts, no confirmations, nothing. However once I pop in the DVD with the exact same DBan ISO on it that I used for USB, it works as intended and asks me what I want to do.

While I am beyond thankful I didn't try this on a computer where I wanted to nuke only specific drives inside (which is crazy in my opinion anyway... I highly advise unplugging any drives you don't want wiped prior to booting to DBan), it's still a situation very worthy of an answer. I can't seem to figure out the difference. Any insight?

---

### Post by UltimateCat on 2013-02-26
Intriguing situation you have!

> I frequently repurpose old computers by putting Xubuntu on them and  handing them out to people who have no computer but could use them

That's really amazing; your a good person Roasted:p

Until I read your post I hadn't heard of DBAN- -

Perhaps this article will enlighten you-
[http://download.cnet.com/Darik-s-Boot-and-Nuke-for-floppy-disks-and-USB/3000-2094_4-10911312.html](http://download.cnet.com/Darik-s-Boot-and-Nuke-for-floppy-disks-and-USB/3000-2094_4-10911312.html)

This article says that:
To guarantee your data's privacy, you pretty much have to take a sledgehammer or a blowtorch to your old drive. **Isn't that a tad over the top? **
[http://www.pcworld.com/article/254509/free_tools_to_wipe_your_drives_securely.html](http://www.pcworld.com/article/254509/free_tools_to_wipe_your_drives_securely.html)

---

### Post by Roasted on 2013-02-26
> **UltimateCat said:**
> 
This article says that:
To guarantee your data's privacy, you pretty much have to take a sledgehammer or a blowtorch to your old drive. **Isn't that a tad over the top? **
[http://www.pcworld.com/article/254509/free_tools_to_wipe_your_drives_securely.html](http://www.pcworld.com/article/254509/free_tools_to_wipe_your_drives_securely.html)

Yeah, I hear ya there. I've put hard drives through drill presses before... but I sort of need the drives intact in order to redo them. That's why DBan is a safe bet since it "safely" destroys the contents. I just found its behavior kind of strange considering when I USB booted it, it wiped my flash drive in the process automagically without asking me anything. :P

I'd like to highlight the importance of only having the drives you want to get wiped plugged in before you boot up to DBan... just in case.

---

### Post by CharlesA on 2013-02-26
You can do the same thing with dd. ;)

I don't know why DBAN is set to autonuke mode. The last time I booted it from USB, it asked me what to do.

Are you using the latest version?

---

### Post by Roasted on 2013-02-26
> **CharlesA said:**
> You can do the same thing with dd. ;)

I don't know why DBAN is set to autonuke mode. The last time I booted it from USB, it asked me what to do.

Are you using the latest version?

Whatever the latest was on the main site, but I thought I remember seeing it labeled as beta. Whatever is on the LiveUSB that acted up on two occasions is the same ISO that is on the LiveCD I made.

Just curious, I use the default DBan option known as the DoD short 3 pass. Is there an equivalent way to get that sort of method but with dd? Or would I just need to run a dd /dev/zero 3 times?

---

### Post by CharlesA on 2013-02-26
> **Roasted said:**
> 
Just curious, I use the default DBan option known as the DoD short 3 pass. Is there an equivalent way to get that sort of method but with dd? Or would I just need to run a dd /dev/zero 3 times?

I'm not sure. The last time I needed to wipe a drive and dban wouldn't boot for me, I just ran:

```
sudo dd if=/dev/urandom of=/dev/sdc bs=1M
```

I wrote a script to run it three times and then move on to the next drive. Dunno what the difference is, but it wiped the drive clean.

The only info I found was this:
[http://superuser.com/questions/528134/difference-between-dban-and-dd-command-to-securely-wipe-a-hdd](http://superuser.com/questions/528134/difference-between-dban-and-dd-command-to-securely-wipe-a-hdd)

---

