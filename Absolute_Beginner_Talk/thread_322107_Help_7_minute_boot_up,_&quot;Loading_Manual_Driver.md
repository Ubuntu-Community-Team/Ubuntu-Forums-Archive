---
title: "Help: 7 minute boot up, &quot;Loading Manual Drivers...&quot;"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by tuco penguin on 2006-12-20
New user, loving my new dual boot Edgy install.  However, Ubuntu takes a long time to boot up which is frustrating.  During the boot sequence, it appears to hang with a long hex string or array on the screen.  If you are patient (say you go take a shower) then eventually it says something like "Not fixing this problem" and continues to boot normally.  I have located the problem in my boot log, and it seems to happen when loading manual drivers--see the 7 minute delay in the boot log below:

```
Dec 19 11:42:40 rcS:  * Reading files needed to boot...       [80G 
[74G[ ok ]
Dec 19 11:42:41 rcS:  * Setting preliminary keymap...       [80G 
[74G[ ok ]
Dec 19 11:42:41 rcS:  * Preparing restricted drivers...       [80G 
[74G[ ok ]
Dec 19 11:42:41 rcS:  * Starting basic networking...       [80G 
[74G[ ok ]
Dec 19 11:42:41 rcS:  * Starting kernel event manager...       [80G 
[74G[ ok ]
Dec 19 16:42:45 rcS:  * Loading hardware drivers...       [80G 
[74G[ ok ]
Dec 19 16:42:45 rcS:  * Loading manual drivers...       [80G 
[74G[ ok ]
Dec 19 16:49:42 rcS:  * Mounting local filesystems...       [80G 
[74G[ ok ]
Dec 19 16:49:42 rcS:  * Activating swapfile swap...       [80G 
[74G[ ok ]
Dec 19 16:49:47 rcS:  * Configuring network interfaces...       [80G 
[74G[ ok ]
Dec 19 16:49:48 rcS:  * Setting up console font and keymap...       [80G 
[74G[ ok ]
Dec 19 16:49:53 rc2:  * Loading ACPI modules...       [80G 
[74G[ ok ]
Dec 19 16:49:53 rc2:  * Starting ACPI services...       [80G 
[74G[ ok ]
Dec 19 16:49:53 rc2:  * Starting system log...       [80G 
```

System configuration is AMD Athalon 1800/256MB/80GB dual boot (WinXP/Edgy) with AGP GeForce FX 5200 video.  To get things working I did have to go through the X reconfiguration utility and manually enter the BUS ID of my video card because it didn't seem to be detected.  Don't know if this is related.

I'm not sure where to go next.  Any ideas?  I would like to boot in under 8 minutes.  Thanks for your help.

---

### Post by po0f on 2006-12-20
tuco penguin,

I hate to tell you this, but only you can figure out this problem.  Some piece of hardware in your computer is causing this long delay in your boot speed.  A work-around is to Ctrl-C *immediately* when you get to that step in the boot process (yes, you are going to have to do that each boot if you want a faster boot time).

---

### Post by towsonu2003 on 2006-12-20
can you:
open a terminal,
```

dmesg >> ~/Desktop/dmesg.txt
cat /var/log/syslog >> ~/Desktop/syslog.txt
cat /var/log/messages >> ~/Desktop/messages.txt

```

but, please do this right after a boot or reboot :)

than just attach those files (which are on your desktop) here. Let's try to find which module is the culprit :)

---

### Post by tuco penguin on 2006-12-20
Thanks for the help!  I will try to do this and post the results tomorrow.  Your help is much appreciated!

---

### Post by tuco penguin on 2006-12-20
Rebooted this morning, copied the log files.  However, log files are too large to attach here--board limits me to 19.5 kB.  dmesg.txt is the only one small enough :-k

Would a certain chunk of the log help?  Syslog is just 30 kB, Messages.txt is 300 kB though.  Are there some red flags I can look for myself?

BTW--Ctrl + C did not help during this morning's bootup.  My only option was to wait it out...

---

### Post by tuco penguin on 2006-12-20
This part of the syslog seems possibly relevant...

```
Dec 20 09:27:27 billy-u-poet kernel: [17180023.096000] Bluetooth: RFCOMM TTY layer initialized
Dec 20 09:27:27 billy-u-poet kernel: [17180023.096000] Bluetooth: RFCOMM ver 1.7
Dec 20 09:27:27 billy-u-poet anacron[4369]: Anacron 2.3 started on 2006-12-20
Dec 20 09:27:27 billy-u-poet anacron[4369]: Normal exit (0 jobs run)
Dec 20 09:27:27 billy-u-poet /usr/sbin/cron[4395]: (CRON) INFO (pidfile fd = 3)
Dec 20 09:27:27 billy-u-poet /usr/sbin/cron[4396]: (CRON) STARTUP (fork ok)
Dec 20 09:27:27 billy-u-poet /usr/sbin/cron[4396]: (CRON) INFO (Running @reboot jobs)
Dec 20 09:32:38 billy-u-poet gdm[4061]: Couldn't authenticate user
Dec 20 09:32:43 billy-u-poet gconfd (craig-4529): starting (version 2.16.0), pid 4529 user 'craig'
Dec 20 09:32:43 billy-u-poet gconfd (craig-4529): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
```

---

### Post by towsonu2003 on 2006-12-20
sorry, I just couldn't find anything. don't know about the "not able to authenticate" issue... 

what I would do is, reboot your computer and note the time. when it gets stuck, note the time again. then open the three log files in three terminals:
```

cat /var/log/syslog| less
cat /var/log/messages| less
dmesg| less

```

