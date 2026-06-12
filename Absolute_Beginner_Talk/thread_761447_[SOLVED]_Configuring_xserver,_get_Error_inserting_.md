---
title: "[SOLVED] Configuring xserver, get Error inserting battery"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by hums07 on 2008-04-21
I have an old desktop Pentium II 350 MHz RAM 256 MB.
I have tried dapper minimal install and add IceWM as desktop manager. It was all ok (except for the sound) and I got correct resolution 1024x768.
I am trying Hardy at the moment using the same approach but I only get low resolution 800x600. When I do "sudo dpkg-reconfigure xserver-xorg", after several screen I get this message
```
FATAL: Error inserting battery (/lib/modules/2.6.24-16-server/kernel/drivers/acpi/battery.ko): No such device

```
Can somebody hint me for a solution or work around please?

---

### Post by bwallum on 2008-04-21
Hmm, very strange! Try:```
sudo apt-get dist-upgrade
```
Then```
sudo apt-get install update
```
Then```
sudo apt-get autoremove
```

---

### Post by Diabolis on 2008-04-21
wow man, probably you should go to hardy development forums. I tried to google the error and the only result that I get is this same post. Just like if this was the first time ever that this error appears.

So seems like hardy thinks that your pc is a laptop, you could remove all the laptop related packages and see if that fixes it.

---

### Post by bwallum on 2008-04-21
oops...should be```
sudo apt-get update
```

---

### Post by Diabolis on 2008-04-21
I found a thread that might be of your interest, specially post number 6.

