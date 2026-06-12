---
title: "HARD lockups (external network card related...)"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by arrrghhh on 2007-10-13
ok... so i have been LOVING ubuntu ever since I switched from windows.  I went so far as to switch over all my systems to it, work and personal.  my boss is nice enough to let me do such things, so long as it doesn't interfere with my work.  so far all i need my VM for is our phone system, which is no big deal.

now here comes the problem that is crippling me... the laptops we use in the field are dells, which have relatively strong screens and cases, but unfortunately seem to have an Achilles heel in the network card and hard drive areas...  so this laptop has had a netgear PCMCIA network card in it since i got the beast, and the internet network card has never worked (for me).

so ubuntu did a WONDERFUL job of detecting the device, i didn't have to do anything there.  kudos.  now i was out in the field the other day, and i was having issues getting a link from one of our canopy antennas.  so my boss suggests pulling the card out and popping it back in.  the SECOND i pull that card, the system locks.  i mean LOCKS.  won't respond to any keystrokes (ctrl-alt-del included) so i am forced to hold the power button for 8 secs until it shuts off, then i power it back on.

everything else with linux has 'just worked' (for the most part) with hardware at least.  also, i have NEVER seen anything lock up linux like this before!  i've had programs crash or start acting strange, but the base linux OS was still fine, i was still able to interact with it like nothing was wrong.  which i simply adore, because this is not true in windows.

does anyone have some ideas as to why the external network card would make the system crash so hard?  it runs wonderfully when i just leave the network card in it.  thanks!

note: i just upgraded from feisty to gusty hoping this would fix the issue... and it has not.

---

### Post by ofb on 2007-10-16
Can't help with the network card, but should mention Ctrl-Alt-Backspace is the combination to restart Gnome.  (Starts you back at the Login screen - it's not a full reboot of the computer, just your session. Often that's enough.)

Ctrl-Alt-Del doesn't do anything in Ubuntu by default. Some people configure it to bring up the System Monitor. IIRC, in Kubuntu you get the shutdown options panel.

And yes, Ubuntu can crash, soft and hard. I've had full lockups a few times, though it's rare.

When only an app freezes, the easiest way to kill it is to right-click the panel entry (panel = 'tool bar') for the app and select Close. That'll bring up a Wait/Kill dialog faster than it takes to start System Monitor.

If you get stuck with no replies, try digging through your logs for a key phrase to google with.
 [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by arrrghhh on 2007-10-16
thanks, i already knew the ctrl-alt-backspace to restart the window manager

the other suggestion about apps freezing doesn't apply since i use xfce.

and ctrl-alt-del reboots my machines in a hurry!  so long as they're not locked up.

i haven't had a hard lock in a while now - but i always keep the network card in the pcmcia slot... hopefully that is the key.  my boss is still hounding me to switch back to windows, i'll probably end up dual-booting and just using linux when he's not around (which is 90% of the time since i work alone in the field usually...)

thanks!

---

