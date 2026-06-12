---
title: "Ubuntu changed my windows partition!"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Muppeteer on 2007-10-18
Ok well i've been using Ubuntu for a year now and had Feisty dual booting alongside windows. They were both on the same hdd but on different partitions of course. All was fine until i decided to fresh install Gutsy. So i just deleted the linux partition and the swap partition and got the installer to automatically partition the free space. Well the install failed and now i can't boot into Windows.

I had the same thing happen on my laptop which was only running windows and i installed Ubuntu Gutsy alonside it also. That install worked fine, i used acronis disk director to make the partiton beforehand. Though i can't get into windows. Somehow the ubuntu installer has replaced the first partition on the hdd with my downloads partition and windows is now the second and linux third. I went into the recovery console etc and fixboot, fixmbr but still no luck. 

Now i've noticed on my desktop the exact same thing has happened. Windows is now on a different partition and drive letter has changed to D: and i cannot boot into it. This has never happened before and i've used Edgy and Feisty without any problems and installed both many times. I managed to reinstall grub on the laptop and boot into ubuntu but now i'm stuck...All my windows boot files were still in the first partition which is no longer windows...I tried moving them over to windows partition but no change. 

Here's my Boot.ini
```
[boot loader]

timeout=1

default=multi(0)disk(0)rdisk(0)partition(2)\WINDOWS

[operating systems]

multi(0)disk(0)rdisk(0)partition(2)\WINDOWS="Microsoft Windows XP Professional" /noexecute=optin /fastdetect
```

Thanks in advance :)

---

### Post by snickers295 on 2007-10-18
linux use either grub or lilo as the master boot record and when you deleted the linux partition you deleted the boot sector.
i don't know what to do with it.

---

### Post by Frak on 2007-10-18
Download the [Super Grub Disk]("http://supergrub.forjamari.linex.org/") and set it to fix your Windows MBR,

---

### Post by Muppeteer on 2007-10-18
So how come the same thing happened on my laptop when it only had Windows? I've installed ubuntu more times than i care to remember and this has never happened...especially on both computers and the same distro...and when i deleted the linux partition from my main computer the installation failed and couldn't install grub. Which is why i tried fixboot and fixmbr but since the partitions were messed up this doesn't work...:(

---

### Post by Frak on 2007-10-18
Wait, so you're saying it messed up the windows partition also?

---

### Post by fallibledragon on 2007-10-18
PLEASE don't take offense at this -- most of us have done it, at one time or another.  But, it sounds like you don't really understand partitioning, and have messed it up yourself.  If you're wise, you have backups, and can simply try again.  If not, there are linux tools that'll help you fix it, as mentioned above.

---

### Post by Muppeteer on 2007-10-18
I'm only posting in beginners to get a quick response...i know how to partition drives...like i said i've installed Ubuntu and other flavours many times...Ubuntu has changed my windows partitions on both computers and they are no longer the first partition on the drive...

---

### Post by Frak on 2007-10-18
Do you have an Ubuntu disc still?

---

### Post by Muppeteer on 2007-10-18
Yeah, i'm in Gutsy on my laptop since i reinstalled grub...

---

### Post by Frak on 2007-10-18
> **Muppeteer said:**
> Yeah, i'm in Gutsy on my laptop since i reinstalled grub...
So, it works now...

---

### Post by Muppeteer on 2007-10-18
Ubuntu works but i can't get into windows since during the installation windows has somehow become the second partition on the disk and same story on my main computer...

---

### Post by Frak on 2007-10-18
Have you tried using the SGD, specifying your windows partition and booting into it?

---

### Post by Muppeteer on 2007-10-18
Yeah i just tried it and went through the option of removing grub and restored the windows boot but when i try and boot, grub is still there. Tbh it's a pretty awful program and badly explained...

Looks like i'll just have to get rid of ubuntu and stick with what works :(

---

### Post by Frak on 2007-10-18
> **Muppeteer said:**
> Yeah i just tried it and went through the option of removing grub and restored the windows boot but when i try and boot, grub is still there. Tbh it's a pretty awful program and badly explained...

Looks like i'll just have to get rid of ubuntu and stick with what works :(
Sounds like a partitioning problem to me. Where Grub is on a different MBR (one per HD)

---

### Post by Muppeteer on 2007-10-18
Strange how it happened on 2 seperate computers though and i was able to install Feisty on both without a problem using the exact same method...:confused:

---

### Post by adrian15 on 2007-10-18
> **Muppeteer said:**
> Yeah i just tried it and went through the option of removing grub and restored the windows boot but when i try and boot, grub is still there.
Which option did you use exactly?

> **Muppeteer said:**
> 
 Tbh it's a pretty awful program and badly explained...

We need your advice. You can make SGD a better program. You can contact me at adrian15sgd THEROUNDTHING gmail DOT com or at the [Super Grub Disk mailing list]("https://listas.ensanjose.net/listinfo/supergrub"). You should tell us what should be the best explanation and where it should be written.

> **Muppeteer said:**
> 
Looks like i'll just have to get rid of ubuntu and stick with what works :(


Did you try **Boot & Tools -> Boot Partition -> And choose your second partition ?** to see if you can boot windows?
And if you choose **Windows -> Boot Windows** does Windows boot?

EDIT-Begin
If you have restored Windows boot and it continues to boot into GRUB it might be that you need to activate the Windows partition too. You can find the option in: **Boot & Tools  -> Activate Partition** then select the first partition or the second partition. One of the two might work.
EDIT-End


adrian15

---

### Post by Muppeteer on 2007-10-18
Well i just formatted the windows partition on both computers and reinstalled windows. On my main computer i reinstalled Gutsy with all but my windows drive unplugged and it worked fine. That's normally what i do but i didn't to it today, so now i'll try again on the laptop and see what probs might arise...

Thanks for the help :)

---

### Post by adrian15 on 2007-10-19
> **Muppeteer said:**
> Well i just formatted the windows partition on both computers and reinstalled windows. On my main computer i reinstalled Gutsy with all but my windows drive unplugged and it worked fine. That's normally what i do but i didn't to it today, so now i'll try again on the laptop and see what probs might arise...

Thanks for the help :)

You never told us that Windows was on a second hard disk! Try to boot it with: **Windows -> Boot Windows from 2nd hard disk** and if it does not work try **Boot & Tools -> Activate Partition -> And select 2nd hard disk -> 1st partition** and try **Windows -> Boot Windows from 2nd hard disk** again.

adrian15

---

