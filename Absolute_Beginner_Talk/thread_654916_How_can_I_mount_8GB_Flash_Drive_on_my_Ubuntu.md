---
title: "How can I mount 8GB Flash Drive on my Ubuntu?"
date: 2007-12-31
forum: Absolute Beginner Talk
---

### Post by JayLiao on 2007-12-31
I have a 8GB USB flash drive. I can not mount it on my Ubuntu 7.10. I also have 2 GB and 1GB USB flash drives. I don't have any problem for both of them. Could you please let me know why I can not mount this new 8 GB flash drive? 

Thank you very much!

Jay.

---

### Post by taurus on 2007-12-31
Are you talking about automount or by hand?  Can you at least try to mount it from a terminal?  What's the output of this command then?

```
sudo fdisk -l
```

---

### Post by dcstar on 2007-12-31
> **JayLiao said:**
> I have a 8GB USB flash drive. I can not mount it on my Ubuntu 7.10. I also have 2 GB and 1GB USB flash drives. I don't have any problem for both of them. Could you please let me know why I can not mount this new 8 GB flash drive? 

Thank you very much!

Jay.

Open a terminal and type this in after you plug in the drive:
```
dmesg
```
Then post the last 20 (or so) lines of output.

You can look at it after you plug in one of the working drives and see if you can spot any differences.

---

### Post by eternicode on 2007-12-31
> **dcstar said:**
> 
```
dmesg
```
Then post the last 20 (or so) lines of output.


:mad: make it easy on the poor guy!

```
dmesg | tail
```

That'll print the last ten lines.

```
dmesg | tail --lines=20
```

That'll print the last 20 lines.  Etc.

---

### Post by dcstar on 2007-12-31
> **eternicode said:**
> :mad: make it easy on the poor guy!

```
dmesg | tail
```

That'll print the last ten lines.

```
dmesg | tail --lines=20
```

That'll print the last 20 lines.  Etc.

So asking a beginner to type a few extra unnecessary items in the command saves him...... maybe 0.05 seconds of CPU than the simple command as the output scrolls past and leave the relevant information on the screen (24 lines on his screen versus 20, big deal.......)?

Does the phrase "sense of proportion" mean much to you?

---

### Post by the_darkside_986 on 2007-12-31
I think there is a bug in 7.10 with auto-mounting devices. Do your other devices automatically mount without any issues?

I had to go into GConf editor and remove the word "use..." something from registry key value "/system/storage/default_options/vfat/mount_options" and reboot. Then I could mount stuff without issues.

Sorry i can't remember the exact word to remove but I think it is last on the list and it starts with "use"

(I know I will be flamed for calling it a registry key, but come on, where else did gconf editor get its design from...)

---

### Post by mh1272 on 2008-04-15
The specific entry is "usefree".

---

