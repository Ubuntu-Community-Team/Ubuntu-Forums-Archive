---
title: "xserver auto config"
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by TxRxBuffer on 2007-03-25
I can't boot up to reach my login in screen. I'm not sure what I did wrong but I was trying to increase my screen resolution. I read something that said that I might be able to configure xserver  setting to do this. After configuring it and rebooting, I could no longer log on. 

So in recovery mode I tried

sudo gdm 

which said x server output fail.

then I tried 

init 2

which gave me the same result in the end.

Is there anything, I can do like set the  xserver to auto config or back to the default settings?

---

### Post by taurus on 2007-03-25
From the recovery mode, run

```
dpkg-reconfigure -phigh xserver-xorg
```
When done, you can reboot with

```
shutdown -r now
```

---

### Post by lamalex on 2007-03-25
boot to your regular kernel, hit control alt f1 to get to a terminal, log in, and follow these commands ```

cd /etc/X11/
ls

```
see if there is a backup of the file xorg.conf, if there is, try renaming it to xorg.conf (mv xorg.conf.bak xorg.conf)
```
startx
```
or
```
dpkg-reconfigure -phish xserver-xorg
```

that should take care of it

---

### Post by TxRxBuffer on 2007-03-26
Thanks for the help guys 
> 
From the recovery mode, run
Code:

dpkg-reconfigure -phigh xserver-xorg

When done, you can reboot with

Code:

shutdown -r now




I tried that but still it didn't let me boot, even though I set the screen resolution to 800x600.
> 
boot to your regular kernel, hit control alt f1 to get to a terminal, log in, and follow these commands
Code:

cd /etc/X11/
ls

see if there is a backup of the file xorg.conf, if there is, try renaming it to xorg.conf (mv xorg.conf.bak xorg.conf)
Code:

startx

or
Code:

dpkg-reconfigure -phish xserver-xorg

that should take care of it



When I booted normally and i hit ctrl+shift+F1, it did nothing. So i tried the steps in recovery mode.  The folder X11 wasn't there when I ran

```

cd etc/
ls

```

Then I tried

```

dpkg-reconfigure -phish xserver-xorg

```

I tried to configure it as best as I could, but no lucky. The results were the same.
Is there anything that I can to get it to boot up, like a fresh install with no graphics drivers installed and basic gnome setup? I really want to avoid re-installing.

---

### Post by cowlip on 2007-03-26
just a quick reaction from me, but  when you say, "The folder X11 wasn't there when I ran" , am I interpreting it correctly that you don't have an X11 folder under /etc at all?

---

### Post by TxRxBuffer on 2007-03-26
um..well it wasn't listed but that's where the folder should be. I didn't use a SUDO command though. Should I retry it with the command SUDO before ls?

---

