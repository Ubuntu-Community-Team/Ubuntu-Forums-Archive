---
title: "Graphical issues with 3.13.1 kernel on Ubuntu 13.10 on MBP 9,1"
date: 2014-01-30
forum: Apple Hardware Users
---

### Post by stephen23 on 2014-01-30
Hello,

I recently added an Ubuntu 13.10 installation to my OSX 10.9.1 and Windows 8.1 dual-boot on a MacBook Pro 9,1.

It  was hard to find documentation for installation on this model, as  everyone seems to be using the Retinas now. However, from what I was  able to find, I settled on this method, which seemed to work alright:

1. partition HDD in advance with OSX Disk Utility
2. Install from normal x64 Ubuntu ISO
3. Install bootloader to Ubuntu boot partition
4. This results in an EFI boot mode.

Everything was going smoothly, even WiFi was working fine. However, a couple of issues stood out:

1.  I don't think graphics are being accelerated. Not sure how to check  definitively, but I notice that notifyOSD notifications are opaque,  which is how I've told in the past.
2. The computer could not properly resume from sleep (I got a blank screen w/ cursor).

By  googling #2, I found someone saying updating to kernel 3.13 RC6 had  fixed the problem. The post was a bit out of date, so I searched and  found that the latest version on that branch was 3.13.1. So, I  downloaded that and installed it as detailed here.  [http://ubuntuguide.net/install-linux-kernel-3-13-1-rc1-in-ubuntu-13-10-13-04](http://ubuntuguide.net/install-linux-kernel-3-13-1-rc1-in-ubuntu-13-10-13-04)

After  installing the update, I found the sleep issue to indeed be solved.  However, a new problem, which I have had no luck in finding reference to  anywhere, emerged: I am now experiencing graphical "lag" everywhere. To  better explain: say I move my cursor quickly: a trail of cursor  "artifacts" is left behind; say I mouse over a button or menu item, or  press Select All: nothing initially appears to be highlighted, except  just around the cursor. In both these situations, moving my cursor  slowly over the area gradually fixes the problem, as if I were  "painting" the correct image back onto the screen with it. There is also  a degree of screen tearing when scrolling webpages. Obviously not  knowing what is selected and similar issues are not really usable in the  long run.

So, I need one of two things:
- A solution to the graphical problem in 3.13.1
-  A solution to the original sleep problem not involving the installation  of 3.13.1 (I can still access the previous kernel through GRUB and  uninstall the new one)

I also would like to make sure that I can  use accelerated graphics. One of the main things I will eventually be  doing on this installation is game playing/testing, which is a primary  reason I multibooted rather than virtualized (VMs always take a  performance hit). From what I can gather, EFI mode and NVidia's drivers  don't go well together atm. Is that the only way to accelerate on a MBP?

Thanks for any help!

---

### Post by stephen23 on 2014-02-05
bump

---

### Post by stephen23 on 2014-02-16
Bump again. Any help here?

---

### Post by Quackers on 2014-02-16
Does your 9,1 have dual graphics?
Have you tried the nvidia-current driver (if that's the one that supports your Nvidia card)?
I had EFI Ubuntu installed on my rMBP 10,1 and although it was a little fiddly (with changes to /etc/default/grub and nvidia.conf files) it ran well. I also needed to use "i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0&#8243;  in /etc/default/grub to keep the Intel graphics chip quiet.
Have a look at the thread below. It's not for your Mac but it may give you some ideas.
[http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/]("http://cberner.com/2013/03/01/installing-ubuntu-13-04-on-macbook-pro-retina/")

I appreciate that there may not be as much documentaion about your particular Mac but sometimes you just have to jump  ):P
Not hugely constructive, I know.

Regarding the sleep problem. As far as I'm aware the standard nouveau driver (for Nvidia cards) in Ubuntu renders the system unable to resume from sleep. The Nvidia drivers I've tried usually solve this.

---

