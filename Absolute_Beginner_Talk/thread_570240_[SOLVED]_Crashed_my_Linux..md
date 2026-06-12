---
title: "[SOLVED] Crashed my Linux."
date: 2007-10-08
forum: Absolute Beginner Talk
---

### Post by jeff4760 on 2007-10-08
I installed Kubuntu on my desktop the other day and today I was updating the nvidia drivers.  I have the nvidia 7600 GT edition.  I was able to see everything clearly ( graphics, color, resolution, ect.) with my install but I assumed I still needed the drivers.  I followed the instructions on the Kubuntu setup, along with adding two sudo commands in the command line.  I rebooted Linux ( not the computer) and it repeated the Kubuntu logon screen then went the a black screen.  The only thing that was there was a blinking indicator.  I rebooted the machine and still the same- no login.  I don't know if I am supposed to type anything else, or I killed my install of Linux.  Either way I just need to know what I possibly did wrong, and if I have to install Linux again, what I can do to avoid this again.

Here's the link for the documentation on installing the nvidia drivers: [https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/hardware.html#graphics-cards]("https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/hardware.html#graphics-cards")

Thanks.

---

### Post by djchandler on 2007-10-08
> **jeff4760 said:**
> I installed Kubuntu on my desktop the other day and today I was updating the nvidia drivers.  I have the nvidia 7600 GT edition.  I was able to see everything clearly ( graphics, color, resolution, ect.) with my install but I assumed I still needed the drivers.  I followed the instructions on the Kubuntu setup, along with adding two sudo commands in the command line.  I rebooted Linux ( not the computer) and it repeated the Kubuntu logon screen then went the a black screen.  The only thing that was there was a blinking indicator.  I rebooted the machine and still the same- no login.  I don't know if I am supposed to type anything else, or I killed my install of Linux.  Either way I just need to know what I possibly did wrong, and if I have to install Linux again, what I can do to avoid this again.

Here's the link for the documentation on installing the nvidia drivers: [https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/hardware.html#graphics-cards](https://help.ubuntu.com/6.10/kubuntu/desktopguide/C/hardware.html#graphics-cards)

Thanks.

Something is hanging the X server, not sure what it could be. Do a search in the threads for "X server will not start." This is not a unique situation.

Try the 3-key combination "ctrl-alt-backspace" to restart the X server instead of re-booting. You may have clobbered the file system by re-starting without a proper shutdown.

If you ever get stuck like this again and nothing responds, simulate a power failure, i.e., turn off the power switch on your surge suppressor or computer power supply. Don't hit the re-set button. Hard drives with power can still write, and may do so in random spots.

DJ

---

### Post by jeff4760 on 2007-10-08
i think I fixed this for now using a note in this thread: [http://ubuntuforums.org/showthread.php?t=565762&highlight=installing+nvidia+drivers]("http://ubuntuforums.org/showthread.php?t=565762&highlight=installing+nvidia+drivers")

---

