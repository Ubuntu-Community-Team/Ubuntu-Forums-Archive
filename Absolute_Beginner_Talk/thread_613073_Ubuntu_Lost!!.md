---
title: "Ubuntu Lost!!"
date: 2007-11-14
forum: Absolute Beginner Talk
---

### Post by Shinji Ikari on 2007-11-14
hi, i'm almost a complete noob but i have been mucking about with ubuntu for a little while now, dual booted on a toshiba satellite a40. i'm trying to get proficient enough to piff windows totally and here's a prime example why.
today, after windows giving me much grief, i formatted the windows partition, and now upon startup, i dont get the OS selection screen where i could previously choose which OS to boot into. Is there a simple fix?](*,)

---

### Post by overdrank on 2007-11-14
> **Shinji Ikari said:**
> hi, i'm almost a complete noob but i have been mucking about with ubuntu for a little while now, dual booted on a toshiba satellite a40. i'm trying to get proficient enough to piff windows totally and here's a prime example why.
today, after windows giving me much grief, i formatted the windows partition, and now upon startup, i dont get the OS selection screen where i could previously choose which OS to boot into. Is there a simple fix?](*,)

HI if you did not delete the partition with ubuntu then you will just have to reinstall the grub
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by Inxsible on 2007-11-14
But if the only OS you have on there is Ubuntu, why do you even need the grub menu to show up?

you are going to boot to it anyway :)

---

### Post by Shinji Ikari on 2007-11-14
thanx guys, i'm gonna read the link you posted. i think i wasnt clear enough, i formatted the wondows partition, and re-installed windows.. but i'll get on to that link now and try to re-install the grub.
will that give me back my original boot list? because i edited it to have xp at the top.

---

### Post by Inxsible on 2007-11-14
Yeah. Installing windows after Linux does that. It does not read the other OS'es sitting on your machine and simply boots you to Windows. Yes you will need to re-install grub.

You can also use the super grub disk. Google for it. I dont remember the link now :(

Good Luck.

---

### Post by Shinji Ikari on 2007-11-14
thanx heaps. the super grub looks a bit scary but the "How to restore Grub from a live Ubuntu cd" seems fairly straightforward enough so.. i'll try that and post back maybe tomorrow. thanx again.[-o<

---

### Post by Duck2006 on 2007-11-14
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by Shinji Ikari on 2007-11-15
:o i used the link you gave me on how to restore my grub to my mbr.. it worked fine, albeit the second time. i dont know but, i ran the commands and it seemed to work fine, but when i rebooted the computer it just went straight into (ugh) windows. so i restarted ubuntu with the live disc *again* and re-ran the commands, rebooted and the grub menu came up fine!! it actually restored my already modified grub file, which has windows as the first selection on the list, so if you just boot up and walk away, it will boot into windows. (i use this because my gf uses the computer and i dont want her to get confused:shock:
But, we're all good now, thanx to your help, and i can continue tinkering with ubuntu in preparation for the full switch:mrgreen:

---

### Post by Inxsible on 2007-11-15
> **Shinji Ikari said:**
> :o i used the link you gave me on how to restore my grub to my mbr.. it worked fine, albeit the second time. i dont know but, i ran the commands and it seemed to work fine, but when i rebooted the computer it just went straight into (ugh) windows. so i restarted ubuntu with the live disc *again* and re-ran the commands, rebooted and the grub menu came up fine!! it actually restored my already modified grub file, which has windows as the first selection on the list, so if you just boot up and walk away, it will boot into windows. (i use this because my gf uses the computer and i dont want her to get confused:shock:
But, we're all good now, thanx to your help, and i can continue tinkering with ubuntu in preparation for the full switch:mrgreen:you are most welcome.

Pleae mark your thread as solved. Thread Tools>>Mark thread as solved :D

---

