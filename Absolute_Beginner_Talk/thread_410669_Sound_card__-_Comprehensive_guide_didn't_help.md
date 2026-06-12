---
title: "Sound card  - Comprehensive guide didn't help"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by Dan334477 on 2007-04-16
Hi,

I've worked through the comprehensive sound guide a few times, but I've had no luck.  Here is my situation:

Many hours ago, I installed a game, but didn't get sound when I ran it.  I attempted to update drivers, but I must have messed something up because now I don't get sound on anything (except these awful BIOS-esque beeps when I search for non-existent terms in Firefox).

I'm using nVida MCP51 High definition audio card, so worked through the guide using the intel8x0 driver.

when I get to the step sudo modprobe snd-intel8x0, I get this output:
```

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] Oops: 0000 [#1]

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] SMP 

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] CPU:    0
Segmentation fault
dan@Shrike:~$ 
Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] EIP is at kref_get+0x6/0x40

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] eax: 07400041   ebx: 07400041   ecx: 00000005   edx: 00000000

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] esi: ef26fbc0   edi: 00000000   ebp: f8eb3288   esp: f1cf7e14

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] ds: 007b   es: 007b   ss: 0068

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] Process modprobe (pid: 5793, threadinfo=f1cf6000 task=dfbe4030)

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] Stack: 00000008 dfbe413c e960f560 e960f560 07400029 c01e118f ef26fc40 c0246ace 

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]        c0246f5c 00000014 ef26fc40 c0380694 ef26f3c0 ef26fbc8 ffffffea 00000001 

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]        ef26fbc0 ef26fbc0 fffffff4 ef26f3c0 f8eb3288 c02472cd f1cf7e98 f1cf7e98 

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] Call Trace:

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]  <c01e118f> kobject_get+0xf/0x20  <c0246ace> class_device_get+0xe/0x20

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]  <c0246f5c> class_device_add+0x5c/0x330  <c02472cd> class_device_create+0x8d/0xc0

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]  <f8ec642f> snd_register_device+0x24f/0x260 [snd]  <f8ae716b> alsa_timer_init+0x16b/0x205 [snd_timer]

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]  <c012f880> blocking_notifier_call_chain+0x30/0x60  <c013cda8> sys_init_module+0x148/0x19c0

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000]  <c012bc00> __mod_timer+0x0/0xd0  <c0102fbb> sysenter_past_esp+0x54/0x79

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] Code: 08 35 00 00 00 c7 44 24 04 77 ce 2f c0 c7 04 24 b3 14 2f c0 e8 ec 10 f4 ff e8 97 30 f2 ff eb 80 90 8d 74 26 00 53 89 c3 83 ec 10 <8b> 00 85 c0 74 08 90 ff 03 83 c4 10 5b c3 c7 44 24 0c f9 38 2e 

Message from syslogd@Shrike at Mon Apr 16 01:28:54 2007 ...
Shrike kernel: [17179767.736000] EIP: [kref_get+6/64] kref_get+0x6/0x40 SS:ESP 0068:f1cf7e14
```

If anyone can help me, I would really appreciate it as I'm just sharpening my teeth in Linux and I'd like to have my sound back.

Thanks,

Dan

---

### Post by renzokuken on 2007-04-16
i had that card on my laptop and i beleive it is based on a realtek chipset, ALC883 or something.....(or is it a realtek card based on an nvidia chipset, cant remember which way round....anyways, its a moot point)

ok on my laptop, sounds appeared to work but nothing ever cam out of the speakers. i use edgy by the way.

i solved my sound issue by upgrading 'alsa-driver' from 1.0.12 (edgy default) to 1.0.14rc2 (latest unstable at the time on the alsa-project website) which has much better support for ALC883.

never had a problem since.

did your sound work before you installed that game?

i can post instructions on how to update alsa-drive if you need

---

### Post by Dan334477 on 2007-04-16
Yes.  Using Edgy 6.10.

Yes.  I had no problem with my soundcard before installing the game.  Only the game had sound issues until I tried to fix it.  That's when everything broke.

I would be very pleased if you posted instructions.  Thank you so much for your help!

Dan

---

### Post by renzokuken on 2007-04-16
well, my sound didnt work in the first place so this may not work for you. but its worth a try anyway i suppose.

before you do try it though. i would suggest posting exactly what you were doing when the sound broke and what steps you have taken already to try and remedy it.

but the instructions for updating alsa-driver are:

1. get the latest alsa-driver from [www.alsa-project.org](www.alsa-project.org) (think 1.0.13 is the latest stable) and save it to your desktop.

2. extract the file (either right click it and "extract here" or run **tar xjf alsa-driver-1.0.13.tar.bz2**

3. open the terminal and first install the stuff necessary to compile from source
```
sudo apt-get install build-essential
```

4. change to the alsa-driver folder

```
cd Desktop/alsa-driver-1.0.13
```

5. run the following commands in this order to compile it from source

```
./configure
make
sudo make install

```

reboot and see what happens

---

### Post by Dan334477 on 2007-04-16
Well, one additional thing that might be wrong is that I don't have a /etc/modprobe.conf file, apparently.  A lot of the troubleshooting guides I've seen refer to it.

---

