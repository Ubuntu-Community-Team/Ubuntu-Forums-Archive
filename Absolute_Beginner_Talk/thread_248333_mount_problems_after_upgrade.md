---
title: "mount problems after upgrade"
date: 2006-08-31
forum: Absolute Beginner Talk
---

### Post by graphius on 2006-08-31
Like a lot of other people, I wanted to try ubuntu. I installed it on my laptop and everything worked (other than the IR port, but I can live with that) until I installed the update. It was the new version, not the "bad one"
Now my usb drive and pcmcia card reader will not automount. 
I have searched for, and tried some of the solutions in these forums, but no luck.

Help!!

---

### Post by kidders on 2006-08-31
This may turn out to be a stupid question, but can you mount them manually? (ie how *bad* is the problem?)

When was the last time they worked for you? Were you maybe using another Linux at the time?

Incidentally, have you posted another thread about the IR port? (They can be a real pain in the neck when they don't cooperate!)

---

### Post by graphius on 2006-08-31
no, I can't mount them manually. 
and I have kind of given up on the IR for now...

---

### Post by kidders on 2006-08-31
Ah. Not good news :(

What error messages do you get?

I suppose what I'm wondering is...

[LIST]
[*]can't you mount your devices because the drivers for the hardware itself aren't loading, or
[*]are you having filesystem-related troubles?
[/LIST]

Could you perhaps post some of the system messages you get when you do a few things ...

[LIST=1]
[*]Plug out your USB disk, say, and take a look @ dmesg
[*]Plug it back in and post the changes
[*]Try to mount a partition on your USB thingy
[*]Post the dmesg changes again.
[/LIST]

Be sure and let me know if these questions are too basic or too complicated!

---

### Post by graphius on 2006-09-01
With nothing in the USB ports
> usb 4-1: new high speed USB device using ehci_hcd and address 87
[17191621.956000] usb 4-1: device not accepting address 87, error -110
[17191622.068000] usb 4-1: new high speed USB device using ehci_hcd and address 88
[17191632.492000] usb 4-1: device not accepting address 88, error -110
[17191632.604000] usb 4-1: new high speed USB device using ehci_hcd and address 89
[17191643.028000] usb 4-1: device not accepting address 89, error -110
[17191643.360000] usb 4-1: new high speed USB device using ehci_hcd and address 90



and on for a lot of address's

then after plugging in USB stick... same message.

no partitions found, nothing...
USB's are working as a mouse plugged in works, and usb stick works in other machines.

when I first plug in the stick, the light flashes to show the system is accessing, but then nothing...

If it makes any difference, I am using an Acer 1350 laptop...

---

### Post by kidders on 2006-09-01
Oh dear. This one crops up every so often and can be due to a number of things, some of them nasty. Basically, you're having a communications problem that prevents the USB stick and the computer even talking to eachother.

A few more questions:

[LIST]
[*]Q1: Are you attaching your USB devices to your computer with dodgy cables?
[*]Q2: Are you trying to plug a high speed device into a low speed port?
[*]Q3: Do *any* USB devices work with these ports (or does your USB stick work in other ports)?
[/LIST]

As a random thought, give this a try, just to see what happens:

```
rmmod ehci-hcd
```

Exactly what version of Ubuntu are you using, by the way? Another possible solution for this one might be to upgrade your kernel. Every now and then some people seem to have this problem, but I'm not aware of a single common solution :(

Was any of that helpful?

---

### Post by graphius on 2006-09-01
kidders, you are a genius. Well almost. did the "sudo rmmod ehci-hcd" thing, and now my usb drives work. My PCMCIA card reader will still not work though...

but thanks. I was this close >--------------< to going back to windows...

---

### Post by kidders on 2006-09-01
Oh crimmony, don't say that!!

I'm sure the PCMCIA problem can also be solved pretty easily, but I'm afraid I would only be guessing :( I've never used one ... they always spell trouble lol.

If you fancy it, post your error messages. If I can't help you, you can always make a new thread :P

---

### Post by Dre1 on 2006-09-02
It seems that I have the same USB problem as the first poster. That is, after the last update the flash disk of my mobile phone connected via USB is no longer automounted (see the output of dmseg below). However, my USB memory stick does automount. Unfortunately, the rmmod-thing that did the trick for the first poster does not work for me. (What I did was 'rmmod uhci_hcd', and I fear that this was no good idea. What do you people think?) Can anybody help?

[4295123.473000] usb 1-1: new full speed USB device using uhci_hcd and address 6
[4295123.586000] usb 1-1: device descriptor read/64, error -71
[4295123.800000] usb 1-1: device descriptor read/64, error -71
[4295124.003000] usb 1-1: new full speed USB device using uhci_hcd and address 7
[4295124.116000] usb 1-1: device descriptor read/64, error -71
[4295124.329000] usb 1-1: device descriptor read/64, error -71
[4295124.532000] usb 1-1: new full speed USB device using uhci_hcd and address 8
[4295124.940000] usb 1-1: device not accepting address 8, error -71
[4295125.042000] usb 1-1: new full speed USB device using uhci_hcd and address 9
[4295125.450000] usb 1-1: device not accepting address 9, error -71

---

### Post by Dre1 on 2006-09-03
I found an acceptable workaround for my problem: If I put the phone into offline mode before I connect it to the USB port, the flash disk of the phone is automounted correctly. The phone automatically enters offline mode as soon as it is connected to the usb-port, and before the update it wasn't necessary to put it into offline mode manually. So it seems there is a handshaking problem since the update. But anyways, I am happy with the solution I found.

---

