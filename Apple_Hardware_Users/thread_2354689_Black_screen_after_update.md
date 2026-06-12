---
title: "Black screen after update"
date: 2017-03-05
forum: Apple Hardware Users
---

### Post by Jethro_Borsje on 2017-03-05
Hi all,

I've been using Kubuntu for the past year on my macbook without any problems. Last week I decided to do a "apt-get dist-upgrade" because the normal "apt-get upgrade" held back the latest version of the kernel and I like to stay up to date. After the installation finished Kubuntu kept asking me to reboot, but I wanted to finish my work in the office. When I was done and went home I closed the lid of my macbook. The next morning when I opened the lid my macbook started to boot into grub instead of resuming where I was.

Once in Grub it doesn't matter what entry I choose, I always end up with a black screen (even if I choose the old kernel which is still also available). Now my only option is to boot into OS X from Grub, because that's the only one which is still working. I suspect my macbook did not correctly suspend and went out of power in my bag and that it somehow corrupted my installation because I upgraded the kernel but did not yet properly reboot.

I really hope somebody knows if there is a way to fix this issue.

Best regards,
Jethro Borsje (a now annoyed OS X user)

---

### Post by mörgæs on 2017-03-08
Yes, dist-upgrade is the way to go, else you will not receive kernel updates.

A good rule of thumb is that if a command is prefixed with sudo it demands full attention, both from you and from the rest of the system. When updating, shut down all other programs, use a powersupply, keep the computer awake and do a reboot right after if the kernel was part of the update.

---

### Post by Jethro_Borsje on 2017-03-09
Hi Morgaes,

Yeah, I know that. But what happened is that my power ran out and that I know get a black screen when starting up Kubuntu. It does't matter which option I pick from Grub. Do you know how to proceed?

I hope someone can help.

Best regards,
Jethro

---

### Post by mörgæs on 2017-03-09
It sounds like you are in a severe mess but before jumping to conclusions you could try booting into recovery mode if you haven't tried already.

---

### Post by Jethro_Borsje on 2017-03-12
> **mörgæs said:**
> It sounds like you are in a severe mess but before jumping to conclusions you could try booting into recovery mode if you haven't tried already. I already tried that, but it also gives a black screen.

---

### Post by luciano.x on 2017-03-12
First things first.
1 - Find what is causing the problem - try to boot a live Kubuntu usb or cd and check these logs
```

/var/log/syslog
/var/log/boot.log 
/var/log/dmesg
/var/log/kern.log

```

2 - Correct the problem. Maybe a file system corruption? fsck is your friend. 
Graphics driver? Install the previous working one (I already had that experience myself when I did the mistake to update nvidia driver. Oh well this fallback didn't worked, had to reinstall linux)

---

### Post by Jethro_Borsje on 2017-03-21
Thanks @luciano.x, today I was finally able to startup my Mac with an USB attached on which I installed Ubuntu.

None of the log files you mentioned contain anything from when I try to startup the laptop using Grub. The last log entries are from somewhere in the middle of the night after the upgrade. They say my laptop is going to sleep, probably because my battery was running low. After that there is nothing.

---

### Post by mörgæs on 2017-03-21
If you have been struggling with the problem now for two weeks I think it's time for a clean install.

---

### Post by Jethro_Borsje on 2017-03-21
I didn't get around to looking at it before today.

---

