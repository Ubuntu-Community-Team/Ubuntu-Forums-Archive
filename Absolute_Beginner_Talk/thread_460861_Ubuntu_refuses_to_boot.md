---
title: "Ubuntu refuses to boot"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by Continental on 2007-06-01
I've got Ubuntu installed on an HP dv9008nr. However, it won't boot. I get past the loading screen, and get a black screen. I get the blinking underscore thing sometimes and I've tried ctrl-alt-f1, which still gets me a black screen after some text. I tried adding noapic to the end of the Ubuntu boot command, and it didn't seem to do anything. Any ideas?

---

### Post by arochester on 2007-06-01
> gets me a black screen after some text

What does that text say?

---

### Post by Continental on 2007-06-01
I can't tell... it's only there a second or less. I thought I saw the word "starting", though.

---

### Post by Aquakidd13 on 2007-06-01
Does it give something along the range of this? kernel panic not syncing VFS unable to mount root fs on unknown block

If so, try installing with the root filesystem of reiserfs and not EXT3 if you used EXT3, I had the problem

---

### Post by Continental on 2007-06-01
Thanks... I'll try again and see what exactly it says.

---

### Post by Continental on 2007-06-02
Ok, here's the message that flashes before the screen goes black. I may have gotten a few digits wrong, though.

Starting up ...
[0.056794] PCI:BIOS Bug #01[149435000] found
Loading, please wait ...
exsplash: setting mode 1152 x 864 failed
exsplash: using mode 1024 x 768
hlmit: name_to_dev_t(/dev/mda5) {a small white box here} mda5(8,5)
hlmit: trying to resume from /dev/mda5
hlmit: no resume image, doing normal boot ...

ubuntu 7.04 ubuntu tty1

Ubuntu login:

The screen goes black. This is all there for a second at most. Can anyone make heads or tails of this? The sooner I'm off of Windows, the better. Thanks.

---

### Post by blackened on 2007-06-03
I remember reading about a problem with hibernation that gave a similar error message. You might try editing your /boot/grub/menu.lst and adding noresume to the end of the #defoptions line a la:

```
# defoptions=quiet splash noresume
```

I'm just grasping at straws though, this might not be it.

---

### Post by Continental on 2007-06-03
I'll give it a try. How do I do that?

---

### Post by blackened on 2007-06-03
You should be able to get to the grub menu by pressing ESC when you see the "Starting Up..." message. Might have to hit it repeatedly just to get it. Once there, go to recovery mode. From there you would 

```
nano /boot/grub/menu.lst
```

Find and replace the line that I put in the last post. To save in nano press ctrl+x, enter, enter.

---

### Post by Continental on 2007-06-03
Ok, so I tried going into recovery mode and doing the editing and saving, and I think I did it right. But then I rebooted and tried Ubuntu again and it still didn't work. So I tried going back into recovery mode and got the following message:

/dev/sda2 has been mounted 28 times without being checked, check forced
/dev/sda:

I'm stuck.

---

### Post by blackened on 2007-06-03
So it's not letting you into the recovery console now either?

---

### Post by jonward0690 on 2007-06-03
> **Continental said:**
> Ok, so I tried going into recovery mode and doing the editing and saving, and I think I did it right. But then I rebooted and tried Ubuntu again and it still didn't work. So I tried going back into recovery mode and got the following message:

/dev/sda2 has been mounted 28 times without being checked, check forced
/dev/sda:

I'm stuck.

So it is not checking the file system.Every 30 boots or so Ubuntu is suposed to check your filesystem to make shure it has not gotton dirty.

---

### Post by blackened on 2007-06-03
If it will let you into neither a normal boot, nor the recovery console, then there's not much else to do but reinstall. You could try running a live CD and mount your drive from there to fix things, but I'm not exactly sure where to go from here. It seems like the noresume option started to fix the problem, but for some reason the drive check borked things up.

---

### Post by Continental on 2007-06-04
Hopefully. Can I reinstall without repartitioning? I've never been able to live boot from the CD, so I've never actually made it to the desktop.

---

### Post by blackened on 2007-06-04
Try the alternate install CD, I too have problems with the live CDs. You shouldn't have to repartition, just let it format your existing ext3 partition and install it there.

---

### Post by pappapump on 2007-06-04
I just googled this model of PC and found that most of the linux problems stem from the fact that its a MCE based laptop with special button funtions.
Try this, go to bios options and set everything to safe or compatibility mode.
Disable any special integrated hardware setups and also disable the battery alarm and system monitor.
Then try the install. 
After a sucessful install, enable one item at a time till your system hangs and you'll most likely find the cause of the stuck install.

---

### Post by Continental on 2007-06-04
Thanks for the help. I'll give both suggestions a try and report back. I appreciate the assistance.:)

---

### Post by Continental on 2007-06-06
Well, I reinstalled and it worked. Now I just have to get the wireless configured. Thanks for the help, everyone... refreshing to see people on forums willing to help.

---

