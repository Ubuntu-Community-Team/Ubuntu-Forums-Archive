---
title: "GRUB refuses to install"
date: 2006-11-19
forum: Absolute Beginner Talk
---

### Post by n3ldan on 2006-11-19
So I f*cked up my MBR, and nothing would boot.
Used an old live cd, grub-install /dev/hda, perfect.
It boots to "GRUB _"
I then realized I needed to tell it where stage1/2 are, so I booted the live cd again, found stage one and two (hd(0,1)), and tried to install.

```
install (hd0,1)/boot/grub/stage1 d (hd0) (hd0,1)/boot/grub/stage2 p (hd0,1)/boot/grub/menu.lst
```

I get ```
Error 28: Selected item cannot fit into memory

```

Theres aboput 400mb of ram available, what is the problem here?

Thanks.

---

### Post by bodhi.zazen on 2006-11-19
> **n3ldan said:**
> So I f*cked up my MBR, and nothing would boot.
Used an old live cd, grub-install /dev/hda, perfect.
It boots to "GRUB _"
I then realized I needed to tell it where stage1/2 are, so I booted the live cd again, found stage one and two (hd(0,1)), and tried to install.

```
install (hd0,1)/boot/grub/stage1 d (hd0) (hd0,1)/boot/grub/stage2 p (hd0,1)/boot/grub/menu.lst
```

I get ```
Error 28: Selected item cannot fit into memory

```

Theres aboput 400mb of ram available, what is the problem here?

Thanks.

To install GRUB to the MBR:

First boot the live CD

In a terminal type: ```
sudo grub
```

You will get a grub prompt

grub>>     GNU GRUB  version 0.97  (640K lower / 3072K upper memory)

 [ Minimal BASH-like line editing is supported.  For the first word, TAB
   lists possible command completions.  Anywhere else TAB lists the possible
   completions of a device/filename. ]

grub>

At the GRUB prompt type:```
root (hd0,1)
setup (hd0)
quit
```

Re-boot and you should be good to go....

---

### Post by n3ldan on 2006-11-19
Ah it feels good to be presented with a boot menu :D

What the hell does "grub-install /dev/hda" do then?

Either way, thanks a ton, I finally have a computer again :D

---

### Post by blasedeviant on 2006-11-29
I tried this, and it says it can't find nterm, and won't start, despite nano finding nterm just fine...

---

### Post by bulldog on 2006-11-29
> **blasedeviant said:**
> I tried this, and it says it can't find nterm, and won't start, despite nano finding nterm just fine...

What is nterm?
You can't copy the commands from some body else,your configuration can be different.
To install GRUB to the hard disk where Ubuntu is installed do the following.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```
This will return a location which you have to use in the next commands. 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Finally exit the grub shell
```
quit
```
Now Grub will be installed to the mbr.

If you have more hdd's and you want to install GRUB on another drive [not recommended] use the hdd number in setup.

---

### Post by jclmusic on 2006-11-30
> **bulldog said:**
> What is nterm?
You can't copy the commands from some body else,your configuration can be different.
To install GRUB to the hard disk where Ubuntu is installed do the following.
Boot into the live Ubuntu cd. 

When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a grub> prompt 
```
find /boot/grub/stage1
```


```

Error 15: File not found

```

what do i do? do i have to reinstall, or just reinstall grub?

---

### Post by bodhi.zazen on 2006-11-30
> **jclmusic said:**
> ```

Error 15: File not found

```
what do i do? do i have to reinstall, or just reinstall grub?

[Reinstall grub](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows#head-68342fc2e30d51fa0aa6f5bf16c911dd8d3663c6)

---

### Post by louieb on 2006-11-30
You may have a seperate boot partition. in that case:
```
find /boot/grub/stage1
```
will return file not found.
If you have a seperate boot partition then try:
```
find /grub/stage1
``` 
That should find the stage1 file. All other instructions remain the same.

---

### Post by shanepardue on 2006-12-01
I'm having the same problem. When I type "find /grub/stage1" it still says 
"error 15: file not found". One note, I'm using a SATA hard drive. For the 
above command, I also tried "root (sd0,1)" and that came back with 
"Error 23: Error while parsing number"

Please help!

---

### Post by shanepardue on 2006-12-01
I was going to fix the mbr from windows recovery, but it's saying there is no
 hard drive being detected. I know my hard drive is detected because I can 
mount it on a live CD and see all the files there. This is getting bad.

---

### Post by louieb on 2006-12-01
> **shanepardue said:**
> I was going to fix the mbr from windows recovery, but it's saying there is no
 hard drive being detected. I know my hard drive is detected because I can 
mount it on a live CD and see all the files there. This is getting bad.
How weird. 
Can you boot to the live CD and post the output from.
```
sudo fdisk -l
```

---

### Post by shanepardue on 2006-12-01
I was able to reinstall Ubuntu from an alternate install cd. No other option would 
work to reinstall grub.

---

