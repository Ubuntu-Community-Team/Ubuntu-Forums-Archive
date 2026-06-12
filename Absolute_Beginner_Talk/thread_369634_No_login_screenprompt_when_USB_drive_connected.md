---
title: "No login screen/prompt when USB drive connected"
date: 2007-02-24
forum: Absolute Beginner Talk
---

### Post by Seine on 2007-02-24
Hi.

If I leave my USB drive connected when powering up, GRUB will fire up, Ubuntu will load all the way up to the time when it should show a login prompt. All I get though is a full screen terminal, with no prompt. Just a blinking underscore cursor. 

At this stage I can type, and it appears on the screen, but nothing has any effect. It's a like a shell that does nothing.

When I press CTRL-ALT-DEL I'm notified that processes are killed. If I keep pressing it I'm eventually told that the CTRL-ALT-DEL process is respawning too quickly. 

In the end my only option is to powerdown and unplug the USB drive before booting again.

Does anyone know what this is about and how I can fix it?

Thanks
Seine

---

### Post by n8bounds on 2007-02-24
Wow....that's crazy...I'm going to have to try that. 

Can you hit CTRL ALT F2  during this time to get a differnt tty than the one gdm was trying to use?  

Look at /var/log/syslog   and /var/log/messages   and /var/log/Xorg.somethingoranotherfile next time you boot normally (w/o the usb drive)...maybe post them here right after doing your little usb key trick if you cant find anything fishy therein...

---

### Post by Seine on 2007-02-28
Thanks for your reply. This behaviour was consistent. But since I wrote this post it happened only on the first reboot and never since. :confused: :) 

That first time it happened I hit ctrl+alt+f2 and it responded with an immediate shutdown (repleat with Ubuntu logo and progress bar).

The log files you mentioned showed nothing odd, as far as I could tell.

I will post back if it happens again.

Seine

---

