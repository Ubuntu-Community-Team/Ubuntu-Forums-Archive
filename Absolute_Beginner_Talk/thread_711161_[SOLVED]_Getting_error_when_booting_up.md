---
title: "[SOLVED] Getting error when booting up"
date: 2008-02-29
forum: Absolute Beginner Talk
---

### Post by noobuntu7 on 2008-02-29
Hello,
I have been very interested in Linux for a long time, so last night I decided to burn a live CD of Xubuntu 7.10 (Gutsy Gibbon). I downloaded and burned the alternate CD because I was installing Xubuntu on a very old computer that had only 64MB of RAM. It failed to install the first to times I attempted, but as they say, the third time is the charm. It installed without a problem and then restarted the machine and it booted into Xubuntu just great, worked fine. I looked around to see what was what, and I launched firefox and it worked great (you probably won't believe this. But once I installed Linux on this old 1999 computer with only 64MB of RAM, it worked just as well with my high-speed internet as my brand new computer with 1.5GB of ram).

So I was all excited and I went to the Update Manager and it said that there were 110 Updates available, so I clicked "Download all available updates" and it took a while, but it completed installing them and told me to restart the computer. I did... and now I have ran into trouble. 

When I boot the computer, it goes to the Gateway start-up screen as usual. Then it goes into what I think is the BIOS (correct me if I'm wrong)... it's code written in white letters on a black screen and it says:
[B]
```
Starting up ...
[	0.000000] ACPI: BIOS age (1999) fails  cutoff (2000), acpi=force is required to 
enable ACPI
[	24.4306921] PCI: Failed to allocate mem resource #6: 10000@f8000000 for 0000:0
1:00.0
[	25.113617] Kernel panic - not syncing: UPS: Unable to mount root fs on unkno
wn-block (0,0)
```[/B]


It won't go past that and I don't know what to do... should I boot from the CD and go into recovery mode? Please help me out as this is my first Linux experiment and so far it is not going to well :(. Thank you.

---

### Post by philinux on 2008-02-29
When it boots and you see grub stage 1.5 hit the ESC key and wait.

When the boot menu appears select the first line and press E to edit the line.

Add

acpi=force

to the end then press the B key to boot. See If this works then post back.

---

### Post by noobuntu7 on 2008-02-29
Hello,
I tried what you said to do but I'm not sure i understand...

I hit Esc when it loaded the Grub stage 1.5 and it brought me to a screen that says:

```
Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+
```

If I select the first one and click 'e' then it brings me to a window that says:

```
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d3dd61b4-3afd-47d8->
initrd /boot/initrd.img-2.6.22-14-generic
quiet
```

If I go to root (hd0,0) it brings me to a window that says:

```
[Minimal BASH-like line editing is supported. For
the first word, TAB lists possible command 
completions. Anywhere else TAB lists the possible 
completions of a device/filename. ESC at any time
exists. ]

grub edit> root (hd0,0)
```

If I type in "acpi=force" and hit Enter it brings me back to the screen that lists root, except now the root line looks like 
```
root (hd0,0) acpi=force
```

If I hit b to boot it gives me the exact same message it gave me in the beginning. Is there anything else I can do?

---

### Post by neurostu on 2008-02-29
you need to add acpi=force to this line:
```

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d3dd61b4-3afd-47d8->

```

so it should look like this

```

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=d3dd61b4-3afd-47d8-> acpi=force

```

---

### Post by dstew on 2008-02-29
No, add that to the kernel line, not the root line.

---

### Post by noobuntu7 on 2008-02-29
Hello,
Thank you for telling me to add the acpi=force to the kernel instead of the root. Unfortunately, even after I add the acpi=force line to the kernel and then boot, it still gives me the same message. Is there anything else I can do?

P.S. - I don't have any important information on this system, is it possible to just boot from the live CD I installed it with and then go to the "Recover a broken system" option? Or would that be harder than something else...

---

### Post by dstew on 2008-02-29
Try the opposite, that is, disable acpi with **acpi=off**

---

### Post by noobuntu7 on 2008-02-29
I tried using apci=off and it gives me the following error message now:

```
Starting up ...
[    54.8498221] PCI: Failed to allocate mem resource #6:10000@f8000000 for 0000:0
1:00.0
[    55.528766] Kernel panic - not syncing: VFS: Unable to mount root fs on unko
wn-block(0,0)
```

I think what I might do is use the Live CD and do recover broken system. If you have any more suggestions though, I'm glad to try.

---

### Post by neurostu on 2008-02-29
honestly using the live cd to reinstall the OS will take less time then you have spent tinkering around with your system... I would recommend trying the recovery option!

---

### Post by MONODA on 2008-02-29
did you remove apci=on from the root?

---

### Post by noobuntu7 on 2008-02-29
Everyone, I've tried to reinstall Xubuntu about 4 times since I reported this error and *every* time I get the same errors. Either I get this one when installing the base system:

```
[!!] Install the base system

Unable to install the selected kernel into the target system.

Kernel Package: 'Linux-generic'.

Check /var/log/syslog or see virtual console 4 for details.
```

OR... I am lucky enough to get past that step without an error message and I get all the way to about 73% of the way through the **Install Software** step and then it stops and gives me another error message that says that the **Install Software** step failed and I can either re-try the step from the menu or skip the step altogether and go on to the next step.

I am very tired of this, I am having serious doubts of how mature of an operating system Xubuntu really is... I've never seen another operating system give anywhere near *so* many errors when installing like Xubuntu. I don't know if it's my system, or it's the CD, or whether it's just my luck. I now have no working operating system on the computer (it deleted Windows). If you can offer any tried-and-true suggestions I would be *much* obliged. Thank you all.

---

### Post by dstew on 2008-02-29
What is the error message? Do ctrl-alt-F4 for virtual console 4. Also, are you installing Xubuntu Desktop or only the base system (sometimes called server)? Is it really a Live CD? I am surprised that will work with 64 Mb RAM.

---

### Post by noobuntu7 on 2008-03-01
Hey everyone! :)
I finally got it to work! I re-installed Xubuntu (it worked after about 5 more tries and a couple hours of work). It doesn't seem as fast now though as it was the first time... maybe it's just my imagination. Anyway, thanks for your suggestions. I am a bit afraid to try to install new updates though... is there a way to *only* install security updates (and not software updates)? That would be great... Anyway, I had one or two more questions, but I'll post them on a new thread.

---

