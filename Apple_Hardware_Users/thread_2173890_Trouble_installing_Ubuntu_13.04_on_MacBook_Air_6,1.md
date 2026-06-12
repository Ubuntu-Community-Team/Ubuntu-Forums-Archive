---
title: "Trouble installing Ubuntu 13.04 on MacBook Air 6,1 11&quot; (A1465)"
date: 2013-09-11
forum: Apple Hardware Users
---

### Post by gettingbored on 2013-09-11
I've been trying to install Linux on my MacBook Air Mid 2013 11" (6,1 Model: A1465) for a little while now. My end goal is a penetration testing distrobution such as [Kali]("http://www.kali.org/"), which I believe is based on Ubuntu. However my initial attempt failed so I tried to install BackBox linux on the machine, which worked to some degree. However the install wasn't stable and there were various problems. You can read what I went through here: [https://forum.backbox.org/general-support/installation-on-macbook-air-6-1-(mid-2013)/](https://forum.backbox.org/general-support/installation-on-macbook-air-6-1-(mid-2013)/)


So I decided to take a few steps back and get a grasp on installing regular Ubuntu onto the machine alongside OS X. 

I was following the super vague guide here: [http://www.miek.nl/s/37ebe31bd0/](http://www.miek.nl/s/37ebe31bd0/) where the author said he got it up and running, Wi-Fi included on my same machine.
This is what happened when I tried to install...

- First I booted into OS X, and made a Time Machine backup of my system
- Then I opened Disk Utility and on the left side selected the "ubuntu-13.04-desktop-amd64.iso" and clicked "Burn" at the top.
- The burn completed, verified, and mounted on the desktop
    - When trying to mount it said "The disk you inserted was not readable by this computer"
    - So I clicked "Ignore"
- I rebooted into an OS X install drive by holding option
- I used the Disk Utility app on the install drive to erase my disk
    - I selected the root of the drive on the left and went to the partition tab
    - I chose 2 partitions:
        1: Mac OS X Extended (Journled) 230 GB
        2: Free Space 21 GB
    - Applied partitions, done
- Then I reinstalled Mountain Lion onto the first partiton
    - Install went fine
    - Transferred files back to the partition after install completed
    - Before moving everything back I looked at the "Users" portion of the time machine backup
    - There was a "Fink build system" entry or something similar so I unchecked that
- Start up, boot into OS X and everything seems fine
- Reboot, hold option, I see rEFIt is still there from before I restored
- Reboot into OS X and follow the uninstall instructions here: [http://refit.sourceforge.net/doc/c1s3_remove.html](http://refit.sourceforge.net/doc/c1s3_remove.html)
    - I removed the /efi partition
    - I removed the /Library/[COLOR=#000000][FONT=Lucida Grande]StartupItems/[/FONT][/COLOR][FONT=Lucida Grande][COLOR=#000000]rEFItBlesser[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- Reboot, hold option, now I see:[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - OS X Install[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Recovery 10.8.4 (Install must have put that there)[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Windows (with a disk icon)[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - EFI Boot (with a disk icon)[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - EFI Boot (with a disk icon) (Yes, there were two of them)[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I chose "Windows" (with the disk icon) and then I get a black screen with blinking underscore[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- A bunch of text is scrolling by, some of which I managed to copy down:[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]```
udeud [119]: timeout killing '/sbin/blkid' -o udev ... (missed the rest)
```[/COLOR][/FONT]

[FONT=Lucida Grande][COLOR=#000000]- Ubuntu splash screen shows up and looks like it's loading[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- A welcome dialog shows up and I click on "Install Ubuntu"[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- At this point I plug in a ethernet -> USB dongle, but it won't recognize I'm connected to the internet[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I move on with the install, clicking "Continue"[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I select "Install Ubuntu alongside Mac OS X" then click "Install Now"[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I select my time zone, keyboard layout, and set up the user account[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- At the bottom it says "Copying files..."[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- After a while a dialog box pops up and it says "Installation complete" and I click "Reboot Now"[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - The CD is ejected[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - The keyboard backlight is still on[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - I unplug the external CD drive[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Then I unplug the ethernet -> USB dongle[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - I press the down arrow and a bunch of text scrolls past the screen super quick and the computer reboots[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- Boot holding option, I now see three choices:[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Mac OS X[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Windows[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - Recovery 10.8.4[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- Select Windows[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I get dropped to a GRUB window[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]- I press "e" to edit the default GRUB profile[/COLOR][/FONT]
[FONT=Lucida Grande][COLOR=#000000]    - [According to Miek]("http://www.miek.nl/s/37ebe31bd0/"), you need to append "**nosmp**" to the kernel boot parameter or it won't boot up
    - I add "**nosmp**" to the **end** of the following line:
```
linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=388d53ce-ddab-44e9-a8ea-ob31105f772f ro    quiet splash $vt_handoff
```
- Then I press F10 to boot
- I get a black screen with a blinking [B]_
[/B]- Then I got what looked like an error but didn't have time to write it all down, here's what I scribbled:
```
Gave up waiting for root device
```
- Then it drops me to a **(initramfs)_ **prompt
- While I was copying down the error it started to scroll some lines again, most of the looking very much just like this:
```
'/sbin/blkid -o udev -p /dev/sda1' [222] terminated by signal 9 (killed)
```
- Then the scrolling stops and I'm back at the **(initramfs)_ **prompt
- I typed **exit **and this was displayed:
```

Gave up waiting for root device. Common problems:
    - Boot args (cat /proc/cmdline)
        - Check rootdelay= (did the system wait long enough)
        - Check root= (did the system wait for the right device?)
    - Missing modules (cat /proc/modules; ls /dev/)
ALERT! /dev/disk/by-uuid/388d53ce-ddab-44e9-a8ea-0b31105f772f does not exist
Dropping to a shell!

BusyBox v1.20.2 (Ubuntu 1:1.20.0-8ubuntu1) built-in shell (ash)
Enter 'help' for a list of built in commands

```

- I reboot holding option, choose Windows and then at GRUB press '**e**' to edit the default option
- At the end of: 
[/COLOR][/FONT][COLOR=#000000][FONT=Lucida Grande]```
linux    /boot/vmlinuz-3.8.0-19-generic root=UUID=388d53ce-ddab-44e9-a8ea-ob31105f772f ro    quiet splash $vt_handoff
```[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]
I add 
```
nosmp rootdelay=90
```
and very briefly on the screen I see something like:
```

Booting a command list
Could not find command

```
then a bunch more of that timeout, and killing as before, then I'm dropped into that same BusyBox shell as before so I reboot.

- Reboot, holding option, Windows > GRUB, '**e**' to edit default option and add
```
acpi=off
``` 
to the end of the kernel line (assuming the kernel line is the one I've been editing)
- Booting up gives me a kernel panic

[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]- Reboot, holding option, Windows > GRUB
[/FONT][/COLOR][COLOR=#000000][FONT=Lucida Grande]- In GRUB, select the advanced options, then select:
```
Ubuntu, with Linux 3.8.0-19-generic(recovery mode)
```
it locks up when at this line:
```
[    0.090497] smpboot: Booting Node 0,    Processors #1
```

- Reboot, holding option, Windows > GRUB
- In GRUB, selected advanced options, then recovery mode, pressed '**e**' to edit the options
- Added **nosmp**to the end of the kernel parameters 
- Failed to boot, gave me this error:
```
udev[103]: '/sbin/blkid -o udev -p /dev/sda2 [215] terminated by signal 9 (killed)
```



Now, I'm not exactly sure what to try next. I've Googled just about everything I can think of. 
It's going to be hard to figure this out I'm guessing since it's probably specific to the hardware or something like that. However if anybody has any suggestions I'm down to try them. 
Let's figure this out people! :)[/FONT][/COLOR]

---

### Post by Sean_V_Kelley on 2013-09-17
See this:

[http://www.miek.nl/blog/archives/2013/08/31/macbook_air_61_2013_model_with_ubuntu/index.html](http://www.miek.nl/blog/archives/2013/08/31/macbook_air_61_2013_model_with_ubuntu/index.html)

---

### Post by Quackers on 2013-09-17
Is 388d53ce-ddab-44e9-a8ea-0b31105f772f the UUID of the partition you have installed Ubuntu to? Which is /dev/sda2 - correct? I would have thought /dev/sda2 was your Mac OSX partition.
It's often wise to boot the cd/usb and select try Ubuntu first so that you can then experiment with boot arguments before installation - so you'll know what is needed.

---

