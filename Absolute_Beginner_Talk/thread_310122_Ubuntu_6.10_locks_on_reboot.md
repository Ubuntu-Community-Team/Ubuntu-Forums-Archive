---
title: "Ubuntu 6.10 locks on reboot"
date: 2006-11-30
forum: Absolute Beginner Talk
---

### Post by Island Hippie on 2006-11-30
Hi,

Newbie to linux.  I have a clean install from the Ubuntu edgy alternate cd.  If I click on shutdown the computer shuts down and turns off ok.  If I click on restart ererything shuts down and then it locks after [17179871.912000] Restarting system.:confused: 

I am using an Asus P4S800D-X motherboard with 1G memory. I used the  alternate cd because I set up a software raid1 and lvm. I plan on using the system as a router/server.

Is there some way I can find out what is locking the system?

Any suggestions?

Thanks.

---

### Post by rbprogrammer on 2006-11-30
i have the same problem sometimes.  i have a Dell Inspiron E1505 and sometimes on boot it just locks up.  Occasionally it will unfreeze after about 10 minutes or so.  But if i dont have the patients for that i just push and hold the power button and shut down.  i then just try to turn it back on, i close my eyes and hope for the best.

but i'm not sure why it locks up for me too.  if i remember correctly, mine says (if i boot in recovery mode) that it found a CPU lockup at block somenumber.  or something along those lines.

---

### Post by LLRNR on 2006-11-30
Hmmm not quite sure... 

**1)** I suppose you ran the option **Check CD for defects** before installing ... ?

Anyway, this could be caused by many things.

**2)** You could force a check of your system. So use this:
```
sudo tune2fs -c 1 /dev/hda1
```
assuming that *hda1* is your boot partition. The line above will force the fsck check at each (**1**) boot. Reboot and just let fsck do its job.

By default, fsck check is done every 30th boot. To re-enable this option, use
```
sudo tune2fs -c 30 /dev/hda1
```

The fsck check should locate possible errors on your filesystem and it will attempt to correct them automatically.

**3)** You could also see what happens if you try to reboot your machine from the CLI. You can use
```
sudo shutdown -rv now
```

The **-r** switch means reboot, the **-v** switch means verbose mode. (You can see other options with *shutdown --help*.)

I don't know what the problem is, but you might want to start by doing these things first. (At least this is what I'd do to try to isolate the problem.)

LLRNR

EDIT - @ Island Hippie: BTW, welcome to Ubuntu :)

---

### Post by Island Hippie on 2006-11-30
Thanks for the input.

The system shuts down its services and turns off the computer OK but it hangs on the reboot.  The machine will be used as a remote server so it is vital that it restarts without problems.

I've tried to do the tune2fs but I can't get it to work.  I have 2 SATA drives (sda & sdb md0) set up with a software raid1, then LVM (vg1). Can't find the right combo to get it to run.

The CLI shut down(restart) does the same thing as the gui restart: It closes down the services and says its restarting the system and then hangs.  A straight shut down closes services and then shuts off the computer.

I am sure that it is not a data coruption on the cd or the install.  I did the install twice to check. When the CD media check is run it validates the CD then hangs on the reboot.

Still stuck and puzzled. :-k

---

### Post by LLRNR on 2006-11-30
For SATA HDDs there's an '**s**' instead of '**h**', I forgot to mention. Also, see [this](http://doc.gwos.org/index.php/ChangeDiskCheckFrequency) for fsck.

Apart from that, I can't tell you anything else, I'm sorry, since I never faced this issue myself I have no idea where to "grab" the problem from.

LLRNR

---

### Post by Island Hippie on 2006-11-30
Thx for the link to fsck. I got it to work with sudo tune2fs -c 1 /dev/mapper/vg1-root.

It showed everything as OK so I'm still stuck.  :(

---

### Post by Mithrilhall on 2006-12-06
I'm having the same problem.





MB: Shuttle : Model SN95G5
Processor: AMD 64 Athlon 3500 (Socket 939)
Geforce 7600GS 512MB
RAM: 2GB
Hard drive: 2 x 250Gb SATA150 (16Mb Cache)

---

### Post by Xel on 2007-05-28
Hey,

I've had similar problems on my Asus P4S800D-X MB as well, I'm pretty sure its a motherboard problem. I've used SimpleMepis on this machine before switching to Ubuntu and it had the same problem (I switched particularly for this reason).

The problem also started after doing a full hardware upgrade, switched to the new Asus MB.

The machine is dual booting as well and Windows shutsdown properly so its something software and Linux specific -- it could either be the kernel or something else.

But its not a Ubuntu problem :D

Currently running Ubuntu 7.04 with the Asus P4S800D-X MB, 512Mb Ram, Nvidia GeForce 5200, 2 P-IDE HDD.

---

