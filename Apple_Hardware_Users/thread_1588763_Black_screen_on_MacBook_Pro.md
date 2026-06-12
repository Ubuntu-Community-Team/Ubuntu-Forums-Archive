---
title: "Black screen on MacBook Pro"
date: 2010-10-05
forum: Apple Hardware Users
---

### Post by Freek07 on 2010-10-05
Hi guys, since yesterday I have HUGE problems booting into linux (and having picture). I always update ubuntu (so it's up-to-date). Yesterday I booted into mac after a long time, there were some Mac software updates:
- Security update 2010-005 version 1.0
- Safari 5.0.2
- iTunes 10.0.1
- iWork update 4 9.0.4

First, some data:
MacBook Pro 5.1 (nvidia graphics + intel integrated for "battery")
Ubuntu 10.10

Been using ubuntu on it for 2 years with no problems, always on "nvidia" drivers.

The problem:

After sleep or shutdown (reboot), the monitor is black. The keyboard is illuminated, I can login blindly and go into terminal and reboot- so everything works, but there is no picture.

I tried connecting VGA monitor thru DisplayPort but there is no picture there, either.

The weird thing: There is picture in MacOS, there is picture in Refit, but right after refit, the monitor blanks- neither GRUB shows!

I tried booting from install CDs- 9.04, 9.10, 10.04, 10.10 daily- both desktop and alternate. Same problem!

After N (N>>10) reboots, the monitor works OK (for 1 run!!!). The only weird thing in syslog is (now I'm in MacOS so I can't copy it) kernel message telling that there are no nvidia graphics present.


Once again, neither grub shows.
Any ideas? :(

---

### Post by Freek07 on 2010-10-05
--- update ---
After hours of struggling the system booted again so I can provide some syslogs.

syslog and xorg.log from boot with blank screen are provided here.

Some nasty stuff from "black screen" syslog (compared to ok boot):
Console: colour dummy device 80x25 (vs. Console: colour VGA+ 80x25)
NVRM: No NVIDIA graphics adapter found! (vs. NVRM: loading NVIDIA UNIX x86 Kernel Module  256.53  Fri Aug 27 21:03:42 PDT 2010)


Any ideas? I'm thinking my card may be failing (but why does osX load flawlessly then?) or there might be some firmware crap in last apple update?

---

### Post by linuxopjemac on 2010-10-05
It does not seem to have any nVidia driver ?

---

### Post by Freek07 on 2010-10-05
xlog returns nvidia driver error BUT in syslog it can be seen that NVRM returns "no cards found"- as there wasn't graphics card in the computer...

---

### Post by inman2787 on 2010-10-06
When i encountered computer problem,i like to reinstall system directly.

---

### Post by Freek07 on 2010-10-07
I think the mac update f*cked it up. I tried disconnecting lid sensor (had to fix DVD anyway) and now non-mac stuff works, too. The lid sensor is not broken because it works(ed) in osX, it may be that is sending other event notification or something...it's weird.

I'll just leave it disconnected until mactel or some other guys fix it- I just can't work in OSX crapware...

it's only that I have to go "gnome->shut down->suspend" when I want to close it and take it away...but, saying that I cannot work on osX, I'll live thru it :)

Hiserdison: if there is no picture even in osX, it may be the [black screen of death.]("http://ariejan.net/2009/04/05/macbook-pro-black-screen-of-death-or-is-it-just-faking/")

---

### Post by disappearedng on 2010-11-24
Me 2. When I close the lid, my macbook pro won't come out of the blank screen. I think sleeping is messed up. 

I am on 6,2 with 10.10

---

### Post by disappearedng on 2011-01-04
me 3

---

### Post by synergy37 on 2011-01-31
> **disappearedng said:**
> Me 2. When I close the lid, my macbook pro won't come out of the blank screen. I think sleeping is messed up. 

I am on 6,2 with 10.10

I am on a Macbook 4,1 with 10.10 and have this same issue. Any ideas on a fix?

---

