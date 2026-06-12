---
title: "Booting and Shutdown issues"
date: 2008-04-17
forum: Absolute Beginner Talk
---

### Post by dover19 on 2008-04-17
Ok, I'm completely new at Linux and I'm having issues with booting up and shutting down. I installed Xubuntu on an old P2 Toshiba Tecra 8000 laptop.

**Whenever I boot up, after I log in I get an error message saying:**

"Could not look up internet address for (none). This will prevent Xfce from operating correctly. It may be possible to correct the problem by adding (none) to the file /etc/hosts on your system."

I was able to find that file in that file, the first line is empty and the second line says:
"# The following lines are desirable for IPv6 capable hosts"

So where would you say I'm supposed to add "(none)"? On the first line before that message, on the third line after that message, or do I just remove that message and type in "(none)"?

Ok, now when I shut down, my laptop actually never shuts down. I gets to a black screen as if it's shutting down where I see text like:

[FONT="Fixedsys"]* Starting deferred execution scheduler atd                                   [ OK ]

* Starting periodic command scheduler crond                                  [ OK ]

* Checking battery state...[/FONT]

Etc.

But then the last two lines say:

[FONT="Fixedsys"]NetworkManager: <WARN> nm_hal_deinit(): libhal shutdown failed - Connection is closed

[ 1953.119839] System halted.[/FONT]

Any ideas of what I need to do?

Thanks!

---

### Post by plucky on 2008-04-17
This is what me etc/hosts on Xubuntu contains ```
127.0.0.1 localhost
127.0.1.1 Xubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


As for your power down problem (I am not sure if this will work on a laptop,but it did on a desktop).

Open a terminal and input this line to edit the file in /etc/modules
```
sudo nano /etc/modules
```
and add the line ```
apm power_off=1
``` at the end of the file.
Save file and exit using Ctrl-O and Ctrl-X.

See if that works.

Good Luck

---

### Post by dover19 on 2008-04-17
> **plucky said:**
> As for your power down problem (I am not sure if this will work on a laptop,but it did on a desktop).

Open a terminal and input this line to edit the file in /etc/modules
```
sudo nano /etc/modules
```
and add the line ```
apm power_off=1
``` at the end of the file.
Save file and exit using Ctrl-O and Ctrl-X.


I can add that line anywhere, or does it go somewhere specific?

What it says in that file right now is:

[I]# /etc/modules: kernel modules to load at boot times.
#
#This file contains the names of kernel modules that should be loaded
#at boot time, one per line. Lines beginning with "#" are ignored/

loop
lp
fuse[/I]

Well, at leased now I know that whenever there's a # it's just for remarks, it doesn't affect any operations, that's ont thing I've learned...lol.

So as I was saying, does it matter whether I put that code in before loop, or after fuse or whatever?

Thanks

---

### Post by spiderbatdad on 2008-04-17
could you run ```
dmesg
```in a terminal, copy and paste the output into a text file, then right click on the text file, and select archive? Upload that archive here using the manage attachment tools below the reply window

---

### Post by dover19 on 2008-04-17
> **spiderbatdad said:**
> could you run ```
dmesg
```in a terminal, copy and paste the output into a text file, then right click on the text file, and select archive? Upload that archive here using the manage attachment tools below the reply window

I'm actually on the forums using a Windows PC. I'm at work and I'm not sure I can actually get my laptop on the network and access the internet with it.

Maybe I could use a flash drive to transfer the file to my Windows machine and then upload it...lol

Lot's of fun learning a new OS :)

---

### Post by spiderbatdad on 2008-04-17
Ok. best of luck. I've answered several thread this morning regarding boot parameters, and I think your issue is similar. Usually hardware detection problems cause the symptoms you've described.
After booting, if you run dmesg in a terminal, you will get a run down of the boot process. It may also offer suggestions for fixing hardware detection issues...like "try using lapic." If you get such a message, someone can describe to you how to fix the problem. It is fairly simple.

---

### Post by dover19 on 2008-04-17
Ok, I was able to get the file here using my Flash Drive lol.

Just out of curiosity, why did you want me to zip it instead of just uploading the text file?

---

### Post by spiderbatdad on 2008-04-17
> **dover19 said:**
> Ok, I was able to get the file here using my Flash Drive lol.

Just out of curiosity, why did you want me to zip it instead of just uploading the text file?

Because it's a lot of output, and many people prefer not to see so much text in the thread...as it can be distracting. Using the code tags above (#) can help with that too.

Anyway...this is significant:
```
ACPI: **no DMI BIOS year, acpi=force is required to enable ACPI**
[    0.000000] ACPI: Disabling ACPI support
[    0.000000] Allocating PCI resources starting at 20000000 (gap: 10100000:efe80000)
[    0.000000] Built 1 zonelists.  Total pages: 16241
[    0.000000] Kernel command line: root=UUID=e6d09c3f-f895-40cf-9ed5-b25dbee773c5 ro quiet
[    0.000000] **Local APIC disabled by BIOS -- you can enable it with "licap"**
```

You are going to have to edit the file named /boot/grub/menu.lst (Lst as in list.)
There are several ways...this is a GUI method, but requires one CLI command. Open the terminal and enter ```
gksu nautilus
```Input password, and navigate to File System>>boot>>grub>>menu.lst.  Scroll way down to the section beginning with #####END DEFAULT OPTIONS####

Just below that is your default boot kernel. On the line that begins with kernel...edit the end of the line by deleting "quiet splash" and replacing with "acpi=force lapic"
Save the file, and reboot. I have not tried those two commands in combination...I don't think there will be an issue. 

Here is an example of mine where I have added lapic pci=routeirq.
```
## ## End Default Options ##

