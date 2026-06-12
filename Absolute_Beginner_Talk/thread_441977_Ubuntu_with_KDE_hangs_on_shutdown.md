---
title: "Ubuntu with KDE hangs on shutdown"
date: 2007-05-13
forum: Absolute Beginner Talk
---

### Post by doriard on 2007-05-13
Ubuntu Fiesty Fawn, with KDE installed hangs (forever) every time I try to shutdown or restart.  It seems to boot up and run okay, but it won't shutdown.  I have to do a hardware reset.    I didn't notice this happening immediately after installing KDE, but it is repeatable now.  I installed Java via Synaptic tonight (after trying several other methods of trying to get java to install), and that's the only other thing I remember doing before the problem started, but I'm not sure if it's related.  How can I identify the problem and fix it?

---

### Post by doriard on 2007-05-13
Anyone have an idea on this one?

---

### Post by Austin_KW on 2007-05-13
Edit the grub command when you boot up, remove the "quiet splash"

When you want to shutdown use a terminal session "ctrl-alt-F1"
login in and shutdown using the command line "sudo shutdown -h now"

Might tell you where it is hanging

---

### Post by doriard on 2007-05-13
Thanks for the reply.  I think I found it.  I uninstalled, via Synaptic, a java plug-in that seemed to be conflicting with the main Sun Java plugin.  It seems to be working okay now.

---

### Post by doriard on 2007-05-13
> **Austin_KW said:**
> Edit the grub command when you boot up, remove the "quiet splash"

When you want to shutdown use a terminal session "ctrl-alt-F1"
login in and shutdown using the command line "sudo shutdown -h now"

Might tell you where it is hanging


The hang on shutdown is back again.  I tried "sudo shutdown -h now" and it didn't hang when I shutdown that method.  When I shutdown via the KDE start menu it hangs.  Any more suggestions?

---

### Post by Meej on 2007-05-14
Hi there,

I'm experiencing the exact same problem with Kubuntu. Have had it for about 2-3 days now. It didn't do it when I first installed. Currently I am getting round it as I found using the shutdown command from the Konsole works fine (as you have also found).
Would I be right in assuming that all the KDE graphical shutdown button does is execute a 'sudo shutdown...' command in the background? If this is so then it must do something else that leads to the system hang. (sorry if thats totally wrong as I'm new to Linux). Looking at the [options] for the shutdown command nothing immediately pops out as being a potential cause but then I don't really know what to look for :confused: 

Over the last few days since I first got Kubuntu I have installed many additional packages so it's difficult to pin down what could be the cause. Looking back I think it might have started after I installed the ATi xorg display drivers for my Radeon Xpress 200M.

It's not really a major problem right now as I don't mind using the Konsole, but I'd sure appreciate any suggestions anyone has!

Thanks,
meej

---

### Post by Austin_KW on 2007-05-14
Ok, From memory so dont quote me on it

Kde calls poweroff/halt/reboot which are all the same program but the action changes based on the name
The /sbin/halt does some cleanup and then calls /sbin/shutdown (which works for you), I dont remember exactly what the cleanup is.

You can modify the program called at shutdown using kcontrol or (KDE menu ->system settings" -> advanced tab -> "login manager"  -> shutdown tab)
Here you can change the shutdown command to the one that works or modify the command options. "man halt" will give you the options to play with.

---

### Post by doriard on 2007-05-14
I found that shutdown actually occurs okay from the KDE start menu, it's only the "restart" that hangs.  I'm dual booting and I switch back and forth between WinXP using restart instead of shutdown.  In the login manager, Grub was not selected as the boot manager, which I added, but it didn't make any difference.  Are there any config files left over from Gnome that would cause this?

---

### Post by darylb on 2007-05-31
Hi,

I installed kubuntu (Feisty) on my laptop about a week ago and I am seeing this behaviour too. I also have been installing lots of packages recently so I wasn't sure what could have caused it, but I tried what doriard mentioned and removed these java packages that I had recently added:

> Commit Log for Thu May 31 21:53:31 2007

Completely removed the following packages:
sun-java6-bin
sun-java6-jre
sun-java6-plugin

Removed the following packages:
ubuntu-restricted-extras

After I removed those the restart and shutdown functions in KDE started working as normal again. Both restart and shutdown were affected for me, not just restart.

Is anyone else experiencing this?
Daryl

---

### Post by Austin_KW on 2007-05-31
One of my systems has started to do this hang on shutdown.  
It is happening when it atttempts to display the splash screen. 
It sometimes hangs, sometimes hangs with the monitor reporting sync errors or sometimes it looks like an unhandled exception is executed and it jump into the bios and warm restarts. 
Whatever is causing it, it looks like memory corruption somewhere.

I have disabled the "splash" from from my boot command options in /etc/boot/menu.lst, and for now at least, it is not hanging.

---

### Post by darylb on 2007-06-01
This is getting weirder. I tested it 2-3 times last night after removing the java packages, and it was restarting/shutting down fine. I wonder was I always doing warm reboots. That would explain why it doesn't do it today after a cold power off last night...

I had already disabled my splash screen Austin in hope of being able to see where it was hanging (it hung at a black screen, after seeming to have turned my laptop display off - ie it goes deep black rather than backlight-is-still-on black). Anyway it doesn't' appear to be related to the splash screen on my system.

However today the problem is back! I had a look into the sun-java6 packages again this morning, and installed/removed and rebooted several times. There seems to be a trend, although its not totally repeatable.

This procedure worked for me about three times (providing temporary relief), but doesn't seem to work every time:

1) Install these packages (I used synaptic):
  sun-java6-bin
  sun-java6-jre
  sun-java6-plugin

2) Restart with KDE menu - hangs for me and I have to power laptop off hard

3) Power on again, boot kubuntu & login again

4) Completely remove (including configuration files) the same packages:
  sun-java6-bin
  sun-java6-jre
  sun-java6-plugin

5) Restart will now work

I know this sounds like voodoo, but I guess it is possible that removing the java packages does something on the system that makes it work temporarily anyway. Either that or its just a coincidence. I tried to verify this with integrit to see what exactly changed on removal of java, but due to bug #82023, I couldn't run integrit :( I'll try compiling it myself or using the older working version if I get a chance.

Running /sbin/reboot on the Konsole works fine for me too, but I'd really like to figure this out!

---

