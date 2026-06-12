---
title: "[SOLVED] No Sound"
date: 2007-08-18
forum: Absolute Beginner Talk
---

### Post by kshane on 2007-08-18
Just made a second user account for my wife.  She has admin access.  We have a dual boot with Vista.  No sound probs in Vista or my Ubuntu account.  After I added my wife's user account, I found there was no sound only for her.  My Ubuntu has sound.  Both our accounts in Vista have sound.  Any ideas?  I had a previous install of Ubuntu (feisty) set up with 2 accounts, but no sound trouble at all...  Any ideas?

Thanks!

---

### Post by Happy_Man on 2007-08-18
Try the command ```
alsamixer
``` and see if all the bars are maxed out.

---

### Post by kshane on 2007-08-18
> **Happy_Man said:**
> Try the command ```
alsamixer
``` and see if all the bars are maxed out.

Thanks for the assist...

Here's the output from that command:
```

sherri@home:~$ alsamixer

alsamixer: function snd_ctl_open failed for default: No such device

```

---

### Post by Happy_Man on 2007-08-18
Oooookaaaay..... that's interesting. I think it's saying that it can't find a sound card. Could you please run the command ```
lspci
``` and post the output?

---

### Post by kshane on 2007-08-18
> **Happy_Man said:**
> Oooookaaaay..... that's interesting. I think it's saying that it can't find a sound card. Could you please run the command ```
lspci
``` and post the output?

Here it is...

```

00:00.0 Host bridge: Silicon Integrated Systems [SiS] 755 Host (rev 01)
00:01.0 PCI bridge: Silicon Integrated Systems [SiS] SG86C202
00:02.0 ISA bridge: Silicon Integrated Systems [SiS] SiS964 [MuTIOL Media IO] (rev 36)
00:02.5 IDE interface: Silicon Integrated Systems [SiS] 5513 [IDE] (rev 01)
00:02.7 Multimedia audio controller: Silicon Integrated Systems [SiS] AC'97 Sound Controller (rev a0)
00:03.0 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.1 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.2 USB Controller: Silicon Integrated Systems [SiS] USB 1.0 Controller (rev 0f)
00:03.3 USB Controller: Silicon Integrated Systems [SiS] USB 2.0 Controller
00:04.0 Ethernet controller: Silicon Integrated Systems [SiS] SiS900 PCI Fast Ethernet (rev 91)
00:05.0 IDE interface: Silicon Integrated Systems [SiS] RAID bus controller 180 SATA/PATA  [SiS] (rev 01)
00:18.0 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] HyperTransport Technology Configuration
00:18.1 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Address Map
00:18.2 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] DRAM Controller
00:18.3 Host bridge: Advanced Micro Devices [AMD] K8 [Athlon64/Opteron] Miscellaneous Control
01:00.0 VGA compatible controller: ATI Technologies Inc Unknown device 71c1 (rev 9e)
01:00.1 Display controller: ATI Technologies Inc Unknown device 71e1 (rev 9e)


```

---

### Post by Happy_Man on 2007-08-18
Hmmm..... from [http://hardware4linux.info/component/16054/](http://hardware4linux.info/component/16054/) , it would appear that alsamixer won't work with this sound card. They suggest to install the package "pcmciautils" and run "pcm". Then it should work.

---

### Post by schorsch on 2007-08-18
O.K. you have sound but not your wife? I guess you are in the group "audio" (this can be checked by the command "id" as your user). Is she in the group "audio",too? This can be checked by the command "id UOYW" with UOYW=username of your wife.
If not you can add her with the follwing command:
```
sudo usermod -aG audio *UOYW*
```. Do not type UOYW but substitute it as mentioned above. That should do the trick.
To be on the safe side I would add her to all the groups that you belong to as long as you trust her ;-)

---

### Post by kshane on 2007-08-18
> **schorsch said:**
> O.K. you have sound but not your wife? I guess you are in the group "audio" (this can be checked by the command "id" as your user). Is she in the group "audio",too? This can be checked by the command "id UOYW" with UOYW=username of your wife.
If not you can add her with the follwing command:
```
sudo usermod -aG audio *UOYW*
```. Do not type UOYW but substitute it as mentioned above. That should do the trick.
To be on the safe side I would add her to all the groups that you belong to as long as you trust her ;-)

Yes!  That did the trick!  Your help is VERY MUCH APPRECIATED!

Thank you also, Happy_Man!

---

### Post by schorsch on 2007-08-18
Glad to hear that! Could you please mark your thread as solved as this could help others, too?

---

### Post by kshane on 2007-08-18
> **schorsch said:**
> Glad to hear that! Could you please mark your thread as solved as this could help others, too?

Done deal!   Thanks again...    :-D

---

### Post by Lord Illidan on 2007-08-18
If you want a GUI way of doing it, here it is..

System -> Administration -> Users and Groups

---

### Post by Happy_Man on 2007-08-18
Aaand, as usual, I run off on completely the wrong track. Ah well, glad to see you got that fixed.

---

