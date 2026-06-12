---
title: "Installation problems-  pnp related"
date: 2006-11-23
forum: Absolute Beginner Talk
---

### Post by akasixcon on 2006-11-23
[ 145.775368] PNPBIOS Fault.. attempting recovery.
[ 145.775484] PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attemtping to continue
[ 145.775551] PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
[ 145.775617] PnPBIOS: Check with your vendor for an updated BIOS
[ 145.775681] PnPBIOS: set_dev_node: unexpected status 0x37
[ 145.775744] pnp: Failed to activate device 00:16.
[ 145.775814] MPU- 401 evice not found or device busy 

                                                                                   [ ok ]

I'm getting these errors during the installation of Linux from the bootable CD. Using windows xp and pentium 3. Any other information needed please let me know. I need a resolution to this problem.

---

### Post by taurus on 2006-11-23
Did you pass along that option "pnpbios=off" when you tried to boot from the LiveCD?

---

### Post by akasixcon on 2006-11-23
No I did not see any options like that before I installed the Live CD>

---

### Post by taurus on 2006-11-23
When you first turn on the computer with the LiveCD in the drive, you can pass a parameter at the prompt when you see the options to choose!

---

### Post by akasixcon on 2006-11-23
I have spent an hour trying to fix Ubuntu on my computer. I'll take a break for today. Can you be more descriptive on this option, as in under which menu will it appear?

---

### Post by taurus on 2006-11-23
When you first boot up before you hit enter to install/run Ubuntu from the CD, you would see a prompt with

boot:

---

### Post by Derek Tomes on 2006-11-23
I googled your error and got a couple of hits:

[http://lkml.org/lkml/2001/10/7/124](http://lkml.org/lkml/2001/10/7/124)

```

 	/* If we got here and this is set the pnp bios faulted on us.. */
 	if(pnp_bios_is_utter_crap)
 	{
-		printk(KERN_ERR "*** Warning: your PnP BIOS caused a fatal error. Attempting to continue\n");
-		printk(KERN_ERR "*** You may need to reboot with the \"nobiospnp\" option to operate stably\n");
-		printk(KERN_ERR "*** Check with your vendor for an updated BIOS\n");
+		printk(KERN_ERR "PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue.\n");
+		printk(KERN_ERR "PnPBIOS: You may need to reboot with the \"nobiospnp\" option to operate stably.\n");
+		printk(KERN_ERR "PnPBIOS: Check with your vendor for an updated BIOS\n");
 	}

```

In technical terms, I believe your BIOS is "utter crap" :D :D :D :D

---

### Post by akasixcon on 2006-11-23
How do I install that?

---

### Post by akasixcon on 2006-11-24
bump

---

### Post by akasixcon on 2006-11-25
bump

---

### Post by akasixcon on 2006-11-28
bump

---

### Post by doobit on 2006-11-28
When you boot the live CD, there comes up a menu with options on what to do next. You are receiving an error that tells you to turn the plug and play option off. You can do that by choosing the boot options screen when you get to that first menu after you boot and adding the command pnpbios=off to the end of the line. 
If you have already installed, then you can add that command in the grub menu.lst on the line for the kernel you boot with.

---

