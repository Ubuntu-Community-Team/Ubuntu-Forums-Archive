---
title: "Need help with ATI drivers...."
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by ghostchamber on 2007-09-16
Ok, so I'm very new to Linux.  I just installed it today, and my first order of business is to get the ATI drivers properly installed.  I got every step in the guide down, except for this last one:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87)

I did the part with the Restricted Drivers Manager, but the part after that is what vexes me: "so you have to blacklist it by changing..."

I'm not sure how to do that.  Like I said, I'm new, and my primary concern at this point is being able to change the refresh rate on my monitor, as 60 is not pleasant at all.

Any help is appreciated.

---

### Post by pay on 2007-09-16
Type into the terminal```
gksudo gedit /etc/default/linux-restricted-modules-common
```A text editor should show up (gedit). In that editor, type > DISABLED_MODULES="somemodule2 fglrx"Save it and exit. Thats it.

---

### Post by Maestro23 on 2007-09-16
> **ghostchamber said:**
> Ok, so I'm very new to Linux.  I just installed it today, and my first order of business is to get the ATI drivers properly installed.  I got every step in the guide down, except for this last one:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87](https://help.ubuntu.com/community/BinaryDriverHowto/ATI#head-b5a44a0fc19768c47798bde0a644306c601aca87)

I did the part with the Restricted Drivers Manager, but the part after that is what vexes me: "so you have to blacklist it by changing..."

I'm not sure how to do that.  Like I said, I'm new, and my primary concern at this point is being able to change the refresh rate on my monitor, as 60 is not pleasant at all.

Any help is appreciated.

You open a terminal edit the **/etc/default/linux-restricted-modules-common**.

They are using the **gedit** editor to do this.  You need to be root to edit the file because it is in the /etc directory which is owned by **root**.  Hence the **gksudo** command.

Once you open the file, find the line they tell you to change and change it, then save/exit.

There are other editors out there: nano, kate, mouse, vi.  Just depends what you have installed on your system.  If you are using Gnome then gedit, KDE = kate.



Read up on RootSudo as well: [https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29](https://help.ubuntu.com/community/RootSudo?highlight=%28RootSudo%29)

---

### Post by asmoore82 on 2007-09-16
I'm quite experienced in Linux but I just went through this "newest ATI drivers on Ubuntu"
yesterday and I don't recommend doing it yourself unless you absolutely have to have
the newest driver for some bizarre reason; that reason will probably become much more
understandable next month when the AIGLX/Composite/compiz compatable driver is released ...

for now, I highly recommend just sticking to the 8.34 version of the driver available in the repos
(newest version direct from ATI is 8.40); the package name in the repos is 'xorg-driver-fglrx'

if you are running Ubuntu 7.04, you should be able to just enable the driver in
"System -> Administration -> Restricted Drivers Manager" and be done with it.

---

### Post by alienexplorers on 2007-09-16
You could try running the ENVY script to load your ATI drivers.  I have used it and it worked for me.

---

### Post by ghostchamber on 2007-09-17
> **asmoore82 said:**
> I'm quite experienced in Linux but I just went through this "newest ATI drivers on Ubuntu"
yesterday and I don't recommend doing it yourself unless you absolutely have to have
the newest driver for some bizarre reason; that reason will probably become much more
understandable next month when the AIGLX/Composite/compiz compatable driver is released ...

for now, I highly recommend just sticking to the 8.34 version of the driver available in the repos
(newest version direct from ATI is 8.40); the package name in the repos is 'xorg-driver-fglrx'

if you are running Ubuntu 7.04, you should be able to just enable the driver in
"System -> Administration -> Restricted Drivers Manager" and be done with it.
That doesn't seem to give me the ability to increase my refresh rate.  That is my primary concern, as 60 is somewhat headache-inducing.

---

### Post by alienexplorers on 2007-09-17
You could try adding a modeline to your monitor section of the xorg.conf file.
Example:
>  # 1024x768 @ 70.00 Hz (GTF) hsync: 56.00 kHz; pclk: 76.16 MHz
  Modeline "1024x768_70.00"  76.16  1024 1080 1192 1360  768 769 772 800  -HSync +Vsync

Yoa can find a modeline maker in my signature line to create your own.

---

