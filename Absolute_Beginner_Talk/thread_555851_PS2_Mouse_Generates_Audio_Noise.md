---
title: "PS/2 Mouse Generates Audio Noise"
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by Bezmotivnik on 2007-09-20
[Nothing definitive in the auto-search...:???:]

I'm putting together a 7.04 Ubuntu box for a friend and the BTC PS/2 scrolling mouse makes a dreadful amount of noise through the speakers from the CM8738 onboard audio.  There was no noise with same computer when previously running Windows, so I would assume it's not the hardware.

Any thoughts?

Thanks!

---

### Post by Daveth on 2007-09-20
are we talking about some sort of feedback directly related to mouse movement, or just a general din when the mouse is plugged in, but stationary? 

Never heard of PS/2 feedback before.

---

### Post by Bezmotivnik on 2007-09-20
> **Daveth said:**
> are we talking about some sort of feedback directly related to mouse movement

Yep.  Bad.

---

### Post by Daveth on 2007-09-20
found this

[http://groups.google.com/group/microsoft.public.windowsxp.hardware/browse_thread/thread/71bfdc4e7de5a20/f18331a250325608?hl=en&lnk=st&q=Ps%2F2+mouse+feedback+noise&rnum=5#f18331a250325608](http://groups.google.com/group/microsoft.public.windowsxp.hardware/browse_thread/thread/71bfdc4e7de5a20/f18331a250325608?hl=en&lnk=st&q=Ps%2F2+mouse+feedback+noise&rnum=5#f18331a250325608)

but this hardware related. 

Another post postulated that the signal path from mouse location was giving feedback intereference to the on-board sound chip-- but no-one answered!
Nearly Christmas- new mouse?

---

### Post by Bezmotivnik on 2007-09-20
> **Daveth said:**
>  new mouse?
I have a few around here; I'll swap some around and see what happens.  I figured any PS/2 mouse was the same as the next.

I was going to use a plain old 2-button serial mouse, but Ubuntu wouldn't recognize it.  Weird, huh?

---

### Post by Daveth on 2007-09-20
what is the motherboard supporting all this kit?

---

### Post by Lord Illidan on 2007-09-20
> **Bezmotivnik said:**
> I have a few around here; I'll swap some around and see what happens.  I figured any PS/2 mouse was the same as the next.

I was going to use a plain old 2-button serial mouse, but Ubuntu wouldn't recognize it.  Weird, huh?

USB?

---

### Post by Bezmotivnik on 2007-09-20
> **Daveth said:**
> what is the motherboard supporting all this kit?
Oh, an older (but almost unused) ASUS A7M266 w/Athlon 1.4G.  A very nice rig in its day. 

Seems to work great so far, other than this racket.  May just be the mouse [shrug]...

---

### Post by dn_desaku on 2007-09-20
This may be unrelated (but it may help kinda), I sometimes get problems with my speakers because the plug is dirty or static affected it.

---

### Post by Bezmotivnik on 2007-09-20
> **Lord Illidan said:**
> USB?
Funny you should mention that!  I just found a new Ubuntu bug:

PS/2 mouse and PS/2 keyboard work fine, but the mouse is noisy in operation.

Shut down.

Replace PS/2 mouse with USB mouse.

Reboot.

USB mouse works (still noisy), but PS/2 keyboard is stone dead.

Reboot.

No change.

Shut down.

Replace USB  mouse with PS/2 mouse.

Reboot.

Both PS/2 mouse and PS/2 keyboard work again. :confused:

As for the original problem, I'll jumper out the onboard audio and try PCI audio.  Supposedly this works to clear noise problems.

---

### Post by Lord Illidan on 2007-09-21
Crazy bug!!

I never heard the like. From googling, I can see one potential solution.

Can you open your /boot/grub/menu.lst please?

```
sudo gedit /boot/grub/menu.lst
```

Scroll down until you see the first paragraph which looks like this :

```
title        Ubuntu, kernel 2.6.20-16-lowlatency (on /dev/sda4)
root        (hd0,3)
kernel        /boot/vmlinuz-2.6.20-16-lowlatency root=UUID=375fef61-bf3d-4772-ab16-45fd522d3d3d ro quiet splash 
initrd        /boot/initrd.img-2.6.20-16-lowlatency
savedefault
boot
```

It will look a bit different since we are on different systems, but that is the gist of it. Now, in the line :
```
root=UUID=375fef61-bf3d-4772-ab16-45fd522d3d3d ro quiet splash 
```

I want you to append : no-hlt to your version..so for example, mine would look like :
```
root=UUID=375fef61-bf3d-4772-ab16-45fd522d3d3d ro quiet splash no-hlt 
```

[B]Make sure that the root = .... is [COLOR=Red]ALL ON ONE LINE[/COLOR]. And, [COLOR=Red]DO NOT COPY[/COLOR] my version and paste it into yours, it will[COLOR=Red] NOT[/COLOR] work.

[/B]Sorry for the shouting but it's very important, as if you make a mistake, you might not be able to boot again without getting into a bigger hassle.

I got the no-hlt thing from here, if anyone is interested : [http://lau.linuxaudio.org/audio_quality_HOWTO.htm](http://lau.linuxaudio.org/audio_quality_HOWTO.htm)

---

### Post by Lord Illidan on 2007-09-25
Did this work, incidentally?

---