### Post by stephen23 on 2014-02-16
Yes, I do have dual graphics in this model.

I do believe nvidia-current is correct for this model, but I haven't tried installing it due to the EFI-boot issues I was hearing of (I remember seeing people say that it rendered Ubuntu unbootable). It doesn't even show up in Restricted Drivers (I've assumed by design due to those issues).
I was actually thinking of switching to BIOS emulation and installing it, but for the life of me I can't find the instructions for switching boot modes I've bumped into multiple times when NOT looking for them... My next step was going to be to just reinstall with a +mac ISO and hope that the install procedure isn't different enough to mess up the currently functional multiboot.

...Oh, just noticed your edit. Alright. 10,1 and 9,1 are close to identical AFAIK, aside from the screen, so instructions *usually* work between them. Graphics are just the area that they don't always. I may as well try them, not like I have anything to lose atm. I'll just try installing into the 3.13.1 environment to start, as the lag thing is most likely driver-related (I remember reading that that kernel disagrees with some graphics drivers right now. No one mentioned my particular manifestation, is all.). If that doesn't work, I'll try again with the older one.

---

### Post by Quackers on 2014-02-16
It must be worth a try, but as I said earlier you will likely need the i915 line in /etc/default/grub and one or two of the others mentioned in that guide.
I'd leave it EFI to be honest.

---

### Post by stephen23 on 2014-02-17
Okay,

So I'm in Ubuntu trying to follow those instructions and have hit a snag in the last place I honestly expected to hit one...
"sudo: nvidia-xconfig: command not found"

That should be the same on any machine...

I did some googling, and I found several people having that problem after trying to reinstall or otherwise muck about with nvidia-current, but no one who gets that immediately after it's installed...
(Well, I found one person, but the solution was just to run "sudo apt-get install nvidia-settings" and "sudo dpkg-reconfigure nvidia-current" which didn't work (I wouldn't expect installing -settings to work, as the xconfig command is part of -current))

Any clue why that command wouldn't be working?

I checked and I really don't have a xorg.conf, so it's not like it was magically created by the package installation or anything.

---

### Post by Quackers on 2014-02-17
You won't have a xorg.conf until sudo nvidia-xconfig has run and saved the file. I'm assuming you didn't have the  " : " after sudo when you ran the command? (As shown).

---

### Post by stephen23 on 2014-02-17
No, I ran the commands without the colons, they were from the error output.

And I know that xconfig is what creates the xorg.conf, I was just double checking.

---

### Post by Quackers on 2014-02-17
Ok, try running ```
sudo apt-get install nvidia-common
``` and when it's installed try xconfig again.

---

### Post by stephen23 on 2014-02-17
-common installed okay but still no dice on xconfig...
*head scratch*

---

