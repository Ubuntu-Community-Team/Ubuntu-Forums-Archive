---
title: "Kubuntu does not start on boot up -"
date: 2007-10-01
forum: Absolute Beginner Talk
---

### Post by dhavalbbhatt on 2007-10-01
There is obviously something wrong that I am doing - although I can't figure out what - I am only installing from the CD on to my various hard drives. Here is what I have / did -

I have on my first hard drive (SATA 160GB) Ubuntu 7.10 installed - works fine, except for the nvidia issue, for which I have a work around for the time being - not entirely happy though - but it works. I don't plan to install any other OS on this HD.

On my second HD, which is an IDE 80GB HD, I (thought!) I installed Kubuntu 7.04 from the CD. However, when the grub loads up and asks me which HD I want to boot from and when I select my IDE HD, it seems to me that the computer freezes and doesn't do anything. I have to power the machine down and re-start - fortunately, I haven't lost my first HD - I can still boot from that HD (phew!).

On my third HD, which is a SATA 320GB, I would like to install either Kubuntu 7.10 or Ubuntu 7.10 but for AMD64 architecture. I have not done anything with that HD - it does have Ubuntu 7.04 on it, however, it has the same problem as the IDE HD - seems to freeze when I select it from the grub.

At the time of install - in the advanced options, it does ask for boot loader options and currently they seem to be pointing to HD0 (my primary SATA 160GB drive). Not sure if that is the reason why my other two HDDs fail to power up. Should I be changing the boot loader option to point to the HDD where I am installing the respective OS? Any help would be greatly appreciated.


Thanks,
DB

---

### Post by benerivo on 2007-10-02
> At the time of install - in the advanced options, it does ask for boot loader options and currently they seem to be pointing to HD0 (my primary SATA 160GB drive). Not sure if that is the reason why my other two HDDs fail to power up. Should I be changing the boot loader option to point to the HDD where I am installing the respective OS?

You should keep at set at HD0 as it needs to be on the drive that your PC's BIOS is set to try and boot from (which is your SATA).

I'm not sure why Kubuntu on your 2nd drive, or your Ubuntu on the 3rd both fail to even start.

---

