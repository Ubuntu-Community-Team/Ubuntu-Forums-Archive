---
title: "Shutdown hangs"
date: 2006-11-12
forum: Absolute Beginner Talk
---

### Post by DapperMe17 on 2006-11-12
Dapper 6.06

During shutdown of Ubuntu, my system continues to experience hanging at precisely the same time at the Ubuntu shutdown screen.

Is there a relatively simply fix?

Thank you

---

### Post by an.echte.trilingue on 2006-11-13
What step of the shutdown does it hang on?

---

### Post by DapperMe17 on 2006-11-16
Thanks for the reply.

It hangs when reaching "Halt" during process shutdown (Ubuntu shutdown screen).

---

### Post by haxality on 2006-11-16
I am actually having the exact same problem on Dapper Drake. Any input here would be great.

---

### Post by Kross on 2006-11-16
This Is what worked for me....

Place this [COLOR="Red"]acpi=off[/COLOR] in your /boot/grub/menu.lst as so

-[COLOR="Green"]kernel	/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 rw [/COLOR][COLOR="Red"]acpi=off [/COLOR]

Then Place [COLOR="Red"]apm power_off=1[/COLOR] in your /ect/modules

Hope that helps..

If you are a noob like me you will have to open the editor using sudo then enter your password.

-[COLOR="Green"]sudo gedit /boot/grub/menu.lst[/COLOR]
-[COLOR="Green"]sudo gedit /ect/modules[/COLOR]

Or copy/paste from here to the Terminal

Let me know if this work for you...

-Kross

---

### Post by ThrobbingBrain66 on 2006-11-16
> **Kross said:**
> This Is what worked for me....

Place this [COLOR="Red"]acpi=off[/COLOR] in your /boot/grub/menu.lst as so

-[COLOR="Green"]kernel	/boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 rw [/COLOR][COLOR="Red"]acpi=off [/COLOR]

Then Place [COLOR="Red"]apm power_off=1[/COLOR] in your /ect/modules

Hope that helps..

If you are a noob like me you will have to open the editor using sudo then enter your password.
-[COLOR="Green"]sudo gedit /boot/grub/menu.lst[/COLOR]
-[COLOR="Green"]sudo gedit /ect/modules[/COLOR]

Or copy/paste from here to the Terminal

Let me know if this work for you...

-Kross

I'm glad this worked for you, but just as a warning to others who may try this, it made my box unable to boot to the desktop...it got as far as the startup sound and would freeze.  The solution would be to boot to recovery mode and use nano (sudo nano /path/to/file) to restore the defaults.  

Anyway, many people (especially laptop owners) are having this issue.  It seems to be an issue with the kernel (not Ubuntu) because another distro, either suse or mandriva, suffers from the same problem.

---

### Post by DapperMe17 on 2006-11-17
I'd like the shutdown to actually work like it's suppose to.

All versions Ubuntu & Simply Mepis share this same behavior, based on my experience.

Is there a stable hack/solution?

Thanks again

---

### Post by Kross on 2006-11-17
> **ThrobbingBrain66 said:**
> I'm glad this worked for you, but just as a warning to others who may try this, it made my box unable to boot to the desktop...it got as far as the startup sound and would freeze.  The solution would be to boot to recovery mode and use nano (sudo nano /path/to/file) to restore the defaults.  

Anyway, many people (especially laptop owners) are having this issue.  It seems to be an issue with the kernel (not Ubuntu) because another distro, either suse or mandriva, suffers from the same problem.

This is good to know, Thank you..

From what i understand,,,That which i have up,,Turns off ACPI and uses AMP to power off,,I look on the web tryed many combos of ACPI=off and AMP=off,,ect.. this worked for me,,I looked farther and I believe this may not be useful for laptops which may need ACPI for engry reasons..

I believe it should be tryed,,and now with you posting a fix it fails, the more so to try.

Thanks again.

