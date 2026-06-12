---
title: "Ubuntu can't be starting with VGA card."
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by thv on 2007-04-06
Hi everybody,
I used ubuntu 6.5. My copmuter was runed with graphic onboard card in mainboard. I seted  up and intalled good, didn't meet problem.

 After that, i replaced my graphic card by VGA nvidia MX 440 AGP 8x. But Ubuntu can't be starting now, it runed welcome screen and dump. i can't control my computer, had to restart computer, tried again but i met problem again. :(

i don't know what it is doing, you can't help me. Thank for you reading my thread.:) 

thv

---

### Post by zvacet on 2007-04-06
You changed graphic card,that what it is.
```
 sudo dpkg-reconfigure xserver-xorg
```
choose **nvidia** and if you still have troubles repet proces and instead of **nvidia** put **nv**  After that install Envy script

---

### Post by freebird54 on 2007-04-06
Just in case that wasn't detailed enough :)

On boot, choose the second option, to boot into recovery mode.

After logging at the recovery console: 

```
sudo dpkg-reconfigure xserver-xorg
```

Which will put you into a text mode interface to resetting your x server options (essentilly rebuilding your xorg.conf file). Most of what you see will be OK to leave either empty, or as default - except the bits about the driver, monitor and resolution settings. By the way - <tab> key to move around between items, <arrow> keys to move within an item, <space> to 'mark' or select items (such as resolution values) and <enter> to choose OK or confirm a choice.

As the previous post stated - try the nvidia driver first time.

When you get to the monitor setting, try to autodetect the monitor. Give it a name when asked. Choose 'MEDIUM' for setting it up. Choose the 'BEST' safe resolution that you know of (perhaps 1280x1024 @ 60 Hz refresh??). When you have the list of possible resolutions, use the space bar to toggle the 'mark' beside it as you wish - BEING SURE NOT TO MARK ANY UNSAFE (too high) RESOLUTIONS!

When you are done - WRITE DOWN the name it saved the backup under - in case you made things worse (unlikely). You will still need to add in the 'bolded' lines from before - this command rewrites the whole thing.  

```
sudo shutdown -r now
```

will reboot your machine to see how you did.

Hope that helps.

---

### Post by thv on 2007-04-06
Thank for you. :) 
When i used recovery mode, i met error which  is under.
```

....
[ Loading hardware driver]: 
....
[  78.503666] Call Trace:
[  78.503805] [<e01040cc>] apic_timer_interrupt+0x1e/0x30
[  78.503993] [<e0844b41>] inter_i830_configure+0xf1/0x110 [inter_agp]
[  78.504185] [<e08cb1e3>] agp_backend_initaialize+0x123/0x180 [agpgart]
[  78.504381] [<e08cb386>] agp_add_bridge+0x66/0x1a0 [agpgart]
[  78.504572] [<c01e6ffe>] _ _ pci_device_probe+0x3c/0x60
......

```
What's happen? :confused: I have used linux for 3 month. I don't much knowledge about linux. Can you help me? Thanks.:(

---