[http://ubuntuforums.org/showthread.php?t=257661&highlight=remove+laptop+related+packages](http://ubuntuforums.org/showthread.php?t=257661&highlight=remove+laptop+related+packages)

---

### Post by hums07 on 2008-04-21
@bwallum
I have tried that. But I have no luck, still get the same error. Probably I should wait till the final release before retrying. Thanks for the suggestions.

@Diabolis
I have searched Google before posting this. Thank you for the link. It's enlightening. I will try again with Hardy final, just 4 days to go. If the problem persists, I will shout again here.

---

### Post by ryanhaigh on 2008-04-21
I don't know why it is trying to insert the battery module after you reconfigure x but to stop it trying you could put it in the blacklist.
```

sudo nano /etc/modprobe.d/blacklist

```
Then add the following line
```

blacklist battery

```

---

### Post by hums07 on 2008-04-21
Thank you ryanhaigh. I'll try.

---

### Post by hums07 on 2008-04-21
I have put the line in the blacklist but unfortunately, the problem persists.
So so weird... .

---

### Post by hums07 on 2008-04-23
To day I installed Gutsy minimalist on the same computer and installed IceWM as window manager. Unfortunately, I face the same problem. When running "sudo dpkg-reconfigure xserver-xorg", I get the same error even though I have edit /etc/modprobe.d/blacklist and add the line "blacklist battery". So it still tries to insert battery although battery is in blacklist.

I also have tried to put kernel option acpi=off (because battery is its member) but it does not make change.

Any hint to solution is very appreciated. Thank you.

Hums.

---

### Post by Diabolis on 2008-04-23
Removing the driver wouldn't have the same effect as black listing it?
Have you tried this:
```
sudo apt-get remove acpi
```

---

### Post by cato58 on 2008-04-23
> **Diabolis said:**
> Removing the driver wouldn't have the same effect as black listing it?
Have you tried this:
```
sudo apt-get remove acpi
```


Thanks!  This worked for me.

---

### Post by riskbreaker927 on 2008-04-24
I have this problem, but the workaround posted did not fix it.

---

### Post by Diabolis on 2008-04-24
Do you mean blacklisting it didn't work? Try removing acpi, if you are on a desktop you won't need it.

---

### Post by hums07 on 2008-04-26
> **Diabolis said:**
> Removing the driver wouldn't have the same effect as black listing it?
Have you tried this:
```
sudo apt-get remove acpi
```

I've just tried this. It says that acpi was not installed. The error persists. It is from kernel driver as it says... .

Thank you for the suggestion tho'.

BTW, I have put the option acpi=off noapic at menu.lst. It should've turned off the driver, shouldn't it?

---

### Post by Diabolis on 2008-04-26
> **hums07 said:**
> 
BTW, I have put the option acpi=off noapic at menu.lst. It should've turned off the driver, shouldn't it?

Yeah, if you placed it in the kernel line.

This error is not harmful and it could be hard to fix if you don't feel comfortable using the terminal and modifying system files. Also be aware that something could go wrong and you could break something else.

According to [this thread]("http://forums.whirlpool.net.au/forum-replies-archive.cfm/522904.html") the problem is caused by some scripts that are trying to load acpi. Since you don't need them, you can remove them and then update your initramfs file.

> -> install initramfs-tools
-> modify the scripts to your hearts content in /usr/share/initramfs-tools
-> execute update-initramfs -c -k 2.6.12-10-386 to build a new image

According to that thread you should have a script called acpi here:
```
cd /usr/share/initramfs-tools/scripts/init-premount/
ls
```

If you have it, you can remove it with this command:
```
sudo remove /usr/share/initramfs-tools/scripts/init-premount/acpi
```

---

### Post by hums07 on 2008-04-26
I dont find **acpi** script in the directory /usr/share/initramfs-tools/scripts/init-premount/
only **udev** and **ps3**

---

### Post by Diabolis on 2008-04-26
If you are using an acer:
> I did acpi=off noacpi (you need both)...

In the last post the output of this command:
**zcat /boot/*initrd.img-2.6.12-10-386* |cpio --list |grep acpi**
gave as part of the output this line:
**scripts/init-premount/acpid**

I executed the same command in my machine, and this is what I got:
```
zcat initrd.img-2.6.22-14-generic |cpio --list |grep acpi
lib/modules/2.6.22-14-generic/kernel/drivers/acpi
lib/modules/2.6.22-14-generic/kernel/drivers/acpi/processor.ko
lib/modules/2.6.22-14-generic/kernel/drivers/acpi/thermal.ko
lib/modules/2.6.22-14-generic/kernel/drivers/acpi/fan.ko
33316 blocks
etc/modprobe.d/thinkpad_acpi.modprobe
etc/modprobe.d/ibm_acpi.modprobe
etc/modprobe.d/toshiba_acpi.modprobe

```
As you can see the output now has 3 different files. It makes sense, the thread I linked to is from 2006 and ubuntu has gone through many changes since then.

The contents of the files are this:
```
$ cat /etc/modprobe.d/thinkpad_acpi.modprobe 
options thinkpad_acpi hotkey=enable,0xffff8f experimental=1

$ cat /etc/modprobe.d/ibm_acpi.modprobe 
options ibm_acpi hotkey=enable,0xff9f experimental=1

$ cat /etc/modprobe.d/toshiba_acpi.modprobe 
options toshiba_acpi hotkeys_over_acpi=1
```

Probably 1 means on, I assume that because I am using a laptop. You could try to change those values to 0 or just remove the files.

---

### Post by ehutch on 2008-05-07
I have been trying to install a minimal server install of 8.04 Husky to an ancient Dell Inspiron 7000 PII 256M RAM and a BIOS so old that acpi complains that it has no date in a "force" statement at boot up.

The login shell $ seems to work fine but I get the same errors as those above. 

I tried the solutions above and ended with editing the blacklist and now when I ran 
sudo dpkg-reconfigure -phigh xserver=xorg 
I got ...
xserver-xorg postinst warning: overwriting possibly customized configuration file; backup in /etc/X11/xorg.conf.20080507120128
FATAL: Error inserting battery (/lib/modules/2.6.24-16-server/kernel/driver/acpi/battery.ko): No such device

Has anybody solved this problem?  Any ideas?

---

### Post by brainstuff on 2008-05-08
Yep this is exactly the same symptoms that I've had - (incidentally P3 450mhz on an old Jetway board with Award BIOS from 1999) - it was causing massive problems getting video working. In the end the thing that fixed it for me was going into the BIOS setup and loading all the defaults.

I'm still getting the error message, but something that got reset in the BIOS must have allowed Ubuntu + Xubuntu 8.04 to see the video card and install (using the open source drivers for the Radeon 9200) - sadly though the big beige box is for my kids - plugged into an analog TV via S-Video - and I couldn't get this TV-Out working as the only output - so the box has gone back to being XP :(

The plus-side though is that it has spurred me to get a nice little mini-itx system which *fingers crossed* will play nicely with 'buntu :) Hopefully arriving today....

My advice is try the BIOS reset (my old PCs tend to get their settings jumbled over the years as I try out tweaks, then promptly forget to undo them) ....or maybe try finding a BIOS update for the board if at all possible. I suppose you could try different video cards if you have any lying around, or if the worst comes to the worst try getting a cheap mobo+processor bundle off ebay? Not ideal I know....Good luck though :)

---

### Post by hums07 on 2008-05-15
Luckily, Xubuntu 6.06 still works well in this old Dell - screen resolution 1024x768. I have tried many other distros and none has gone as far as Dapper.
Elive - won't boot
Puppy - fail to configure xorg, just xvesa with low resolution, not usable
Damn Small Linux - low resolution, not usable
Arch Linux - fail to configure xorg
PCFluxboxOS - won't boot

Well at least Dapper is still supported untill next year.

---

### Post by BlairKatu on 2008-05-25
I have found a workaround for the dpkg-reconfigure xserver-xorg error, 
live boot to ubuntu 7.10 (knoppix works too and probably just about any live boot) then copy the xorg.conf file from /etc/X11/ to a flashdrive, reboot to 8.04 and replace the xorg.conf file. (make sure to live boot with the same hardware).

Good luck

---

### Post by hums07 on 2008-05-28
Thank you BlairKatu for the brilliant idea.

As I said on my previous post, my Xubuntu Dapper works well in the machine. So I copied /etc/X11/xorg.conf from the running Dapper to a pendrive, then I installed Xubuntu Hardy, and replaced the xorg.conf. Now Hardy gives the correct screen resolution!

Note that at startup, the kernel complains that the chipset is too old so ACPI is forced. Also I still get the above error message (Error inserting battery....), nevertheless the machine works.

EDIT: I have tried the same xorg.conf to another linux distro but it didn't work. It said that it didn't recognize the "glint" driver. Then I see in the Dapper xorg.conf that it uses "glint" driver for the screen device. Dapper recognizes my screen device as "Texas Instruments TVP4020 [Permedia 2]". I attach my xorg.conf, in case it would be useful for some geeks.

---

### Post by pdwhittaker on 2008-06-13
SOLUTION: Add "exit 1" line to /usr/sbin/laptop-detect script, to force detection of desktop mode before reaching "modprobe battery" line.

BACKGROUND/DETAILS: I've had problems with the issues discussed above, using Hardy and an old (1999) BIOS that lacks ACPI support.  I'm trying to reconfigure xserver-xorg, but kept getting battery errors.  I tried the following things, without success

[LIST]
[*]"sudo aptitude purge acpi" (and then accepted the choice to remove the xubuntu-desktop package - see [>this post<]("http://ubuntuforums.org/showpost.php?p=1503448&postcount=6") if you don't know why that would be ok)
[*]Added "blacklist battery" to /etc/modprobe.d/blacklist
[*]Added "acpi=off" kernel parameter in /boot/grub/menu.lst
[/LIST]

So I had a look into what was happening under the hood, by running ```
sudo strace -fF dpkg-reconfigure -phigh xserver-xorg 2> strace-output.txt
```

Searching through strace-output.txt I could see that a call to "modprobe battery" was being made from the /usr/sbin/laptop-detect script.  I tried removing the laptop-detect package, but this appeared to be depended on by many other things and I didn't want to force it, so I patched the script instead.

I added a line reading "exit 1" to the start of /usr/sbin/laptop-detect, so that it never reached the line reading "/sbin/modprobe battery || true", which was where the problem was.  (I suspect this is the reason that blacklisting it doesn't work, since modprobe is being explicitly asked for this module.)  The easiest place to add the extra line is on the second line of the script, right after the #! line: this makes the start of the file look like this:

```

#!/bin/sh -e
# HACK TO WORK AROUND ACPI BATTERY PROBLEM
exit 1
# END HACK

....[rest of script]....
```

I actually put it on line 39, after the option handling had been properly taken care of, just to be on the safe side.  (This put it just before the "#Are we a mac?" line.)  If you know what you're doing and have more time for this, you could take a look at the ACPI logic around line 65 and do something a little bit more subtle instead.  The exit value 1 is used to indicate that a desktop machine was found, not a laptop.  Since I'm always running this on a desktop (it's not on a bootable USB stick, for example) I know this will always be the case.

If that script editing sounds too complicated, but you a) know how to use sudo, and b) trust me ;-), cut and paste this into a terminal instead:

```
echo -e '/Are we a mac\ni\n#FORCE DESKTOP DETECTION\nexit 1\n\n.\nwq' | sudo ed /usr/sbin/laptop-detect
```

---

### Post by robinPain on 2008-07-16
I let the latest update replace my menu.lst and then I got the above "Error inserting battery..." error when trying to run

sudo dpkg-reconfigure -phigh xserver-xorg

Changing the
acpi=off
to
acpi=force
in menu.lst

seemed to be the thing that then allowed Ubuntu to reconfigure xorg.conf the way it wanted and then System->Preferences->Screen resolution provides a huge list again.

But 
System->Administration->NVIDIA X Server Settings still report

"You do not appear to be using the NVIDIA X driver...(just run nvidia-xconfig as root)..."

And then when I do that I get:

"Data incomplete in file /etc/X11/xorg.conf..."Configured Video Device" must have a driver line."

and it write a new xorg.conf and then when I restart I get the "Ubuntu is running in low-graphics mode" palaver so I configure that to "Generic" "LCD Panel 1280x102" then OK then OK - it comes up in low-res then I power/down/up and all is well. In other words don't do that! (don't do nvidia-xconfig).

Also when I do the
sudo dpkg-reconfigure -phigh xserver-xorg
I get an:
"xserver-org postinst warning: overwriting..."
i.e. not the original "Error inserting battery..." and again that overwrites xorg.conf but after a power/down/up it start OK in high-res.

SUMMARY
both dpkg-reconfigure... and nvidia-xconfig made no difference but acpi=force did the trick. (It stopped the "Error insering battery..."

---