I also hope that if it did work for other,,and not just me,, I like to know of this.

Thank You.
-Kross

---

### Post by Kross on 2006-11-17
> **DapperMe17 said:**
> I'd like the shutdown to actually work like it's suppose to.

All versions Ubuntu & Simply Mepis share this same behavior, based on my experience.

Is there a stable hack/solution?

Thanks again

I think this says it

"It seems to be an issue with the kernel (not Ubuntu) because another distro, either suse or mandriva, suffers from the same problem."

I think that the ACPI, (or New Power Controls) in the Kernel are in a way bugy,,the old way APM did not have as many options, 

If someone has more Information Please Post..

But you may want to try, Using an older Kernel. This MAY help..

Good Luck.
Please keep us INFO'ed

-Kross

---

### Post by budman21901 on 2006-11-24
Going through this now trying to get Edgy installed in my sister in laws DESKTOP computer as a dual boot.  She wants to try it out.  Its working great, but when i try the kernel trick posted here i get exactly what throbbingBrain66 gets.  Kernel panic error, and then boot into recovery, and change everything back.  Then it boots again, but wont shutdown.

I am relatively new to linux so i wrote some stuff down just in case it would help someone figure it out.


My var/log/kern.log  constantly updates this message, and never stops.  
[PHP]Nov 23 22:44:21 amanda-desktop syslogd 1.4.1#18ubuntu6: restart.
Nov 23 22:44:25 amanda-desktop kernel: [17179933.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:44:31 amanda-desktop kernel: [17179939.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:44:37 amanda-desktop kernel: [17179945.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:44:43 amanda-desktop kernel: [17179951.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:44:49 amanda-desktop kernel: [17179957.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:44:55 amanda-desktop kernel: [17179963.384000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:45:01 amanda-desktop kernel: [17179969.388000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:45:07 amanda-desktop kernel: [17179975.388000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:45:13 amanda-desktop kernel: [17179981.388000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:45:19 amanda-desktop kernel: [17179987.392000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
Nov 23 22:45:25 amanda-desktop kernel: [17179993.392000] ACPI: Unable to turn cooling device [dbfdddec] 'on'
[/PHP]

When changing to what this post says to do i get 
[PHP]Kernel Panic - not syncing kernel attempting kill[/PHP]

When in recovery mode where i see CL shutdown sequence i get this, but it just hangs there.  
[PHP][17179867.576000] Restarting System[/PHP]
 
Hell, i don't know if that can help anything, but it can't hurt i guess.  I am also searching for a fix, so if anyone finds one please post back.

---

### Post by DapperMe17 on 2006-12-01
What are the commands for the acpi fix...under Xubuntu(XFCE)??? 

Those two sudo commands didn't work for me.

Thanks

---

### Post by DapperMe17 on 2006-12-01
Anyone:-#

---

### Post by DapperMe17 on 2006-12-02
bump

---

### Post by dcmarsh on 2007-08-15
I tried the acpi fix on a sony vaio vgn-bx196vp, It killed ubuntu stone dead as throbbingbrain66 has said. 

fixed with the nano trick though.

Anyone out there with a fix as I have to dual boot with a certain other operating system that really doesn't like starting dirty.

---

### Post by dewcansam on 2008-01-29
> **ThrobbingBrain66 said:**
> I'm glad this worked for you, but just as a warning to others who may try this, it made my box unable to boot to the desktop...it got as far as the startup sound and would freeze. The solution would be to boot to recovery mode and use nano (sudo nano /path/to/file) to restore the defaults.

Anyway, many people (especially laptop owners) are having this issue. It seems to be an issue with the kernel (not Ubuntu) because another distro, either suse or mandriva, suffers from the same problem.
Kross was close, i just did the "apm power_off=1" line in my /etc/modules file and that seemed to do it with no problem. So try that 

```

$sudo vi /etc/modules
##....
apm power_off=1

```

---