title		Ubuntu 8.04, kernel 2.6.24-16-generic
root		(hd0,0)
**kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq**
initrd		/boot/initrd.img-2.6.24-16-generic
quiet
savedefault

title		Ubuntu 8.04, kernel 2.6.24-16-generic (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.24-16-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro single
initrd		/boot/initrd.img-2.6.24-16-generic

title		Ubuntu 8.04, kernel 2.6.22-14-generic
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=604f2b74-7f64-424f-a8bf-1160a71d9ea3 ro lapic pci=routeirq
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
savedefault
```

After you're up and running, you will probably need to run ```
sudo dpkg-reconfigure xserver-xorg
``` to get other hardware tuned up.

---

### Post by dover19 on 2008-04-17
I'm running Xubuntu, and  I  think "gksu nautilus" might not work in Xubuntu because it didn't seam to load any type of GUI or anything.

Anyway, I typed this in the terminal instead:
[FONT="Fixedsys"]sudo nano /boot/grub/menu.lst[/FONT]

I scrolled down to the section you tld me to go to, but I don't see anything that says "quiet splash" so I'm not sure what to do. I don't think I should be copy pasting exactly what you're file says (lapic pci=routeirq).

So I uploaded a text file (since it's not a lot of text this time lol) of that section of my "menu.lst" file.

Thanks again for all the help.

---

### Post by spiderbatdad on 2008-04-17
That is a little strange..especially since dmesg shows 'ro quiet splash' in the kernel line...no worries though...just add at the end of the kernel line (beginning with a space) "ro acpi=force lapic" without quotes. Ctrl-o to save and enter to confirm the filename, and ctrl-x to exit...reboot.

Not sure why you have a $ sign there either...you have installed the system right...not running on cd?

---

### Post by dover19 on 2008-04-17
lol, yeah, it's installed, I couldn't run it on a CD, not on this system...

anyway, I did the changes and it seams to be working fine now, it just takes longer to boot up and actually runs slower than it was before (it was already pretty slow, I only have 64 mb of ram, waiting for 256 mb to arrive by mail).

Does that make any sense?

---

### Post by spiderbatdad on 2008-04-17
More ram will definitely help. I am no expert on boot parameters, as you have probably guessed. Those parameters may not be ideal for your machine. I was making a guess based on dmesg.
My friend runs xubuntu on an older rig like that with the parameters: noapic nolapic vga=791
Those parameters might suit your machine better. You can try a one time boot like that from the grub menu...press esc before boot begins if you grub menu is hidden. Press 'e' to edit, then use the arrow key to move to the kernel line and press 'e' again. delete the end of the line and input noapic nolapic vga=791  Then press enter and 'b' to boot. That may significantly increase your performance. If it does, edit /menu.lst accordingly.
Once things are booting correctly, you can follow the above procedure and make a "profile" of the boot process, to shave a few more seconds off boot time, by appending the existing kernel line with 'profile' from the the grub menu. That one time profile will take slightly longer to boot, but after that, it will shorten the boot time.
Regards.

---

### Post by dover19 on 2008-04-17
Cool, thanks for all the help!

---

### Post by oboedad55 on 2008-04-17
> **plucky said:**
> This is what me etc/hosts on Xubuntu contains ```
127.0.0.1 localhost
127.0.1.1 Xubuntu

# The following lines are desirable for IPv6 capable hosts
::1 ip6-localhost ip6-loopback
fe00::0 ip6-localnet
ff00::0 ip6-mcastprefix
ff02::1 ip6-allnodes
ff02::2 ip6-allrouters
ff02::3 ip6-allhosts
```


As for your power down problem (I am not sure if this will work on a laptop,but it did on a desktop).

Open a terminal and input this line to edit the file in /etc/modules
```
sudo nano /etc/modules
```
and add the line ```
apm power_off=1
``` at the end of the file.
Save file and exit using Ctrl-O and Ctrl-X.

See if that works.

Good Luck

I'm having a similar issue. When I want to reboot, log out, shutdown, after I click on the icon and make my choice the system then hangs on the desktop, cntrl-alt-backspace then clears the desktop. Would your fix take care of my issue as well?

Thanks!

---

### Post by plucky on 2008-04-17
> Would your fix take care of my issue as well?

No, I don't think so.This fix is for the system not powering off after it has already gone through the shutdown routine and leaving the Xubuntu logo on the screen,but not powering off.

Your problem sounds more like a Gnome or Compiz desktop problem.
Have you tried to shutdown from a terminal window?
```
sudo shutdown -h now
``` to see what happens.

Good Luck

---

### Post by oboedad55 on 2008-04-17
> **plucky said:**
> No, I don't think so.This fix is for the system not powering off after it has already gone through the shutdown routine and leaving the Xubuntu logo on the screen,but not powering off.

Your problem sounds more like a Gnome or Compiz desktop problem.
Have you tried to shutdown from a terminal window?
```
sudo shutdown -h now
``` to see what happens.

Good Luck

I'll give that a try next  time. I think it's a Compiz issue. I believe it started after I set all the desktop goodies up. Do you have any idea where to start looking for the issue?

Thanks,
oboedad55

---

