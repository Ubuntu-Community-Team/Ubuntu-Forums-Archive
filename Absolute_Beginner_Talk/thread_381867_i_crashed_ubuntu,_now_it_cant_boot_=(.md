---
title: "i crashed ubuntu, now it cant boot =("
date: 2007-03-11
forum: Absolute Beginner Talk
---

### Post by soul814 on 2007-03-11
So I was loading up beryl and then suddenly I got an BSOD sort of thing and it said some XGL error. I pressed "OKAY" and then I was in some black screen and I could type random stuff but commands didnt do anything. Like it was just plain black. So I restarted my computer and tried to boot again and now it hangs =( I tried normal boot and recovery. Any ideas?

---

### Post by Kobalt on 2007-03-11
I think you just broke your xserver... Did you make any backup of your xorg.conf file before messing with Beryl ? How did you install it by the way ?

---

### Post by soul814 on 2007-03-11
Xserver is the login screen which you choose which session to boot? Well, my linux was working fine since yesterday. I booted into windows to get some registries files in order to get my wine working and when I booted back into linux. I went to turn on my beryl and it gave me errors. When I run through recovery I see this.


usb 3-1: new full speed USB device using ohci_hcd and address 2
/sbin/int: error while loading shared libraries: /lib/tls/i686/cmov/libc.so.6: file too short
Kernel panic - not syncing: Attempted to kill init!
_ (<--- blinking cursor)

there are numbers before each line

---

### Post by soul814 on 2007-03-11
Well thanks for your help, I remember what I was doing before the crash. I installed ubuntu on my notebook so I was trying to get the hibernate feature to work. I used the command prompt and typed in the hibernate command and then I got an error. After that I found the mouse to be really slow so I restarted my system and then I loaded beryl again and I crashed. The hibernate made my computer crash I guess. I'm just going to reinstall ubuntu. Shouldn't take that long now that I got the hang of it. This time I won't mess around w/ hibernating I guess.

---

### Post by mamanmapillai on 2008-02-01
Hi,
I have over written the file /lib/tls/i686/cmov/libc.so.6
Now I am getting error like this.

error while loading shared libraries:/lib/tls/i686/cmov/libc.so.6:file too short


Any suggest how to correct this?

---

### Post by mamanmapillai on 2008-02-05
Hi,

I got the solution To solve Kernel panic - not syncing, attempting to kill init! problem.

First insert ubuntu livecd in your cd-rom and boot form cd-rom.
select install it will lead to some process after that you will find ubuntu Desktop.
open terminal and switch to root user  mount the root partition to some other directory and copy /lib files from some other machine and replace it. Now restart your system. It will Work.

Note: The file copied from the another machine should be the same version of Ubuntu

---

### Post by mamanmapillai on 2008-02-05
Hi,

I got the solution To solve Kernel panic - not syncing, attempting to kill init! problem.

First insert ubuntu livecd in your cd-rom and boot form cd-rom.
select install it will lead to some process after that you will find ubuntu Desktop.
open terminal and switch to root user  mount the root partition to some other directory and copy /lib files from some other machine and replace it. Now restart your system. It will Work.

Note: The file copied from the another machine should be the same version of Ubuntu

---