### Post by Quackers on 2014-02-17
I haven't seen this before but after some googling I found this from 2011 which might be worth a try
[http://linux.granularproject.org/wiki/en/%22nvidia-settings%22_and_%22nvidia-xconfig%22_commands_not_working]("http://linux.granularproject.org/wiki/en/%22nvidia-settings%22_and_%22nvidia-xconfig%22_commands_not_working")

---

### Post by stephen23 on 2014-02-17
Didn't work either.

However, I looked in those directories. I simply have files missing...
There is NO nvidia-current folder in usr/lib/

I tried sudo apt-get install --reinstall nvidia-current. No dice. Folder still not there.
So I've found the problem.... but why would that folder just be missing?

---

### Post by Quackers on 2014-02-17
That sounds like it hasn't fully installed though your later commands should have fixed it.
I don't know what to suggest really. Obviously you could install the driver direct from the Nvidia site but you'd need to reboot to do that iirc and you might then have to edit the files via tty (if it won't boot to a desktop). Though that's not necessarily the end of the world  :)

---

### Post by stephen23 on 2014-02-17
Yeah. Well I'll try purging nvidia-current, doing another update to be safe, and reinstalling from scratch. If that doesn't work, I'll purge the other packages and try direct from NVidia. If THAT doesn't work... then this might be the Twilight Zone or something because really it should be working now.

---

### Post by Quackers on 2014-02-17
lol, good luck to you :D

---

### Post by stephen23 on 2014-02-17
Figured it out! When I reinstalled, I noticed it wasn't creating an "nvidia-current" folder; it was using a version number instead of "current." The folder was called nvidia-304 (which, when I looked back in the apt-get output, was the version number installed). Why the xconfig command wasn't added to the path, I don't know, but calling it via the path, using 304 instead of current, worked. Moving on with the other instructions.

---

### Post by stephen23 on 2014-02-17
Now I just have a question. The instructions are a little unclear as to how I should insert the line into my grub file.
Should it look like this:
GRUB_CMDLINE_LINUX_DEFAULT="quiet &#8220;i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0&#8243; splash"

EDIT: Nvm, found answer here: [http://ubuntuforums.org/archive/index.php/t-2182943.html](http://ubuntuforums.org/archive/index.php/t-2182943.html)

It's GRUB_CMDLINE_LINUX_DEFAULT="quiet i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0 splash"

---

### Post by stephen23 on 2014-02-17
Well rats. No idea what went wrong, everything was followed to the letter, but after completing all the steps (which were also identical to the ones used by the person linked above who did have a 9,1), I boot to a TTY. X won't start.
startx gives the error "Fatal server error: (EE) no screens found(EE)"

Looking through the log file, the first error I see is "Failed to load module "nvidia" (module does not exist, 0)
Toward the end is also "Screen(s) found, but none have a usable configuration"

In the middle of the log, at a couple places, are also these:
(WW) Falling back to old probe method for modesetting
(EE) open /dev/dri/card0: no such file or directory
(WW) Falling back to old probe method for fbdev

and this:
(EE) VESA(0): V_BIOS address 0xd00 out of range

---

### Post by Quackers on 2014-02-18
In mine it's
"quiet splash i915.lvds_channel_mode=2 i915.modeset=0 i915.lvds_use_ssc=0" 
which I suspect is correct.

Did you also edit xorg.conf Devices section?

DId you sudo update-grub after changes? Just checking  :)

---

### Post by stephen23 on 2014-02-18
I did edit xorg.conf after it was finally created and I did sudo update-grub.

I will try (and probably fail) to remember how to use Vi (and then probably just use a live environment, instead) to edit my grub file to look like yours. Hopefully that will work.

Pre-post-edit: Actually, while I'll still try that, I think I may have found the actual issue: [https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268771](https://bugs.launchpad.net/ubuntu/+source/nvidia-graphics-drivers-331/+bug/1268771)
Looks like driver version 331 is the earliest that works with 3.13.1 After more googling to educate myself, nvidia-current is the version released with the 13.10 code freeze. nvidia-current-updates is the latest version approved for update distribution. I'll have to look at its version number in the repo (which I honestly will have to figure out how to do from the terminal), but if it's 331 or newer, that'll probably be my fix. If it's not that new, I'll need to figure out what the lowest branch is that is at that version.

EDIT: [http://packages.ubuntu.com/saucy/nvidia-current-updates](http://packages.ubuntu.com/saucy/nvidia-current-updates) Alright, so not at that version. Unless they fixed it for everyone. So trying to find 331 somewhere...

---

### Post by Quackers on 2014-02-18
Interesting. I think the nvidia-current driver is 304 iirc, which is quite old.
Good luck sir :)

---

### Post by stephen23 on 2014-09-03
Rather old thread, I know, but I just felt I should give it some closure for anyone who might come across it (I know I would thank many an OP for doing the same...).

Getting this working got pushed to the backburner for far too long, but the simple story is that that actually helped. 14.04 has NVidia 331 available directly through the Other Drivers window, so everything went swimmingly from there.

---

