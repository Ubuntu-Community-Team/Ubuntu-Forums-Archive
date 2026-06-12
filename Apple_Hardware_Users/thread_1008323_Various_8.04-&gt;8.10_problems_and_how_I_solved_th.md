---
title: "Various 8.04-&gt;8.10 problems and how I solved them."
date: 2008-12-11
forum: Apple Hardware Users
---

### Post by nblender on 2008-12-11
My Macmini mythfrontend was working pretty good on 8.04 but I decided to upgrade to 8.10.. That was more work than I thought it would be ...  Maybe some of what I went through was common and maybe this post might help... I'm not saying how I resolved things is correct; mind you...

(1) After the upgrade, the system wouldn't boot beyond reFIT. Black screen with only the word "GRUB" on the top left corner. That told me it had only loaded the MBR and that's it. I had to:

    sudo grub
    find /boot/grub/stage1
    root (hd0,2)  <-- s/2/whatever find returns/
    setup (hd0)

(2) then X (keyboard/mouse) didn't work due to HAL complaints in Xorg.0.log.  I had to restore my old xorg.conf using the old kbd/mouse driver stanzas.

(3) no Audio on the optical out.  I recompiled a newer version of Alsa from source. That fixed it immediately. (./configure && make && make install && reboot)

(4) No sound in mplayer. Change mplayer config in mythfrontend
    Old:  -ao alsa:device=plughw=0.1
    New:  -ao alsa:device=iec958,0,0

(5) kernel panic using smbfs and CIFS accessing a mountpoint on my Airport Extreme.  The panic was sporadic depending on the contents of the directory itself so there was some issue with the metadata.  ie: it mostly worked until I added another file to the directory from my Mac and then tried to access it from 8.10 through CIFS; instant kernel panic. I found a bunch of CIFS commits on Dec 3rd so I upgraded the kernel to 2.6.27.8 from kernel.org and now CIFS doesn't cause a panic.  Alsa sound from within 2.6.27.8 also works.

My remaining problem is my Apple bluetooth keyboard.  It doesn't connect on boot even though all the bluetooth modules are enabled and HIDD is enabled.  I have to run a little script from rc.local that periodically monitors /proc/bus/input/devices for the presence of my keyboard and failing that, reconnects:

#!/bin/sh
while true
do
grep -q Apple /proc/bus/input/devices  || hidd --connect 00:1D:4F:A6:19:61
sleep 10
done

Hope this helps someone.[CENTER][/CENTER]

---

### Post by milkwood on 2008-12-11
I would like you to die.
Good luck!
Bye):P

---

### Post by nblender on 2008-12-11
Just what is that supposed to mean? Or is my sarcasm bit broken?

---

### Post by swimon on 2008-12-11
is your mac a PPC or intel ?

Grtz

---

### Post by nblender on 2008-12-11
Oops. Should have specified. 

vendor_id       : GenuineIntel
cpu family      : 6
model           : 15
model name      : Intel(R) Core(TM)2 CPU         T5600  @ 1.83GHz
stepping        : 2
cpu MHz         : 1833.287
cache size      : 2048 KB

---

### Post by milkwood on 2008-12-12
I'm so sorry!
I'd just done a wrong thing to you.
I even didn't intend to do this for you.
I'm so sorry.
I was just going to say that to someone else.
Please forgive me:cry:!

Sincerely,
milkwood.

---

### Post by Leslie Viljoen on 2008-12-12
You could edit the message? No harm in removing mistakes.

---

### Post by cyberdork33 on 2008-12-12
Would you mind trying to update this page?
[https://help.ubuntu.com/community/Mac_mini](https://help.ubuntu.com/community/Mac_mini)

It is a bit out of date.

---

### Post by nblender on 2008-12-12
hmm. It's not clear that anything I have to say will update anything on that page.  When I installed 8.04 from DVD, it didn't go nicely either... ie: the system was not bootable after the installation either; I had to reboot to a rescue shell and use grub-install /dev/sda3.  I'm also not running any of the default desktop environments (gdm and openbox straight into Mythfrontend)... 

I'm happy to contribute but I'm a linux newbie.. I hack BSD kernels for a living.

---

### Post by cyberdork33 on 2008-12-12
> **nblender said:**
> hmm. It's not clear that anything I have to say will update anything on that page.  When I installed 8.04 from DVD, it didn't go nicely either... ie: the system was not bootable after the installation either; I had to reboot to a rescue shell and use grub-install /dev/sda3.  I'm also not running any of the default desktop environments (gdm and openbox straight into Mythfrontend)... 

I'm happy to contribute but I'm a linux newbie.. I hack BSD kernels for a living.
well, ok. If you come across anything that is useful please do add.

---

