---
title: "Automatic Sleep &amp; Wake Up"
date: 2008-02-22
forum: Apple Intel Users
---

### Post by antonluque on 2008-02-22
I have mythtv running on ubuntu 7.10 on a intel mac mini, and I would like to know if it would be possible to configure the computer so that it would go to sleep mode at night and wake up in the morning automatically, is that possible?? 

If it is possible, could you detail me how I would have to configure it??

Thanks,
Antonio

---

### Post by cyberdork33 on 2008-02-22
I don't think you can. Well, technically, you should be able to on a Mac, just like you can under OS X, but there is no way to do it in linux that I know of. You can add a cron entry at a certain time everyday (or even shutdown completely), but there is no code running in sleep, so you can't have cron wake up the computer too. I looked into something about this for a digital picture frame I built, and never found any information that led me to believe otherwise.

---

### Post by edm1 on 2008-02-22
Well you could use the shudown command with cron. But i think startup would be dependant on your bios. I know my laptop has a wake up time in bios but even then it would only bring you to the log in screen.

---

### Post by cyberdork33 on 2008-02-22
> **edm1 said:**
> Well you could use the shudown command with cron. But i think startup would be dependant on your bios. I know my laptop has a wake up time in bios but even then it would only bring you to the log in screen.No BIOS on a Mac...

The Mac firmware is capable of timed startups / wakeups, but it likely involves writing  certain NVRAM variables or EFI variables both of which are not easy to do right now on an Intel mac. In fact, I think it might require booting Linux from EFI which also nobody is doing right now because of limited software support.

---

### Post by antonluque on 2008-02-22
That's what I was going to say, that Macs have no Bios, and that I had to install Bootcamp and rEfit to boot the Ubuntu Partition.

I have configured rEfit so that it automatically boots the Ubuntu Partition, and I have configured the Ubuntu Settings so that it automaticaly logs in and start Mythtv.

So that I would just need to be able to wake up the computer in some way.

Thanks,
Antonio

---