page up and down will scroll up and down the lines...

try to find your latest reboot in syslog (press <end> on the keyboard, and then go up using <page up>, and especially the lines with the timestamp that is similar to what you noted when the boot got stuck previously. Then try to compare the three log files referring back and forth between the lines.

I know I couldn't explain it...

What I expect is that it is trying to load a module or enable some feature but for some reason it can't. So it times out after a while and boots. Try to find that feature or module, than may be you can solve the problem by either disabling it or searching around for a way out.

---

### Post by po0f on 2006-12-20
tuco penguin,

While the boot is stalled at that one step, is there a lot of hard disk activity going on?  maybe it is doing an fsck every boot.  The only reason I ask is because of this line:
```
[FONT="Courier New"]Dec 20 **09:27:27** billy-u-poet /usr/sbin/cron[4396]: (CRON) INFO (**Running @reboot jobs**)
Dec 20 **09:32:38** billy-u-poet gdm[4061]: Couldn't authenticate user[/FONT]
```
(Bold is mine, obviously.)


towsonu2003,

```
[FONT="Courier New"]$ less /var/log/messages
$ less /var/log/syslog[/FONT]
```

;)

---

### Post by towsonu2003 on 2006-12-20
hmm, also try this (you will be modifying boot arguments temporarily for one boot only) to find exactly where it hangs:

    * Boot-up computer
    * If GRUB menu is hidden, press 'Esc' to enter the GRUB menu
    * If GRUB password is set, press 'p' to unlock the GRUB menu
    * Select the upper line where it will say something like

Ubuntu, kernel ......

    * Press 'e' to edit the commands before booting
    * Select 

kernel /boot/vmlinuz-<somethingsomething-numbers> root=/dev/blabla ro **quiet splash**

    * Press 'e' to edit the selected command in the boot sequence
    * Delete the two words "quite splash" so the line will read:

kernel /boot/vmlinuz-<somethingsomething-numbers> root=/dev/blabla ro

    * Press 'b' to boot 

Note that the only thing you need to edit is in bold :) you will see a bunch of lines scrolling by, and at one point it will stall. note what it is trying to do :mrgreen: ctrl+c might help this time if you finished noting the stuff on the screen.


[source]("http://ubuntuguide.org/wiki/Ubuntu:Edgy/BootMenu#How_to_modify_kernel_boot-up_arguments.2C_to_gain_root_user_access")

PS. thanks po0f :)

---

### Post by tuco penguin on 2007-01-17
po0f:

The hard drive is actually not active during the delay.

Apologies for the delayed response... since the system still boots and rarely requires rebooting, solving this has taken a back seat to other issues.  I have some time to deal with this right now.

---

### Post by tuco penguin on 2007-01-17
towsonu2003:

Thanks for the tips.  The bootup info scrolls past pretty quickly, and is mid-array when it hangs (as described in the opening post for this thread.)  This is the same array that is eventually shown when booting with the quiet splash activated, so there's nothing new there.  Unfortunately, I am unable to scroll up and see what the system was doing just before this massive array began scrolling past.  Arrow keys, page up keys... none seem to help--I cannot scroll back up.  Is it some sort of hardware probe?

However, I have noted that the last number displayed in the array is 439:  (The format seems to be ###:<hexadecimal>, where ### is a three digit decimal number and <hexadecimal> is some hex value in a length I cannot recall, then a few spaces and another set of values.  There is no hex value displayed with 439 though.)  This is reproducible--it always hangs on the same number in what appears to be a long array.  And as I noted above, the hard drive is eerily silent (no activity LED either) during  the long pause.  And ctrl+C still does not do anything.

What is the difference between "Loading hardware drivers" which seems to complete just fine and "Loading manual drivers" which is when the problem occurs?  If these are optional devices, is there some central place I can go to try individually disabling them one at a time?

Again, I apologize for the delayed response... since the system still boots (eventually) and rarely requires rebooting, solving this has taken a back seat to other issues. I have some time to deal with it this week.

---

### Post by tuco penguin on 2007-01-29
I finally figured this one out myself and am posting the result here in case it helps someone else some day.

Somehow I got the notion that the delay was happening near the time when hard drives were being mounted (from what I could see during bootup with the quiet splash option disabled--see towsonu2003's instructions above).  I have an old FAT32 slave drive that stores some really old windows data.  It is hdb1 and successfully mounts to /windows/f, but I tried disabling this in /etc/fstab and the machine boots in about 30 seconds now... of course without access to that drive.  That's OK, I haven't accessed anything from that drive in years, except to backup the things that might have been important.  It's probably time to reformat it and repurpose it in a print server or MythTV box or something...

```
# /dev/hdb1
#UUID=0B4A-1301  /windows/f      vfat    defaults,utf8,umask=007,gid=46 0       1
```

Since I always like to understand how things work, any comments about what might be wrong with the above line in fstab are welcome, but I don't intend to bang my head trying to get this drive to mount cleanly.  I was kind of impressed that I was able to access any of my windows data at all from ubuntu when I made the switch, and I still can access all the data on my primary windows drive.  Strange that there was no visible hard drive activity during my long bootup delay, though.

An interesting side effect--my other nagging problem with this machine was also solved:  I have a networked samba share that would not mount on startup, but mounted fine with manual script execution or even a "mount -a" from a command line AFTER startup once I had it listed properly in fstab.  With the fat drive commented out of fstab, that samba share mounts on startup just fine!

Thanks to Po0f and towsonu2003 for your helpful comments.

---

